---
title: 编辑器2.0的扩展框架更改
description: 了解Editor 2.0扩展框架中的更改
feature: Web Editor Configuration
role: Admin
level: Experienced
source-git-commit: 3f38264b6ce09366d07cdd302c9c53e8abcf4b7c
workflow-type: tm+mt
source-wordcount: '2003'
ht-degree: 4%

---

# 编辑器2.0（新编辑器）的扩展框架更改

本文档介绍了作为新编辑器（基于ProseMirror的编辑器）的扩展框架的一部分添加到`guides.editor`（和`guides`）的所有API。 这些API允许外部扩展与编辑器交互，而无需直接DOM操作或内部实施知识。

## 概述

全局`guides`对象是所有扩展集成的入口点：

```js
guides.editor    // Editor interaction APIs
guides.util      // Utility libraries (lodash, async)
guides.ready(cb) // Lifecycle hook fires when the editor is fully loaded
```

可从扩展控制器、工具栏处理程序和对话框逻辑安全地调用所有`guides.editor` API。

## 生命周期

`guides.ready(callback)`：注册回调以在页面视图管理器完全加载后执行。 在注册插件或执行任何编辑器设置之前使用此选项。

**签名：**

```ts
guides.ready(callback: () => void): void
```

**示例：**

```js
guides.ready(() => {
  // Safe to access guides.editor APIs here
  guides.editor.registerPlugin(createMyPlugin);
});
```

## 编辑器状态属性

- `guides.editor.filePath`：返回当前活动文档的文件路径。

  **类型：** `string | undefined`

  **示例：读取元数据API调用的文件路径：**

  ```js
  const filePath = guides.editor.filePath;
  if (filePath) {
  tcx.api.getMetadata(filePath).subscribe((metadata) => {
    // use metadata...
    });
  }
  ```

  **示例：基于文件位置的条件逻辑**

  ```js
  const filePath = guides.editor.filePath;
  if (filePath?.endsWith(".ditamap")) {
    // ditamap-specific handling
  }
  ```

- `guides.editor.version`：返回当前加载的编辑器的版本字符串。

  | 值 | 编辑器 |
  |---------|------------------------------------|
  | `1.0.0` | 旧版CKEditor (`xml_author_view`) |
  | `2.0.0` | 新编辑器（基于ProseMirror） |

  **类型：** `string`

  **示例：**

  ```js
  if (guides.editor.version  === '1.0.0') {
    // CKEditor specific logic 
  }
  ```

- `guides.editor.appState(keyName)`：按键名从应用程序模型读取值。

  **签名：**

  ```ts
  guides.editor.appState(keyName: string): unknown
  ```

  **示例：**

  ```js
  const editorMode = guides.editor.appState('editorMode');
  ```

## 编辑器交互

- `guides.editor.focus()`：将焦点设置为活动编辑器。 在执行要求编辑器具有焦点的命令之前，请调用此项。

  **签名：**

  ```ts
  guides.editor.focus(): boolean
  ```

  **示例：插入内容前焦点**

  ```js
  guides.editor.focus();
  const hasSelection = !!guides.editor.runUtil('hasSelection');
  // ...proceed with wrap or insert
  ```

- `guides.editor.canInsertXmlElement(tagName, insertAfter?)`：检查给定的XML元素是否可以插入到当前光标位置。

  **签名：**

  ```ts
  guides.editor.canInsertXmlElement(tagName: string, insertAfter?: boolean): boolean
  ```

  **示例：插入`<xref>`**&#x200B;之前的guard

  ```js
  const canInsert = guides.editor.canInsertXmlElement("xref");
  if (!canInsert) {
    return tcx.util.showAlert("warning", "xref is not allowed here");
  }
  ```

  **示例：插入`<sup>` /`<sub>`**&#x200B;之前需要保护

  ```js
  const canInsert = guides.editor.canInsertXmlElement("sup");
  if (!canInsert) {
    return tcx.util.showAlert("warning", "superscript is not allowed here");
  }
  ```

- `guides.editor.selectCurrentBlockElement()`：在编辑器中选择当前的块级元素。

  **签名：**

  ```ts
  guides.editor.selectCurrentBlockElement(): boolean
  ```

  **示例：**

  ```js
  guides.editor.selectCurrentBlockElement();
  ```

- `guides.editor.getValidElementNamesForInsertion(args)`：返回可在当前位置插入的有效XML元素名称列表。

  **签名：**

  ```ts
  guides.editor.getValidElementNamesForInsertion(args: {
    insertMode?: 'after' | 'before' | 'rename',
    strict: boolean
  }): string[] | false
  ```

  **示例：**

  ```js
  const validElements = guides.editor.getValidElementNamesForInsertion({
    insertMode: 'after',
    strict: true
  });
  ```

- `guides.editor.updateAttributeByXpath(args)`：更新由其XPath标识的节点上的特定XML属性。 委派给活动编辑器的`updateAttributeByXpath`方法。

  **签名：**

  ```ts
  guides.editor.updateAttributeByXpath(args: UpdateXpathArgs): any
  ```

## 命令执行

- `guides.editor.runCommand(commandName, ...args)`：在新编辑器上执行命名命令。 如果命令成功，则返回`true`，否则返回`false`。

  **签名：**

  ```ts
  guides.editor.runCommand(commandName: string, ...args: any[]): boolean
  ```

  **可用命令**

  >[!NOTE]
  >
  > 稳定性：下面列出的命令是公共接口的一部分。 它们的名称、特征码和观察到的行为被认为是稳定的，并保持兼容性。 编辑器中可能会出现其他命令；但是，这些命令是内部命令，不适用于外部命令，未经事先通知可能会更改或删除这些命令。

  | 类别 | 命令 | 参数 | 描述 |
  |---|---|---|---|
  | 常规 | `undo` | _（无）_ | 撤消上一个文档更改 |
  | 常规 | `redo` | _（无）_ | 重新执行上次撤消的更改 |
  | 选择区域 | `select` | `from: number, to?: number` | 选择从`from`到`to`的范围（如果省略`to`，则仅选择`from`） |
  | 选择区域 | `cursor` | `pos: number` | 将光标移动到`pos` |
  | 选择区域 | `selectNodesFromXpaths` | `xpaths: Array<{path: Array<{name: string, count: number}>}>` | 选择由XPath位置标识的节点 |
  | 格式 | `toggleBold` | _（无）_ | 切换当前选定内容上的粗体格式 |
  | 格式 | `toggleItalic` | _（无）_ | 在当前选定内容上切换斜体格式 |
  | 格式 | `toggleUnderline` | _（无）_ | 切换当前选定内容上的下划线格式 |
  | 格式 | `toggleFormatting` | `markType: string, allowEmptySelection?: boolean` | 切换所选内容上的格式元素（例如，`'b'`、`'i'`、`'sup'`、`'sub'`） |
  | 插入 | `insertText` | `text: string` | 在光标处插入纯文本 |
  | 插入 | `insertXml` | `xml: string, position?: number, options?: InsertXmlOptions` | 在光标或给定位置插入原始XML |
  | 插入 | `insertXmlAfterElement` | `elementName: string, xmlString: string` | 在匹配`elementName`的最近上级之后立即插入XML |
  | 插入 | `replaceSelectionWithXml` | `xmlString: string` | 将当前选择替换为给定的XML |
  | 节点操作 | `surroundWithElement` | `tagName: string, attrs?: Record<string,unknown>, replaceTextWithEmptyNode?: boolean` | 将当前选定内容与给定元素括起来 |
  | 节点操作 | `wrapNode` | `type: string, target?: number, attrs?: Record<string, unknown>` | 将`target`处的节点（或当前节点）包装在`type`的元素中 |
  | 节点操作 | `renameNode` | `newNodeName: string` | 重命名当前节点的元素 |
  | 节点操作 | `unwrapNode` | _（无）_ | 删除当前节点的包装器元素，保留其内容 |
  | 删除 | `deleteSelection` | _（无）_ | 删除当前选定的内容 |
  | 删除 | `deleteNode` | _（无）_ | 删除整个当前节点 |
  | 属性 | `setNodeXmlAttributes` | `position: number, attrs: Record<string, unknown>` | 在`position`处的节点上设置多个XML属性 |
  | 属性 | `setNodeXmlAttribute` | `position: number, attrName: string, value: string` | 在`position`处的节点上设置单个XML属性 |
  | 列表 | `toggleList` | `listName: 'ol' \| 'ul'` | 在给定类型的列表和段落之间切换当前块 |
  | 表格 | `addRowAfter` | `count?: number` | 在当前行下添加`count`行（默认为1） |
  | 表格 | `addColumnAfter` | `count?: number` | 在当前列的右侧添加`count`列（默认为1） |
  | 表格 | `deleteRow` | _（无）_ | 删除当前行 |
  | 表格 | `deleteColumn` | _（无）_ | 删除当前列 |
  | 表格 | `mergeCells` | _（无）_ | 合并当前选定的单元格 |
  | 剪贴板 | `copy` | _（无）_ | 将当前选定内容复制到剪贴板 |
  | 剪贴板 | `cut` | _（无）_ | 将当前选定内容剪切到剪贴板 |
  | 查找和替换 | `setSearchQuery` | `query: string, options?: { caseSensitive?: boolean, regex?: boolean }` | 设置活动搜索查询 |
  | 查找和替换 | `findNext` | _（无）_ | 移到下一个搜索匹配 |
  | 查找和替换 | `replaceAll` | `replacement?: string` | 将当前搜索查询的所有匹配项替换为`replacement` |

   - **示例：在节点**&#x200B;上设置多个属性

     ```js
     guides.editor.runCommand(
       "setNodeXmlAttributes",
       rootRange.from,
       { createdDate: "2024-01-01", author: "Jane Doe" }
     );
     ```

   - **示例：在节点**&#x200B;上设置单个属性

     ```js
     guides.editor.runCommand(
       "setNodeXmlAttribute",
       range.from,
       "placeholdertext",
       "Chapter 3 — Safety Requirements"
     );
     ```

   - **示例：使用元素环绕选择并设置属性**

     ```js
     const didWrap = guides.editor.runCommand(
       "surroundWithElement",
       "ph",
       { outputclass: "highlight" },
       true   // replace text content with empty node
     );
     ```

   - **示例：`<sup>`中的换行选择（打开上标）**

     ```js
     const didWrap = guides.editor.runCommand('surroundWithElement', 'sup');
     if (!didWrap) {
       tcx.util.showAlert("warning", "superscript is not allowed here");
     }
     ```

   - **示例：取消当前节点的包装（关闭上标）**

     ```js
     const didUnwrap = guides.editor.runCommand('unwrapNode');
     ```

   - **示例：在光标处插入XML，插入符号位于**&#x200B;内

     ```js
     guides.editor.runCommand(
       'insertXml',
       '<sup></sup>',
       undefined,
       { setCursorInContent: true, focusEditor: true, selectInsertedXml: false }
     );
     ```

- `guides.editor.canRunCommand(commandName, ...args)`：检查命名命令当前是否可以执行，而不实际运行它。

  **签名：**

  ```ts
  guides.editor.canRunCommand(commandName: string, ...args: any[]): boolean
  ```

  **示例：**

  ```js
  if (guides.editor.canRunCommand('surroundWithElement', 'sup')) {
    guides.editor.runCommand('surroundWithElement', 'sup');
  }
  ```

## 实用程序函数

- `guides.editor.runUtil(utilName, ...args)`：从新编辑器的实用工具注册表调用命名实用工具。 返回实用工具的结果，如果找不到该实用工具，则返回`undefined`。

  **签名：**

  ```ts
  guides.editor.runUtil(utilName: string, ...args: any[]): any
  ```

  **可用的实用工具**

  >[!NOTE]
  >
  > 稳定性：下面列出的实用程序是公共界面的一部分。 它们的名称、特征码和观察到的行为被认为是稳定的，并保持兼容性。 编辑器中可能会出现其他命令；但是，这些命令是内部命令，不适用于外部命令，未经事先通知可能会更改或删除这些命令。


  | 类别 | 实用工具 | 参数 | 返回 | 描述 |
  |---|---|---|---|---|
  | 位置 | `getTextPos` | _（无）_ | `{ start: number, end: number }` | ProseMirror文档中当前选定内容的开始位置和结束位置 |
  | 位置 | `getNodePosition` | `position?: number` | `number` | 当前选定/焦点节点的文档位置 |
  | 位置 | `mapToXpath` | `position: number` | `XPathPosition` | 将ProseMirror位置映射到XPath描述符 |
  | 位置 | `inverseMap` | `xpath: XPathPosition \| number` | `number` | 将XPath描述符（或数字位置）映射回ProseMirror位置 |
  | 文档 | `getNodeTree` | _（无）_ | `NodeTree \| null` | 文档的树表示，适用于轮廓渲染 |
  | 文档 | `getAncestorsNames` | `position?: number` | `string[]` | 位于`position`的上级节点的XML标记名称 |
  | 文档 | `getAncestorsDetails` | `position?: number` | `{ currNode: string, ancestors: Array<{tagName: string}>, previousSibling?: string, nextSibling?: string } \| undefined` | 当前节点、祖先和位于`position`的直接同级 |
  | 文档 | `getAncestorXpaths` | `includeId?: boolean` | `AncestorXpathItem[]` | 所有上级节点的XPath字符串 |
  | 文档 | `getPreviousSibling` | `position?: number` | `string \| undefined` | 上一个同级的标记名称（如果有） |
  | 文档 | `getNextSibling` | `position?: number` | `string \| undefined` | 下一个同级标记的标记名称（如果有） |
  | 文档 | `getTagName` | `position?: number` | `string \| null` | 位于`position`处的元素的标记名称（或光标） |
  | 元素搜索 | `findPositionRange` | `tagName: string` | `{ from: number, to: number } \| undefined` | 具有给定标记的第一个元素的范围 |
  | 元素搜索 | `findPositionRanges` | `tagName: string` | `Array<{ from: number, to: number }>` | 匹配`tagName`的元素的所有范围 |
  | 属性 | `getAttributeAtPosition` | `position: number, attrName: string` | `unknown` | 从`position`处的节点读取XML属性值 |
  | 属性 | `getSerializableAttributes` | `xpath: string` | `Record<string, unknown>` | 位于`xpath`的节点的所有可序列化XML特性 |
  | 序列化 | `serialize` | _（无）_ | `string` | 将整个文档序列化为XML |
  | 序列化 | `serializeToText` | _（无）_ | `string` | 将整个文档序列化为纯文本 |
  | 序列化 | `getRangeXml` | `xpaths: AncestorXpathItem[]` | `string` | 返回XPath定义范围的XML |
  | 选择区域 | `getSelectedXml` | _（无）_ | `string` | 当前选定内容作为XML字符串 |
  | 选择区域 | `getSelectedText` | _（无）_ | `string` | 所选文本不含任何标记 |
  | 选择区域 | `hasSelection` | _（无）_ | `boolean` | 如果存在活动文本/节点选择，则为`true` |
  | 选择区域 | `isSelectionEditable` | _（无）_ | `boolean` | 当前选择是否位于可编辑内容中 |
  | 选择区域 | `isPositionEditable` | `position: number` | `boolean` | `position`是否位于可编辑内容内 |
  | 插入 | `canInsert` | `name: string, position?: number, insertMode?: 'after' \| 'before' \| 'rename'` | `boolean` | 是否可以在`position`（或游标）处插入`name` |
  | 插入 | `getInsertPosition` | `name: string, position?: number, insertMode?: 'after' \| 'before' \| 'rename'` | `number \| null` | `name`的有效插入位置，如果不可插入，则为`null` |
  | 插入 | `getNodeXml` | `nodeName: string, nodeContent?: string` | `string \| null` | 节点类型的XML模板 |
  | 换行/重命名 | `getValidWrapNodeElementNames` | _（无）_ | `string[]` | 可能包含当前选定内容的元素名称 |
  | 换行/重命名 | `getValidRenameNodeElementNames` | _（无）_ | `string[]` | 元素名称可以将当前节点重命名为 |
  | 表格 | `getTableInfo` | `position?: number` | `{ rows: number, cols: number, header: number }` | 当前表的尺寸 |
  | 标记视图 | `isTagViewActive` | _（无）_ | `boolean` | 标记视图渲染是否处于活动状态 |

  **示例：获取游标位置和祖先名称**

  ```js
  const textPos = guides.editor.runUtil("getTextPos");
  const ancestorNames = guides.editor.runUtil(
    "getAncestorsNames",
    typeof textPos === "number" ? textPos : undefined
  );
  ```

  **示例：查找所有`<xref>`元素并读取其属性**

  ```js
  const xrefRanges = guides.editor.runUtil("findPositionRanges", "xref") || [];
  xrefRanges.forEach((range) => {
    const id = guides.editor.runUtil("getAttributeAtPosition", range.from, "id");
    const placeholderText = guides.editor.runUtil(
      "getAttributeAtPosition",
      range.from,
      "placeholdertext"
    );
  });
  ```

  **示例：查找根元素范围并读取其属性**

  ```js
  const rootRange = guides.editor.runUtil("findPositionRange", "concept"); // or "topic"
  if (rootRange) {
    const createdDate = guides.editor.runUtil(
      "getAttributeAtPosition",
      rootRange.from,
      "createdDate"
    );
    const author = guides.editor.runUtil(
      "getAttributeAtPosition",
      rootRange.from,
      "author"
    );
  }
  ```

  **示例：检查选择并在操作**&#x200B;之前验证上级上下文

  ```js
  const ancestorsDetails = guides.editor.runUtil('getAncestorsDetails');
  const selectedText = guides.editor.runUtil('getSelectedPlainText');
  const hasSelection = !!guides.editor.runUtil('hasSelection');
  
  const firstAncestor = ancestorsDetails?.currNode || ancestorsDetails?.ancestors?.[0]?.tagName;
  if (firstAncestor === 'ph') {
    tcx.util.showAlert("warning", "Operation is not allowed inside this element type.");
    return;
  }
  ```

  **示例：从上级XPath获取元素ID**

  ```js
  const ancestorItems = guides.editor.runUtil('getAncestorXpaths', true);
  for (const item of ancestorItems) {
    const attrs = guides.editor.runUtil('getSerializableAttributes', item.xpath);
    if (attrs?.id) { /* use element ID */ }
  }
  ```

## 修饰API

修饰API为编写用于常见可视化自定义设置的完整ProseMirror插件提供了更高级别的替代方法。 您不是手动管理`Plugin`、`PluginKey`和`DecorationSet`，而是描述&#x200B;*要装饰的内容*&#x200B;和&#x200B;*方式*，编辑器的中央装饰管理器在内部处理ProseMirror状态。

装饰由字符串`id`标识，因此可以随时单独更新或删除它们。

>[!NOTE]
>
> **仅限新编辑器**&#x200B;这些API在旧版编辑器(`version === '1.0.0'`)中是空操作。

- `guides.editor.addDecoration(id, selector, options)`：添加或替换修饰规则。 将根据`options`修饰当前文档中与`selector`匹配的所有节点。 每次文档更改时，都会自动重新应用修饰。

  **签名：**

  ```ts
  guides.editor.addDecoration(
    id: string,
    selector: string,
    options: DecorationOptions
  ): boolean
  ```

  **`DecorationOptions`字段：**

  | 字段 | 类型 | 描述 |
  |---|---|---|
  | `class` | `string` | 已将CSS类名称添加到匹配节点 |
  | `computeAttributes` | `(node, context) => Record<string, string>` | 函数返回每个节点的动态`data-*`或其他HTML属性 |
  | `filter` | `(node) => boolean` | 可选谓词 — 仅修饰其返回`true`的节点 |

  传递到`computeAttributes`的`context`对象包括：
   - `index` — 在匹配选择器的同级节点中，从0开始的节点位置

  **示例：将CSS类添加到所有`<section>`元素**

  ```js
  guides.editor.addDecoration('highlight-sections', 'section', {
    class: 'my-section-highlight'
  });
  ```

  **示例：将计算的`data-number-label`属性添加到每个节**

  ```js
  guides.editor.addDecoration('section-numbers', 'section', {
    computeAttributes: (node, context) => ({
      'data-number-label': String(context.index + 1)
    })
  });
  ```

  **示例：仅修饰具有`importance="high"`属性**&#x200B;的部分

  ```js
  guides.editor.addDecoration('important-sections', 'section', {
    class: 'section-important',
    filter: (node) => node.attrs?.xmlAttrs?.importance === 'high'
  });
  ```

  **示例：组合类和计算属性**

  ```js
  guides.editor.addDecoration('numbering-mode', 'conbody', {
    class: 'legacy-numbering'
  });
  
  guides.editor.addDecoration('section-numbers', 'section', {
    computeAttributes: (node, context) => ({
      'data-number-label': String(context.index + 1)
    })
  });
  ```

- `guides.editor.removeDecoration(id)`：删除以前通过其ID添加的修饰。

  **签名：**

  ```ts
  guides.editor.removeDecoration(id: string): boolean
  ```

  **示例：**

  ```js
  guides.editor.removeDecoration('section-numbers');
  ```

- `guides.editor.batchDecorations(changes)`：在单个ProseMirror调度中应用多个添加/删除修饰更改。 在同时切换多个装饰时使用此选项以避免多次重新渲染。

  **签名：**

  ```ts
  guides.editor.batchDecorations(changes: DecorationBatchChange[]): boolean
  
  type DecorationBatchChange =
    | { action: 'add', id: string, selector: string, options: DecorationOptions }
    | { action: 'remove', id: string }
  ```

  **示例：在两种编号模式之间自动切换**

  ```js
  guides.editor.batchDecorations([
    { action: 'remove', id: 'legacy-numbering' },
    {
      action: 'add',
      id: 'division-numbering',
      selector: 'conbody',
      options: { class: 'division-numbering' }
    }
  ]);
  ```

  **示例：清除一个修饰并添加两个新修饰**

  ```js
  guides.editor.batchDecorations([
    { action: 'remove', id: 'old-highlights' },
    {
      action: 'add',
      id: 'section-labels',
      selector: 'section',
      options: {
        computeAttributes: (node, ctx) => ({ 'data-section-index': String(ctx.index) })
      }
    },
    {
      action: 'add',
      id: 'note-style',
      selector: 'note',
      options: { class: 'styled-note' }
    }
  ]);
  ```

- `guides.editor.clearDecorations()`：删除由修饰管理器管理的所有活动修饰。

  **签名：**

  ```ts
  guides.editor.clearDecorations(): boolean
  ```

  **示例：**

  ```js
  guides.editor.clearDecorations();
  ```

- `guides.editor.getDecorations()`：返回当前所有活动装饰的ID。

  **签名：**

  ```ts
  guides.editor.getDecorations(): string[]
  ```

  **示例：**

  ```js
  const active = guides.editor.getDecorations();
  console.log('Active decorations:', active);
  // e.g. ['section-numbers', 'numbering-mode', 'note-style']
  ```


### 修饰API与`registerPlugin`

| 场景 | 使用 |
|---|---|
| 将CSS类或`data-*`属性应用到匹配的元素 | `addDecoration` |
| 根据运行时状态（元数据、用户操作）切换或更新样式 | `addDecoration` / `removeDecoration` / `batchDecorations` |
| 复杂的插件逻辑：自定义状态、键绑定、构件装饰、事件处理程序 | `registerPlugin` |
| 将CSS注入影子DOM | `registerPlugin`包含`css`字段 |


## ProseMirror插件注册

- `guides.editor.registerPlugin(factory)`：注册要包含在每个New Editor实例中的ProseMirror插件工厂。 仅接受工厂函数，拒绝直接插件实例。 每个编辑器实例调用一次工厂，确保处于隔离的插件状态。

  **签名：**

  ```ts
  guides.editor.registerPlugin(factory: () => PluginConfig): void
  
  interface PluginConfig {
    plugin: ProseMirrorPlugin | ProseMirrorPlugin[]
    css?: string  // Injected into editor's shadow DOM
  }
  ```

  **示例：在编辑器准备就绪后注册插件**

  ```js
  guides.ready(() => {
    guides.editor.registerPlugin(createNumberingPlugin);
    guides.editor.registerPlugin(createXrefPlugin);
  });
  ```

  **示例：使用CSS的内联工厂**

  ```js
  guides.editor.registerPlugin(() => ({
    plugin: new guides.editor.prosemirror.state.Plugin({
      key: new guides.editor.prosemirror.state.PluginKey("myPlugin"),
      props: {
        decorations(state) {
          // return DecorationSet...
        }
      }
    }),
    css: `.my-decoration { background: yellow; }`
  }));
  ```

  >[!NOTE]
  >
  > 通过`css`传递的CSS将插入到编辑器的影子DOM中。 常规页面级样式表不适用于该编辑器。

## ProseMirror库

- `guides.editor.prosemirror`：直接公开ProseMirror包以用于插件开发。 这无需在扩展代码中单独捆绑ProseMirror。

  | 属性 | 包 |
  |---|---|
  | `state` | `prosemirror-state` |
  | `model` | `prosemirror-model` |
  | `view` | `prosemirror-view` |
  | `transform` | `prosemirror-transform` |
  | `commands` | `prosemirror-commands` |
  | `keymap` | `prosemirror-keymap` |
  | `history` | `prosemirror-history` |
  | `tables` | `prosemirror-tables` |
  | `dropcursor` | `prosemirror-dropcursor` |
  | `markdown` | `prosemirror-markdown` |

  **示例：创建节点修饰插件**

  ```js
  const myPluginKey = new guides.editor.prosemirror.state.PluginKey("myPlugin");
  
  const createMyPlugin = () => {
    const { Plugin } = guides.editor.prosemirror.state;
    const { Decoration, DecorationSet } = guides.editor.prosemirror.view;
  
    return {
      plugin: new Plugin({
        key: myPluginKey,
        state: {
          init() { return { enabled: true }; },
          apply(tr, value) {
            const meta = tr.getMeta(myPluginKey);
            return meta ? { ...value, ...meta } : value;
          }
        },
        props: {
          decorations(state) {
            const decorations = [];
            state.doc.descendants((node, pos) => {
              if (node.type.name === "section") {
                decorations.push(
                  Decoration.node(pos, pos + node.nodeSize, { class: "my-section" })
                );
              }
            });
            return DecorationSet.create(state.doc, decorations);
          }
        }
      }),
      css: `.my-section { border-left: 3px solid #ccc; padding-left: 8px; }`
    };
  };
  ```

  **示例：创建构件修饰插件（内联显示文本）**

  ```js
  const xrefPluginKey = new guides.editor.prosemirror.state.PluginKey("xrefDisplay");
  
  const createXrefPlugin = () => {
    const { Plugin } = guides.editor.prosemirror.state;
    const { Decoration, DecorationSet } = guides.editor.prosemirror.view;
  
    return {
      plugin: new Plugin({
        key: xrefPluginKey,
        props: {
          decorations(state) {
            const decorations = [];
            state.doc.descendants((node, pos) => {
              if (node.type.name.includes("xref")) {
                const display = node.attrs?.xmlAttrs?.placeholdertext;
                if (display) {
                  decorations.push(
                    Decoration.widget(pos + 1, () => {
                      const el = document.createElement("span");
                      el.textContent = `[${display}]`;
                      el.setAttribute("contenteditable", "false");
                      return el;
                    }, { key: `xref-${pos}` })
                  );
                }
              }
            });
            return DecorationSet.create(state.doc, decorations);
          }
        }
      }),
      css: `.xref-display-text { color: #0074d9; pointer-events: none; }`
    };
  };
  ```

## 将CSS插入编辑器

Guides DITA编辑器从类别为`apps.guides.dita_editor.content`的clientlib加载其创作模式内容样式。 该clientlib有一个`embed`声明，该声明自动拉入在类别下注册的任何clientlib：

```
apps.guides.xml_editor.dita_content_overrides
```

要在编辑器的内容区域中插入自定义CSS，请创建具有此类别的AEM clientlib节点。 无需其他布线，加载编辑器页面时，“参考线”会自动选取它。

**AEM clientlib节点结构(`/apps/my-extension/clientlibs/editor-content-overrides/.content.xml`)**

```xml
<?xml version="1.0" encoding="UTF-8"?>
<jcr:root xmlns:cq="http://www.day.com/jcr/cq/1.0"
          xmlns:jcr="http://www.jcp.org/jcr/1.0"
    jcr:primaryType="cq:ClientLibraryFolder"
    categories="[apps.guides.xml_editor.dita_content_overrides]"/>
```

将CSS文件（`css.txt` + `.css`文件）放置在此文件夹中。 它将自动嵌入到编辑器的内容样式表中。

**示例：在创作模式下覆盖节标题样式**

```css
/* /apps/my-extension/clientlibs/editor-content-overrides/css/content.css */

/* Increase section title font size in author mode */
.section > title {
  font-size: 1.4em;
  font-weight: bold;
  color: #333;
}

/* Highlight note blocks */
.note {
  border-left: 4px solid #0074d9;
  padding-left: 12px;
  background: #f0f7ff;
}
```

>[!NOTE]
>
>此CSS仅定向旧版基于CKEditor的创作表面。 它在使用影子DOM的新编辑器(ProseMirror)中没有任何效果。


### 新编辑器： `registerPlugin`中的`css`

新编辑器在&#x200B;**影子DOM**&#x200B;内渲染，这将使其与所有页面级样式（包括AEM `clientlibs`）隔离。 要将CSS插入到新编辑器的创作表面，请传递作为插件工厂返回的`PluginConfig`一部分的`css`字符串。

每次创建编辑器实例时，CSS将作为`<style>`标记直接插入编辑器的影子根中。

**示例：将样式与装饰插件一起插入**

```js
guides.ready(() => {
  guides.editor.registerPlugin(() => ({
    plugin: createMyPlugin(), // your ProseMirror plugin
    css: `
      /* Styles scoped to the New Editor shadow DOM */
      .section > .title-node {
        font-size: 1.4em;
        font-weight: bold;
        color: #333;
      }

      .note-node {
        border-left: 4px solid #0074d9;
        padding-left: 12px;
        background: #f0f7ff;
      }
    `
  }));
});
```

**示例：仅CSS插件（无修饰逻辑）**

```js
guides.ready(() => {
  guides.editor.registerPlugin(() => ({
    plugin: new guides.editor.prosemirror.state.Plugin({}), // no-op plugin
    css: `
      /* Custom author-mode typography */
      [data-xml-element="codeblock"] {
        font-family: monospace;
        background: #f5f5f5;
        padding: 8px;
        border-radius: 4px;
      }
    `
  }));
});
```

>[!NOTE]
>
> 此CSS仅适用于新编辑器影子DOM。 它对页面的其余部分或旧版编辑器没有影响。


## 上下文菜单扩展(`contextMenuWidget`)

扩展可以通过在其扩展配置中声明`contextMenuWidget`字段来将项目添加到编辑器的右键单击/痕迹导航上下文菜单。 这会告知框架要定位哪个编辑器的菜单。

### 构件ID

| 构件ID | 编辑器 |
|---|---|
| `dita_editor_menu` | 旧版CKEditor创作表面（痕迹导航+元素上下文菜单） |
| `markup_editor_menu` | 新编辑器(ProseMirror)痕迹导航和元素上下文菜单 |

两个构件同时安装在页面上。 根据此字段，框架会将每个扩展与正确的菜单进行匹配。

> 扩展还可以通过传递数组来定位两个编辑器： `contextMenuWidget: ["dita_editor_menu", "markup_editor_menu"]`

### 旧版编辑器： `dita_editor_menu`

对于应显示在旧版CKEditor上下文菜单中的扩展，请使用此选项。

```js
const myContextMenuExtension = {
  id: "dita_author_view_menu",
  contextMenuWidget: "dita_editor_menu",
  view: {
    items: [
      {
        displayName: "My Custom Action",
        data: { eventid: "myCustomAction" },
        icon: "textSpaceAfter",
        target: {
          key: "displayName",
          value: "Wrap Element",   // insert after this existing menu item
          viewState: "append",
        },
      },
    ],
  },
  controller: {
    myCustomAction() {
      console.log("Custom action triggered");
    },
  },
};
```

### 新编辑器： `markup_editor_menu`

对于应显示在新编辑器上下文菜单（痕迹导航和右键单击元素）中的扩展，请使用此选项。 控制器通过`handleExtensionEvent`接收事件，它将本地处理程序路由到`markup_editor_menu`控制器，并通过应用程序事件处理程序调度全局事件。

```js
const myMarkupContextMenu = {
  id: "dita_author_view_menu",
  contextMenuWidget: "markup_editor_menu",
  view: {
    items: [
      {
        displayName: "Edit Cross Reference",
        data: { eventid: "editCrossReference" },
        icon: "link",
        target: {
          key: "displayName",
          value: "Cut",
          viewState: "prepend",
        },
      },
      {
        displayName: "Remove Cross Reference",
        data: { eventid: "removeCrossReference" },
        icon: "deleteOutline",
        target: {
          key: "displayName",
          value: "Edit Cross Reference",
          viewState: "append",
        },
      },
    ],
  },
  controller: {
    editCrossReference() {
      // Use guides.editor APIs to read context
      const ancestorXpaths = guides.editor.runUtil("getAncestorXpaths", true);
      // open dialog or take action...
    },
    removeCrossReference() {
      guides.editor.runCommand("unwrapNode");
    },
  },
};
```

## 实用工具库

- `guides.util.lodash`:The lodash实用程序库，与编辑器捆绑在一起的相同实例。

  ```js
  const uniqueIds = guides.util.lodash.uniq(ids);
  ```

- `guides.util.async`：用于扩展的异步实用工具库。

  ```js
  guides.util.async.parallel([task1, task2], callback);
  ```

## 完整API参考

| API | 描述 |
|---|---|
| `filePath` | 获取活动文档的文件路径 |
| `version` | 获取加载的编辑器版本字符串 |
| `appState(key)` | 从应用程序模型读取值 |
| `focus()` | 将焦点置于活动编辑器 |
| `canInsertXmlElement(tag, insertAfter?)` | 检查是否可以在光标处插入元素 |
| `selectCurrentBlockElement()` | 选择当前块元素 |
| `getValidElementNamesForInsertion(args)` | 列出要插入的有效元素名称 |
| `updateAttributeByXpath(args)` | 按XPath更新属性 |
| `runCommand(name, ...args)` | 执行命名编辑器命令 |
| `canRunCommand(name, ...args)` | 检查命令是否可以执行 |
| `runUtil(name, ...args)` | 调用命名编辑器实用程序 |
| `addDecoration(id, selector, options)` | 在匹配元素中添加或替换命名的修饰规则 |
| `removeDecoration(id)` | 按ID删除修饰规则 |
| `batchDecorations(changes)` | 在一个调度中应用多个添加/删除修饰更改 |
| `clearDecorations()` | 删除所有活动的修饰规则 |
| `getDecorations()` | 获取所有当前活动装饰的ID |
| `registerPlugin(factory)` | 注册ProseMirror插件工厂（也是影子DOM CSS注入的机制） |
| `prosemirror.state` | `prosemirror-state`包 |
| `prosemirror.model` | `prosemirror-model`包 |
| `prosemirror.view` | `prosemirror-view`包 |
| `prosemirror.transform` | `prosemirror-transform`包 |
| `prosemirror.commands` | `prosemirror-commands`包 |
| `prosemirror.keymap` | `prosemirror-keymap`包 |
| `prosemirror.history` | `prosemirror-history`包 |
| `prosemirror.tables` | `prosemirror-tables`包 |
| `prosemirror.dropcursor` | `prosemirror-dropcursor`包 |
| `prosemirror.collab` | `prosemirror-collab`包 |
| `prosemirror.markdown` | `prosemirror-markdown`包 |
