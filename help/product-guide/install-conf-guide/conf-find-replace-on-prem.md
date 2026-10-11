---
title: 为内部部署配置查找和替换（Source视图）
description: 了解如何为内部部署配置查找和替换（Source视图）
feature: Configuration
role: Admin
level: Experienced
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: fae5e35a-80c9-4b94-9352-1a060a6aab1d
    internal-label: Experience Manager Guides
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 81a0e7f0736ba4970673dd87a888a4c60d3c1b4e
workflow-type: tm+mt
source-wordcount: '84'
ht-degree: 2%
---
# 为内部部署配置查找和替换（Source视图）

以下步骤说明了如何在内部部署环境中启用查找和替换（Source视图）。

1. 打开Adobe Experience Manager Web控制台配置页面。

   用于访问配置页面的默认URL为：

   ```http
   http://<server name>:<port>/system/console/configMgr
   ```

1. 搜索并选择&#x200B;**com.adobe.fmdita.config.ConfigManager**&#x200B;包。

1. 启用设置&#x200B;**启用标记查找和替换** (enable.markup.findreplace)。

1. 选择&#x200B;**保存**。
