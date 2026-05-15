---
title: 从Web编辑器创建输出预设
description: 从Web编辑器创建输出预设。 了解如何在AEM Guides中编辑、重命名、复制和删除输出预设。
feature: Authoring, Features of Web Editor, Publishing
role: User
hide: true
exl-id: ce8e3614-907b-4172-a8f0-e81e4dc096df
TQID: https://experienceleague.adobe.com/nCmtXuQXfOVVHbmGrRT6rVzEa6NlR-o9TGmwhqczWPs
product_v2: id: fae5e35a-80c9-4b94-9352-1a060a6aab1did: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2: id: a3bd6397-2eb2-4908-a61c-226e26855dcaid: ab01a588-7dea-43f2-a699-0b3f128465d6id: cb8c6a2a-3c38-4e40-867c-756f8c36bb0e
subfeature_v2: id: ad602516-aca3-4247-9ae8-f393d958efa9id: f89f75b0-cf2e-4e96-aec8-fe8c39cbd0efid: fd6cc9e1-e5e5-494e-b7b1-a32f2d6cd7c9
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554
source-git-commit: 8ed5c9cb07c56b84b36ef56a55af8738989a6d3f
workflow-type: tm+mt
source-wordcount: 370
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

   ![](images/output-tab-preset_cs.png){width="350"}

1. 在“添加预设”对话框中输入预设的名称，然后单击&#x200B;**添加**。

1. 输入以下配置详细信息。

   1. 在&#x200B;**常规**&#x200B;选项卡中选择所需的选项。 您可以选择创建附带条件或不附带条件的输出预设。 也可以使用DITVAL文件。 AEM Guides还允许您选择用于发布DITA映射特定版本的基线。
   1. 在&#x200B;**AEM**&#x200B;选项卡中输入AEM站点详细信息。 **站点**&#x200B;显示您的AEM存储库中可用的AEM Sites列表。 **类别**、**节模板**&#x200B;和&#x200B;**文章模板**&#x200B;是用于组织输出外观的结构组件。 这些是在AEM站点模板中预定义的。

      >[!NOTE]
      >
      > 刷新每个下拉菜单以在下一个下拉菜单中获取进一步的分类。

   1. 从&#x200B;**文章**&#x200B;选项卡中，选择要为其生成输出的主题。
1. 选择顶部的&#x200B;**生成预设**&#x200B;图标以生成输出。

   ![](images/add-preset-articles-tab_cs.png){width="800"}

1. 您将看到输出生成过程的状态。 **主题**&#x200B;列列出正在为其生成输出的主题，而&#x200B;**状态**&#x200B;列显示每个主题的发布状态。

   要查看输出，请将鼠标指针悬停在主题上，然后单击“查看输出”。

   ![](images/add-preset-output-generated_cs.png){width="800"}


>[!NOTE]
>
> 也可以从“选项”菜单中编辑、重命名、复制或删除现有的输出预设。

![](images/edit-preset_cs.png){width="550"}

**父主题：**[&#x200B;从Web编辑器中基于文章的发布](web-editor-article-publishing.md)
