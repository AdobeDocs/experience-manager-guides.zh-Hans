---
title: 在同一选项卡中打开DITA主题或映射文件
description: 了解如何在同一选项卡中打开DITA主题或映射文件
exl-id: 466cbea4-c75a-488e-bde2-465cf2c184d5
feature: Web Editor Configuration
role: Admin
level: Experienced
TQID: https://experienceleague.adobe.com/futODy2B62sg-Epb4bnmxHVAOUVoGDoKg5WJWV-7bpM
product_v2: id: fae5e35a-80c9-4b94-9352-1a060a6aab1did: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2: id: cb8c6a2a-3c38-4e40-867c-756f8c36bb0eid: d90290ec-3e61-4ebd-8649-bcafe0836803
subfeature_v2: id: b0521e56-a0b2-40b6-bf47-ebc98751f9ba
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
source-git-commit: 8ed5c9cb07c56b84b36ef56a55af8738989a6d3f
workflow-type: tm+mt
source-wordcount: 207
ht-degree: 0%

---

# 在同一选项卡中打开DITA主题或映射文件 {#id223HH0301J3}

在某些工作流中，当您单击主题或映射文件的链接时，它将在新选项卡中打开。 这可能会导致在浏览器中打开许多选项卡，从而影响您的工作效率。 您可以更改在新选项卡中打开主题或映射文件的这种行为，并在当前选项卡中强制打开它。

使用[配置覆盖](download-install-additional-config-override.md#)中提供的说明创建配置文件。 在配置文件中，提供以下\(property\)详细信息以在新选项卡中打开主题或映射文件：

| PID | 属性键 | 属性值 |
|---|------------|--------------|
| `com.adobe.fmdita.xmleditor.config.XmlEditorConfig` | `xmleditor.openinsametab` | 布尔值\(true/false\)。<br> **默认值**： `false` |

此设置会影响以下位置，您可以从中访问主题或映射文件：

- 创建DITA主题\（在工作流结束时，单击&#x200B;**打开主题**&#x200B;按钮\）

- 创建DITA映射\（在工作流结束时，单击&#x200B;**打开映射**&#x200B;按钮\）

- DITA映射控制台中的“主题”选项卡

- DITA映射控制台中的“基线”选项卡

- DITA映射控制台中的“报表”选项卡


**父主题：**[&#x200B;自定义Web编辑器](conf-web-editor.md)
