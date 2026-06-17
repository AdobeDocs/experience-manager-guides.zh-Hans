---
title: 启用新的PDF引擎
description: 了解如何在Experience Manager Guides中启用新的PDF引擎
feature: Web Editor Configuration
role: Admin
level: Experienced
source-git-commit: f3f30400f776f746427e257e2c937ff3413aa9ac
workflow-type: tm+mt
source-wordcount: '74'
ht-degree: 2%

---


# 配置本机PDF引擎v2

本机PDF的新发布引擎（即&#x200B;_本机PDF引擎v2_）提供了更新的PDF渲染功能，并修复了&#x200B;_本机PDF引擎v1_&#x200B;问题。

使用[配置覆盖](../install-conf-guide/download-install-config-override.md)中提供的说明创建配置文件。 在配置文件中，提供以下（属性）详细信息：

| PID | 属性键 | 属性值 |
|-----|--------------|----------------|
| `com.adobe.fmdita.publish.config.GuidesPublishConfiguratorService` | `guides.publish.config` | `{"PDF_ENGINE": "v2"}` <br>默认值： `v1` |