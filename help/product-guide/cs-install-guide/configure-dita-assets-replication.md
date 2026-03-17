---
title: 为云服务配置DITA Assets复制
description: 了解如何为Cloud Service配置Dita Assets复制
feature: Output Generation
role: Admin
level: Experienced
source-git-commit: 356ea6edd5e688fb1f77e737c705ed0bd4d2e7f0
workflow-type: tm+mt
source-wordcount: '60'
ht-degree: 3%

---

# 配置DITA assets复制

要配置资产处理功能，请执行以下步骤：

1. 使用[配置覆盖](../cs-install-guide/download-install-additional-config-override.md)中提供的说明创建配置文件。

1. 在配置文件中，提供以下（属性）详细信息：

   | PID | 属性键 | 属性值 |
   |---|---|---|
   | `com.adobe.fmdita.config.ConfigManager` | `publish.replicate` | **默认值：** &quot;true&quot; |
