---
title: 安装用于基于文章的发布的包
description: 了解如何安装包以进行基于文章的发布
exl-id: d83fc1a9-0822-47f0-8099-22a74b9ced2a
feature: Web Editor Configuration
role: Admin
level: Experienced
source-git-commit: 0513ecac38840a4cc649758bd1180edff1f8aed1
workflow-type: tm+mt
source-wordcount: '348'
ht-degree: 0%

---

# 安装用于基于文章的发布的包 {#id21BNL02052Z}

AEM Guides提供了与Web编辑器集成的强大的基于文章的发布功能。 使用此功能，您可以同时发布一个或多个主题。 在地图编辑器中打开地图后，您可以导航到输出选项卡以创建预设，然后选择一个或多个主题以生成输出。 您可以使用基于文章的发布功能递增地生成一个或多个主题的输出，或以逐篇文章的方式将内容发布到知识库平台。 有关更多详细信息，请参阅用户指南中的Web编辑器部分&#x200B;*中基于文章的发布。*

要创建用于发布基于文章的输出的AEM站点，请执行以下步骤：

1. 从您的[XML Documentation软件分发门户](https://experience.adobe.com/#/downloads/content/software-distribution/en/general.html)下载Cloud Service **的** Adobe组件内容包。
1. 打开AEM包管理器。 访问包管理器的默认URL为： `https://<hostname>/crx/packmgr/index.jsp`
1. 上传用于Cloud Service的XML Documentation组件内容包，然后安装它。
1. 从[Adobe软件分发门户](https://experience.adobe.com/#/downloads/content/software-distribution/en/general.html)下载`Knowledge-base-template-for-article-based-publishing-for-cloud-service.zip`文件。
1. 从全局导航中选择&#x200B;**站点**。
1. 在站点UI中，单击右上角的&#x200B;**创建**&#x200B;按钮。
1. 从&#x200B;**创建**&#x200B;下拉列表中选择&#x200B;**从模板**&#x200B;创建站点。
1. 单击“**导入**”按钮，然后选择在您的系统上下载的`Knowledge-base-template-for-article-based-publishing-for-cloud-service.zip`。 导入站点模板后，该模板将列在底部。

   >[!NOTE]
   >
   > 您只需在第一次导入ZIP文件即可。 导入后，站点模板即可在列表中找到。

   选择&#x200B;**基于文章的发布的知识库模板**&#x200B;以创建AEM站点，然后单击右上角的&#x200B;**下一步**。

1. 输入&#x200B;**站点标题**&#x200B;和&#x200B;**站点名称**，然后单击右上角的&#x200B;**创建**。 AEM站点是使用Tragopan站点模板创建的。 \(Tragopan站点是一个示例知识库AEM站点，其中包含用于类别、分区和文章页面的模板。\)

   >[!NOTE]
   >
   > 您可以使用同一模板创建多个AEM站点。


您可以使用AEM站点通过Web编辑器中的输出预设发布文章。

**父主题：**[&#x200B;自定义Web编辑器](conf-web-editor.md)
