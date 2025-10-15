---
title: 发行说明 | 修复了Adobe Experience Manager Guides 5.1.0 Service Pack 1版本中的问题
description: 了解Adobe Experience Manager Guides 5.1.0 Service Pack 1版本中的错误修复
role: Leader
source-git-commit: 575488e1b378c17419add75876a8e7f7423d5116
workflow-type: tm+mt
source-wordcount: '148'
ht-degree: 1%

---

# 修复了5.1.0 Service Pack 1版本（2025年10月）中的问题


本文介绍Adobe Experience Manager Guides 5.1.0 Service Pack 1版本中修复的各个方面的错误。

了解5.1.0 Service Pack 1版本[的](upgrade-instructions-5-1-0-sp1.md)升级说明。


## 平台

- 从非UUID迁移到UUID并升级到最新版本（5.0及更高版本）时，如果在文件夹之间移动引用的图像然后将DITA文件（其中引用了这些图像）恢复到以前的版本，则会导致图像引用断开。 (指南 — 34315)

## 发布

- 在AEM Sites上使用基线（使用旧版组件映射）发布DITA映射时，也会发布属性为`processing-role = resource-only`的映射元素。 (指南 — 34298)
