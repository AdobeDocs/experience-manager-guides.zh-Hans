---
title: 启用新的PDF引擎
description: 了解如何在Experience Manager Guides中启用新的PDF引擎
feature: Web Editor Configuration
role: Admin
level: Experienced
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: fae5e35a-80c9-4b94-9352-1a060a6aab1d
    internal-label: Experience Manager Guides
feature_v2:
  - id: cb8c6a2a-3c38-4e40-867c-756f8c36bb0e
    internal-label: Configuration
subfeature_v2:
  - id: b0521e56-a0b2-40b6-bf47-ebc98751f9ba
    internal-label: Web Editor configuration
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 81a0e7f0736ba4970673dd87a888a4c60d3c1b4e
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

