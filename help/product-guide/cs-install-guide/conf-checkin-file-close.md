---
title: 配置关闭时签入文件的提示
description: 了解如何配置关闭时签入文件的提示
exl-id: 5b09ec46-aea4-4a3f-8bab-42414e31e37d
feature: Web Editor Configuration
role: Admin
level: Experienced
source-git-commit: 0513ecac38840a4cc649758bd1180edff1f8aed1
workflow-type: tm+mt
source-wordcount: '174'
ht-degree: 1%

---

# 配置关闭时签入文件的提示 {#id222HC040PE8}

当用户尝试使用文件选项卡上的&#x200B;**关闭**&#x200B;按钮或“选项”菜单中的&#x200B;**关闭**&#x200B;选项关闭在Web编辑器中打开的文件时，如果文件包含未保存的数据或未保存的版本，则会出现一个对话框。 如果文件已锁定，则提示用户解锁文件。

使用[配置覆盖](download-install-additional-config-override.md#)中提供的说明创建配置文件。 在配置文件中，提供以下\(property\)详细信息以配置关闭时签入文件的提示：

| PID | 属性键 | 属性值 |
|---|------------|--------------|
| `com.adobe.fmdita.xmleditor.config.XmlEditorConfig` | `xmleditor.checkin` | 布尔值\( true/ false\)。<br> **默认值**： false |

启用此配置后，默认情况下会选中对话框中的&#x200B;**解锁文件**&#x200B;复选框。

有关更多详细信息，请参阅《使用Adobe Experience Manager Guidesas a Cloud Service指南》中的&#x200B;*文件关闭和保存方案*&#x200B;部分。

**父主题：**&#x200B;[&#x200B;自定义Web编辑器](conf-web-editor.md)
