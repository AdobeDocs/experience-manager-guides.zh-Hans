---
title: 将高级映射编辑器设置为默认值
description: 了解如何将高级映射编辑器设置为默认值
feature: Web Editor Configuration
role: Admin
level: Experienced
source-git-commit: 6f3f05419f4f5cdd45ab580cdee6fa869f20f01d
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 0%

---

# 将高级映射编辑器设置为默认值 {#id181AI0003PN}

>[!NOTE]
>
> 以前在Experience Manager Guides中提供的Basic Map Editor已从版本4.3和2307开始弃用。 您不能访问“基本映射编辑器”来创建和管理DITA映射。
>建议您使用高级映射编辑器。 高级映射编辑器提供了增强功能和更好的自定义选项。 详细了解如何使用[高级映射编辑器](../user-guide/map-editor-advanced-map-editor.md)。

对于4.3和2307之前的版本，Experience Manager Guides附带了基本映射编辑器和高级映射编辑器。 基本映射编辑器为您提供了创建映射文件所需的所有功能。 高级映射编辑器功能更丰富，并且集成在Web编辑器中。 高级映射编辑器允许作者使用易于使用的界面创建和编辑DITA映射文件。

默认情况下，每当创建新映射文件时，都会在“基本映射编辑器”中打开该文件。 通过启用默认打开“高级映射编辑器”的设置，可以更改此行为。

以下选项卡提供了有关如何根据您的Experience Manager Guides设置将高级映射编辑器设置为映射文件的默认编辑器的说明：Cloud Service或内部部署。


>[!BEGINTABS]

>[!TAB Cloud Service]

使用[配置覆盖](download-install-config-override.md#)中提供的说明创建配置文件。 在配置文件中，提供以下\(property\)详细信息以启用基本映射编辑器：

| PID | 属性键 | 属性值 |
|---|------------|--------------|
| `com.adobe.fmdita.xmleditor.config.XmlEditorConfig` | ``fmdita.hide.oldmapeditor`` | 布尔值\(true/false\)。 如果默认情况下要使用高级映射编辑器，则将此属性设置为true。<br> **默认值**： false |

>[!NOTE]
>
> 默认情况下，当作者创建映射文件并选择打开该文件进行编辑时，将启动“基本映射编辑器”。 从Assets UI为映射文件选择编辑选项后，也会在基本映射编辑器中打开该选项。

>[!TAB 内部部署]

1. 打开Adobe Experience Manager Web控制台配置页面。

   用于访问配置页面的默认URL为：

   ```http
   http://<server name>:<port>/system/console/configMgr
   ```

1. 搜索并单击&#x200B;**com.adobe.fmdita.xmleditor.config.XmlEditorConfig**&#x200B;包。

1. 选择&#x200B;**隐藏基本映射编辑器**&#x200B;选项。

   选中此选项后，用户将看不到用户界面中任何位置的“基本映射编辑器”链接。 默认情况下，映射文件将在高级映射编辑器中打开。

>[!ENDTABS]

**父主题：**&#x200B;[&#x200B;自定义Web编辑器](customize-overview.md)
