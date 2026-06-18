---
title: 在编辑器中自动保存配置文件
description: 了解如何在编辑器中配置文件自动保存
exl-id: 23fe404c-c76d-43ba-9b28-c49ab1e524de
feature: Web Editor Configuration
role: Admin
level: Experienced
TQID: https://experienceleague.adobe.com/-VGsv3zHE6oACLVpnYm24-rX9-H6uUGyz3SEsP2ILBE
product_v2: id: fae5e35a-80c9-4b94-9352-1a060a6aab1did: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2: id: cb8c6a2a-3c38-4e40-867c-756f8c36bb0e
subfeature_v2: id: b0521e56-a0b2-40b6-bf47-ebc98751f9ba
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
source-git-commit: cc73b81787a3c3dbe8390d93e558064327e59965
workflow-type: tm+mt
source-wordcount: 197
ht-degree: 1%

---

# 在编辑器中自动保存配置文件 {#id199CC0J0M5Z}

基于浏览器的编辑器中最常见的功能之一是，在特定时间段后能够保存数据。 AEM Guides编辑器还支持在指定的时间间隔自动保存主题和映射文件。 触发此功能时，将保存主题或映射的工作副本。 不会创建主题或映射的新版本。 要创建新版本，您必须单击编辑器工具栏中的保存修订版本图标。

默认情况下，不会启用自动保存功能，您需要从configMgr启用此功能。 执行以下步骤以在编辑器中启用自动保存功能：

1. 打开Adobe Experience Manager Web控制台配置页面。

   用于访问配置页面的默认URL为：

   ```http
   http://<server name>:<port>/system/console/configMgr
   ```

1. 搜索并单击&#x200B;**com.adobe.fmdita.xmleditor.config.XmlEditorConfig**&#x200B;包。

1. 在&#x200B;*XmlEditorConfig*&#x200B;设置中，选择&#x200B;**自动保存**&#x200B;选项。

1. 在&#x200B;**自动保存时间间隔**&#x200B;字段中，以秒为单位指定时间间隔以触发自动保存功能。

1. 单击&#x200B;**保存**。


**父主题：**[&#x200B;自定义编辑器](conf-web-editor.md)
