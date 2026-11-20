---
title: 发行说明 |修复了Adobe Experience Manager Guides 2026.11.0 Service Pack 1版本中的问题
description: 了解Adobe Experience Manager Guides as a Cloud Service 2026.11.0 Service Pack 1版本中的错误修复。
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: fae5e35a-80c9-4b94-9352-1a060a6aab1d
    internal-label: Experience Manager Guides
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
source-git-commit: 8821e671951d83439688aa33f88ac1f91f0919eb
workflow-type: tm+mt
source-wordcount: '315'
ht-degree: 0%
---
# 修复了2026.11.0 Service Pack 1版本中的问题

本文介绍Adobe Experience Manager Guides as a Cloud Service 2026.11.0 Service Pack 1版本中修复的错误。

## 发布

发布到AEM Sites（使用复合组件映射）时出现以下问题：

- 通过`microservice-based`发布重新生成选定主题或子映射大约需要生成完整映射的时间。 （指南 — 59322）
- 重新生成包含分块主题的子映射会导致目录显示错误的标题和链接。 每个分块主题条目都会显示最后一个分块主题的标题。 （指南 — 58650）

使用动态基线（旧版）或新基线发布到AEM Sites时，会出现以下问题：

- 在同一发布操作期间多次重建基线，这会延长发布时间，并且在某些情况下会导致重建停止。 对于新基线，增量发布还会使用过时的基线，而不是当前基线，因此输出可能不会反映最新内容。 （指南 — 60189）
- 使用地图仪表板时，出现一些性能问题。 （GUIDES-60189和GUIDES-55646）

## 已知问题

Adobe发现了2026.11.0 Service Pack 1版本的以下已知问题：

- 使用Experience Manager Guides as a Cloud Service 2026.11.0或更高版本时，如果AEM在发布过程中（例如服务器实例启动时）重新启动某些内部服务，则发布会失败并出现应用程序错误。 (GUIDES-60804)<br>**解决方法：**&#x200B;要解决此问题，请重试发布。
- 当通过&#x200B;**映射集合**&#x200B;或API为多个AEM Sites（使用复合组件映射）预设或本机PDF预设生成输出时，输出生成失败，并出现`Rebuild the Baseline`异常。 <br>**解决方法：**&#x200B;按顺序而非同时发布预设以避免出现此问题。