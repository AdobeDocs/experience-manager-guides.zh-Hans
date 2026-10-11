---
title: 配置选项以在氧气中进行编辑
description: 了解如何配置在氧气连接器插件中编辑的选项。
feature: Web Editor Configuration
role: Admin
level: Experienced
exl-id: 41ecbbb2-81c3-473d-b48b-7370a74a6474
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: fae5e35a-80c9-4b94-9352-1a060a6aab1d
    internal-label: Experience Manager Guides
feature_v2:
  - id: cb8c6a2a-3c38-4e40-867c-756f8c36bb0e
    internal-label: Configuration
subfeature_v2:
  - id: b0521e56-a0b2-40b6-bf47-ebc98751f9ba
    internal-label: Web Editor configuration
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 81a0e7f0736ba4970673dd87a888a4c60d3c1b4e
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
