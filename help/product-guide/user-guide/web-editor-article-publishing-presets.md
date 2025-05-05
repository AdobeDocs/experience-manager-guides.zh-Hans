---
title: 从Web编辑器创建输出预设
description: 从Web编辑器创建输出预设。 了解如何在AEM Guides中编辑、重命名、复制和删除输出预设。
exl-id: cd38b039-ef91-45c9-a226-433e57b09873
feature: Authoring, Features of Web Editor, Publishing
role: User
source-git-commit: ac83f613d87547fc7f6a18070545e40ad4963616
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---

# 从编辑器为知识库创建输出预设 {#id218CL400JW3}

执行以下步骤可为DITA映射创建输出预设：

1. 在Assets UI中，导航到要编辑的映射文件。

1. 若要获取映射文件的独占锁定，请选择映射文件，然后选择&#x200B;**签出**。

1. 从映射文件的操作菜单中选择&#x200B;**编辑主题**&#x200B;选项。

   将在编辑器中打开映射文件进行编辑。

   >[!NOTE]
   >
   > 您可以使用高级映射编辑器在映射中添加或删除任何主题。 有关详细信息，请查看[使用高级映射编辑器](map-editor-advanced-map-editor.md#)。

1. 选择&#x200B;**在地图控制台中打开**&#x200B;图标。 将在映射控制台中打开映射。

1. 导航到&#x200B;**输出预设**&#x200B;选项卡，并选择+图标以创建DITA映射的输出预设。

1. 从&#x200B;**类型**&#x200B;下拉列表中选择&#x200B;**知识库**，输入名称，然后在&#x200B;**新建输出预设**&#x200B;对话框中选择&#x200B;**Adobe Experience Manager**。
1. 选择&#x200B;**添加到当前文件夹配置文件**&#x200B;选项，为当前文件夹配置文件创建输出预设。 ![文件夹配置文件图标](images/global-preset-icon.svg)图标表示文件夹配置文件级别预设。

   了解有关[管理全局和文件夹配置文件输出预设](./web-editor-manage-output-presets.md)的更多信息。

1. 选择&#x200B;**添加**。

   将创建知识库预设。


   ![新](images/knowledge-base-preset-dialog-box.png){align="left"}

创建预设后，即可生成特定知识库文章的输出。 为此，请导航到&#x200B;**文章**&#x200B;选项卡，并选择要为其生成输出的主题。
1. 选择顶部的&#x200B;**生成输出**&#x200B;以生成输出。

   ![](images/add-preset-articles-tab_cs.png){align="left"}

1. 在&#x200B;**确认要发布的文件**&#x200B;提示中，选择要发布的文件，并通过选择&#x200B;**发布**&#x200B;进行确认。

   ![新](images/knowledge-base-confirm-files-for-publishing.png){align="left"}

您将查看输出生成过程的状态。 **主题**&#x200B;列列出正在为其生成输出的主题，而&#x200B;**状态**&#x200B;列显示每个主题的发布状态。


![](images/add-preset-output-generated_cs.png){align="left"}

要查看输出，请关闭“生成的输出”对话框，然后在预设页面上选择&#x200B;**查看输出**。


>[!NOTE]
>
> 也可以从“选项”菜单中重命名现有输出预设、复制或删除现有输出预设。



**父主题：**&#x200B;[&#x200B;编辑器中基于文章的发布](web-editor-article-publishing.md)
