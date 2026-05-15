---
title: PDF预设类型
description: 了解您可以使用Adobe Experience Manager Guides创建的PDF预设的类型。
exl-id: f12c91fd-3f95-478e-a9cd-68d037206ee8
feature: Publishing
role: User
TQID: https://experienceleague.adobe.com/RN5CYho8TpklBivMgK6ifb--eTwlBQgD-1jNU8HvF7E
product_v2:
  - id: fae5e35a-80c9-4b94-9352-1a060a6aab1d
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: a3bd6397-2eb2-4908-a61c-226e26855dca
subfeature_v2:
  - id: d5ea0417-7932-4688-a3e2-4d3b2e7076a3
  - id: d6596f3f-92a7-43ec-b444-237db6adad05
  - id: f9dbea21-a714-40dd-bc90-080d8046c93f
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
source-git-commit: 8ed5c9cb07c56b84b36ef56a55af8738989a6d3f
workflow-type: tm+mt
source-wordcount: 330
ht-degree: 0%

---

# PDF输出预设概述 {#id205BE600HAH}

借助Experience Manager Guides，您可以创建PDF预设以生成各个主题的PDF或整个映射文件。 您可以使用以下三种方法之一，以PDF格式发布内容：

**DITA-OT**

使用此方法可从地图控制台或地图仪表板为地图生成PDF输出。 您可以通过在地图控制台或地图功能板中为打开的地图创建输出预设，在生成PDF之前设置发布属性。

有关使用DITA-OT方法创建PDF输出预设的详细信息，请查看[创建DITA-OT PDF输出预设](./generate-output-pdf-dita-ot.md)

**FrameMaker Publishing Server (FMPS)**

>[!NOTE]
>
> FMPS发布选项仅在“地图”功能板中可用。

使用此方法可从PDF存储库中可用的DITA内容以及FrameMaker文档(.book和.fm)生成AEM输出。 PDF可通过配置输出预设来创建，并使用FrameMaker Publishing Server (FMPS)发布。 您可以为PDF和其他格式设计和配置输出的外观，并将其存储在设置文件(.sts)中。 然后，FMPS使用此设置文件来生成DITA映射或.book文件的输出。 要创建或编辑输出预设，请查看[了解输出预设](../user-guide/generate-output-understand-presets.md)。

有关配置FMPS的详细信息，请查看[从FrameMaker文档生成输出](../user-guide/fm-output-generatation.md)。

**本机PDF**

使用此方法可根据W3C CSS3和CSS分页媒体标准生成功能丰富的PDF输出。 通过本机PDF发布，您可以使用模板来设置内容的布局和样式，并应用各种设置来微调PDF。 此外，您可以使用模板编辑器修改和创建自己的模板。

有关创建本机PDF预设的详细信息，请查看[创建本机PDF输出预设](../web-editor/native-pdf-web-editor.md)。





**父主题：**&#x200B;[&#x200B;了解输出预设](generate-output-understand-presets.md)
