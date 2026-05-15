---
title: 配置自定义DITA主题模板
description: 了解如何配置自定义DITA主题模板
exl-id: 5a2f4897-9697-4c5c-b5be-8fdb3a211948
feature: Template Configuration
role: Admin
level: Experienced
TQID: https://experienceleague.adobe.com/PX1v2yPqLErAIST8JPr-vUwV81HH6EeFQ4LqKES9gkI
product_v2: id: fae5e35a-80c9-4b94-9352-1a060a6aab1did: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2: id: ab01a588-7dea-43f2-a699-0b3f128465d6id: cb8c6a2a-3c38-4e40-867c-756f8c36bb0e
subfeature_v2: id: b1ef4d86-3917-4b76-a0bc-4a4771f9b3b0id: df6fa66f-4542-4a6d-90ca-9f146eb5d494
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2: id: c1579802-ddd4-4214-8a91-97b2066abe11
source-git-commit: 8ed5c9cb07c56b84b36ef56a55af8738989a6d3f
workflow-type: tm+mt
source-wordcount: 354
ht-degree: 2%

---

# 配置自定义DITA主题模板 {#id16A7G0O02TD}

AEM Guides附带以下DITA主题模板：

- 主题

- 任务

- 概念

- 引用

- 术语表

- 疑难解答

- 空白


可根据创作要求使用任意这些模板来创建主题模板。 空白DITA模板不包含与其它模板类似的任何结构或元素。 如果模板是高度自定义的并且不基于任何常规DITA主题模板，则可以使用“空白”模板作为基础。

要自定义DITA主题模板并将其用于创作，您需要执行以下三个主要任务：

1. *\（可选\）* [配置自定义DITA模板文件夹路径](#id191LCF0095Z)

1. [创建自定义创作模板](conf-folder-level.md#id1917D0EG0HJ)

1. 将自定义模板添加到全局或文件夹级别的配置文件中，如[配置创作模板](conf-folder-level.md#id1889D0IL0Y4)部分中所述


## 配置自定义DITA模板文件夹路径 {#id191LCF0095Z}

AEM Guides允许您配置文件夹以存储自定义的DITA映射和模板。 默认情况下，模板文件存储在DAM的以下文件夹中：

`/content/dam/dita-templates/`

要管理主题和映射模板文件，有专用的文件夹用于存储主题和映射模板。 默认情况下，所有主题模板都存储在`/content/dam/dita-templates/topics`下

文件夹。 所有映射模板都存储在`/content/dam/dita-templates/maps`文件夹下。

作为管理员，您可以选择在默认文件夹中创建自定义映射或主题模板，或者创建自己的文件夹来存储自定义模板。 如果您计划使用默认文件夹，则可以跳过此过程。

使用[配置覆盖](download-install-additional-config-override.md#)中提供的说明创建配置文件。 在配置文件中，提供以下\(property\)详细信息，以便为自定义DITA主题模板配置文件夹：

>[!IMPORTANT]
>
> 如果要使用默认文件夹存储自定义模板，则可以跳过此过程。

| PID | 属性键 | 属性值 |
|---|------------|--------------|
| `com.adobe.fmdita.config.ConfigManager` | `topic.templates` | 指定用于存储自定义模板的位置。<br> 如果DAM中存在指定的位置，则所有默认映射和主题模板都将复制到该文件夹中。 如果该位置不存在，则使用所有默认映射和主题模板创建文件夹。 |

**父级主题：**[&#x200B;配置主题并映射模板](conf-template-tags.md)
