---
title: 在编辑器中自动保存配置文件
description: 了解如何在编辑器中配置文件自动保存
feature: Web Editor Configuration
role: Admin
level: Experienced
exl-id: 142a588a-3d26-48ee-a3fe-23882922243c
source-git-commit: cc73b81787a3c3dbe8390d93e558064327e59965
workflow-type: tm+mt
source-wordcount: '275'
ht-degree: 1%

---

# 在编辑器中自动保存配置文件 {#id199CC0J0M5Z}

基于浏览器的编辑器中最常见的功能之一是，能够在特定时间段后保存数据。 AEM Guides编辑器还支持在指定的时间间隔自动保存主题和映射文件。 触发此功能时，将保存主题或映射的工作副本。 不会创建主题或映射的新版本。 要创建新版本，您必须单击编辑器工具栏中的保存修订版本图标。

默认情况下不启用自动保存功能，您需要使用Cloud Service的配置文件和内部部署的`configMgr`中的配置文件启用此功能。

以下选项卡提供了有关如何根据您的Experience Manager Guides设置在Cloud Service编辑器中启用自动保存功能的说明：内部部署。

>[!BEGINTABS]

>[!TAB Cloud Service]

使用[配置覆盖](download-install-config-override.md#)中提供的说明创建配置文件。 在配置文件中，提供以下\(property\)详细信息以配置文件的自动保存和自动保存时间间隔：

| PID | 属性键 | 属性值 |
|---|------------|--------------|
| `com.adobe.fmdita.xmleditor.config.XmlEditorConfig` | `xmleditor.autosave` | 布尔值\(true/false\)。<br> **默认值**： false |
| `xmleditor.autosaveinterval` | 以秒为单位指定触发自动保存功能的时间间隔。 |  |

>[!TAB 内部部署]

1. 打开Adobe Experience Manager Web控制台配置页面。

   用于访问配置页面的默认URL为：

   ```http
   http://<server name>:<port>/system/console/configMgr
   ```

1. 搜索并单击&#x200B;**com.adobe.fmdita.xmleditor.config.XmlEditorConfig**&#x200B;包。

1. 在&#x200B;*XmlEditorConfig*&#x200B;设置中，选择&#x200B;**自动保存**&#x200B;选项。

1. 在&#x200B;**自动保存时间间隔**&#x200B;字段中，以秒为单位指定时间间隔以触发自动保存功能。

1. 单击&#x200B;**保存**。

>[!ENDTABS]
