---
title: 配置标记视图的默认值
description: 了解如何为标记视图配置默认值
exl-id: 52214459-74b8-47ec-982b-6176145348a8
feature: Web Editor Configuration
role: Admin
level: Experienced
source-git-commit: 0513ecac38840a4cc649758bd1180edff1f8aed1
workflow-type: tm+mt
source-wordcount: '214'
ht-degree: 0%

---

# 配置标记视图的默认值 {#id223GN0M0NDC}

AEM Guides允许您在Web编辑器中配置“标记视图”的默认状态，这有助于在默认情况下为新用户的会话打开或关闭标记视图。执行以下步骤来配置“标记视图”的默认值：

1. 以管理员身份登录Adobe Experience Manager以下载用户界面配置文件。
1. 单击顶部的Adobe Experience Manager链接，然后选择&#x200B;**工具**。
1. 从工具列表中选择&#x200B;**指南**，然后单击&#x200B;**文件夹配置文件**。
1. 单击&#x200B;**全局配置文件**&#x200B;拼贴。
1. 选择&#x200B;**XML编辑器配置**&#x200B;选项卡，然后单击顶部的&#x200B;**编辑**&#x200B;图标。
1. 在&#x200B;**XML编辑器UI配置**&#x200B;部分中，单击&#x200B;**下载**&#x200B;图标以在本机系统上下载`ui_config.json`文件。
1. 在`ui_config.json`文件中，通过更改defaultValues部分来更改默认标记视图状态，如下所示：

   ```json
   "defaultValues":
                   {
                   "tagsView": true
                   }
   ```

1. 保存文件并将其上传。

>[!NOTE]
>
> 用户在Web编辑器中启用/禁用标记视图的首选项优先于此默认值。 因此，如果用户从Web编辑器启用标记视图，则即使跨会话，该视图也会保持启用状态。

**父主题：**[&#x200B;自定义Web编辑器](conf-web-editor.md)
