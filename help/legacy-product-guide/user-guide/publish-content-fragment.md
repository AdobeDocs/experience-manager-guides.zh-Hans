---
title: Publish内容片段的主题
description: 在AEM Guides中，将主题或主题中的元素Publish为内容片段。  了解如何查看呈现给某个主题的内容片段并重新发布它们。
feature: Publishing
role: User
source-git-commit: 76c731c6a0e496b5b1237b9b9fb84adda8fa8a92
workflow-type: tm+mt
source-wordcount: '925'
ht-degree: 0%

---

# Publish内容片段

内容片段是Adobe Experience Manager中的离散内容片段。 它们是基于内容模型的结构化内容。 内容片段是纯内容，没有设计或布局信息。 它们可以独立于AdobeExperience Manager支持的渠道进行创作和管理。 内容片段是模块化的，其中的内容被划分为较小的组件。

Adobe Experience Manager Guides允许您将主题或主题中的元素发布到内容片段。 您可以在主题和内容片段模型之间创建基于JSON的映射。 使用此映射将主题或主题中的元素发布到内容片段。 然后，您可以在任何Adobe Experience Manager站点中使用内容片段或通过内容片段支持的API提取详细信息。


要创建内容片段，请执行以下步骤：

1. 在Adobe Experience Manager Assets中创建[内容片段模型](https://experienceleague.adobe.com/docs/experience-manager-65/assets/content-fragments/content-fragments-models.html?lang=zh-Hans)。
1. 创建一个文件夹，以保存您根据内容片段模型创建的内容片段。 例如，“stock-content-fragments”。
1. 编辑文件夹的属性（例如，“stock-content-fragments”）并添加文件夹的路径，其中包含云配置中的内容片段模型。
例如，在云配置中添加`/conf/we-retail`。 此配置将所有内容片段模型连接到文件夹。\
   ![在文件夹属性中添加云配置详细信息](images/fragment-folder-cloud-configuration.png){width="650" align="left"}
   *在文件夹属性中添加云配置以将其与片段模型连接。*

1. 要生成内容片段，请从主题&#x200B;**文件属性**&#x200B;的&#x200B;**输出**&#x200B;节中选择&#x200B;**新输出** ![新输出图标](./images/Add_icon.svg)。
1. 选择&#x200B;**内容片段**。\
   ![文件属性选项选项卡](./images/file-properties-outputs-tab.png){width="300" align="left"}

   *从主题*&#x200B;的文件属性中添加新的内容片段。

1. 在&#x200B;**生成内容片段**对话框中，填写以下详细信息：
   ![在Publish中添加片段模型和映射详细信息作为内容片段对话框](images/content-fragment-publish.png){width="500" align="left"}
   *添加路径、模型和映射详细信息，将主题或其元素发布为内容片段。 您可以覆盖现有的内容片段。*

   >[!NOTE]
   >
   >您还可以从&#x200B;**存储库视图**&#x200B;发布内容片段。 选择要作为内容片段发布的主题。 然后，从&#x200B;**选项**&#x200B;菜单中选择&#x200B;**Publish As** > **内容片段**。

   * **路径**：浏览并选择要发布内容片段的文件夹的路径。 如果选择现有的内容片段，则会覆盖映射字段的内容。
   * **标题**：键入内容片段的标题。 默认情况下，标题中填充了主题的标题。 您可以对其进行编辑。 此标题用于生成内容片段的名称。
   * **名称**：键入内容片段的名称。 默认情况下，该名称将填充主题标题，空格将替换为“_”。 例如，*sample_content_fragment*。 您可以对其进行编辑。  此名称用于生成内容片段的URL。
   * **模型**：选择要用于创建内容片段的内容片段模型。 将从已在云服务中配置的文件夹中选取模型。
   * **映射**：从下拉列表中选择映射。 它会从&#x200B;*contentFragmentMapping.json*&#x200B;文件中选取映射。



     您的管理员可以在&#x200B;*contentFragmentMapping.json*&#x200B;文件中添加映射。 请参阅安装和配置指南以了解有关如何[创建主题和内容片段之间的映射](/help/product-guide/cs-install-guide/conf-content-fragment-mapping-cs.md)的详细信息。

   * 您还可以选择不同的条件来发布内容。  选择以下选项之一：


      * **无**：如果不想对已发布的输出应用任何条件，请选择此选项。
      * **使用DITAVAL**：选择DITAVAL文件以生成包含特定内容的输出。 可使用浏览对话框或键入文件路径来选择DITAVAL文件。
      * **使用属性**：您可以在DITA主题中定义条件属性。 然后选择条件属性以发布相关内容。
     >[!NOTE]
     > 
     >仅当在主题中定义了条件属性时，才会启用条件。



   * 如果您的内容片段已存在，并且要覆盖现有内容，请选择&#x200B;**覆盖现有内容**。 如果您未选中复选框并且您的内容片段已存在，则Experience Manager Guides会显示错误。
1. 单击&#x200B;**生成**&#x200B;以发布内容片段。

1. 您可以在&#x200B;**文件属性**&#x200B;的&#x200B;**输出**&#x200B;部分下查看主题的内容片段。

   ![查看主题的内容片段](images/outputs-options-menu.png){width="300" align="left"}

   *查看某个主题存在的内容片段并重新发布它们。*


发布内容片段后，还可以在任何Adobe Experience Manager站点中使用它们。




## 内容片段的“选项”菜单

您还可以从&#x200B;**选项**&#x200B;菜单为内容片段执行以下操作：

* **生成**：重新发布内容片段以使用DITA主题中的最新内容对其进行更新。 在重新生成输出时，无法更改内容片段的路径、名称、标题、模型和映射。 但是，在再生输出时可以选择不同的条件。

* **重复**：重复内容片段。 您可以更改路径、名称、标题、模型和映射。 在复制内容片段时，您还可以选择不同的条件。

* **移除**：从输出列表中移除内容片段。 出现确认提示。 确认后，内容片段将从&#x200B;**输出**&#x200B;列表中删除。

  >[!NOTE]
  >
  > 此操作不会从内容片段中删除任何内容。

* **视图**：查看内容片段编辑器。 您还可以进行更改并保存它们。


