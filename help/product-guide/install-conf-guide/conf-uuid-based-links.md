---
title: 配置基于UUID的链接的显示
description: 了解如何配置基于UUID的链接的显示
feature: Web Editor Configuration
role: Admin
level: Experienced
source-git-commit: 6f3f05419f4f5cdd45ab580cdee6fa869f20f01d
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 1%

---

# 配置基于UUID的链接的显示 {#id2035G20M0QN}

默认情况下，在编辑器中使用“插入引用”或“插入重用内容”选项创建链接时，将使用引用内容的UUID创建链接。 引用内容的&#x200B;**Link**&#x200B;属性\（在“属性”面板中\）可以配置为显示引用内容的相对文件路径或UUID。 对于Cloud Service，默认情况下，引用内容的UUID会显示在“属性”面板中。 对于内部部署，此显示由&#x200B;**中的**&#x200B;启用UUID`configMgr`选项控制。 默认情况下，此功能处于打开状态，这意味着引用内容的UUID显示在“属性”面板中。

以下选项卡提供了有关如何根据您的Experience Manager Guides设置在编辑器中显示引用内容的相对路径或UUID的说明： Cloud Service或内部部署。

>[!BEGINTABS]

>[!TAB Cloud Service]

使用[配置覆盖](download-install-config-override.md#)中提供的说明创建配置文件。 在配置文件中，提供以下\(property\)详细信息以在编辑器中显示引用内容的相对路径或UUID。

| PID | 属性键 | 属性值 |
|---|------------|--------------|
| `com.adobe.fmdita.xmleditor.config.XmlEditorConfig` | `xmleditor.uuid` | 布尔值\(true/false\)。 如果要显示链接内容的相对路径，则将此属性设置为false。<br> **默认值**： true |


>[!TAB 内部部署]

1. 打开Adobe Experience Manager Web控制台配置页面。

   用于访问配置页面的默认URL为：

   ```http
   http://<server name>:<port>/system/console/configMgr
   ```

1. 搜索并单击&#x200B;**com.adobe.fmdita.xmleditor.config.XmlEditorConfig**&#x200B;包。

1. 在&#x200B;*XmlEditorConfig*&#x200B;设置中，**启用UUID**&#x200B;选项默认处于启用状态。 这意味着引用内容的UUID显示在“属性”面板的&#x200B;**Link**&#x200B;属性中。

   如果要显示链接内容的相对路径，请取消选择&#x200B;**启用UUID**&#x200B;选项。

1. 单击&#x200B;**保存**。

>[!ENDTABS]

**父主题：**[&#x200B;自定义Web编辑器](customize-overview.md)
