---
title: 在DITA AEM Guides中使用Markdown
description: 在DITA AEM Guides中迁移和使用Markdown
author: Pulkit Nagpal(punagpal)
exl-id: a94c0129-df40-4b61-ac60-679b2ffe7e86
TQID: https://experienceleague.adobe.com/z41KjrBkAeDaH-iKXOFLH44qOQElziip1FqcRhnKaUI
product_v2: id: fae5e35a-80c9-4b94-9352-1a060a6aab1did: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2: id: a3bd6397-2eb2-4908-a61c-226e26855dcaid: ab01a588-7dea-43f2-a699-0b3f128465d6
subfeature_v2: id: ad602516-aca3-4247-9ae8-f393d958efa9
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: 8ed5c9cb07c56b84b36ef56a55af8738989a6d3f
workflow-type: tm+mt
source-wordcount: 281
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


#### 发布到PDF和Web输出

AEM Guides提供了Web (Html5/AEM Site)和PDF (Native-PDF/DITA-OT)选项，用于发布包含Markdown内容的Ditamap

### 选项2 ：将Markdown转换为DITA格式

充分利用AEM Guides中提供的内容可重复使用、条件处理翻译、基线等功能。但是，需要提前将`.md`转换为`.dita`格式。

可以使用Adobe FrameMaker和DITA-OT等外部工具将Markdown转换为DITA。


对于Adobe FrameMaker，请参阅：[导入Markdown](https://www.adobe.com/in/products/framemaker/features.html#import-markdown)

对于DITA-OT，请参阅：[Markdown作为输入](https://www.dita-ot.org/dev/topics/markdown-input.html)

使用Adobe FrameMaker转换的示例文件：[Markdown转换为DITA示例](https://acrobat.adobe.com/id/urn:aaid:sc:AP:874881f3-ba43-410c-abc6-2df899536d79)

#### 发布到PDF和Web输出

一旦Markdown文件转换为DITA，用户即可将输出无缝发布到AEM Guides中可用的任何格式。

AEM Guides中的可用格式：[输出格式](../../../../user-guide/generate-output-understand-presets.md)
