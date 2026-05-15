---
title: 发行说明 |修复了Adobe Experience Manager Guides 5.1.0 Service Pack 1版本中的问题
description: 了解Adobe Experience Manager Guides 5.1.0 Service Pack 1版本中的错误修复
role: Leader
exl-id: 4b51085b-1f71-41e2-b0a9-88a12990fc97
TQID: https://experienceleague.adobe.com/HEWV5RxPUfqUYf6m6kQW-fU-LiAM0UFGbfzKjtOCZxk
product_v2: id: fae5e35a-80c9-4b94-9352-1a060a6aab1did: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2: id: a3bd6397-2eb2-4908-a61c-226e26855dca
role_v2: id: f8a45b24-4be7-4f1b-909b-60d06b483a20
source-git-commit: 8ed5c9cb07c56b84b36ef56a55af8738989a6d3f
workflow-type: tm+mt
source-wordcount: 144
ht-degree: 1%

---

# 修复了5.1.0 Service Pack 1版本（2025年10月）中的问题


本文介绍Adobe Experience Manager Guides 5.1.0 Service Pack 1版本中修复的各个方面的错误。

了解5.1.0 Service Pack 1版本](upgrade-instructions-5-1-0-sp1.md)的[升级说明。


## 平台

- 从非UUID迁移到UUID并升级到最新版本（5.0及更高版本）时，如果在文件夹之间移动引用的图像然后将DITA文件（其中引用了这些图像）恢复到以前的版本，则会导致图像引用断开。 （指南 — 34315）

## 发布

- 在AEM Sites上使用基线（使用旧版组件映射）发布DITA映射时，也会发布属性为`processing-role = resource-only`的映射元素。 （指南 — 34298）
