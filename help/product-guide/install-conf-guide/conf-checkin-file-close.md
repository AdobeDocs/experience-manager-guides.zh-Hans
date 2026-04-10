---
title: 配置关闭时签入文件的提示
description: 了解如何配置关闭时签入文件的提示
feature: Web Editor Configuration
role: Admin
level: Experienced
source-git-commit: 6f3f05419f4f5cdd45ab580cdee6fa869f20f01d
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 1%

---

# 配置关闭时签入文件的提示 {#id222HC040PE8}

当用户尝试使用文件选项卡上的&#x200B;**关闭**&#x200B;按钮或“选项”菜单中的&#x200B;**关闭**&#x200B;选项关闭在Web编辑器中打开的文件时，如果文件包含未保存的数据或未保存的版本，则会出现一个对话框。 如果文件已锁定，则提示用户解锁文件。

以下选项卡提供了相关说明，用于根据您的Experience Manager Guides设置，在Web编辑器中配置提示以签入关闭时文件选项：Cloud Service或内部部署。

>[!BEGINTABS]

>[!TAB Cloud Service]

使用[配置覆盖](download-install-config-override.md#)中提供的说明创建配置文件。 在配置文件中，提供以下\(property\)详细信息以配置关闭时签入文件的提示：

| PID | 属性键 | 属性值 |
|---|------------|--------------|
| `com.adobe.fmdita.xmleditor.config.XmlEditorConfig` | `xmleditor.checkin` | 布尔值\( true/ false\)。<br> **默认值**： false |

启用此配置后，默认情况下会选中对话框中的&#x200B;**解锁文件**&#x200B;复选框。

有关更多详细信息，请参阅“使用Adobe Experience Manager Guides as a Cloud Service”指南中的&#x200B;*文件关闭和保存方案*&#x200B;部分。

>[!TAB 内部部署]

>[!NOTE]
>
>默认情况下，**解锁文件**&#x200B;复选框未启用，您需要从configMgr启用它。 执行以下步骤以在Web编辑器中默认启用此选项：

1. 打开Adobe Experience Manager Web控制台配置页面。

   用于访问配置页面的默认URL为：

   ```http
   http://<server name>:<port>/system/console/configMgr
   ```

1. 搜索并单击&#x200B;**com.adobe.fmdita.xmleditor.config.XmlEditorConfig**&#x200B;包。

1. 选择&#x200B;**关闭时要求签入**&#x200B;选项。

1. 单击&#x200B;**保存**。


启用此配置后，默认情况下会选中对话框中的&#x200B;**解锁文件**&#x200B;复选框。

有关更多详细信息，请参阅“使用Adobe Experience Manager Guides as a Cloud Service”指南中的&#x200B;*文件关闭和保存方案*&#x200B;部分。

>[!ENDTABS]

**父主题：**[&#x200B;自定义Web编辑器](customize-overview.md)
