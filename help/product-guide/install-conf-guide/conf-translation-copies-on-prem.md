---
title: 在内部部署的翻译工作流中配置目标副本初始化
description: 了解如何在本地的翻译工作流中启用或禁用目标副本的初始化
feature: Configuration
role: Admin
level: Experienced
source-git-commit: 8d231bdbf00adb354bc31616e880495b00a3959c
workflow-type: tm+mt
source-wordcount: '111'
ht-degree: 1%

---

# 在内部部署的翻译工作流中配置目标副本初始化

以下步骤说明如何在本地环境的翻译工作流中启用目标副本初始化。

1. 打开Adobe Experience Manager Web控制台配置页面。

   用于访问配置页面的默认URL为：

   ```http
   http://<server name>:<port>/system/console/configMgr
   ```

1. 搜索并选择&#x200B;**com.adobe.fmdita.config.ConfigManager**&#x200B;包。

1. 根据您的要求，启用或禁用设置&#x200B;**使用源内容** ( translation.workflow.propagate.source.content)初始化目标语言副本。 此设置仅在禁用旧版翻译工作流时适用。

1. 选择&#x200B;**保存**。
