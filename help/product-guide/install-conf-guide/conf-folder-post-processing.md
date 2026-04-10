---
title: 配置文件名
description: 了解如何为上传到Adobe Experience Manager Assets的文件夹禁用后处理
feature: Filename Configuration
role: Admin
level: Experienced
source-git-commit: 6f3f05419f4f5cdd45ab580cdee6fa869f20f01d
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 0%

---

# 禁用文件夹的后处理

默认情况下，所有上传的资产都使用DAM更新资产工作流进行处理。 作为此工作流的一部分，Experience Manager Guides会运行一个名为后处理的额外处理。 这还有助于生成UUID

在将文件和文件夹上传到&#x200B;*Adobe Experience Manager Assets*&#x200B;服务器时，您还可以禁用后处理和UUID生成。

以下选项卡提供了有关根据您的Experience Manager Guides设置禁用文件夹后处理的说明：Cloud Service或内部部署。

>[!BEGINTABS]

>[!TAB Cloud Service]

使用[配置覆盖](download-install-config-override.md#)中的说明创建配置文件。 在配置文件中，提供以下（属性）详细信息以禁用给定路径的后处理或忽略文件夹的后处理：

| PID | 属性键 | 属性值 |
|---|------------|--------------|
| `com.adobe.fmdita.config.ConfigManager` | `ignored.post.processing.paths` | 用于设置任何标准NODE_OPTIONS的字符串值（多值属性，路径末尾省略`/`的字符串）<br> **默认值**： `/content/dam/projects/translation_output` |
| `com.adobe.fmdita.config.ConfigManager` | `enabled.post.processing.paths` | 用于设置任何标准NODE_OPTIONS的字符串值（多值属性，路径末尾省略`/`的字符串）<br> **默认值**： `/content/dam` |

>[!TAB 内部部署]

执行以下步骤可禁用给定路径的后处理或忽略文件夹的后处理：


1. 打开Adobe Experience Manager Web控制台配置页面。

   用于访问配置页面的默认URL为：

   ```http
   http://<server name>:<port>/system/console/configMgr
   ```

1. 搜索并单击&#x200B;**com.adobe.fmdita.config.ConfigManager**&#x200B;包。

1. 选择&#x200B;**忽略后处理的路径**&#x200B;选项，以忽略后处理文件夹。

   用于设置任何标准NODE_OPTIONS的字符串值（多值属性，路径末尾省略`/`的字符串）

   **默认值**： `/content/dam/projects/translation_output`

   >[!NOTE]
   >
   > 默认情况下，此属性处于禁用状态，并且地图功能板上提供翻译选项卡。

1. 选择&#x200B;**启用后处理的路径**&#x200B;选项，启用后处理的路径。

   用于设置任何标准NODE_OPTIONS的字符串值（多值属性，路径末尾省略`/`的字符串）

   **默认值**： `/content/dam/`

   >[!NOTE]
   >
   > 默认情况下，此属性处于禁用状态，并且地图功能板上提供翻译选项卡。


1. 单击&#x200B;**保存**。

>[!ENDTABS]

## 启用或禁用后处理的规则

默认情况下，会对Experience Manager DAM文件夹下的每个文件夹路径执行后处理。 根据以下规则为任何文件夹应用配置：

* 如果忽略父文件夹进行后处理，但启用了子文件夹，则子文件夹及其所有后续文件夹均被视为已启用。
* 如果为父项启用后处理，但忽略子项，则将忽略子项及其所有后续项。
* 如果ignored.post.processing.paths和enabled.post.processing.paths配置中存在相同的文件夹路径，则后处理时会将其忽略。

