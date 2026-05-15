---
title: 在Web编辑器中配置翻译功能
description: 了解如何在Web编辑器中配置翻译功能
exl-id: e25473c3-9a84-4658-87c9-6fd72bcaa2b6
feature: Web Editor Configuration
role: Admin
level: Experienced
TQID: https://experienceleague.adobe.com/7-SFQ0FXQ6bGo3pjAOK-18sEsU4-zriruioG2nMx2o0
product_v2:
  - id: fae5e35a-80c9-4b94-9352-1a060a6aab1d
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: cb8c6a2a-3c38-4e40-867c-756f8c36bb0e
subfeature_v2:
  - id: b0521e56-a0b2-40b6-bf47-ebc98751f9ba
  - id: b1ef4d86-3917-4b76-a0bc-4a4771f9b3b0
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
source-git-commit: 8ed5c9cb07c56b84b36ef56a55af8738989a6d3f
workflow-type: tm+mt
source-wordcount: 154
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
