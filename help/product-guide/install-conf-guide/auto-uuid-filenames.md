---
title: 根据UUID配置自动文件名
description: 了解如何根据UUID配置自动文件名
feature: Filename Configuration
role: Admin
level: Experienced
source-git-commit: 6f3f05419f4f5cdd45ab580cdee6fa869f20f01d
workflow-type: tm+mt
source-wordcount: '318'
ht-degree: 1%

---

# 根据UUID配置自动文件名 {#id205QG070D5Z}

默认情况下，在创建主题或映射文件时，作者也可以选择指定文件名。 作者可以根据自己的要求自由分配文件名。 但是，这可能会导致不一致，并且在大型文档系统中可以看到范围广泛的文件名。 作为管理员，您可以限制作者为他们在系统中创建的文件指定文件名。 对于每个新主题或映射文件，您可以选择自动指定基于UUID的文件名。

以下选项卡提供了有关如何根据基于Experience Manager Guides设置的UUID配置自动文件名的说明：Cloud Service或内部部署。


>[!BEGINTABS]

>[!TAB Cloud Service]

使用[配置覆盖](download-install-config-override.md#)中提供的说明创建配置文件。 在配置文件中，提供以下\(property\)详细信息以根据UUID配置自动文件名：

| PID | 属性键 | 属性值 |
|---|------------|--------------|
| `com.adobe.fmdita.xmleditor.config.XmlEditorConfig` | `xmleditor.uniquefilenames` | 布尔值\(true/false\)。<br> **默认值**： false |

>[!NOTE]
>
> 启用此选项后，作者在创建新主题或映射文件时，将不会看到指定文件名的选项。 可以从Assets UI和Web编辑器创建新主题或映射文件。

>[!TAB 内部部署]

执行以下步骤，自动为系统中创建的所有新文件指定基于UUID的文件名：

1. 打开Adobe Experience Manager Web控制台配置页面。

   用于访问配置页面的默认URL为：

   ```http
   http://<server name>:<port>/system/console/configMgr
   ```

1. 搜索并单击&#x200B;*com.adobe.fmdita.xmleditor.config.XmlEditorConfig*&#x200B;包。

1. 选择&#x200B;**使用基于UUID的系统文件名**&#x200B;选项。

1. 单击&#x200B;**保存**。


>[!NOTE]
>
> 默认情况下，此选项处于关闭状态。 启用此选项后，作者在创建新主题或映射文件时，将不会看到指定文件名的选项。 可以从Assets UI和Web编辑器创建新主题或映射文件。

>[!ENDTABS]

