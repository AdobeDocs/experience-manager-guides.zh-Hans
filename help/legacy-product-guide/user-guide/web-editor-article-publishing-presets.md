---
title: 从Web编辑器创建输出预设
description: 从Web编辑器创建输出预设。 了解如何在AEM Guides中编辑、重命名、复制和删除输出预设。
feature: Authoring, Features of Web Editor, Publishing
role: User
hide: true
exl-id: ce8e3614-907b-4172-a8f0-e81e4dc096df
source-git-commit: a70b3ce942b3e69445ad1d7ba6c8f7542e0ff176
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# 从Web编辑器创建输出预设 {#id218CL400JW3}

执行以下步骤可为DITA映射创建输出预设：

1. 在Assets UI中，导航到要编辑的映射文件。

1. 若要获取映射文件的独占锁定，请选择映射文件，然后单击&#x200B;**签出**。

1. 从映射文件的操作菜单中选择&#x200B;**编辑主题**&#x200B;选项。

   将打开映射文件以便在Web编辑器中编辑。

   >[!NOTE]
   >
   > 您可以使用高级映射编辑器在映射中添加或删除任何主题。 有关详细信息，请参阅[使用高级映射编辑器](map-editor-advanced-map-editor.md#)。

1. 在&#x200B;**输出**&#x200B;选项卡中，选择+图标以创建DITA映射的输出预设。

   ![](images/output-tab-preset_cs.png){width="350" align="left"}

1. 在“添加预设”对话框中输入预设的名称，然后单击&#x200B;**添加**。

1. 输入以下配置详细信息。

   1. 在&#x200B;**常规**&#x200B;选项卡中选择所需的选项。 您可以选择创建附带条件或不附带条件的输出预设。 也可以使用DITVAL文件。 AEM Guides还允许您选择用于发布DITA映射特定版本的基线。
   1. 在&#x200B;**AEM**&#x200B;选项卡中输入AEM站点详细信息。 **站点**&#x200B;显示您的AEM存储库中可用的AEM Sites列表。 **类别**、**节模板**&#x200B;和&#x200B;**文章模板**&#x200B;是用于组织输出外观的结构组件。 这些是在AEM站点模板中预定义的。

      >[!NOTE]
      >
      > 刷新每个下拉菜单以在下一个下拉菜单中获取进一步的分类。

   1. 从&#x200B;**文章**&#x200B;选项卡中，选择要为其生成输出的主题。
1. 选择顶部的&#x200B;**生成预设**&#x200B;图标以生成输出。

   ![](images/add-preset-articles-tab_cs.png){width="800" align="left"}

1. You will see the status of the output generation process. The **Topics** column lists the topics for which output is being generated while the **Status** column displays the publishing status of each topic.

   To view the output, hover the mouse pointer over the topic and click View Output.

   ![](images/add-preset-output-generated_cs.png){width="800" align="left"}


>[!NOTE]
>
> You can also Edit, Rename, Duplicate, or Delete an existing output preset from the Options menu.

![](images/edit-preset_cs.png){width="550" align="left"}

**Parent topic:**&#x200B;[&#x200B; Article-based publishing from the Web Editor](web-editor-article-publishing.md)
