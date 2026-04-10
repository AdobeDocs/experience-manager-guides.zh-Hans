---
title: 为有效的文件名字符配置Regx
description: 了解如何为有效的文件名字符配置Regx
feature: Filename Configuration
role: Admin
level: Experienced
source-git-commit: 6f3f05419f4f5cdd45ab580cdee6fa869f20f01d
workflow-type: tm+mt
source-wordcount: '506'
ht-degree: 0%

---

# 为有效的文件名字符配置Regx {#id214BD0550E8}

从AEM Guides 3.8版本开始，作为管理员，您可以定义一个列表，其中包含允许在文件名中使用的有效特殊字符。 在早期版本中，允许用户定义包含特殊字符（如`@`、`$`、`>`等）的文件名。 这些特殊字符在DITA映射仪表板中打开主题或单击目录中的主题链接时会导致问题，这通常会导致URL中的特殊字符导致页面无法打开。

使用允许您为有效文件名字符定义regx的配置，您可以完全控制如何在系统中命名文件。 您可以定义文件名中允许使用的特殊字符列表。 默认情况下，有效的文件名配置包含“`a-z A-Z 0-9 - _`”。 创建新文件时，文件的标题中可以包含任何特殊字符，但在内部，文件名中将替换为“`-`”。 例如，文件的标题可以是“Introduction 1”或“Introduction@1”，针对这两种情况生成的相应文件名是“Introduction-1”。

定义有效字符列表时，请记住，这些字符“`*/:[\]|#%{}?&<>"/+`”将始终替换为“`-`”。

如果未配置有效的特殊字符列表，文件创建过程可能会给您一些意外的结果。 为避免此类错误，强烈建议更改此配置。

以下选项卡提供了有关如何根据Experience Manager Guides设置为有效文件名字符配置Regx的说明： Cloud Service或内部部署。


>[!BEGINTABS]

>[!TAB Cloud Service]

使用[配置覆盖](download-install-config-override.md#)中提供的说明创建配置文件。 在配置文件中，提供以下\(property\)详细信息以配置有效文件名字符的正则表达式：

| PID | 属性键 | 属性值 |
|---|------------|--------------|
| `com.adobe.fmdita.xmleditor.config.XmlEditorConfig` | `valid.characters` | 该值是一个正则表达式模式。 它必须具有三个基本字符，并且列表必须以连字符\(-\)开头。<br> **默认值**： \[-a-zA-Z0-9\_\] |

>[!NOTE]
>
> 与有效文件名字符列表类似，您还可以为AEM站点输出指定有效文件名字符列表。 有关更多详细信息，请参阅[为AEM站点输出配置有效文件名](conf-file-names-valid-regx-aem-site-output.md#)。

>[!TAB 内部部署]

要为文件名中的有效\（或允许\）字符配置regx，请执行以下步骤：

1. 打开Adobe Experience Manager Web控制台配置页面。

   用于访问配置页面的默认URL为：

   ```http
   http://<server name>:<port>/system/console/configMgr
   ```

1. 搜索并单击&#x200B;*com.adobe.fmdita.config.ConfigManager*&#x200B;包。

1. 在&#x200B;**有效字符的正则表达式**&#x200B;属性中，确保将该属性设置为\[-a-zA-Z0-9\_\]。 您可以向此列表添加更多字符，但是，它必须具有这些基本字符，并且列表必须以连字符“ — ”开头。

   >[!NOTE]
   >
   > 此属性仅适用于文件名，不适用于文件夹名称。

1. 单击&#x200B;**保存**。


>[!NOTE]
>
> 与有效文件名字符列表类似，您还可以为AEM站点输出指定有效文件名字符列表。 有关更多详细信息，请参阅[为AEM站点输出配置有效文件名](conf-file-names-valid-regx-aem-site-output.md#)。

>[!ENDTABS]
