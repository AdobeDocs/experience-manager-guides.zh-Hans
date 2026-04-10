---
title: 集成基于桌面的XML编辑器
description: 了解如何集成基于桌面的XML编辑器
feature: Publishing FrameMaker Documents
role: Admin
level: Experienced
exl-id: 86ba53fa-0e08-4791-9018-09fe974691da
hidefromtoc: true
source-git-commit: 564ee1731be2378744ffd2ed54a2fd423901a0b3
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 1%

---

# 集成基于桌面的XML编辑器

市面上有许多XML编辑器，您已经可以使用了一个。 Adobe FrameMaker是最强大的XML编辑器之一，它与AEM连接器一起提供。 使用FrameMaker中的AEM连接器，您可以轻松连接到AEM存储库、签出和签入文件以及直接在FrameMaker中编辑文件。 您还可以配置Experience Manager Guides以从Web编辑器启动FrameMaker。 在FrameMaker中打开文件后，您可以编辑该文件并将其签回AEM存储库。

## 从Web编辑器在FrameMaker中启用文件编辑

您可以使用FrameMaker或任何其他DITA编辑器创建和更新DITA内容。 但是，如果贵组织使用FrameMaker作为DITA编辑器，则可以为用户提供一个选项，以直接从AEM在FrameMaker中打开DITA文档。


默认情况下，您的用户在AEM工具栏上看不到&#x200B;**在FrameMaker中打开**&#x200B;按钮。 执行以下步骤以在AEM工具栏中添加此按钮：

使用[配置覆盖](download-install-additional-config-override.md#)中提供的说明创建配置文件。 在配置文件中，提供以下\(property\)详细信息以在AEM工具栏上添加此按钮：


| PID | 属性键 | 属性值 |
|---|------------|--------------|
| `com.adobe.fmdita.xmleditor.config.XmlEditorConfig` | `xmleditor.openinframebuttonshow` | 布尔值\(true/false\)。 如果要显示&#x200B;**在FrameMaker中打开**&#x200B;按钮，则将此属性设置为true。<br> **默认值**： false |



如果您使用的是版本2409和FrameMaker 2022 9月版 — 更新3，则必须为用户启用&#x200B;**FrameMaker版本2022更新3或更高版本**&#x200B;配置以将Experience Manager Guides服务器详细信息传递到FrameMaker。  默认情况下，该选项处于禁用状态。


| PID | 属性键 | 属性值 |
|---|------------|--------------|
| `com.adobe.fmdita.xmleditor.config.XmlEditorConfig` | `xmleditor.openinframe2022above` | 布尔值\(true/false\)。 如果您使用的是FrameMaker 2022年9月版 — 更新3 ，则将此属性设置为true。<br> **默认值**： false |



将&#x200B;*openinframebuttonshow*&#x200B;属性设置为true时，选择AEM存储库中的任何DITA文件时都会显示&#x200B;**在FrameMaker中打开**&#x200B;按钮。 此属性未设置为&#x200B;*true*&#x200B;时，仅当在存储库中选择.fm或.book文件时，才会显示&#x200B;**在FrameMaker中打开**&#x200B;按钮。
