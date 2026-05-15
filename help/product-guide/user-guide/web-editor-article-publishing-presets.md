---
title: 从Web编辑器创建输出预设
description: 从Web编辑器创建输出预设。 了解如何在AEM Guides中编辑、重命名、复制和删除输出预设。
exl-id: cd38b039-ef91-45c9-a226-433e57b09873
feature: Authoring, Features of Web Editor, Publishing
role: User
TQID: https://experienceleague.adobe.com/e5BEPmlmFDY2ipC8nNQPjrgGx3cV6AaD4PmZYw4hAYI
product_v2:
  - id: fae5e35a-80c9-4b94-9352-1a060a6aab1d
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: a3bd6397-2eb2-4908-a61c-226e26855dca
  - id: ab01a588-7dea-43f2-a699-0b3f128465d6
  - id: cb8c6a2a-3c38-4e40-867c-756f8c36bb0e
subfeature_v2:
  - id: ad602516-aca3-4247-9ae8-f393d958efa9
  - id: f89f75b0-cf2e-4e96-aec8-fe8c39cbd0ef
  - id: fd6cc9e1-e5e5-494e-b7b1-a32f2d6cd7c9
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
source-git-commit: 8ed5c9cb07c56b84b36ef56a55af8738989a6d3f
workflow-type: tm+mt
source-wordcount: 368
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


   ![新](images/knowledge-base-preset-dialog-box.png)

创建预设后，即可生成特定知识库文章的输出。 为此，请导航到&#x200B;**文章**&#x200B;选项卡，并选择要为其生成输出的主题。
1. 选择顶部的&#x200B;**生成输出**&#x200B;以生成输出。

   ![](images/add-preset-articles-tab_cs.png)

1. 在&#x200B;**确认要发布的文件**&#x200B;提示中，选择要发布的文件，并通过选择&#x200B;**发布**&#x200B;进行确认。

   ![新](images/knowledge-base-confirm-files-for-publishing.png)

您将查看输出生成过程的状态。 **主题**&#x200B;列列出正在为其生成输出的主题，而&#x200B;**状态**&#x200B;列显示每个主题的发布状态。


![](images/add-preset-output-generated_cs.png)

要查看输出，请关闭“生成的输出”对话框，然后在预设页面上选择&#x200B;**查看输出**。


>[!NOTE]
>
> 也可以从“选项”菜单中重命名现有输出预设、复制或删除现有输出预设。



**父主题：**&#x200B;[&#x200B;编辑器中基于文章的发布](web-editor-article-publishing.md)
