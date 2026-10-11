---
title: 原生PDF |为本机PDF发布配置节点进程
description: 了解如何为本机PDF发布配置节点进程
feature: Output Generation
role: Admin
level: Experienced
exl-id: 5321c785-8259-4ee2-9ada-ee70fb99b4fd
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: fae5e35a-80c9-4b94-9352-1a060a6aab1d
    internal-label: Experience Manager Guides
feature_v2:
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
source-wordcount: '122'
ht-degree: 1%
---
# 为Cloud Service的本机PDF发布配置节点进程

本机PDF发布会启动一个单独的NodeJs进程，以将发布进程中生成的文件转换为最终的PDF。 您可能需要调整此节点进程（运行本机PDF发布）的配置以支持各种场景。 例如，要运行较大的工作负载，应增加派生的NodeJs进程可用的最大栈大小。

使用[配置覆盖](../install-conf-guide/download-install-config-override.md)中提供的说明创建配置文件。在配置文件中，提供以下（属性）详细信息：

| PID | 属性键 | 属性值 |
|---|---|---|
| `com.adobe.fmdita.config.ConfigManager` | `native.pdf.node.opts` | 用于设置任何标准`NODE_OPTIONS`.<BR>的字符串值 默认值：“” |
