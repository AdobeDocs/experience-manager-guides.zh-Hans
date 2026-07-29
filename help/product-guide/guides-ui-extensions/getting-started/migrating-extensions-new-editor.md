---
title: 迁移编辑器2.0的扩展框架更改
description: 了解如何迁移到Editor 2.0的扩展框架
feature: Web Editor Configuration
role: Admin
level: Experienced
source-git-commit: 75954eab3ac1738705fe2a7280973af39b9214df
workflow-type: tm+mt
source-wordcount: '1904'
ht-degree: 0%

---


# 将扩展框架迁移到编辑器2.0（新编辑器）

本指南可帮助扩展作者了解将其自定义项从AEM Guides中的&#x200B;**旧编辑器**&#x200B;移动到&#x200B;**新编辑器**&#x200B;所涉及的操作，以便他们能够以最小的干扰顺利规划过渡。

>[!IMPORTANT]
> 
> 如果您现有AEM Guides扩展（旧编辑器），包括自定义上下文菜单项、工具栏按钮、对话框、属性或元数据逻辑或内容样式，本指南将帮助您保持该扩展可使用新编辑器。

## 概述

- **您的注册未更改**：继续使用`window.extension` / `tcx.extension.register`。
- **编辑器画布是新表面。**上下文菜单项必须声明新的构件ID
  `markup_editor_menu`；编辑器中的行为必须停止接触DOM。
- **停止读取/写入DOM**：将`tcx.curEditor.*` DOM访问权限替换为
  `guides.editor` API：[使用`runUtil(...)`](#migrate-reads-dom-runutil)读取，[使用`runCommand(...)`](#migrate-writes-dom-mutation-runcommand)写入，[样式使用装饰](#migrate-rendering-only-logic-dom-paint-decorations)，以及[通过应用程序事件运行全局操作（保存）](#migrate-global-actions-savefocus-app-events) 。
- **App-shell菜单（存储库、映射查看器、文件/文件夹）未更改**：它们仍在运行
旧版框架。
- **两个编辑器同时存在**：将两个编辑器与数组一起作为目标。 当无条件加载&#x200B;**注册**&#x200B;插件时；由`guides.editor.version`仅门&#x200B;*运行时*&#x200B;操作（在文件打开之前保持`1.0.0`，查看[安全检测编辑器和引导](#detect-the-Editor-and-bootstrap-safely)）。


## 为什么会改变？

| 标准 | 旧版CKEditor | 新建MarkupEditor |
|---|---|---|
| Source真相 | DOM | ProseMirror文档 |
| 选择区域 | 根文档上的`getSelection()` | ProseMirror选择（位置/范围） |
| 更改内容 | 修改DOM属性/类 | 发送命令（事务） |
| 呈现 | DOM是永久性的 | DOM是影子DOM中的临时渲染，可随时重建 |
| 样式 | Page或clientlib CSS | CSS通过寄存器插件注入影子DOM。 请参考[Hello world：仅CSS高亮插件](#hello-world-a-css-only-highlight-plugin)，以使用现有类并添加CSS；以及[迁移仅渲染逻辑](#migrate-rendering-only-logic-dom-paint-decorations)，以添加新类并添加样式。 |

任何更改DOM或任何DOM更改的扩展都不会保留，它们将在下次重新渲染时被清除。 迁移基本上是&#x200B;*从DOM-first移动到模型 — first*。

## 安全地检测编辑器和引导

全局`guides`对象是所有新集成的入口点：

```js
guides.editor    // editor interaction APIs
guides.util      // bundled utility libs (lodash, async)
guides.ready(cb) // fires once at app load (view system ready) — before any file is open
```

`guides.editor.version`报告&#x200B;**当前打开的编辑器**，因此它只在
文件实际上已打开：

| `guides.editor.version` | 含义 |
|---|---|
| `2.0.0` | MarkupEditor (ProseMirror)文件已打开 |
| `1.0.0` | 旧版CKEditor文件已打开或尚未打开任何文件 |

>[!IMPORTANT]
>
> 发生`guides.ready`事件时，尚未打开任何文件，因此，无论MarkupEditor是否已启用，`version`都将报告为`1.0.0`。 不要使用`version`来确定插件是否获得&#x200B;*已注册* （查看[插件注册和运行时选通](#plugin-registration-and-runtime-gating)）。 仅将其用于分支&#x200B;*运行时*&#x200B;行为，并在执行点（例如，在菜单处理程序中）对其进行评估，此时文件必定是打开的。

### 插件注册和运行时选通

- **注册** （`registerPlugin`，一次性设置）：在`guides.ready`中无条件运行它&#x200B;****。 在旧版编辑器中，这是一项无害的无操作操作：旧版编辑器从不读取插件注册表，并且您的工厂仅在实际构建MarkupEditor时才运行。 它会&#x200B;**不**&#x200B;丢弃。

- **运行时调用** (`runCommand`， `runUtil`， `addDecoration`， ...)：存在门别版本并且在调用时不等于“1.0.0”。 它们不会抛出旧版编辑器（它们安全地返回`false`/`undefined`），但门控可避免无操作警告，并允许您保留旧版回退。

```js
guides.ready(() => {
  // Always register — inert on legacy, applied only when a MarkupEditor opens.
  guides.editor.registerPlugin(createMyPlugin);
});

function onMenuClick() {
  if (guides.editor.version && guides.editor.version !== "1.0.0") {
    guides.editor.runCommand('surroundWithElement', 'sup'); // MarkupEditor path
  } else {
    // legacy path (or no-op)
  }
}
```

将&#x200B;**工厂** `() => ({ plugin, css })`传递给`registerPlugin`，绝不传递构造的插件实例。 非函数是唯一拒绝的输入（在两个编辑器中抛出）。 不要缓存编辑器实例；每次都调用`guides.editor.*` fresh。

### Hello world：仅限CSS的高亮插件

最小的有用扩展仅提供&#x200B;**CSS**无操作ProseMirror插件和样式。 此
突出显示编辑器内具有黄色背景的每个`<note>`元素：

```js
guides.ready(() => {
  guides.editor.registerPlugin(() => ({
    plugin: new guides.editor.prosemirror.state.Plugin({}), // no behavior — CSS only
    css: `[data-xml-element="note"] { background: #fff3cd; outline: 1px solid #ffe08a; }`
  }));
});
```

- 每个元素都呈现为`data-xml-element="<tag>"`，因此您可以通过这种方式定位任何DITA元素
(`note`，`codeblock`，`section`，`table`， ...)。
- CSS **必须**通过registerPlugin发运：编辑器位于影子DOM中，因此page/clientlib CSS无法发送
找到它。
- 打开包含`<note>`的DITA主题以查看其应用。 注册是无条件的(§2.1)，
因此即使`version`在`guides.ready`时间仍为`1.0.0`，这是安全的。


## 清点扩展（grep核对清单）

```bash
# DOM-first reads that will break
grep -rnE "rootDocument|rootElement|getSelection\(|selectedHtml|selectedText|\.xmlDoc|\.ancestors\b" src

# DOM/legacy writes that will break
grep -rnE "updateAttributes\(|setAttribute\(|classList\.|\.saveFile\(|resetDirty\(|validateRangeForInsertion\(" src

# The editor handle itself
grep -rn "tcx.curEditor" src

# Context-menu targeting + page CSS
grep -rnE "contextMenuWidget|dita_editor_menu|author_outline_element" src
grep -rn "dita_content_overrides" .
```

每次点击都是一个迁移项目。 将每个分类为： *上下文菜单表面*、*状态读取*、*内容
写入*、*全局操作*、*仅呈现*&#x200B;或&#x200B;*CSS*。


## 对两个编辑器均通用

以下行为和结构同样适用于两个编辑器：

- **注册：** `window.extension[id] = config`和/或`tcx.extension.register(id, config)`，日期
`tcx-loaded`事件。
- **配置对象形状：** `{ id, contextMenuWidget, view: { items }, controller }`。
- **App-shell上下文菜单**&#x200B;保留其现有构件ID和旧版行为：

  | 表面 | 构件ID（未更改） |
  |---|---|
  | 存储库面板（文件/文件夹） | `repository_panel` / `file_options` / `folder_options` |
  | 映射查看器 | `ditamap_viewer` / `map_view_options` |
  | 基线/预设面板 | `baseline_panel_menu` / `preset_item_menu` |

  针对这些表面的项目需要新编辑器进行&#x200B;**无更改**，不要将其移动到
  `markup_editor_menu`.

## API替换参考

| 旧版(`tcx.curEditor…` / DOM) | 新建MarkupEditor |
|---|---|
| `tcx.curEditor.filePath` | `guides.editor.filePath` |
| `getSelection()` / `selectedHtml` / `selectedText` | `runUtil('getSelectedXml' / 'getSelectedPlainText' / 'hasSelection')` |
| `rootDocument.querySelector(tag)` | `runUtil('findPositionRange' / 'findPositionRanges', tag)` |
| 元素`.getAttribute` / `xmlDoc.attributes` | `runUtil('getAttributeAtPosition', pos, name)` / `getSerializableAttributes(xpath)` |
| 根ID (`querySelector('[concept]').id`) | `runUtil('getAttributeAtPosition', 0, 'id')` |
| `editor.ancestors` | `runUtil('getAncestorsDetails' / 'getAncestorXpaths')` |
| `editor.updateAttributes(attrs, root)` | `runCommand('setNodeXmlAttributes', 0, attrs)` |
| 在元素上设置属性 | `runCommand('setNodeXmlAttribute', pos, name, value)` |
| 自动换行/插入/取消换行 | `runCommand('surroundWithElement' / 'insertXml' / 'unwrapNode', …)` |
| `canInsertXmlElement` / `validateRangeForInsertion` | `canRunCommand(name, …)` / `canInsertXmlElement(tag)` |
| `editor.focus()` | `guides.editor.focus()` |
| `tcx.curEditor.saveFile()` | `tcx.eventHandler.next(KEYS.AUTHOR_SAVE_KEY)` |
| 样式的`setAttribute` / `classList` | `addDecoration` / `batchDecorations` / `registerPlugin` |
| 编辑器内容的page/clientlib CSS | `registerPlugin({ css })` （影子DOM） |
| `contextMenuWidget: 'dita_editor_menu'` | `['dita_editor_menu', 'markup_editor_menu']` |


## 迁移上下文菜单项（编辑器画布）

这仅适用于面向&#x200B;**编辑器** (`dita_editor_menu`，
`author_outline_element`)，即编辑界面中的右键单击/痕迹导航菜单。

### 如何在新编辑器中路由

```
window.extension[id]  ─►  filtered by contextMenuWidget == 'markup_editor_menu'
                      ─►  view.items rendered in the canvas menu
   (click) ───────────►  fires an extension event:
                          • eventid is a known global key  → run as a built-in editor command
                          • otherwise                       → your controller[eventid]() runs
```

### 添加新的构件ID（数组保持旧版正常工作）

```js
// BEFORE
contextMenuWidget: 'dita_editor_menu',
// AFTER
contextMenuWidget: ['dita_editor_menu', 'markup_editor_menu'],
```

### 保持预期的形状

- 可操作项位于`view.items`下，具有`data.eventid`。
- 每个`controller`方法名称&#x200B;**与**&#x200B;其`eventid`完全匹配。

```js
view: {
  items: [{
    displayName: 'Edit Cross Reference',
    icon: 'link',
    data: { eventid: 'editCrossReference' },
    target: { key: 'displayName', value: 'Cut', viewState: 'prepend' }
  }]
},
controller: {
  editCrossReference() { /* runs on click */ }
}
```

### 重新定位`target`

新菜单针对MarkupEditor自己的菜单项解析`target`。

- `target.key`：`displayName | id | icon | eventid`
- `target.viewState`：`append | prepend | replace`
- 定位到稳定的本机项，如&#x200B;**`Cut`**。
- 如果锚点未解析，项目仍会出现，但会登陆默认位置
（修复锚点不是错误）。

### 按物料选择工艺路线

```js
data: { eventid: 'AUTHOR_CUT' }          // built-in command → routed natively, no controller needed
data: { eventid: 'editCrossReference' }  // custom → runs controller.editCrossReference()
```

在只读内容中必须保持启用的项目上添加`readOnly: true`。

### 重写处理程序主体

处理程序通常会读取所选内容并修改节点，从DOM中迁移这些内容。

## 迁移读取(DOM： `runUtil`)

```js
// BEFORE — DOM selection / queries
const { editor } = tcx.curEditor;
const html = editor.selectedHtml;
const topicId = editor.rootDocument.querySelector('[data-tcx-tag="concept"]').id;

// AFTER — read from the document model
const selectedXml = guides.editor.runUtil('getSelectedXml');
const hasSel      = !!guides.editor.runUtil('hasSelection'); // check if selection is empty
const topicId     = guides.editor.runUtil('getAttributeAtPosition', 0, 'id'); // root = position 0
```

按标记查找节点，按ID匹配，读取XML属性：

```js
let value = '';
for (const range of (guides.editor.runUtil('findPositionRanges', 'xref') || [])) {
  const id = guides.editor.runUtil('getAttributeAtPosition', range.from, 'id');
  if (String(id) !== String(targetId)) continue;
  value = guides.editor.runUtil('getAttributeAtPosition', range.from, 'placeholdertext') || '';
  break;
}
```

**读取实用工具：** `getTextPos`，`getNodePosition`，`getSelectedXml`，`getSelectedPlainText`，
`hasSelection`, `getAncestorsNames`, `getAncestorsDetails`, `getAncestorXpaths`,
`findPositionRange`, `findPositionRanges`, `getAttributeAtPosition`, `getSerializableAttributes`. 请参阅[附录](#appendix-a-more-exposed-utils-examples)。


## 迁移写入（DOM突变： `runCommand`）

```js
// BEFORE
const root = editor.rootElement.findOne('[data-tcx-tag="concept"]');
editor.updateAttributes({ docOwner: 'Jane' }, root);

// AFTER — update the model; persists across rerenders
guides.editor.runCommand('setNodeXmlAttributes', 0, { docOwner: 'Jane' });
```

```js
// Set one attribute at a found position
guides.editor.runCommand('setNodeXmlAttribute', pos, 'placeholdertext', text);

// Wrap / insert / unwrap
guides.editor.runCommand('surroundWithElement', 'sup');
guides.editor.runCommand('insertXml', '<sup></sup>', undefined, { setCursorInContent: true });
guides.editor.runCommand('unwrapNode');
```

**先决条件**

```js
guides.editor.focus();
if (!guides.editor.canInsertXmlElement('xref')) {
  return tcx.util.showAlert('warning', 'xref is not allowed here'); 
}
if (guides.editor.canRunCommand('surroundWithElement', 'sup')) {
  guides.editor.runCommand('surroundWithElement', 'sup');
}
```

**命令：** `setNodeXmlAttributes`，`setNodeXmlAttribute`，`surroundWithElement`，`insertXml`，
`unwrapNode`. 请参阅[附录](#appendix-b-more-exposed-commands-examples)。

## 迁移全局操作（保存/集中：应用程序事件）

```js
// BEFORE
tcx.curEditor?.saveFile?.();
// AFTER
tcx.eventHandler.next(tcx.eventHandler.KEYS.AUTHOR_SAVE_KEY);
```

`resetDirty(...)`和`tcx.curEditor.html`没有MarkupEditor等效项，因此请删除它们；保存
通过事件集中处理脏状态。 使用`guides.editor.focus()`作为焦点。


## 迁移仅渲染逻辑（DOM绘制：装饰）

通过修改DOM而添加CSS类、`data-*`属性或“显示文本”的任何内容都必须
成为**装饰**，或者该装饰在重新渲染时消失。 以下是简单的声明性用例：

```js
guides.editor.addDecoration('important-sections', 'section', {
  class: 'section-important',
  computeAttributes: (node, ctx) => ({ 'data-number-label': String(ctx.index + 1) }),
  filter: (node) => node.attrs?.xmlAttrs?.importance === 'high'
});

guides.editor.batchDecorations([
  { action: 'remove', id: 'legacy-numbering' },
  { action: 'add', id: 'division-numbering', selector: 'conbody', options: { class: 'division-numbering' } }
]);

guides.editor.removeDecoration('important-sections');
guides.editor.clearDecorations();
guides.editor.getDecorations();
```

复杂案例（自定义状态、通过事务元产生的中断状态、小组件文本）：注册
ProseMirror插件一次，使用公开的库：

```js
const createXrefPlugin = () => {
  const { Plugin, PluginKey } = guides.editor.prosemirror.state;
  const { Decoration, DecorationSet } = guides.editor.prosemirror.view;
  return {
    plugin: new Plugin({ key: new PluginKey('xrefDisplay'), props: { decorations(state) { /* … */ } } }),
    css: `.xref-broken { text-decoration: underline wavy red; }`
  };
};

guides.ready(() => guides.editor.registerPlugin(createXrefPlugin));
```

在应用程序加载时注册插件（一次），而不是在对话框内注册插件，或者重复注册插件，注册表不会进行重复数据删除。`registerPlugin`仅接受&#x200B;**工厂函数**，不接受插件实例。
`guides.editor.prosemirror`公开： `state`、`model`、`view`、`transform`、`commands`、`keymap`、
`history`，`tables`，`dropcursor`，`collab`，`markdown`。


## 迁移CSS（页面clientlib→影子DOM）

MarkupEditor在&#x200B;**影子DOM**&#x200B;中渲染；页面级和AEM clientlib CSS无法访问它。

```js
guides.editor.registerPlugin(() => ({
  plugin: new guides.editor.prosemirror.state.Plugin({}),   // no-op, CSS only
  css: `[data-xml-element="codeblock"] { font-family: monospace; background: #f5f5f5; }`
}));
```

旧版内容clientlib类别(`apps.guides.xml_editor.dita_content_overrides`)仍为
仅设置旧版编辑器的样式，如果您同时支持这两个编辑器，请将其保留，但知道该编辑器在MarkupEditor中是惰性的。

## 访问实时EditorView（插件`view` prop）： DOM转义剖面线

首选方法是装饰和命令。 但是，有些效果不能作为装饰实施。 在这些情况下，请使用插件`view`属性访问实时`EditorView`并在`editorView.dom`上操作。 这是直接与渲染的编辑器DOM交互的唯一受支持方法。

```js
const createMyPlugin = () => {
  const { Plugin } = guides.editor.prosemirror.state;
  return {
    plugin: new Plugin({
      view(editorView) {
        const root = editorView.dom;          // the shadow-DOM editor node
        const apply = () => { /* re-color / rewrite target nodes in `root` */ };
        apply();
        return {
          update(view, prevState): apply,                       // re-apply after every rerender
          destroy() { /* remove any listeners/observers */ },
        };
      },
    }),
    css: `/* ... */`,
  };
};

guides.ready(() => guides.editor.registerPlugin(createMyPlugin));
```

**护栏**：

- 仅对剖面线进行转义，对类、标签和样式使用修饰。
- `editorView.dom`是唯一受支持的句柄；
- 从`update()`重新应用，以使更改保留在渲染中；在`destroy()`中清除。

## 插件注册生命周期

`guides.ready`中的`registerPlugin`只注册一次工厂。 工厂本身又开始运转了
每次打开文件时 — 每个MarkupEditor文件打开时都会重新调用它，以构建该文件的
插件实例。

## 常见问题

- 其中DOM代码寻址节点和`Range`，MarkupEditor寻址&#x200B;**位置**，纯整数索引到文档（`0` =文档开始，即根）。 `range`是`{ from, to }`，两个位置包围一个范围 — 不是DOM `Range`。 位置会随着文档更改而改变，因此不要在编辑过程中缓存位置。
- **项目未出现在“新建编辑器”菜单中**：缺少`contextMenuWidget`
  `markup_editor_menu`，或配置在&#x200B;*编辑器打开后*注册（配置已读取）
  一次在编辑器构建时注册一次在应用程序加载时)。
- **项目出现在错误的位置**： `target`锚点无法解析；锚点指向的项
存在于新菜单中（例如`Cut`）。
- **更改“工作”后消失**：您已更改DOM。 使用命令（写入）或修饰
（样式）。
- **CSS无效**：它属于页面级别；编辑器位于影子DOM中。 使用`registerPlugin({ css })`。
- **不安全的防护抛出**：类似`if (!tcx.curEditor && !tcx.curEditor.editor)`的模式评估
  在假对象上执行`.editor`。改为保护`guides.editor`功能：
  `if (!guides?.editor) return;`.
- **正在尝试迁移app-shell菜单**：存储库/映射/文件菜单不是编辑器画布；
保留为其旧版构件ID。

## 验证核对清单

- 上下文菜单项同时出现在&#x200B;**旧版和MarkupEditor菜单**&#x200B;中。
- 项目位于预期位置。
- 自定义`eventid`运行`controller[eventid]`；全局键触发内置命令。
- 状态读取在键入/重新渲染后返回正确的值（模型，而不是陈旧的DOM）。
- 内容写入&#x200B;*在保存并重新打开*&#x200B;后持续存在。
- 重新演绎之后仍保留着装饰。
- Shadow-DOM CSS会明显应用于编辑器中。
- 通过`AUTHOR_SAVE_KEY`保存触发并清除已修改状态。
- `readOnly`项在锁定的内容中行为正确。
- 预览或并排；有意的只读DOM工作保持不变。
- `grep -rn "tcx.curEditor" src`是干净的（或仅记录有意的剩余部分）。
- 插件在`guides.ready`内只注册一次。


## 建议的转出序列

1. **Bootstrap**：在`guides.ready`中完成安装；无条件注册插件并仅添加`version`选通&#x200B;*运行时*&#x200B;操作（有关详细信息，请查看[插件注册和运行时选通](#plugin-registration-and-runtime-gating)）。
2. **上下文菜单表面**：添加`markup_editor_menu`，修复`target`锚点。 现在会显示项目。
3. **读取**：将选择/属性读取迁移到`runUtil`。
4. **写入**：将突变迁移到`runCommand`；保存到应用程序事件。
5. **呈现**：将DOM样式移动到装饰/ `registerPlugin`；将CSS移动到影子DOM。
6. **硬化**：修复不安全的防护，移除编辑器句柄，在两个编辑器上进行验证。

每次迁移一个表面，并保持旧路径正常运行（数组+版本选通），以便
在整个过渡期间，单个扩展构建会在两个编辑器中运行。

## 附录A：更公开的实用程序（示例）

通过`runUtil`查找以下要使用的util。

| 直到 | 参数→返回 | 作用 |
|---|---|---|
| `getTextPos` | `(): { start, end }` | 当前选定的文本节点边界 |
| `getValidElementNames` | `(ancestorLevel?): ElementName[]` | 可在当前选定内容中合法插入/封装的元素名称。 |
| `getValidElementNamesBefore` | `(): ElementName[]` | 元素名称在当前选定内容之前有效。 |
| `getSelectedText` | `(): string` | 原始选定文本。 |
| `getSerializableAttributes` | `(): { [key]: string }` | 当前节点的XML属性映射，以属性名称作为键值。 |
| `getTagName` | `(): string \| null` | 当前节点的标记名称。 |
| `hasSelection` | `(): boolean` | 当前是否选择了任何内容。 |
| `isSelectionEditable` | `(): boolean` | 是否可以编辑当前选择。 |
| `getAncestorPos` | `(name): number \| undefined` | 当前选定内容中具有给定元素名称的最近祖先的位置。 |
| `getValidWrapNodeElementNames` | `(): ElementName[]` | 在当前选择位置对`wrapNode`有效的元素名称。 |
| `getValidRenameNodeElementNames` | `(): ElementName[]` | 元素名称当前节点可合法重命名为。 |
| `getValidSurroundElementNames` | `(): ElementName[]` | 在当前选择位置对`surroundWithElement`有效的元素名称。 |
| `serialize` | `(doc?): string` | 将ProseMirror文档（或整个文档）序列化为XML。 |
| `getSelectedXml` | `(range?): string` | 当前选择的XML，或显式`{ from, to }`范围。 |
| `getRangeXml` | `(xpaths): string` | 一个或多个xpath对象范围的XML（请参阅§8的xpath注意事项 — 这是对象表单，而不是字符串表单）。 |
| `mapToXpath` | `(position, doc?): XPathPosition` | 将位置转换为对象表单xpath。 |
| `inverseMap` | `(xpath \| position, doc?): number` | 将对象形式的xpath（或位置）转换回某个位置。 |
| `getAncestorsDetails` | `(): { ancestors, previousSibling, nextSibling, currNode } \| undefined` | 当前节点的上级链加上直接同级。 |
| `getAncestorsNames` | `(): ElementName[]` | 上阶链仅作为当前节点的元素名称。 |
| `getPreviousSibling` | `(): ElementName \| undefined` | 上一个同级元素的名称。 |
| `getNextSibling` | `(): ElementName \| undefined` | 下一个同级元素的名称。 |
| `getAncestorXpaths` | `(includeNodeAtPosition?): { tag, xpath }[]` | 上阶链为`{tag, xpath}`对 — 对象形式的xpath，而不是`updateAttributeByXpath`字符串形式(§8)。 |
| `getSelectedPlainText` | `(range?): string` | 当前选定内容的纯文本或显式范围。 |
| `getDecorations` | `(): string[]` | 当前应用的所有修饰的ID。 |
| `getResolvedDitaDocumentTitle` | `(props?): string` | 已解析DITA文档的显示标题。 `props`： `doc`以特定文档为目标，`allowedPrefixElements`以允许标题前缀元素。 |

## 附录B：更多公开的命令（示例）

以下命令是通过`guides.editor.runCommand(name, ...args)`公开内容的其他示例。
如果任何带有`guides.editor.canRunCommand(name, ...args)`的命令可能不适用于当前上下文，请首先保护该命令。

| 命令 | 参数 | 作用 |
|---|---|---|
| `focusEditor` | `()` | 焦点位于编辑器中。 |
| `unwrapNode` | `()` | 删除当前选定内容处的包装元素，保留其子项。 |
| `surroundWithElement` | `(elementName, attrs?, groupInline?)` | 在新的内联/块元素中封装当前选定内容。 `attrs`：要在新包装元素上设置的XML属性映射。 |
| `insertXml` | `(xml)` | 在光标处插入XML片段。 |
| `replaceSelectionWithXml` | `(xml)` | 用XML替换当前选择。 |
| `insertText` | `(text)` | 在光标处插入纯文本。 |
| `selectNodesFromXpaths` | `(xpaths)` | 选择给定对象格式xpath的一个或多个节点。 |
| `delete` | `()` | 删除当前选择。 |
| `undo` / `redo` | `()` | 标准撤消/重做。 |
| `removeDecoration` | `(id)` | 按ID删除单个修饰。 |
| `clearDecorations` | `()` | 删除当前打开文件中的所有装饰。 |
| `setFileReadOnly` | `(readOnly: boolean)` | 切换文件的只读模式。 |
| `generateUniqueId` | `()` | 生成唯一id属性并将其分配给当前节点。 |