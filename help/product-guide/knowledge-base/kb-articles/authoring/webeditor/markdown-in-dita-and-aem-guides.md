---
title: 在DITA AEM Guides中使用Markdown
description: 在DITA AEM Guides中迁移和使用Markdown
source-git-commit: b4235841798fb12b3d0491e33b4466073ac02ef3
workflow-type: tm+mt
source-wordcount: '256'
ht-degree: 0%

---

# 在AEM Guides中使用Markdown

## 可用选项

在AEM Guides中使用Markdown文件有2个选项：

- 选项1 ：在AEM Guides中导入现有Markdown，并直接在ditamap中使用它们进行发布

- 选项2 ：将现有Markdown文件转换为DITA

让我们讨论一下每个选项：

### 选项1：在AEM Guides中导入现有Markdown，并直接在ditamap中使用它们进行发布

它的设置更简单，实施更快。 但是，AEM Guides功能（如内容重复利用）的功能利用率有限。

用户需要添加属性`format="markdown" `或`format="mdita"`，以便发布引擎了解文件类型并相应地发布。

示例文件： [Markdown Ditamap](https://acrobat.adobe.com/id/urn:aaid:sc:AP:da31137e-be84-44fb-8974-d038eeff0283)

![参考屏幕快照](../../assets/authoring/markdown_map.png)


#### Publish到PDF和Web输出

AEM Guides提供了Web (Html5/AEM站点)和PDF(本机PDF/DITA-OT)选项，用于发布包含Markdown内容的ditamap

### 选项2 ：将Markdown转换为DITA格式

充分利用AEM Guides中提供的内容可重复使用、条件处理翻译、基线等功能。 但是，需要提前将`.md`转换为`.dita`格式。

可以使用Adobe FrameMaker和DITA-OT等外部工具将Markdown转换为DITA。


对于Adobe FrameMaker，请参阅：[导入Markdown](https://www.adobe.com/in/products/framemaker/features.html#import-markdown)

对于DITA-OT，请参阅：[Markdown作为输入](https://www.dita-ot.org/dev/topics/markdown-input.html)

使用Adobe FrameMaker转换的示例文件：[Markdown转换为DITA示例](https://acrobat.adobe.com/id/urn:aaid:sc:AP:874881f3-ba43-410c-abc6-2df899536d79)

#### Publish到PDF和Web输出

一旦Markdown文件转换为DITA，用户即可将输出无缝发布到AEM Guides中可用的任何格式。

AEM Guides中的可用格式：[输出格式](../../../../user-guide/generate-output-understand-presets.md)
