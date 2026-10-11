---
title: 使用DITA-OT将元数据传递到输出
description: 了解如何使用AEM Guides中的DITA-OT发布将元数据传递到输出。
feature: Publishing, Metadata Management
role: User
hide: true
exl-id: 55d70c6d-feb0-43f7-9f18-6d1ccdd1e728
TQID: 'https://experienceleague.adobe.com/I-DddG1Wq9cXsF1IZt6B0XFzbR1gbtvtKPoO-g2nLM0'
product_v2:
  - id: fae5e35a-80c9-4b94-9352-1a060a6aab1d
    internal-label: Experience Manager Guides
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
feature_v2:
  - id: a3bd6397-2eb2-4908-a61c-226e26855dca
    internal-label: Publishing
  - id: f59890ff-de81-47d5-9ef8-7ab2dd10c6c3
    internal-label: Authoring and publishing content
  - id: e88e74c7-6080-446a-8eb0-496f1ac5f7e6
    internal-label: Administration
subfeature_v2:
  - id: fd6cc9e1-e5e5-494e-b7b1-a32f2d6cd7c9
    internal-label: Output generation
  - id: f901afa4-5613-4581-add5-219fa5f03fb5
    internal-label: Publishing
  - id: da9cce28-0561-45e7-851e-4500741b9744
    internal-label: Metadata management
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
topic_v2:
  - id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dc
    internal-label: Metadata
  - id: ebde5b41-29c9-4f5e-9ef6-1197e85409e3
    internal-label: Data management
source-git-commit: 81a0e7f0736ba4970673dd87a888a4c60d3c1b4e
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 0%
---
# 使用DITA-OT将元数据传递到输出 {#id21BJ00QD0XA}

元数据是有关输出的其他信息。 在AEM Guides中，您可以传递现有元数据或创建自定义元数据标记。 您可以使用DITA-OT发布将元数据传递到AEM、PDF、HTML5、EPUB和自定义格式输出。

执行以下步骤，使用DITA-OT发布将元数据传递到输出：

1. 在&#x200B;**Assets UI**&#x200B;中，导航到要为其将元数据传递到DITA-OT的DITA映射文件并单击该文件。
1. 选择并编辑要向其传递元数据字段的输出预设。 例如，选择PDF输出预设。
1. 在所选输出预设中的生成&lt;output\>使用选项下选择&#x200B;**DITA-OT**。

   ![](images/custom-meta-data-output-preset.png){width="800"}

1. 从属性下拉列表中选择要传递到DITA-OT发布的元数据。

   “属性”下拉列表同时列出了自定义属性和默认属性。 例如，在上述屏幕快照作者中，是自定义属性，而`dc:description`、`dc:language`、`dc:title`和`docstate`是默认属性。

   >[!NOTE]
   >
   > 这些属性是从以下位置可用的metadataList文件中选取的： `/libs/fmdita/config/metadataList`。 默认情况下，此文件中列出了四个属性 — `dc:description`、`dc:language`、`dc:title`和`docstate`。

   此文件可以覆盖在： `/apps/fmdita/config/metadataList`。

   要传递已为其定义值的自定义属性，请参阅[在DITA-OT PDF输出中使用AEM元数据](https://experienceleaguecommunities.adobe.com/t5/xml-documentation-discussions/use-aem-metadata-in-dita-ot-pdf-output/td-p/411880?profile.language=zh-Hans)。

1. 从&#x200B;**属性**&#x200B;下拉列表中，选择所需的自定义属性和默认属性。 例如，选择`author`、`dc:title`和`dc:description`。 这些是在我们创建文件后创建的标准`metadata/properties`。 选定的属性列在收存箱的下方。

   ![](images/selected-metadata-properties.png){width="300"}

1. 单击左上方的&#x200B;**完成**&#x200B;以保存更改。
1. 生成输出。

所选的元数据属性将传递到使用DITA-OT生成的输出。

**父主题：**&#x200B;[&#x200B;输出生成](generate-output.md)
