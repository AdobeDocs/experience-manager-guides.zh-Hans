---
title: 配置UUID文件名模式
description: 了解如何配置UUID文件名模式
feature: Migration
role: Admin
level: Experienced
exl-id: 63d19ec4-1313-4691-b83e-38b67f9d2050
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: fae5e35a-80c9-4b94-9352-1a060a6aab1d
    internal-label: Experience Manager Guides
feature_v2:
  - id: 5be0fc8f-1cff-5c3e-bb92-2903a56a3de6
    internal-label: Migration
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 81a0e7f0736ba4970673dd87a888a4c60d3c1b4e
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 1%
---
# 配置UUID文件名模式

导入内容时，文件名不必基于UUID。 在使用基于UUID的文件名的系统中，必须使用UUID而不是原始文件名引用所有文件。 如果导入的文件没有基于UUID的文件名，则可以将系统配置为向其文件属性添加UUID。 然后，使用此UUID来引用此类文件，其中UUID不用于命名文件。

## 配置UUID文件名模式的步骤

以下选项卡提供了有关如何根据Experience Manager Guides设置配置UUID文件名模式的说明：Cloud Service或内部部署。

>[!BEGINTABS]

>[!TAB Cloud Service]

使用[配置覆盖](download-install-config-override.md#)中提供的说明创建配置文件。 在配置文件中，提供以下\(property\)详细信息以配置UUID文件名模式：

| PID | 属性键 | 属性值 |
|---|------------|--------------|
| `com.adobe.fmdita.config.ConfigManager` | `uuid.regex` | 指定UUID文件名模式的正则表达式的字符串。<br> 如果文件不遵循指定的模式，则会将UUID添加到文件的属性中，并且使用分配给文件的UUID更新对该文件的所有引用。<br> **默认值**： `"^GUID-(?<id>.*)"` |

>[!TAB 内部部署]

执行以下步骤以根据UUID模式检查文件名，并将UUID分配给未分配UUID的文件：

1. 打开Adobe Experience Manager Web控制台配置页面。

   用于访问配置页面的默认URL为：

   ```http
   http://<server name>:<port>/system/console/configMgr
   ```

1. 搜索并选择&#x200B;*com.adobe.fmdita.config.ConfigManager*&#x200B;包。

1. 在&#x200B;**UUID文件名模式**&#x200B;属性中，指定模式以检查导入的文件名。

   如果文件不遵循指定的模式，则会将UUID添加到文件的属性中，并且使用分配给文件的UUID更新对该文件的所有引用。

1. 选择&#x200B;**保存**。

>[!ENDTABS]
