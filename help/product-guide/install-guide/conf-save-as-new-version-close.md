---
title: 配置关闭时另存为新版本的提示
description: 了解如何配置关闭时另存为新版本的提示
exl-id: 1b8c3eaa-a654-4563-9541-18a59b7d306c
feature: Web Editor Configuration
role: Admin
level: Experienced
TQID: https://experienceleague.adobe.com/VdnwN--C-0kLd-vo5RDFLNXNBKzU7wofWZJsvPuVGAA
product_v2:
  - id: fae5e35a-80c9-4b94-9352-1a060a6aab1d
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: cb8c6a2a-3c38-4e40-867c-756f8c36bb0e
subfeature_v2:
  - id: b0521e56-a0b2-40b6-bf47-ebc98751f9ba
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
source-git-commit: 8ed5c9cb07c56b84b36ef56a55af8738989a6d3f
workflow-type: tm+mt
source-wordcount: 213
ht-degree: 0%

---

# 配置关闭时另存为新版本的提示 {#id222HBI00XXA}

当用户尝试使用文件选项卡上的&#x200B;**关闭**&#x200B;按钮或“选项”菜单中的&#x200B;**关闭**&#x200B;选项关闭在Web编辑器中打开的文件时，如果文件包含未保存的数据或未保存的版本，则会出现一个对话框。 如果未保存该版本，则提示用户将文件另存为新版本。

默认情况下未启用&#x200B;**另存为新版本**&#x200B;复选框，您需要从configMgr启用此复选框。 执行以下步骤以在Web编辑器中默认启用此选项：

1. 打开Adobe Experience Manager Web控制台配置页面。

   用于访问配置页面的默认URL为：

   ```http
   http://<server name>:<port>/system/console/configMgr
   ```

1. 搜索并单击&#x200B;**com.adobe.fmdita.xmleditor.config.XmlEditorConfig**&#x200B;包。

1. 选择&#x200B;**关闭**&#x200B;时询问新版本选项。

1. 单击&#x200B;**保存**。


选中此选项后，默认情况下会选中对话框中的&#x200B;**另存为新版本**&#x200B;复选框。

有关更多详细信息，请参阅“使用Adobe Experience Manager Guides as a Cloud Service”指南中的&#x200B;*文件关闭和保存方案*&#x200B;部分。

**父主题：**&#x200B;[&#x200B;自定义Web编辑器](conf-web-editor.md)
