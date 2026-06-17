---
title: 原生PDF的新发布引擎 | PDF输出生成
description: 了解如何使用新的发布引擎进行本机PDF发布
feature: Publishing, Native PDF Output
role: User
TQID: https://experienceleague.adobe.com/GV3iYtBdFVrQwFjdvfqnfDIWPMugO3hFjS4FZqspG2M
product_v2: id: fae5e35a-80c9-4b94-9352-1a060a6aab1did: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2: id: a3bd6397-2eb2-4908-a61c-226e26855dcaid: ab01a588-7dea-43f2-a699-0b3f128465d6id: afb45297-4313-4f67-818e-bc0b03abe086id: cb8c6a2a-3c38-4e40-867c-756f8c36bb0e
subfeature_v2: id: ad602516-aca3-4247-9ae8-f393d958efa9id: d6596f3f-92a7-43ec-b444-237db6adad05id: f6b497f1-f8e0-42ce-8e95-56c28d94026eid: f9dbea21-a714-40dd-bc90-080d8046c93fid: fd6cc9e1-e5e5-494e-b7b1-a32f2d6cd7c9
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2: id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dcid: cc72dcf1-72e1-48cc-b434-e7c27d62d67cid: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: 39af88b1d4bd424a8e56f3a217bcd8ee79f4be15
workflow-type: tm+mt
source-wordcount: 844
ht-degree: 0%

---

# 使用本机PDF引擎v2

新发布引擎&#x200B;*原生PDF引擎v2*&#x200B;基于升级的PDF生成框架，并包括对字体处理、CSS处理和渲染行为的更改。

因此，使用新发布引擎生成的PDF输出可能与使用现有PDF引擎生成的输出不同（*原生PDF引擎v1*）。 在文本布局、间距、样式、图像渲染和脚注格式等区域中，差异可能可见。

例如，本机PDF引擎v2支持`OpenType`字体，而本机PDF引擎v1主要依赖于`TrueType`字体。 类似的渲染增强功能可能会影响生成的PDF的整体外观。

有关如何在您的环境中启用本机PDF引擎v2的详细信息，请查看[为本机PDF配置新发布引擎](./conf-new-pdf-engine.md)。

## 建议新发布引擎使用的CSS更新

如果要在使用本机PDF引擎v2时恢复本机PDF引擎v1生成的PDF输出的外观，您可能需要更新自定义CSS。 下面介绍的建议CSS更改有助于在启用新设置后维护输出一致性。

| 描述 | 建议的CSS更新 |
|-------------|------------------------------------------------|
| 缩放的图像可能会因图像渲染行为的更改而显示不同。 | 要恢复图像渲染行为，请添加：<br><br> `image-rendering: pixelated` |
| 目录引线(TOC)对齐方式可能会因引线渲染行为的更改而略有不同。 | 要恢复目录引线对齐，请调整自定义样式表中目录引线元素的样式。 所需的CSS更改可能会因您的目录布局和格式而异。 |
| 由于字体渲染和字形布局处理中的更改，文本间距和换行可能会有所不同。 | 如果您的样式表使用`sans-serif`字体系列或显示间距差异的字体，请添加：<br><br> `-ro-glyph-layout-mode: quality;` |
| 由于默认脚注样式发生了更改，脚注引用可能不再显示为上标标记。 | 要恢复上标样式的脚注标记，请添加：<br><br>`.fn::footnote-marker` <br> `{ content: counter(footnote) " ";`<br> `vertical-align: super;`<br>`font-size: 65%;}` |
| 由于下划线位置的更改，文本与下划线之间的间距可能会增加，因此下划线文本可能会出现。 | 要恢复下划线位置，请使用`text-underline-offset`属性并根据需要调整偏移值。 例如：<br><br>`text-decoration: underline;`<br>`text-underline-offset: -0.1em;` |
| 列表标记和列表项文本之间的间距可能会因列表渲染行为的更改而有所不同。 | 要恢复间距，请增加列表项的左边距。 例如：<br><br>`.step {`<br> ` margin-top: 0.3rem;`<br> `margin-bottom: 0.5rem;`<br> `padding-left: calc(1.5rem + 1ch);}` |
| 由于边距折叠行为的变化，标题前的间距可能会有所不同。 | 要恢复间距，请检查相邻元素的边距，并根据需要减少或移除重叠的顶边距和底边距。 例如：<br><br>`h1.chapter { `<br> `margin-top: 0;` <br>`}`<br>`chaptoc-body { margin-bottom: 0;`<br>` }` |
| 通过CSS生成的复选标记可能以不同的大小或样式显示，因为它们使用不同的回退字体渲染。 | 要以一致的方式呈现标记，请使用包含两个字形的字体系列。 例如：<br><br>`::marker {`<br> `font-family: -ro-symbols !important;}` |
| 由于标记的位置行为发生更改，CSS生成的圆形列表标记可能会出现部分剪切或截断。 | 要恢复圆形列表标记的外观，请避免使用标记的绝对定位。 如果需要绝对定位，请明确指定适当的`top`值以正确定位标记。 |
| 当列表项使用`position: relative`等定位样式时，PDF/UA输出中列表项的读取顺序可能会有所不同。 | 若要使阅读顺序更遵循源文档结构，请将以下CSS属性应用于列表项：<br><br>`li {`<br>`-ro-paint-reordering: avoid;}` |


## 已知问题的解决方法

使用本机PDF引擎v2时，以下解决方法可以帮助解决生成的PDF输出中的已知问题。

- 应用于表内容的`text-decoration` css属性未在PDF输出中渲染。

  **解决方法**：将文本修饰属性应用于表内容中的`span`元素，而不是将其直接应用于表元素。

- `-ro-colorbar-top-left`和`-ro-colorbar-top-right` CSS属性不会影响PDF输出中的颜色栏。

  **解决方法**：从`mergedHTML.json`中的用户样式表中删除相应的值，或者将`!important`添加到文档CSS中的属性值，以便这些值不会被用户样式表覆盖。

- 当页面宽度受限时，色条可能会显示为合并，因为色条不会随PDF输出中的页面大小而缩小。

  **解决方法**：在页面的不同侧面显示灰色和彩色条，或者调整颜色条设置，以使它们在较小的页面宽度上不重叠。

## 修复了新发布引擎的问题

使用&#x200B;_本机PDF引擎v1_&#x200B;生成的PDF输出中的以下问题已在&#x200B;_本机PDF引擎v2_&#x200B;中修复：

- 在为某些内容生成本机PDF输出时，尽管中间HTML包含多个页面中的完整内容，但PDF中仅呈现第一页。 （指南 — 28270）
- 启用了辅助功能设置的本机PDF输出中的内容读取顺序不正确。 页脚中的页码在主内容之前而不是结尾处读取。 （指南 — 27790）
- 当自定义页面大小时，原生PDF输出中的颜色条不会拉伸整个页面宽度，并且会重叠，从而导致隐藏某些颜色框。 （指南 — 15505）
- 本机PDF输出中不允许`CSS:is()pseudo-class`选择器，从而导致样式与浏览器呈现样式不同。 （指南 — 11328）