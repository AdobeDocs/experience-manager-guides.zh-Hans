---
title: 配置文件名
description: 了解如何为上传到Adobe Experience Manager Assets的文件夹禁用后处理
feature: Filename Configuration
role: Admin
level: Experienced
exl-id: 42722c6f-1b1c-4a7e-89ef-a373623eb774
source-git-commit: 635206ca34db633a998b0156e2549d86a83f8131
workflow-type: tm+mt
source-wordcount: '574'
ht-degree: 0%

---

# 禁用文件夹的后处理

默认情况下，所有上传的资产都使用DAM更新资产工作流进行处理。 作为此工作流的一部分，Experience Manager Guides会运行一个名为后处理的额外处理。 这还有助于生成UUID

在将文件和文件夹上传到&#x200B;*Adobe Experience Manager Assets*&#x200B;服务器时，您还可以禁用后处理和UUID生成。

使用[配置覆盖](download-install-additional-config-override.md#)中的说明创建配置文件。 在配置文件中，提供以下（属性）详细信息以禁用给定路径的后处理或忽略文件夹的后处理：

>[!NOTE]
>
> 您还可以使用正则表达式（正则表达式）定义应用于多个文件夹或整个文件夹层次结构的规则。 有关更多详细信息，请查看[使用regex启用或禁用后处理](#use-regex-to-enable-or-disable-post-processing)部分。

| PID | 属性键 | 属性值 |
|---|------------|--------------|
| `com.adobe.fmdita.config.ConfigManager` | `ignored.post.processing.paths` | 用于设置任何标准NODE_OPTIONS的字符串值（多值属性，路径在结尾或正则表达式处省略`/`的字符串）<br> **默认值**： `/content/dam/projects/translation_output` |

| PID | 属性键 | 属性值 |
|---|------------|--------------|
| `com.adobe.fmdita.config.ConfigManager` | `enabled.post.processing.paths` | 用于设置任何标准NODE_OPTIONS的字符串值（多值属性，路径在结尾或正则表达式处省略`/`的字符串）<br> **默认值**： `/content/dam` |

## 启用或禁用后处理的规则

默认情况下，会对Experience Manager DAM文件夹下的每个文件夹路径执行后处理。 根据以下规则为任何文件夹应用配置：

* 如果忽略父文件夹进行后处理，但启用了子文件夹，则子文件夹及其所有后续文件夹均被视为已启用。
* 如果为父项启用后处理，但忽略子项，则将忽略子项及其所有后续项。
* 如果`ignored.post.processing.paths`和`enabled.post.processing.paths`配置中存在相同的文件夹路径，则后处理时会将其忽略。

## 使用正则表达式启用或禁用后处理

您可以使用正则表达式(regex)来定义适用于多个文件夹或整个文件夹层次结构的规则，而不是指定单个文件夹路径。

在后处理期间，将针对整个资产路径评估正则表达式模式。

当使用正则表达式（正则表达式）配置忽略和启用的后处理路径时，AEM Guides会根据资源路径评估这两个配置。 如果路径同时匹配忽略规则和启用规则，则忽略规则始终优先。

以下示例说明了如何评估基于正则表达式的忽略和启用规则。

## 后处理正则表达式评估方案

### 忽略父层次结构，启用特定文件夹

**忽略正则表达式**

`regex:/content/dam/lang-test/.*`

**启用regex**

`regex:/content/dam/lang-test/.*/parent1`

在上述示例中，`/content/dam/lang-test/en/parent1`将禁用后处理。

尽管路径与启用正则表达式匹配，但它已与ignore正则表达式匹配。 忽略规则优先，因此不启用后处理。

### 忽略特定文件夹，启用更广泛的层次结构

**忽略正则表达式**

`regex:/content/dam/lang-test/.*/parent1`

**启用regex**

`regex:/content/dam/lang-test/.*`

在上例中，`/content/dam/lang-test/en/parent1`将禁用后处理，而`/content/dam/lang-test/en/parent2`将启用后处理。

`parent1`路径被显式忽略，并且保持禁用状态。 只与启用正则表达式匹配的其他文件夹将被处理。

### 忽略父文件夹，启用子文件夹

**忽略正则表达式**

`regex:/content/dam/lang-test/.*/parent1`

**启用regex**

`regex:/content/dam/lang-test/.*/parent1/child1`

在上例中，`/content/dam/lang-test/en/parent1`和`/content/dam/lang-test/en/parent1/child2`的后处理将被禁用，`/content/dam/lang-test/en/parent1/child1`将启用。

处理正则表达式显式启用的子文件夹。 其他子文件夹仍保持禁用状态，因为其父路径与忽略正则表达式匹配。

### 忽略特定的子文件夹，启用父层次结构

**忽略正则表达式**

`regex:/content/dam/lang-test/.*/parent1/child1`

**启用regex**

`regex:/content/dam/lang-test/.*/parent1`

在上述示例中，`/content/dam/lang-test/en/parent1/child1`将禁用后处理，并为`/content/dam/lang-test/en/parent1`和`/content/dam/lang-test/en/parent1/child2`启用后处理。

仅跳过被显式忽略的子文件夹。 处理父文件夹和其他子文件夹，因为它们与启用正则表达式匹配，与忽略正则表达式不匹配。

