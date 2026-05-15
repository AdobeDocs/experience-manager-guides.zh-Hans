---
title: 原生PDF |为本机PDF发布配置节点进程
description: 了解如何为本机PDF发布配置节点进程
feature: Output Generation
role: Admin
level: Experienced
exl-id: f470939b-a5cb-4d28-92d1-7a0a52c4c637
TQID: https://experienceleague.adobe.com/7i-6SjvI5FuSNsWPy9sX96UsXld9fJjAjHNKDKzo824
product_v2: id: fae5e35a-80c9-4b94-9352-1a060a6aab1did: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2: id: a3bd6397-2eb2-4908-a61c-226e26855dcaid: cb8c6a2a-3c38-4e40-867c-756f8c36bb0e
subfeature_v2: id: d6596f3f-92a7-43ec-b444-237db6adad05id: fd6cc9e1-e5e5-494e-b7b1-a32f2d6cd7c9
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
source-git-commit: 8ed5c9cb07c56b84b36ef56a55af8738989a6d3f
workflow-type: tm+mt
source-wordcount: 122
ht-degree: 1%

---

# 为Cloud Service的本机PDF发布配置节点进程

本机PDF发布会启动一个单独的NodeJs进程，以将发布进程中生成的文件转换为最终的PDF。 您可能需要调整此节点进程（运行本机PDF发布）的配置以支持各种场景。 例如，要运行较大的工作负载，应增加派生的NodeJs进程可用的最大栈大小。

使用[配置覆盖](../install-conf-guide/download-install-config-override.md)中提供的说明创建配置文件。在配置文件中，提供以下（属性）详细信息：

| PID | 属性键 | 属性值 |
|---|---|---|
| `com.adobe.fmdita.config.ConfigManager` | `native.pdf.node.opts` | 用于设置任何标准`NODE_OPTIONS`.<BR>的字符串值 默认值：“” |
