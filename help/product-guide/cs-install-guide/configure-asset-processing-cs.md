---
title: 为云服务配置资产处理
description: 了解如何为Cloud Service配置资产处理
feature: Output Generation
role: Admin
level: Experienced
source-git-commit: 5b29b2b5f725b5d9a2029fb232e62f387a5338fd
workflow-type: tm+mt
source-wordcount: '58'
ht-degree: 3%

---

# 配置资源处理功能

要配置资产处理功能，请执行以下步骤：

1. 使用[配置覆盖](../cs-install-guide/download-install-additional-config-override.md)中提供的说明创建配置文件。

1. 在配置文件中，提供以下（属性）详细信息：

   | PID | 属性键 | 属性值 |
   |---|---|---|
   | `com.adobe.fmdita.config.ConfigManager` | `enable.asset.processing.scheduler` | **默认值：** &quot;true&quot; |
