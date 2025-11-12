---
title: 为云服务配置B树清理作业
description: 为云服务配置B树清理作业
feature: Output Generation
role: Admin
level: Experienced
source-git-commit: 5b29b2b5f725b5d9a2029fb232e62f387a5338fd
workflow-type: tm+mt
source-wordcount: '125'
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