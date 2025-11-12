---
title: 为On-Premise服务配置B树清理作业
description: 为On-Premise服务配置B树清理作业
feature: Output Generation
role: Admin
level: Experienced
source-git-commit: e1b332b100cc8e3937557e4617d66352c1a0dc3c
workflow-type: tm+mt
source-wordcount: '145'
ht-degree: 2%

---

# 配置B树清理

设置B树清理作业并管理`Guides B-tree deletion`设置以保持系统优化和存储清洁。

## 配置B树清理作业

执行以下步骤来配置B树清理作业：

1. 打开Adobe Experience Manager Web控制台配置页面。

   用于访问配置页面的默认URL为：

   ```http
   http://<server name>:<port>/system/console/configMgr
   ```

1. 搜索并选择&#x200B;*com.adobe.guides.utils.schedulers.GuidesBTreesCleanupSchedulerJob*&#x200B;捆绑包。

1. 更新cron表达式以设置B树清理计划程序作业运行频率。

1. 配置B树清理计划程序，如下所示。

   ![](assets/btree-cleanup-config.png){align="left"}

1. 选择&#x200B;**保存**。


## 配置指南B树删除启用设置

执行以下步骤以启用设置：

1. 打开Adobe Experience Manager Web控制台配置页面。

   用于访问配置页面的默认URL为：

   ```http
   http://<server name>:<port>/system/console/configMgr
   ```

1. 搜索并选择&#x200B;*com.adobe.fmdita.config.ConfigManager*&#x200B;包。
1. 启用设置`Guides btree deletion enabled`。

   ![](assets/btree-cleanup-setting.png){align="left"}

1. 选择&#x200B;**保存**。

