---
title: AEM Sites的组件映射
description: 了解如何为AEM Sites进行组件映射
feature: Installation
role: Admin
level: Experienced
exl-id: 376aea7a-7850-44d4-a620-6b1a798a0801
source-git-commit: beb1ca15fdfb0e7ea30e6e685ac67a2a398cc064
workflow-type: tm+mt
source-wordcount: '1042'
ht-degree: 0%

---

# AEM Sites的组件映射

本文讨论了AEM站点的组件映射（使用复合组件映射）的各个方面。

## 组件映射规则

使用JSON规则数组（您的`componentmapping.json`）将HTML转换为组件。 保持规则尽可能简单、明确和具体。

### 定位HTML元素及其类

- 在`name`中写入HTML标记名称。
- 在`class`中包含应用于该元素的CSS类（如果类存在）。
示例：

  ```html
  <div class ="sample-class">
  <p> Sample html element </p>
  </div>
  ```

  ```json
  {
  "name": "div",
  "class": "sample-class",
  "resourceType": "guides-components/components/table",
  "attributeMap": []
  }
  ```

在定义上述元素时，请确保满足以下条件：

- `name`可以是以逗号分隔的列表（例如，`"h1, h2"`）。
- 元素上必须存在`class`（所有列出的类必须匹配）。
- `resourceType`指示您打算使用`table`组件。 `guides-components`包是由Guides提供的OOTB。 您还可以根据需要使用其他组件包，如`core/wcm/`。

### 使用attributeMap保存JCR节点上的属性

将条目添加到`attributeMap`以设置输出节点的属性。 每个条目都会生成`attrs[to] = value`。
常见模式：

```json
// copy an attribute
{ "attribute": "src", "to": "image-src" }
// read content or tag name
{ "from": "textContent", "to": "jcr:title" }
{ "from": "outerHTML",  "to": "text" }
{ "from": "innerHTML",  "to": "text" }
{ "from": "name",       "to": "type" }  // the tag name, e.g., "h2"
// constant value
{ "value": true, "to": "textIsRich" }
```

以下是图像元素的HTML到JSON示例。

```html
<img src="/content/dam/aemg-docs/tragopan.svg" class="cmp-image__image" itemprop="contentUrl" data-cmp-hook-image="image" alt="">
```

```json
{
    "name": "img",
    "resourceType": "core/wcm/components/image/v2/image",
    "attributeMap": [
      {
        "from": "src",
        "to": "fileReference"
      },
      {
        "value": ["fileReference"],
        "to": "path-attributes"
      }
    ]
  }
```

### 通过专用条目标准化路径

如果要标准化（生成绝对）值，请使用以下内容声明应标准化的属性键：

```json
{
  "value": ["text"],
  "to": "path-attributes"
}
```

确保注意以下重要事项：

- 将您要规范化的属性名称列表放在`value`中（例如，`["text"]`或`["href", "src"]`）。
- 在构建最终组件时，系统将标准化在这些属性名称下找到的任何值。


### 在拆分为组件之前提取HTML值

使用`from`指定在将文档拆分为单独的组件之前如何从元素中读取值：

- `"textContent"`：元素的纯文本
- `"outerHTML"`：元素及其内部标记
- `"innerHTML"`：仅元素的内部标记
- 任何其他字符串：被视为属性名称（例如，`"src"`、`"href"`）


示例：

```json
{ "from": "textContent", "to": "jcr:title" }
{ "from": "outerHTML",  "to": "text" }
{ "from": "innerHTML",  "to": "snippet" }
{ "from": "src",        "to": "image#src" }
```

### componentmapping.json中的最小端到端示例

```json
[
  {
    "name": "h1, h2",
    "class": "topic-title",
    "resourceType": "core/wcm/components/title/v2/title",
    "attributeMap": [
      { "from": "textContent", "to": "text" },
      { "from": "name",        "to": "type" }
    ]
  },
  {
    "name": "img",
    "class": "hero",
    "resourceType": "weretail/components/content/heroimage",
    "attributeMap": [
      { "from": "src", "to": "image#src" },
      { "value": ["image#src"], "to": "path-attributes" }
    ]
  },
  {
    "name": "#element",
    "resourceType": "core/wcm/components/text/v2/text",
    "attributeMap": [
      { "from": "outerHTML", "to": "text" },
      { "value": true,        "to": "textIsRich" }
    ]
  }
]
```

定义要定位的元素和类，使用`attributeMap`设置节点属性，添加`path-attributes`条目以标准化路径，并为要提取的值选择正确的`from`。 上面使用的`heroimage`是`we-retail`站点中的组件。

**注意**：请务必讨论默认富文本，并识别使用它的元素。

## 构建自定义组件

了解如何创建在其单元格中显示图像的自定义表组件。 此方法可确保为动态内容提供干净且可重用的设计。 它涵盖了您将构建的内容、为什么它有效、关键先决条件、高级设计等。

### 您将构建的内容

一个自定义表组件，它接受HTML表内容并将其中的每`<img>`替换为AEM核心图像组件的输出。 这让您可以重复使用核心图像的功能（响应式图像、替代处理、辅助功能），同时保持对表标记的完全控制。
使用此方法，您可以为AEM站点构建其他自定义组件（使用复合组件映射）。

### 为什么选择这种方法

- **重用**：利用核心映像的成熟行为，而不是重新实现它。
- **一致性**：您表中的映像的行为与网站上其他位置的映像相同。
- **服务器端**：图像在服务器上呈现，以实现性能、SEO和可访问性。

### 先决条件

- AEM SDK正在运行，并签出了此项目。
- AEM实例上安装的核心组件。
- Maven可用于构建和部署。

### 高级设计

- 作者在组件对话框中为表提供了HTML。
- Sling模型解析HTML，找到`<img>`个标记，并为每个图像调用一个在服务器端呈现核心图像组件的服务。
- 该模型将原始`<img>`与捕获的核心图像HTML交换，并将已完成的HTML传递给HTL输出。

您的表只输出一次，已包含核心图像标记。 无需客户端DOM操作。

### 文件夹结构和关键文件（在此存储库中）

- 组件HTL和clientlibs： `ui.apps/src/main/content/jcr_root/apps/guides-components/components/table/`
   - `table.html` （HTL渲染器）
   - `_cq_editConfig.xml` （刷新侦听器）
   - `clientlibs/`与`css.txt`，`js.txt`，`css/table.css`，`js/table.js`
- Sling模型： `core/src/main/java/com/adobe/guides/aem/components/core/models/TableModel.java`
- 图像渲染服务： `core/src/main/java/com/adobe/guides/aem/components/core/services/ImageComponentRenderer.java`

### 实施步骤

**定义表组件（组件节点）**

在`apps/guides-components/components/table`下创建组件。 如果您还没有模板文件，请添加下面的最小`.content.xml`以在侧面板中注册它。

```xml
<?xml version="1.0" encoding="UTF-8"?>
<jcr:root xmlns:sling="http://sling.apache.org/jcr/sling/1.0"
          xmlns:jcr="http://www.jcp.org/jcr/1.0"
          jcr:primaryType="cq:Component"
          jcr:title="Table"
          componentGroup="Guides - Custom"/>
```

向AEM指示这是一个可供作者添加到页面的组件。

**使用HTL渲染并包含样式**

使用Sling模型并输出已处理的HTML。 包含您的CSS/JS clientlib类别。

```html
<sly data-sly-use.model="com.adobe.guides.aem.components.core.models.TableModel"
     data-sly-use.clientLib="/libs/granite/sightly/templates/clientlib.html">
</sly>
<sly data-sly-call="${clientLib.css @ categories='guides-components.table'}"></sly>
<sly data-sly-test="${wcmmode.edit && !model.hasContent}">
  <div class="cq-placeholder" data-emptytext="${component.title}"></div>
</sly>
<div data-sly-test="${model.hasContent}"
     class="gu-table-wrapper ${model.enableResponsive ? 'gu-table--responsive' : ''} gu-table--style-${model.tableStyle}"
     id="${model.componentId}">
  ${model.processedTableHtml @ context='unsafe'}
</div>
```

该模型会返回完整的HTML，并且核心图像已渲染，因此HTL只打印它。

**添加Sling模型以处理HTML并渲染核心图像**

模型读取对话框字段，解析表HTML，找到每个`<img>`，然后通过服务将其替换为核心图像HTML。

以下是`TableModel`的一些重要知识：

- 从资源属性中读取`tableHtml`、`enableResponsive`、`tableStyle`。
- 使用Jsoup安全地解析和编辑HTML。
- 调用`ImageComponentRenderer`以渲染核心图像并捕获HTML。
- 保留原始`<img>`中的CSS类和样式。
- 标准化DAM路径（删除`/jcr:content/renditions/*`）。

```java
@Model(adaptables = {Resource.class, SlingHttpServletRequest.class},
       defaultInjectionStrategy = DefaultInjectionStrategy.OPTIONAL)
public class TableModel {
  @ValueMapValue private String tableHtml;
  @ValueMapValue private boolean enableResponsive;
  @ValueMapValue private String tableStyle;
  @OSGiService private ImageComponentRenderer imageRenderer;
  // ...
  @PostConstruct
  protected void init() {
    // parse HTML, for each <img> build image props (fileReference, alt, title)
    // call imageRenderer.renderImageComponent(...)
    // replace <img> with returned Core Image HTML
  }
  public String getProcessedTableHtml() { /* return final HTML */ }
}
```

这会集中服务器上的逻辑并重用核心图像行为。

**通过服务（服务器端包含）渲染核心图像**

`ImageComponentRenderer`渲染核心图像组件并捕获输出。 It

- 封装强制`core/wcm/components/image/v2/image`的资源。
- 使用`RequestDispatcher#include`渲染它。
- 将响应捕获为字符串。

```java
@Component(service = ImageComponentRenderer.class)
public class ImageComponentRenderer {
  private static final String IMAGE_RESOURCE_TYPE = "core/wcm/components/image/v2/image";
  public String renderImageComponent(Resource base, Map<String,Object> props,
                                     SlingHttpServletRequest req, SlingHttpServletResponse resp) {
    // create wrapped resource with IMAGE_RESOURCE_TYPE and props
    // dispatcher.include(...) with a response wrapper to capture HTML
    // return captured HTML
  }
}
```

这样，您就可以&#x200B;**放入**&#x200B;核心图像所需的任何位置，而不只是将其作为子组件。

**客户端库**

为小样式或未来JS创建clientlib。 上述HTL加载`guides-components.table`类别。

```java
clientlibs/css.txt
  #base=css
  table.css
clientlibs/js.txt
  #base=js
  table.js
  
```

这可使样式/脚本保持模块化且可发现。

**对话框字段（作者输入）**

添加至少具有以下属性的对话框：

- **表HTML**： `./tableHtml` (textarea)；表的HTML。
- **启用响应式**： `./enableResponsive` （复选框）；切换响应式包装器类。
- **表样式**： `./tableStyle` （选择）；应用样式修饰符类。

这些将1:1映射到Sling模型的属性和控件渲染。

**在模板上允许该组件**

在模板编辑器中，编辑布局容器策略>允许的组件>在&#x200B;**指南 — 自定义**&#x200B;下启用表组件。

在策略允许之前，作者无法添加组件。

## 创作提示

- 粘贴表的有效HTML。 该模型可清理和调整图像URL。
- 对图像使用DAM资源路径；将演绎版标准化为原始资源路径。
- 尽可能在HTML中提供替换文本；否则，图像将标记为装饰性。

## 约束

- 该服务强制核心映像v2。 若要切换版本，请更新`IMAGE_RESOURCE_TYPE`。
- 对于合成渲染，模型会将核心图像生成的`.coreimg.`个URL替换为直接DAM路径，并删除`srcset`以避免损坏的URL。
- 所有渲染在服务器上执行一次；JavaScript是可选的。

## 快速参考（实施）

- HTML： `ui.apps/.../components/table/table.html`
- Clientlibs： `ui.apps/.../components/table/clientlibs/`
- 模型： `core/.../models/TableModel.java`
- 服务： `core/.../services/ImageComponentRenderer.java`

此模式显示如何使用核心组件服务器端构建自定义组件，在重用核心逻辑时保留您的标记。
