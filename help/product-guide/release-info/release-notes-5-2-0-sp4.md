---
title: 发行说明 | Adobe Experience Manager Guides 5.2.0 Service Pack 4版的发行说明
description: 了解Adobe Experience Manager Guides 5.2.0 Service Pack 4版本中的升级流程和错误修复
role: Leader
TQID: https://experienceleague.adobe.com/HEWV5RxPUfqUYf6m6kQW-fU-LiAM0UFGbfzKjtOCZxk
product_v2:
  - id: fae5e35a-80c9-4b94-9352-1a060a6aab1d
    internal-label: Experience Manager Guides
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
feature_v2:
  - id: a3bd6397-2eb2-4908-a61c-226e26855dca
    internal-label: Publishing
role_v2:
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
    internal-label: Leader
source-git-commit: ad78587f55ec7190443dbbce80f596821ec41f9f
workflow-type: tm+mt
source-wordcount: '528'
ht-degree: 1%
---
# 5.2.0 Service Pack 4版（2026年11月）的发行说明

本文提供了有关Adobe Experience Manager Guides 5.2.0 Service Pack 4版本中的升级说明、Java SDK兼容性、修复问题和已知问题的信息。

## Java SDK资源

在开发自定义Java插件或与Experience Manager Guides的集成时，请使用以下资源。 确保SDK版本与您安装的Experience Manager Guides版本匹配。

| 发行版本 | Java SDK版本 | Maven Central | Java API参考 |
|---|---|---|----|
| 5.2.0 Service Pack 4 (UUID) | 5.2.2 | [AEM Guides SDK API 5.2.2](https://central.sonatype.com/artifact/com.adobe.aem/aem-guides-sdk-api/5.2.2/) | [Javadoc 5.2.2](https://javadoc.io/doc/com.adobe.aem/aem-guides-sdk-api/latest/index.html) |

有关更多详细信息，请查看[从Maven Central存储库](https://experienceleague.adobe.com/en/docs/experience-manager-guides/using/api-reference/introduction)配置并使用API JAR。

## 升级到Experience Manager Guides的5.2.0 Service Pack 4版本

了解如何安装Experience Manager Guides 5.2.0 Service Pack 4版本。

>[!NOTE]
>
>此版本仅适用于AEM 6.5 LTS。 支持的Service Pack是AEM 6.5 LTS Service Pack 2。

### 先决条件

在启动Experience Manager Guides 5.2.0 Service Pack 4升级过程之前，请确保您使用的是版本5.2.0 Service Pack 1。

### 升级过程5.2.0 Service Pack 4版本

1. 下载Experience Manager Guides包版本5.2.0 Service Pack 4。
1. 使用包管理器(`/crx/packmgr`)将包上载到实例。
1. 安装包。 然后验证`fmdita`包是否已返回到&#x200B;**活动**&#x200B;状态。 您可以在`/system/console/bundles`处检查包状态。
1. 清除浏览器缓存。

## 修复的问题

修复了多个区域中的错误如下：

### 创作

- 当您将资产从资源管理器面板拖放到映射中，而另一个作者移动该资产后未刷新该映射时，断开的引用将添加到映射中。 （指南 — 57869）

### 资产管理

- 使用&#x200B;**覆盖现有文件**&#x200B;选项覆盖现有的非DITA资源（如图像）时，不会创建已上载图像的新版本。 因此，使用基线生成的输出将包含较旧的资源。 （指南 — 59287）

- 从非UUID设置迁移到UUID设置的非DITA资产（例如图像）恢复或分支到其他版本时，其UUID会发生更改。 不再解析对资产的现有引用，并且图像在引用资产的主题中显示为断开。 （指南 — 58414）

### 发布

- 在导出其他映射的同时发布映射时，输出会间歇性地使用较低质量的图像格式，而不是原始矢量图像。 （指南 — 55221）

## 已知问题

Adobe已在5.2.0 Service Pack 4版本中发现以下已知问题：

- 将元素拖放到无效位置时，编辑器会将其移动到最近的有效位置，在此过程中，引用可能会保留其存储库路径。 同样，当使用拖放替换DITA映射中的现有引用时，新引用可能会保留其存储库路径。 （指南 — 60688）