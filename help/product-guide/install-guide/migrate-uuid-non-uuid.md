---
title: 非UUID到UUID内容迁移
description: 了解如何将非UUID迁移到UUID内容
exl-id: f8b723bf-84c0-4fe6-936e-63970fb3e417
feature: Migration
role: Admin
level: Experienced
source-git-commit: 6e23f52fc9124d0f07f8108da1b5fe574f553469
workflow-type: tm+mt
source-wordcount: '205'
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
| 4.3.1非UUID | 4.3.2 UUID | 迁移到版本4.3.2 UUID后，您可以直接安装4.6.0 (UUID)。 在4.6.0上运行后，升级到5.1.0版，然后安装5.1.0 Service Pack 1。 |
| 4.6.0 Service Pack 4非UUID | 4.6.1 UUID | 迁移到版本4.6.1 UUID后，您可以直接升级到5.1.0 (UUID)。 升级完成后，安装版本5.1.0 Service Pack 1。 |

有关迁移内容的详细步骤，请参阅以下文章：

- [从&#x200B;**4.3.1非UUID迁移到4.3.2 UUID内容**](./migrate-non-uuid-4-3.md)
- [从&#x200B;**4.6.0 Service Pack 4非UUID迁移到4.6.1 UUID内容**](./migrate-non-uuid-uuid-4-6.md)



