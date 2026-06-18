---
title: 配置选项以在氧气中进行编辑
description: 了解如何配置在氧气连接器插件中编辑的选项。
feature: Web Editor Configuration
role: Admin
level: Experienced
exl-id: 41ecbbb2-81c3-473d-b48b-7370a74a6474
source-git-commit: cc73b81787a3c3dbe8390d93e558064327e59965
workflow-type: tm+mt
source-wordcount: '104'
ht-degree: 1%

---

# 配置在Cloud Service的氧气中编辑的选项

AEM Guides还允许用户在氧气连接器插件中编辑其DITA主题和DITA映射。

使用[配置覆盖](download-install-config-override.md#)中提供的说明创建配置文件。 在配置文件中，提供以下（属性）详细信息以配置&#x200B;**在氧气中编辑**&#x200B;选项：



| PID | 属性键 | 属性值 |
|---|------------|--------------|
| `com.adobe.fmdita.xmleditor.config.XmlEditorConfig` | `xmleditor.editinoxygen` | 布尔值\(true/false\)。 **默认值**： false |

>[!NOTE]
>
> 默认情况下，此配置处于禁用状态，并且编辑器中不提供该选项。

**父主题：**&#x200B;[&#x200B;自定义编辑器](customize-overview.md)
