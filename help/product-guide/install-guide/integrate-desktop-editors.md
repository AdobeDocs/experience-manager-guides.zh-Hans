---
title: 集成基于桌面的XML编辑器
description: 了解如何集成基于桌面的XML编辑器
exl-id: 268e8613-bb3b-4577-96fb-a588dabfd834
feature: Publishing FrameMaker Documents
role: Admin
level: Experienced
source-git-commit: 434d7efd24147af23b4c65aeebf4c144ce3adda7
workflow-type: tm+mt
source-wordcount: '317'
ht-degree: 0%

---

# 集成基于桌面的XML编辑器 {#id181GB01G0HS}

市面上有许多XML编辑器，您已经可以使用了一个。 Adobe FrameMaker是最强大的XML编辑器之一，它附带AEM连接器。 在FrameMaker中使用AEM连接器，您可以轻松地与AEM存储库连接、签出和签入文件，以及直接在FrameMaker中编辑文件。 您还可以将Experience Manager Guides配置为从Web编辑器启动FrameMaker。 在FrameMaker中打开文件后，您可以编辑该文件并将其签回AEM存储库中。

## 从Web编辑器以FrameMaker启用文件编辑

可以使用FrameMaker或任何其他DITA编辑器创建和更新DITA内容。 但是，如果贵组织使用FrameMaker作为DITA编辑器，则可以为用户提供选项以直接从AEM在FrameMaker中打开DITA文档。

默认情况下，您的用户在AEM工具栏上看不到&#x200B;**在FrameMaker中打开**&#x200B;按钮。 执行以下步骤以在AEM工具栏中添加此按钮：

1. 打开Adobe Experience Manager Web控制台配置页面。

   用于访问配置页面的默认URL为：

   ```http
   http://<server name>:<port>/system/console/configMgr
   ```

1. 搜索并单击&#x200B;**com.adobe.fmdita.xmleditor.config.XmlEditorConfig**包。
   ![](assets/open-in-fm-config.png)

1. 选择&#x200B;**在FrameMaker中显示打开按钮**&#x200B;选项。

1. 如果您使用的是版本4.6和FrameMaker2022 9月版 — 更新3，则必须启用&#x200B;**FrameMaker版本2022更新3或更高版本**&#x200B;配置以便用户将Experience Manager Guides服务器详细信息传递到FrameMaker。 默认情况下，该选项处于禁用状态。


1. 单击&#x200B;**保存**。


启用&#x200B;**在FrameMaker中显示打开按钮**&#x200B;选项后，选择AEM存储库中的任何DITA文件时都会显示&#x200B;**在FrameMaker中打开**&#x200B;按钮。 当此选项为&#x200B;*未启用*&#x200B;时，仅当您在存储库中选择.fm或.book文件时，才会显示&#x200B;**在FrameMaker中打开**&#x200B;按钮。



