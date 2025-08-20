---
title: 发行说明 | Adobe Experience Manager Guides 2025.06.0版本中的新增功能
description: 了解Adobe Experience Manager Guides 2025.06.0版本中的新增功能和增强功能
role: Leader
exl-id: 48f27aa6-d870-4228-8e62-db81699a25f7
source-git-commit: d418ffb254b11430509609b91e0174690815cf73
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 4%

---

# 2025.06.0版本（2025年6月）的新增功能

本文介绍Adobe Experience Manager Guides as a Cloud Service 2025.06.0版本中引入的新增功能和增强功能。

有关此版本中修复的问题列表，请查看 [2025.06.0 版本中已修复的问题](fixed-issues-2025-06-0.md)。

了解2025.06.0版本[的](../release-info/upgrade-instructions-2025-06-0.md)升级说明。

## 会话超时提示以防止意外内容丢失

现在，当Adobe Experience Manager会话过期且您因非活动状态而注销时，系统会弹出一条消息通知您。 会话结束后，当您尝试在Experience Manager Guides中编辑内容时，将触发此消息。 该功能有助于降低丢失未保存工作的风险，并提高体验的整体可靠性和流动性，即使是在不活动期间。

![](assets/sign-out-prompt.png)

了解有关Experience Manager Guides中[会话超时提示](../user-guide/session-timeout-prompt.md)的更多信息。

## 编辑器中的增强映射下载选项

Experience Manager Guides在&#x200B;**下载映射**&#x200B;对话框中引入了新的&#x200B;**使用实际文件名**&#x200B;选项。 现在，当您下载映射文件时，您可以选择保留其原始文件名而不是默认UUID，从而更易于识别和管理您的文件。 仅当您选择&#x200B;**保留文件层次结构**&#x200B;时，此选项才可用，当您选择&#x200B;**拼合文件层次结构**&#x200B;时，此选项将禁用，这样您就可以在组织下载的映射时更加灵活。

有关详细信息，请查看[下载文件](../user-guide/authoring-download-assets.md#download-a-dita-map-file-from-the-editor)。

![](assets/download-map-dialog-new.png){width="300" align="left"}


## 在编辑器中增强了`navref`处理

对编辑器的最新增强功能改进了对DITA映射中`navref`元素的处理。 现在，当您将`navref`元素添加到地图时，**选择路径**&#x200B;对话框打开，允许您轻松选择要作为导航链接包含在地图中的地图引用。 添加后，所添加地图的标题会同时显示在创作视图和布局视图中，这样可在创作期间更好地显示包含的导航。  此外，添加的`navref`元素会自动解析以在编辑器中显示引用的映射。

有关详细信息，请查看[添加导航引用](../user-guide/map-editor-other-features.md#add-navigation-references)。

## AI助手中的性能增强

此发行版本引入了AI Assistant后端引擎的增强功能，提供了改进的性能和更好的稳定性。 要启用此更新并继续使用AI助手帮助，请执行以下操作：

- 更新`chat.url`配置以反映新的端点URL。
- 在Cloud Manager中添加新的环境变量`GUIDES_AI_SITE_ID`。

有关详细信息，请查看[配置AI助手](../cs-install-guide/conf-smart-suggestions.md)。

