---
title: 发行说明 | Adobe Experience Manager Guides as a Cloud Service，2023年4月版
description: 2023年4月版Adobe Experience Manager Guides as a Cloud Service
exl-id: 269e3a13-584d-4cff-a18a-d4fa89646a5a
feature: Release Notes
role: Leader
TQID: https://experienceleague.adobe.com/c1aOcwHgxAs11yAalOnlW-ghsTP1Or32TnBwLsc59-M
product_v2:
  - id: fae5e35a-80c9-4b94-9352-1a060a6aab1d
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: a3bd6397-2eb2-4908-a61c-226e26855dca
subfeature_v2:
  - id: d6596f3f-92a7-43ec-b444-237db6adad05
role_v2:
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
topic_v2:
  - id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dc
source-git-commit: 8ed5c9cb07c56b84b36ef56a55af8738989a6d3f
workflow-type: tm+mt
source-wordcount: 386
ht-degree: 0%

---

# Adobe Experience Manager Guides as a Cloud Service 2023年4月版的新增功能

本文介绍Adobe Experience Manager Guides版本2023年4月中的新增功能和增强功能（以后称为&#x200B;*AEM Guides as a Cloud Service*）。

有关升级说明、兼容性矩阵以及此版本中修复的问题的更多详细信息，请参阅[发行说明](release-notes-2023-4-0.md)文章。

## PDF发布中的高级元数据支持

AEM Guides现在为映射到PDF输出中元数据的元数据提供高级支持。 元数据选项包括有关文档及其内容的信息，如作者姓名、文档标题、关键字、版权信息和其他数据字段。

<img src="assets/pdf-metadata.png" alt=" 原生pdf元数据">

您可以导入XMP文件，AEM Guides可以从文件中选取信息。 您还可以选择使用下拉菜单提供元数据名称和值。 您还可以通过直接在名称字段中键入来添加自定义元数据。


## 增强的大纲视图面板

AEM Guides提供了一个改进的“大纲视图”面板，您可以在其中获得文档中所用元素的分层视图。

<img src="assets/select-element-content-outline-view_cs.png" alt=" 原生pdf元数据">

“大纲视图”提供了以下增强功能：

* “视图选项”下拉列表显示在“大纲视图”面板的顶部。 如果元素具有ID、属性和文本，则可以从下拉列表中选择它们，以与元素一起显示它们。 可以在“大纲视图”面板中显示的属性由管理员在&#x200B;**编辑器设置**&#x200B;中配置的显示属性设置决定。

* 使用搜索功能，您可以按元素的名称、ID、文本或属性值搜索元素。


## AEM Guides as a Cloud Service基于微服务的发布

AEM Guides as a Cloud Service提供了与基于微服务的发布同时运行大型发布工作负载的功能，并利用业界领先的Adobe I/O Runtime无服务器平台。

现在，在4月版中，您可以使用基于微服务的本机PDF发布来同时运行多个发布请求并非常高效地生成批量PDF输出。
有关详细信息，请参阅[为AEM Guides as a Cloud Service配置新的基于微服务的发布](../knowledge-base/publishing/configure-microservices.md)。
