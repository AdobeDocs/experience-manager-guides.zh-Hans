---
title: 生成知识库输出
description: 了解如何从“地图”控制台发布一个或多个文章。 在AEM Guides中为DITA映射中的一个或多个主题生成输出。
exl-id: d89ce69d-8d4c-4265-bfca-60763f561afd
feature: Publishing
role: User
source-git-commit: ac83f613d87547fc7f6a18070545e40ad4963616
workflow-type: tm+mt
source-wordcount: '341'
ht-degree: 0%

---

# 生成知识库输出 {#id218CL05J0M1}

Adobe Experience Manager Guides附带基于文章的发布功能，允许用户同时发布一个或多个知识库文章。

此引擎还附带一个OOTB内容模板，该模板基于Adobe Experience Manager核心组件构建，允许用户创建技术内容的基于知识的存储库。 可以自定义此模板以满足客户的需求。此引擎允许用户以累加方式构建DITA映射，并在准备好时发布主题。

如果您仅更新了DITA映射中几个主题的内容，则不必始终发布整个映射。 您只能选择和发布更新的主题。

对于基于文章的发布，您需要为知识库DITA映射创建输出预设。 地图必须包含要发布的主题。 您还可以应用条件并为输出预设指定AEM Sites详细信息。 然后，您可以使用&#x200B;**生成输出**&#x200B;功能生成输出。

执行以下步骤可生成基于文章的输出：

1. [为基于文章的输出创建知识库预设](./generate-output-knowledge-base.md)。
1. 导航到&#x200B;**文章**&#x200B;选项卡，并选择要为其生成输出的主题。
1. 选择顶部的&#x200B;**生成输出**&#x200B;以生成输出。

   ![](images/add-preset-articles-tab_cs.png){align="left"}

1. 在&#x200B;**确认要发布的文件**&#x200B;提示中，选择要发布的文件，并通过选择&#x200B;**发布**&#x200B;进行确认。

   ![新](images/knowledge-base-confirm-files-for-publishing.png){align="left"}

   您将查看输出生成过程的状态。 **主题**&#x200B;列列出正在为其生成输出的主题，而&#x200B;**状态**&#x200B;列显示每个主题的发布状态。


   ![](images/add-preset-output-generated_cs.png){align="left"}

   要查看输出，请关闭&#x200B;**生成的输出**&#x200B;对话框，然后在预设页面上选择&#x200B;**查看输出**。


   >[!NOTE]
   >
   > 也可以从“选项”菜单中重命名现有输出预设、复制或删除现有输出预设。


**父主题：**&#x200B;[&#x200B;使用编辑器](web-editor.md)
