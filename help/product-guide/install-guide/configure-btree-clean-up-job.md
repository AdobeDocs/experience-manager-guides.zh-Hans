---
title: 为On-Premise服务配置B树清理作业
description: 为On-Premise服务配置B树清理作业
feature: Output Generation
role: Admin
level: Experienced
exl-id: ff6f968c-3440-4757-882a-676711ad05c3
TQID: 'https://experienceleague.adobe.com/qvOHGtHbgKS3xUv0pEXKTqeWblIDj8JKJwik8heXwPo'
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
source-wordcount: '156'
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

   ![](assets/btree-cleanup-config.png)

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

   ![](assets/btree-cleanup-setting.png)

1. 选择&#x200B;**保存**。
