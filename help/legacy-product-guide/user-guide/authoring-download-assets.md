---
title: 下载文件
description: 了解如何从AEM Guides中的DITA映射控制台下载文件，以及导出AEM存储库中的DITA映射文件。
feature: Content Management
role: User
hide: true
exl-id: b04a0abe-a029-44ac-b8f4-138d78908d44
TQID: https://experienceleague.adobe.com/iCZL0VgkFqcKWqnTpNWkXvJUXyMbLUL6wENBvVXe40Y
product_v2: id: fae5e35a-80c9-4b94-9352-1a060a6aab1did: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2: id: a3bd6397-2eb2-4908-a61c-226e26855dcaid: ab01a588-7dea-43f2-a699-0b3f128465d6
subfeature_v2: id: f9dbea21-a714-40dd-bc90-080d8046c93f
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554
source-git-commit: 8ed5c9cb07c56b84b36ef56a55af8738989a6d3f
workflow-type: tm+mt
source-wordcount: 440
ht-degree: 0%

---

# 下载文件 {#id216MC0H0BE8}

您可以下载包括DITA和非DITA文件的资源。 您可以通过多种方式下载资源，有些方法是AEM的固有方法，而其他方法受AEM Guides支持。 有关本机AEM资源下载信息，请参阅AEM文档中的[从Adobe Experience Manager下载资源](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/manage/download-assets-from-aem.html)。 以下部分将介绍通过AEM Guides中的DITA映射控制台下载文件的机制。

## 导出DITA映射文件

在AEM存储库中拥有DITA映射文件后，即可下载映射文件及其依赖项。 这使您能够灵活地共享完整的映射文件，以便进行离线编辑、验证、审阅或只是创建备份。

执行以下步骤下载DITA映射文件及其依赖文件：

1. 在Assets UI中，导航到要下载的DITA映射。

1. 单击DITA映射以在DITA映射控制台中将其打开。

1. 选择&#x200B;**主题**&#x200B;选项卡以查看DITA映射中可用的主题列表。

1. 在主工具栏中，单击&#x200B;**下载地图**。

   出现“Download Map（下载映射）”对话框。

   ![](images/download-map.png){width="300"}

1. 单击&#x200B;**“下载”。** 在“下载映射”对话框中，您可以选择以下选项：

   - **使用基线**：选择此选项可获取为DITA映射创建的基线列表。 如果要根据特定基线下载映射文件及其内容，请从下拉列表中选择基线。 有关使用基线的更多详细信息，请参阅[使用基线](generate-output-use-baseline-for-publishing.md#)。
   - **平面化文件层次结构**：选择此选项可将所有引用的主题和媒体文件保存在单个文件夹中。
   >[!NOTE]
   >
   > 您也可以在不选择任何选项的情况下下载映射文件。 在这种情况下，将下载引用的主题和媒体文件的最新保留版本。

1. 单击&#x200B;**下载**&#x200B;按钮后，映射下载请求将排入队列。 一旦地图可供下载，您将收到以下通知。

   ![](images/download-map-prompt.png){width="550"}

   - 单击&#x200B;**下载**&#x200B;以.zip格式下载映射文件。

   - 单击&#x200B;**稍后下载**&#x200B;稍后下载映射文件。 可以从AEM通知收件箱访问下载链接。 单击收件箱中生成的映射通知，以.zip格式下载映射。

   >[!NOTE]
   >
   > 默认情况下，下载的地图会在AEM通知收件箱中保留五天。

![](images/download-map-inbox.png){width="300"}

下载地图后，您可以选择该地图并使用顶部的打开图标打开选定的报表。

**父主题：**[&#x200B;管理内容](authoring.md)
