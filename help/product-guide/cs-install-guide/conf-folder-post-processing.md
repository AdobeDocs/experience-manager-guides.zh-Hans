---
title: 配置文件名
description: 了解如何为上传到Adobe Experience Manager Assets的文件夹禁用后处理
feature: Filename Configuration
role: Admin
level: Experienced
exl-id: 42722c6f-1b1c-4a7e-89ef-a373623eb774
source-git-commit: 5d99274da8fdacbd255d426fa4913b5773ca45f8
workflow-type: tm+mt
source-wordcount: '258'
ht-degree: 1%

---

# 禁用文件夹的后处理

默认情况下，所有上传的资产都使用DAM更新资产工作流进行处理。 作为此工作流的一部分，Experience Manager Guides会运行一个名为后处理的额外处理。 这还有助于生成UUID

在将文件和文件夹上传到&#x200B;*Adobe Experience Manager Assets*&#x200B;服务器时，您还可以禁用后处理和UUID生成。


使用[配置覆盖](download-install-additional-config-override.md#)中的说明创建配置文件。 在配置文件中，提供以下（属性）详细信息以禁用给定路径的后处理或忽略文件夹的后处理：

| PID | 属性键 | 属性值 |
|---|------------|--------------|
| `com.adobe.fmdita.config.ConfigManager` | `ignored.post.processing.paths` | 用于设置任何标准NODE_Property的字符串值(多值OPTIONS，路径末尾省略`/`的字符串)<br> **默认值**： `/content/dam/projects/translation_output` |


| PID | 属性键 | 属性值 |
|---|------------|--------------|
| `com.adobe.fmdita.config.ConfigManager` | `enabled.post.processing.paths` | 用于设置任何标准NODE_Property的字符串值(多值OPTIONS，路径末尾省略`/`的字符串)<br> **默认值**： `/content/dam` |


## 启用或禁用后处理的规则

默认情况下，会对Experience ManagerDAM文件夹下的每个文件夹路径执行后处理。 根据以下规则为任何文件夹应用配置：

* 如果忽略父文件夹进行后处理，但启用了子文件夹，则子文件夹及其所有后续文件夹均被视为已启用。
* 如果为父项启用后处理，但忽略子项，则将忽略子项及其所有后续项。
* 如果ignored.post.processing.paths和enabled.post.processing.paths配置中存在相同的文件夹路径，则后处理时会将其忽略。
