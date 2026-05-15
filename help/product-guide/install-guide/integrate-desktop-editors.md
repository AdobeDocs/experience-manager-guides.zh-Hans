---
title: 集成基于桌面的XML编辑器
description: 了解如何集成基于桌面的XML编辑器
exl-id: 268e8613-bb3b-4577-96fb-a588dabfd834
feature: Publishing FrameMaker Documents
role: Admin
level: Experienced
TQID: https://experienceleague.adobe.com/wILI1Y5nUtUiEuHG0wN4q2KCQko5mKN6CKy1Cs5kxTU
product_v2: id: fae5e35a-80c9-4b94-9352-1a060a6aab1did: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2: id: a3bd6397-2eb2-4908-a61c-226e26855dcaid: cb8c6a2a-3c38-4e40-867c-756f8c36bb0e
subfeature_v2: id: bf79f6d3-0ad0-4d82-99e4-42ce98324d60id: fd6cc9e1-e5e5-494e-b7b1-a32f2d6cd7c9
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
source-git-commit: 8ed5c9cb07c56b84b36ef56a55af8738989a6d3f
workflow-type: tm+mt
source-wordcount: 322
ht-degree: 0%

---

# 集成基于桌面的XML编辑器 {#id181GB01G0HS}

市面上有许多XML编辑器，您已经可以使用了一个。 Adobe FrameMaker是最强大的XML编辑器之一，它与AEM连接器一起提供。 使用FrameMaker中的AEM连接器，您可以轻松连接到AEM存储库、签出和签入文件以及直接在FrameMaker中编辑文件。 您还可以配置Experience Manager Guides以从Web编辑器启动FrameMaker。 在FrameMaker中打开文件后，您可以编辑该文件并将其签回AEM存储库。

## 从Web编辑器在FrameMaker中启用文件编辑

您可以使用FrameMaker或任何其他DITA编辑器创建和更新DITA内容。 但是，如果贵组织使用FrameMaker作为DITA编辑器，则可以为用户提供一个选项，以直接从AEM在FrameMaker中打开DITA文档。

默认情况下，您的用户在AEM工具栏上看不到&#x200B;**在FrameMaker中打开**&#x200B;按钮。 执行以下步骤以在AEM工具栏中添加此按钮：

1. 打开Adobe Experience Manager Web控制台配置页面。

   用于访问配置页面的默认URL为：

   ```http
   http://<server name>:<port>/system/console/configMgr
   ```

1. 搜索并单击&#x200B;**com.adobe.fmdita.xmleditor.config.XmlEditorConfig**包。
   ![](assets/open-in-fm-config.png)

1. 选择&#x200B;**在FrameMaker中显示打开按钮**&#x200B;选项。

1. 如果您使用的是版本4.6和FrameMaker 2022 9月版 — 更新3，则必须启用&#x200B;**FrameMaker版本2022更新3或更高版本**&#x200B;配置以便用户将Experience Manager Guides服务器详细信息传递到FrameMaker。 默认情况下，该选项处于禁用状态。


1. 单击&#x200B;**保存**。


启用&#x200B;**在FrameMaker中显示打开**&#x200B;选项后，选择AEM存储库中的任何DITA文件时都会显示&#x200B;**在FrameMaker中打开**&#x200B;按钮。 当此选项为&#x200B;*未启用*&#x200B;时，仅当您在存储库中选择.fm或.book文件时，才会显示&#x200B;**在FrameMaker中打开**&#x200B;按钮。



