---
title: 原生PDF |为本机PDF发布配置节点进程
description: 了解如何为本机PDF发布配置节点进程
feature: Output Generation
role: Admin
level: Experienced
exl-id: f470939b-a5cb-4d28-92d1-7a0a52c4c637
source-git-commit: ccaf2ead1a9a24ab822298c6b9ef6866a1c32e8c
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
