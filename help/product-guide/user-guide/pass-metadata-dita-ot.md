---
title: 使用DITA-OT将元数据传递到输出
description: 了解如何使用AEM Guides中的DITA-OT发布将元数据传递到输出。
exl-id: 70ca32dc-56c3-45ee-b6b9-0efb8cc79ea1
feature: Publishing, Metadata Management
role: User
source-git-commit: ac83f613d87547fc7f6a18070545e40ad4963616
workflow-type: tm+mt
source-wordcount: '571'
ht-degree: 0%

---

# 使用DITA-OT将元数据传递到输出 {#id21BJ00QD0XA}

元数据是有关输出的其他信息。 在Adobe Experience Manager Guides中，您可以传递现有元数据或创建自定义元数据标记。 您可以使用DITA-OT发布将元数据传递到AEM、PDF、HTML5、EPUB和自定义格式输出。

使用DITA-OT时，可通过两种方式将元数据传递到输出：

- [使用地图控制台](#using-map-console)
- [使用地图仪表板](#using-map-dashboard)

## 使用地图控制台

执行以下步骤，使用DITA-OT发布将元数据传递到输出：

1. [在映射控制台](./open-files-map-console.md)中打开要为其将元数据传递到DITA-OT的DITA映射文件。
1. 选择并打开要向其传递元数据字段的输出预设。 例如，选择PDF输出预设。 确保使用&#x200B;**DITA-OT**&#x200B;选项创建它。
1. 从&#x200B;**文件属性**&#x200B;下拉列表中，选择要传递到DITA-OT发布的元数据。

   ![](images/custom-metadata-output-preset-new.png){align="left"}

   “属性”下拉列表同时列出了自定义属性和默认属性。 例如，在上面的屏幕快照中，`dc:description`、`dc:language`、`dc:title`和`docstate`是默认属性。

   >[!NOTE]
   >
   > 这些属性是从以下位置可用的metadataList文件中选取的： `/libs/fmdita/config/metadataList`。 默认情况下，此文件中列出了四个属性 — `dc:description`、`dc:language`、`dc:title`和`docstate`。

   此文件可以覆盖在： `/apps/fmdita/config/metadataList`。

   要传递已为其定义值的自定义属性，请查看[在DITA-OT PDF输出中使用AEM元数据](https://experienceleaguecommunities.adobe.com/t5/xml-documentation-discussions/use-aem-metadata-in-dita-ot-pdf-output/td-p/411880)。

1. 所选属性列在下拉列表下方。

   ![](images/metadata-added-dropdown.png){width="300" align="left"}

1. 选择右上方的&#x200B;**保存**&#x200B;以保存更改。
1. 选择&#x200B;**生成输出**。

所选的元数据属性将传递到使用DITA-OT生成的输出。

>[!NOTE]
>
> 自2502版Experience Manager Guides起，通过DITA-OT命令行传递根映射元数据参数的功能已被弃用。 但是，为了避免出现任何中断，`Config.Manager`中添加了一个新属性以启用或禁用该功能。  有关详细信息，请查看[配置输出生成设置](../cs-install-guide/conf-output-generation.md#configure-the-dita-ot-command-line-arguement-field-on-the-dita-map-dashboard)。

## 使用地图仪表板

如果使用&#x200B;**Assets UI**，请执行以下步骤，以使用DITA-OT发布将元数据传递到输出：

1. 在&#x200B;**Assets UI**&#x200B;中，导航到要为其将元数据传递到DITA-OT的DITA映射文件并选择该文件。
1. 选择并编辑要向其传递元数据字段的输出预设。 例如，选择PDF输出预设。
1. 在所选输出预设中选择&#x200B;**DITA-OT**&#x200B;选项。

   ![](images/custom-meta-data-output-preset.png){align="left"}

1. 从属性下拉列表中选择要传递到DITA-OT发布的元数据。

   “属性”下拉列表同时列出了自定义属性和默认属性。 例如，在上述屏幕快照作者中，是自定义属性，而`dc:description`、`dc:language`、`dc:title`和`docstate`是默认属性。

   >[!NOTE]
   >
   > 这些属性是从以下位置可用的metadataList文件中选取的： `/libs/fmdita/config/metadataList`。 默认情况下，此文件中列出了四个属性 — `dc:description`、`dc:language`、`dc:title`和`docstate`。

   此文件可以覆盖在： `/apps/fmdita/config/metadataList`。

   要传递已为其定义值的自定义属性，请查看[在DITA-OT PDF输出中使用AEM元数据](https://experienceleaguecommunities.adobe.com/t5/xml-documentation-discussions/use-aem-metadata-in-dita-ot-pdf-output/td-p/411880)。

1. 从&#x200B;**属性**&#x200B;下拉列表中，选择所需的自定义属性和默认属性。 例如，选择`author`、`dc:title`和`dc:description`。 这些是在我们创建文件后创建的标准`metadata/properties`。 选定的属性列在收存箱的下方。

   ![](images/selected-metadata-properties.png){width="300" align="left"}

1. 选择左上方的&#x200B;**完成**&#x200B;以保存更改。
1. 生成输出。

所选的元数据属性将传递到使用DITA-OT生成的输出。



**父主题：**&#x200B;[&#x200B;输出生成](generate-output.md)
