---
title: 上载文件
description: 了解如何将文件上传到AEM存储库并处理错误。 了解资源控制台用户界面、AEM桌面应用程序、资源批量提取器，并使用FrameMaker进行批量上传。
feature: Content Management
role: User
hide: true
exl-id: fcb2cc43-6a36-42f2-a695-7a50ae1031a0
source-git-commit: 7286c3fb36695caa08157296fd6e0de722078c2b
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 0%

---

# 上载文件 {#id176FF000JUI}

您很可能有一个包含要与AEM Guides一起使用的现有DITA内容的存储库。 对于此类现有内容，您可以使用以下任意方法将您的内容批量上传到AEM存储库：

>[!IMPORTANT]
>
> 有关AEM中支持的内容上传方法的详细信息，请参阅[将数字资源添加到Adobe Experience Manager as a Cloud Service Assets](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/manage/add-assets.html?lang=zh-Hans)。

## Assets Console用户界面

您可以在桌面上选择内容，然后在AEM用户界面\（Web浏览器\）上拖动到目标文件夹。 有关详细信息，请参阅AEM文档中的[上传资源](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/manage/add-assets.html?lang=zh-Hans#upload-assets)。

## AEM 桌面应用程序

如果您是创意专业人士并想要在本地桌面上管理资源，请使用AEM桌面应用程序。 您可以使用桌面应用程序打开和编辑这些资源。 您还可以维护版本并与其他用户共享您的文件。 有关更多详细信息，请参阅[AEM桌面应用程序](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html?lang=zh-Hans)。

## 资源批量提取器

如果您进行了大规模迁移并偶尔进行了批量摄取，请使用资产批量摄取器上传您的内容。 使用此工具，您可以从受支持的数据存储（如Azure或S3）上载批量内容。 有关更多详细信息，请参阅[资产批量引入器](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/manage/add-assets.html?lang=zh-Hans#asset-bulk-ingestor)。

## 使用FrameMaker进行批量上传

Adobe FrameMaker附带强大的AEM连接器，可让您轻松地将现有DITA和其他FrameMaker文档\（`.book`和`.fm`\）上传到AEM。 您可以使用各种文件上传功能，例如上传单个文件、上传具有或不具有依赖关系的完整文件夹\（如内容引用、交叉引用和图形\）。

有关在FrameMaker中使用批量上传功能的更多详细信息，请参阅《FrameMaker用户指南》中的&#x200B;*创建CRX文件夹并上传文件*&#x200B;部分。

## 上传内容时出错 {#id201MI0I04Y4}

如果上传一个或多个文件失败，将在上传过程结束时显示一条提示，其中包含上传失败的文件列表：

![](images/uuid-files-failed-to-upload_cs.png){width="650" align="center"}

有关各种文件上传方案的详细信息，请参阅[上传DITA内容](authoring-file-management.md#)。

如果您使用AEM桌面应用程序或资产批量引入器等工具，则对重复文件执行的操作将由AEM服务器中的设置控制。 请与系统管理员联系以了解此配置。

**父主题：**&#x200B;[&#x200B;管理内容](authoring.md)
