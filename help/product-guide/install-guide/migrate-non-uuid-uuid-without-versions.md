---
title: 将不带版本的非UUID内容转换为UUID内容
description: 了解如何迁移不带版本的非UUID内容。
exl-id: 44b5660d-9961-4463-9686-53085249fb05
feature: Migration
role: Admin
level: Experienced
hidefromtoc: 'yes'
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: fae5e35a-80c9-4b94-9352-1a060a6aab1d
    internal-label: Experience Manager Guides
feature_v2:
  - id: 5be0fc8f-1cff-5c3e-bb92-2903a56a3de6
    internal-label: Migration
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 81a0e7f0736ba4970673dd87a888a4c60d3c1b4e
workflow-type: tm+mt
source-wordcount: '88'
ht-degree: 0%
---
# 迁移不带版本的内容

>[!IMPORTANT]
>
> 如果打算忽略或不迁移资产版本，可以选择此迁移方法。


1. 使用AEM桌面应用程序等Adobe工具，直接从AEM Assets UI将资产从非UUID实例下载并上传到UUID实例。

1. 确保您启用了DAM更新资产工作流，并在导入内容以创建GUID后在所有资产上执行该工作流。
