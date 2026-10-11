---
title: 配置基于UUID的链接的显示
description: 了解如何配置基于UUID的链接的显示
exl-id: 2ae6a27f-983b-4aa0-be29-166899aeb4ff
feature: Web Editor Configuration
role: Admin
level: Experienced
TQID: 'https://experienceleague.adobe.com/--RdjezGIsplCdBLF8u-3LvR92rVBcgGmPo8a7GbQys'
product_v2:
  - id: fae5e35a-80c9-4b94-9352-1a060a6aab1d
    internal-label: Experience Manager Guides
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
feature_v2:
  - id: cb8c6a2a-3c38-4e40-867c-756f8c36bb0e
    internal-label: Configuration
subfeature_v2:
  - id: b0521e56-a0b2-40b6-bf47-ebc98751f9ba
    internal-label: Web Editor configuration
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 81a0e7f0736ba4970673dd87a888a4c60d3c1b4e
workflow-type: tm+mt
source-wordcount: '162'
ht-degree: 1%
---
# 配置基于UUID的链接的显示 {#id2035G20M0QN}

默认情况下，在Web编辑器中使用“插入引用”或“插入重用内容”选项创建链接时，将使用引用内容的UUID创建链接。 引用内容的&#x200B;**Link**&#x200B;属性\（在“属性”面板中\）可以配置为显示引用内容的相对文件路径或UUID。 默认情况下，引用内容的UUID会显示在“属性”面板中。

使用[配置覆盖](download-install-additional-config-override.md#)中提供的说明创建配置文件。 在配置文件中，提供以下\(property\)详细信息以在Web编辑器中显示引用内容的相对路径或UUID：

| PID | 属性键 | 属性值 |
|---|------------|--------------|
| `com.adobe.fmdita.xmleditor.config.XmlEditorConfig` | `xmleditor.uuid` | 布尔值\(true/false\)。 如果要显示链接内容的相对路径，则将此属性设置为false。<br> **默认值**： true |

**父主题：**&#x200B;[&#x200B;自定义Web编辑器](conf-web-editor.md)
