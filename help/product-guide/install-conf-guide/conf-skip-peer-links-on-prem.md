---
title: 在内部部署中配置基线V1的对等链接跳过
description: 了解如何在On-Premise中启用或禁用基线V1的对等链接跳过
feature: Configuration
role: Admin
level: Experienced
source-git-commit: 8d231bdbf00adb354bc31616e880495b00a3959c
workflow-type: tm+mt
source-wordcount: '101'
ht-degree: 1%

---

# 在内部部署中为旧基线配置对等链接跳过

以下步骤说明如何在On-Premise环境中为旧基线启用对等链接跳过。

1. 打开Adobe Experience Manager Web控制台配置页面。

   用于访问配置页面的默认URL为：

   ```http
   http://<server name>:<port>/system/console/configMgr
   ```

1. 搜索并选择&#x200B;**com.adobe.fmdita.config.ConfigManager**&#x200B;包。

1. 启用设置&#x200B;**跳过基线V1**&#x200B;的对等链接(guides.baseline.v1.skip.peer.links)。 默认情况下，此设置处于禁用状态。

1. 选择&#x200B;**保存**。
