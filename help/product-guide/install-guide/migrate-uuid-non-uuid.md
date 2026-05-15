---
title: 非UUID到UUID内容迁移
description: 了解如何将非UUID迁移到UUID内容
exl-id: f8b723bf-84c0-4fe6-936e-63970fb3e417
feature: Migration
role: Admin
level: Experienced
TQID: https://experienceleague.adobe.com/pZ0HRoSRWcGz2IT9tWAZ-vZYLc-Zc4kyYt8OXRohmTU
product_v2: id: fae5e35a-80c9-4b94-9352-1a060a6aab1did: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2: id: b1210526-416b-4ef6-bcc0-1692e99f30e9id: e88e74c7-6080-446a-8eb0-496f1ac5f7e6
subfeature_v2: id: c8841798-1a28-4264-a46a-984860f8e6f6
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2: id: d095671a-1355-40aa-8b5f-06c33c68080bid: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 8ed5c9cb07c56b84b36ef56a55af8738989a6d3f
workflow-type: tm+mt
source-wordcount: 320
ht-degree: 0%

---

# 非UUID到UUID内容迁移 {#id226TI0U20XA}


您可以根据正在使用的Experience Manager Guides的当前版本，将非UUID内容迁移到UUID。

>[!IMPORTANT]
>
> 在将内容迁移到UUID服务器之前，请确保您的非UUID服务器上安装了兼容的AEM Guides版本。

## 兼容性矩阵

请根据您当前的非UUID版本使用以下矩阵来确定正确的迁移路径。 这确保在迁移后实现平稳过渡。

| 迁移需要非UUID版本 | 迁移后的UUID版本 | 迁移后支持的升级路径 |
|---|---|---|
| 4.3.1非UUID | 4.3.2 UUID | 迁移到版本4.3.2 UUID后，您必须直接安装4.6.0 (UUID)。 在4.6.0上运行后，升级到5.1.0版，然后安装5.1.0 Service Pack 3。 |
| 4.6.0 Service Pack 4非UUID | 4.6.1 UUID | 迁移到版本4.6.1 UUID后，您必须直接升级到5.1.0 (UUID)。 升级完成后，安装版本5.1.0 Service Pack 3。 |

## 迁移时间估计

迁移实用程序以平均速率（每个资产约50毫秒）处理资产。 下表提供了配置了64个vCPU、128 GB RAM和SSD备份存储的系统的迁移时间估计值。 对于具有许多演绎版或高分辨率二进制文件的较大存储库或资产，内存需求可能会增加。

>[!NOTE]
>
> 实际迁移时间可能因硬件性能、存储吞吐量、并发AEM活动和整体系统负载而异。


| **资源计数** | **约 时间** |
|-----------------|-------------------------|
| 1万 | ~8-9分钟 |
| 5万 | 约42分钟 |
| 10万 | ~1.4小时 |
| 25万 | 约3.5小时 |
| 50万 | ~7小时 |
| 75万 | ~10.5小时 |
| 100万 | ~14小时 |
| 200万 | 约28小时（~1.2天） |
| 3M | 约42小时（~1.75天） |
| 5分钟 | 约69小时（~2.9天） |
| 10分钟 | 约139小时（~5.8天） |


有关迁移内容的详细步骤，请参阅以下文章：

- [**从4.3.1非UUID迁移到4.3.2 UUID内容**](./migrate-non-uuid-4-3.md)
- [**4.6.0 Service Pack 4非UUID到4.6.1 UUID内容迁移**](./migrate-non-uuid-uuid-4-6.md)



