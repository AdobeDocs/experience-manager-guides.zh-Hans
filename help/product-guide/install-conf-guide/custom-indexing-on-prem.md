---
title: 用于内部部署设置的自定义索引部署
description: 了解如何为内部部署设置自定义索引内容
feature: Web Editor Configuration
role: Admin
level: Experienced
exl-id: 87c0519d-120a-4bb7-b70f-7d217bcd7580
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
source-wordcount: '135'
ht-degree: 0%
---
# 为内部部署的查找和替换（Source视图）功能重新编制索引

需要重新索引才能启用&#x200B;**查找和替换（Source视图）**&#x200B;功能，该功能允许您扫描在“创作”视图中可见的整个内容，以及搜索字符串的基础Source内容（XML结构，包括元素、标记和属性值）。

## 重新索引

对于内部部署设置，索引定义包含在包中。 要启用该功能，必须重新索引内容。

在节点` /oak:index/guidesAssetLucene`上设置属性`reindex=true (Boolean)`以重新索引以前捕获的内容，从而开始重新索引。

重新索引过程将继续，直到系统自动将此属性更改为false。 您可以在系统日志中监视重新索引操作的进度。
