---
title: 为云服务配置B树清理作业
description: 为云服务配置B树清理作业
feature: Output Generation
role: Admin
level: Experienced
exl-id: de464e92-f17b-4c99-98f2-fdba8d214129
TQID: 'https://experienceleague.adobe.com/-n4Winzqo-HNb2FDH6RI223UT9uvuOc8-OT7mgXjblc'
product_v2:
  - id: fae5e35a-80c9-4b94-9352-1a060a6aab1d
    internal-label: Experience Manager Guides
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
feature_v2:
  - id: cb8c6a2a-3c38-4e40-867c-756f8c36bb0e
    internal-label: Configuration
  - id: a3bd6397-2eb2-4908-a61c-226e26855dca
    internal-label: Publishing
subfeature_v2:
  - id: fd6cc9e1-e5e5-494e-b7b1-a32f2d6cd7c9
    internal-label: Output generation
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 81a0e7f0736ba4970673dd87a888a4c60d3c1b4e
workflow-type: tm+mt
source-wordcount: '132'
ht-degree: 3%
---
# 配置B树清理

设置B树清理作业并管理`Guides BTree deletion`设置以保持系统优化和存储清洁。

## 配置B树清理作业

执行以下步骤来配置B树清理作业：

1. 使用[配置覆盖](../cs-install-guide/download-install-additional-config-override.md)中提供的说明创建配置文件。

1. 在配置文件中，提供以下（属性）详细信息：

   | PID | 属性键 | 属性值 |
   |---|---|---|
   | `com.adobe.guides.utils.schedulers.GuidesBTreesCleanupSchedulerJob` | `cronExpression` | **默认值：** &quot;0 0 0 * * ？&quot; |


## 配置指南B树删除启用设置

执行以下步骤以启用设置：

1. 使用[配置覆盖](../cs-install-guide/download-install-additional-config-override.md)中提供的说明创建配置文件。

1. 在配置文件中，提供以下（属性）详细信息：

   | PID | 属性键 | 属性值 |
   |---|---|---|
   | `com.adobe.fmdita.config.ConfigManager` | `btree.deletion.enabled` | **默认值：** &quot;True&quot; |
