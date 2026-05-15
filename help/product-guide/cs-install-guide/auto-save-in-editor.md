---
title: 在Web编辑器中配置文件自动保存
description: 了解如何在Web编辑器中配置文件自动保存
exl-id: 4d99c3d8-cf6a-4cf3-aaec-9009a0376c1e
feature: Web Editor Configuration
role: Admin
level: Experienced
TQID: https://experienceleague.adobe.com/yHZSl9G2a6ras7kUUpNho5TG8yeIJzeFXzwxGQSWp44
product_v2:
  - id: fae5e35a-80c9-4b94-9352-1a060a6aab1d
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: cb8c6a2a-3c38-4e40-867c-756f8c36bb0e
subfeature_v2:
  - id: b0521e56-a0b2-40b6-bf47-ebc98751f9ba
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
source-git-commit: 8ed5c9cb07c56b84b36ef56a55af8738989a6d3f
workflow-type: tm+mt
source-wordcount: 190
ht-degree: 1%

---

# 在Web编辑器中配置文件自动保存 {#id199CC0J0M5Z}

基于浏览器的编辑器中最常见的功能之一是，在特定时间段后能够保存数据。 AEM Guides Web编辑器还支持在指定的时间间隔自动保存主题和映射文件。 触发此功能时，将保存主题或映射的工作副本。 不会创建主题或映射的新版本。 要创建新版本，您必须单击Web编辑器工具栏中的“保存修订版本”图标。

默认情况下，不会启用自动保存功能，您需要使用配置文件启用该功能。

使用[配置覆盖](download-install-additional-config-override.md#)中提供的说明创建配置文件。 在配置文件中，提供以下\(property\)详细信息以配置文件的自动保存和自动保存时间间隔：

| PID | 属性键 | 属性值 |
|---|------------|--------------|
| `com.adobe.fmdita.xmleditor.config.XmlEditorConfig` | `xmleditor.autosave` | 布尔值\(true/false\)。<br> **默认值**： false |
| `xmleditor.autosaveinterval` | 以秒为单位指定触发自动保存功能的时间间隔。 |  |

**父主题：**&#x200B;[&#x200B;自定义Web编辑器](conf-web-editor.md)
