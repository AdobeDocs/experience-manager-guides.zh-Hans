---
title: 将高级映射编辑器设置为默认值
description: 了解如何将高级映射编辑器设置为默认值
exl-id: 365264ab-f990-42c1-ab79-61a40ecea42f
feature: Web Editor Configuration
role: Admin
level: Experienced
source-git-commit: 126cecdaa481b9da1add4ba3664c26c2bc5da068
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 0%

---

# 将高级映射编辑器设置为默认值 {#id181AI0003PN}

>[!NOTE]
>
> 以前在Experience Manager Guides中提供的Basic Map Editor已从版本4.3和2307开始弃用。 您不能访问“基本映射编辑器”来创建和管理DITA映射。
>建议您使用高级映射编辑器。 高级映射编辑器提供了增强功能和更好的自定义选项。 详细了解如何使用[高级映射编辑器](../user-guide/map-editor-advanced-map-editor.md)。

对于4.3和2307之前的版本，Experience Manager Guides附带了基本映射编辑器和高级映射编辑器。 基本映射编辑器为您提供了创建映射文件所需的所有功能。 高级映射编辑器功能更丰富，并且集成在Web编辑器中。 高级映射编辑器允许作者使用易于使用的界面创建和编辑DITA映射文件。

默认情况下，每当创建新映射文件时，都会在“基本映射编辑器”中打开该文件。 通过启用默认打开“高级映射编辑器”的设置，可以更改此行为。

使用[配置覆盖](download-install-additional-config-override.md#)中提供的说明创建配置文件。 在配置文件中，提供以下\(property\)详细信息以启用基本映射编辑器：

| PID | 属性键 | 属性值 |
|---|------------|--------------|
| `com.adobe.fmdita.xmleditor.config.XmlEditorConfig` | ``fmdita.hide.oldmapeditor`` | 布尔值\(true/false\)。 如果默认情况下要使用高级映射编辑器，则将此属性设置为true。<br> **默认值**： false |

>[!NOTE]
>
> 默认情况下，当作者创建映射文件并选择打开该文件进行编辑时，将启动“基本映射编辑器”。 从Assets UI为映射文件选择编辑选项后，也会在基本映射编辑器中打开该选项。

**父主题：**&#x200B;[&#x200B;自定义Web编辑器](conf-web-editor.md)
