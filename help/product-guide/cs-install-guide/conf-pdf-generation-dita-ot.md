---
title: 配置单主题PDF生成
description: 了解如何配置单主题PDF生成
exl-id: 5b66fd3b-6450-49ce-b06e-d2d5bab37990
feature: Web Editor Configuration
role: Admin
level: Experienced
TQID: https://experienceleague.adobe.com/DinL1ZwovhmP61iQOQkW6XR-ALahlONxOU4e5UXpSGY
product_v2:
  - id: fae5e35a-80c9-4b94-9352-1a060a6aab1d
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: a3bd6397-2eb2-4908-a61c-226e26855dca
  - id: cb8c6a2a-3c38-4e40-867c-756f8c36bb0e
subfeature_v2:
  - id: b0521e56-a0b2-40b6-bf47-ebc98751f9ba
  - id: b1ef4d86-3917-4b76-a0bc-4a4771f9b3b0
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
source-git-commit: 8ed5c9cb07c56b84b36ef56a55af8738989a6d3f
workflow-type: tm+mt
source-wordcount: 271
ht-degree: 0%

---

# 配置单主题PDF生成 {#id22ADC70M0XA}

借助AEM Guides，您可以生成单个主题的PDF或整个映射文件。 您可以使用本机PDF或DITA-OT方法以PDF格式发布主题。 使用本机PDF方法，根据W3C CSS3和CSS分页媒体标准生成功能丰富的PDF输出。 可以使用DITA-OT方法从映射仪表板为映射生成PDF输出。

>[!NOTE]
>
> 本机PDF是在当前版本的AEM Guides中生成PDF的默认方法。

要在主题预览模式下通过DITA-OT启用旧PDF生成，请执行以下步骤：

1. 以管理员身份登录Adobe Experience Manager并下载用户界面配置文件。

1. 为此，请单击顶部的Adobe Experience Manager链接，然后选择&#x200B;**工具**。
1. 从工具列表中选择&#x200B;**指南**，然后单击&#x200B;**文件夹配置文件**。
1. 单击&#x200B;**全局配置文件**&#x200B;拼贴。
1. 选择&#x200B;**XML编辑器配置**&#x200B;选项卡，然后单击顶部的&#x200B;**编辑**&#x200B;图标
1. 单击&#x200B;**下载**&#x200B;图标可在本地系统上下载ui\_config.json文件。 然后，您可以对文件进行更改，然后上传相同的更改。
1. 在`ui_config.json`文件中，查找以下配置：

   ```
   {
                           "component": "button",
                           "variant": "action",
                           "quiet": true,
                           "icon": "filePDF",
                           "title": "Download as PDF",
                           "on-click": "EDITOR_SAVE_AS_PDF"
                           }
   ```

   并将其替换为

   ```
   {
                           "component": "button",
                           "icon": "filePDF",
                           "variant": "action",
                           "quiet": true, "title": "Export as PDF",
                           "on-click": "DOWNLOAD_TOPIC_PDF",
                           "show" : ["@isPreviewMode", "@isXmlMode"]
                           }
   ```

1. 保存文件并将其上传。

执行上述步骤后，如果从Web编辑器的“用户首选项”中选择相同的文件夹配置文件，则将在主题的预览模式下看到用于生成PDF的选项。

**父主题：**&#x200B;[&#x200B;自定义Web编辑器](conf-web-editor.md)
