---
title: Publish指向体验片段的主题
description: 在AEM Guides中，将主题或主题中的元素Publish为体验片段。  了解如何查看呈现给某个主题的体验片段并重新发布它们。
feature: Publishing
role: User
source-git-commit: 76c731c6a0e496b5b1237b9b9fb84adda8fa8a92
workflow-type: tm+mt
source-wordcount: '995'
ht-degree: 0%

---

# Publish Experience Fragments

体验片段是Adobe Experience Manager中的模块化内容片段。 这些内容块基于模板并封装内容及其布局。 这些可重复使用的内容片段允许内容创建者跨Experience Manager支持的多个渠道组合并提供一致的可扩展体验。 此功能可帮助您轻松高效地创建一致的营销体验，例如新闻稿、促销横幅和客户评价。

Experience Manager Guides允许您将主题或其元素发布到体验片段。 您可以在主题及其体验片段中的元素之间创建基于JSON的映射。 然后，使用映射将主题或其元素发布到体验片段。 然后，您可以在任何Experience Manager站点中使用体验片段，或通过体验片段支持的API提取详细信息。




要生成体验片段，请执行以下步骤：


1. 在体验片段中创建文件夹。 使用此文件夹可保存您基于体验片段模板创建的体验片段。 例如，*sales-experience-fragments*。
1. 选择文件夹，然后从顶部选择&#x200B;**属性**&#x200B;图标。
1. 编辑文件夹的属性（例如，*sales-experience-fragments*）。


   * **标题**：查看或编辑文件夹的标题。

   * **允许的模板**：包含可作为Experiencefragment的子页面添加的模板列表。 要添加允许的模板，请在&#x200B;**允许的模板**字段中指定用于检索所需模板的正则表达式。
例如：
     `/libs/cq/experience-fragments/components/experiencefragment/template`

     如果没有为文件夹定义允许的模板，则默认情况下会从父文件夹或模板文件夹中选取模板。
   * **可排序**：允许您更改文件夹中资产的顺序。
     ![在文件夹属性中添加云配置详细信息](images/experience-fragment-folder-properties.png){width="650" align="left"}
     *在文件夹属性中添加云配置以将其与片段模板连接。*
1. 要生成体验片段，请从主题&#x200B;**文件属性**&#x200B;的&#x200B;**输出**&#x200B;部分中选择&#x200B;**新输出** ![新输出图标](./images/Add_icon.svg)。
1. 选择&#x200B;**体验片段**。\
   ![文件属性选项选项卡](./images/file-properties-outputs.png){width="300" align="left"}

   *从主题*&#x200B;的文件属性中添加新的体验片段。

   >[!NOTE]
   >
   > 您还可以从&#x200B;**存储库视图**&#x200B;发布体验片段。 选择要作为体验片段发布的主题。 然后，从&#x200B;**选项**&#x200B;菜单中选择&#x200B;**Publish As** > **体验片段**。

1. 在&#x200B;**生成体验片段**对话框中，填写以下详细信息：
   ![在Publish中添加片段模型和映射详细信息作为体验片段对话框](images/experience-fragment-generate.png){width="500" align="left"}

   *添加路径、模板和映射详细信息，将主题或其元素发布为体验片段。 您可以覆盖现有的体验片段。*

   * **路径**：浏览并选择要发布体验片段的文件夹的路径。 您还可以选择现有的体验片段并重新发布。
   * **标题**：键入体验片段的标题。 默认情况下，标题中填充了主题的标题。 您可以对其进行编辑。 此标题用于生成体验片段的名称。
   * **名称**：键入体验片段的名称。 默认情况下，该名称将填充主题标题，空格将替换为“_”。 例如，*sample_experience_fragment*。 您可以对其进行编辑。 此名称用于生成体验片段的URL。
   * **模板**：选择要用于创建体验片段的体验片段模板。 模板是从您在属性中配置的文件夹中选取的。
   * **映射**：从&#x200B;*experienceFragmentMapping.json*&#x200B;文件中选取映射并显示它。



     您的管理员可以在&#x200B;*experienceFragmentMapping.json*&#x200B;文件中添加映射。  请参阅安装和配置指南以了解有关如何[创建主题和体验片段](/help/product-guide/cs-install-guide/conf-experience-fragment-mapping-cs.md)之间的映射的详细信息。

   * 您还可以选择不同的条件来发布内容。  选择以下选项之一：


      * **无**：如果不想对已发布的输出应用任何条件，请选择此选项。
      * **使用DITAVAL**：选择DITAVAL文件以生成个性化内容。 可使用浏览对话框或键入文件路径来选择DITAVAL文件。
      * **使用属性**：您可以在DITA主题中定义条件属性。 然后选择条件属性以发布相关内容。

     >[!NOTE]
     > 
     >仅当在主题中定义了条件属性时，才会启用条件。


   * 如果您的体验片段已存在，并且您想要覆盖它，请选中&#x200B;**覆盖现有内容**&#x200B;复选框。 如果您未选中复选框并且您的体验片段已存在，则Experience Manager Guides会显示错误。
1. 单击&#x200B;**生成**&#x200B;以发布体验片段。
1. 您可以在&#x200B;**文件属性**&#x200B;的&#x200B;**输出**&#x200B;部分下查看主题的体验片段。 体验片段会根据其发布的日期和时间显示，最新的体验片段显示为第一个体验片段。

   ![查看主题的体验片段](images/experience-fragment-outputs.png){width=300 align=&quot;left&quot;}

   *查看某个主题存在的体验片段并重新发布它们。*




发布体验片段后，您还可以在任何Adobe Experience Manager网站上使用它们。


## 体验片段的“选项”菜单

您还可以从&#x200B;**选项**&#x200B;菜单为体验片段执行以下操作：

* **生成**：重新发布体验片段，以使用DITA主题中的最新内容对其进行更新。 在重新生成输出时，无法更改体验片段的路径、名称、标题和模板。 但是，在再生输出时可以选择不同的条件。

* **复制**：复制体验片段。 您可以更改路径、名称、标题和模板。 您还可以在复制体验片段时选择不同的条件。

* **移除**：从输出列表中移除体验片段。 出现确认提示。 确认后，体验片段将从&#x200B;**输出**&#x200B;列表中移除。 但不会从文件夹中删除体验片段。

* **视图**：查看体验片段编辑器。 您还可以进行更改并保存它们。