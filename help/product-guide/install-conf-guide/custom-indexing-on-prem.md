---
title: 用于内部部署设置的自定义索引部署
description: 了解如何为内部部署设置自定义索引内容
feature: Web Editor Configuration
role: Admin
level: Experienced
source-git-commit: 834959a6a0e22cd5d2b2c5d0e57ceb6d45c0c666
workflow-type: tm+mt
source-wordcount: '131'
ht-degree: 0%

---

# 为内部部署的查找和替换（Source视图）功能重新编制索引

需要重新索引才能启用&#x200B;**查找和替换（Source视图）**&#x200B;功能，该功能允许您扫描在“创作”视图中可见的整个内容，以及搜索字符串的基础Source内容（XML结构，包括元素、标记和属性值）。

## 重新索引

对于内部部署设置，索引定义包含在包中。 要启用该功能，必须重新索引内容。

在节点`reindex=true (Boolean)`上设置属性` /oak:index/guidesAssetLucene`以重新索引以前捕获的内容，从而开始重新索引。

重新索引过程将继续，直到系统自动将此属性更改为false。 您可以在系统日志中监视重新索引操作的进度。
