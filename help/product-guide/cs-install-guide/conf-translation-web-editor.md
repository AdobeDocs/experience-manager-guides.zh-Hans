---
title: 在Web编辑器中配置翻译功能
description: 了解如何在Web编辑器中配置翻译功能
exl-id: e25473c3-9a84-4658-87c9-6fd72bcaa2b6
feature: Web Editor Configuration
role: Admin
level: Experienced
source-git-commit: 0513ecac38840a4cc649758bd1180edff1f8aed1
workflow-type: tm+mt
source-wordcount: '154'
ht-degree: 0%

---

# 在Web编辑器中配置翻译功能 {#id21BONI0J0YR}

Web编辑器提供强大的翻译功能，可将您的内容翻译成多种语言。

您可以使用Web编辑器中的&#x200B;**管理**&#x200B;选项卡来翻译您的内容。 默认情况下，此选项卡可用。

要在Web编辑器中隐藏&#x200B;**管理**&#x200B;选项卡，请执行以下步骤：

1. 以管理员身份登录&#x200B;**Adobe Experience Manager**。
1. 单击顶部的&#x200B;**Adobe Experience Manager**&#x200B;链接，然后选择&#x200B;**工具**。
1. 从工具列表中选择&#x200B;**指南**，然后单击&#x200B;**文件夹配置文件**。
1. 单击&#x200B;**全局配置文件**&#x200B;拼贴。
1. 单击&#x200B;**XML编辑器配置**。
1. 单击顶部的&#x200B;**编辑**&#x200B;图标。
1. 下载`ui\_config.json`文件。从下载的文件中删除以下代码片段：

   ```json
   {
       "component":"tab",
       "id":"workflow",
       "title":"Manage",
       "on-click":"APP_MODE_CHANGE",
       "items":
       [
           {
               "component":"label",
               "label":"Manage"
           }
       ]
   },
   ```

1. 上传更新的ui\_config.json文件。

请注意，**管理**&#x200B;筛选器不再可用。

**父主题：**&#x200B;[&#x200B;自定义Web编辑器](conf-web-editor.md)
