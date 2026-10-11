---
title: 根据UUID配置自动文件名
description: 了解如何根据UUID配置自动文件名
feature: Filename Configuration
role: Admin
level: Experienced
exl-id: 2b591ddc-173b-484a-995f-1b3322babbbd
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: fae5e35a-80c9-4b94-9352-1a060a6aab1d
    internal-label: Experience Manager Guides
feature_v2:
  - id: cb8c6a2a-3c38-4e40-867c-756f8c36bb0e
    internal-label: Configuration
subfeature_v2:
  - id: ccd46b93-df7f-4458-ba4c-90a3562d9ab0
    internal-label: Filename configuration
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 81a0e7f0736ba4970673dd87a888a4c60d3c1b4e
workflow-type: tm+mt
source-wordcount: '325'
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
> 启用此选项后，作者在创建新主题或映射文件时，将不会看到指定文件名的选项。 可以从Assets UI和编辑器创建新主题或映射文件。

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
> 默认情况下，此选项处于关闭状态。 启用此选项后，作者在创建新主题或映射文件时，将不会看到指定文件名的选项。 可以从Assets UI和编辑器创建新主题或映射文件。

>[!ENDTABS]
