---
title: 在AEM Guides中管理DITA文件的标记
description: 关于在AEM Guides中管理cq：tags的简短文章
exl-id: 2d805c26-df9b-405a-81ca-7aa84c6f86c8
feature: Metadata Management
author: Pulkit Nagpal(punagpal)
role: User, Admin
TQID: https://experienceleague.adobe.com/u3MZ3fUZIp-FYQE895I7kDRkF3l96KhwYMRMJ-rG2RE
product_v2: id: fae5e35a-80c9-4b94-9352-1a060a6aab1did: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2: id: ab01a588-7dea-43f2-a699-0b3f128465d6id: cb8c6a2a-3c38-4e40-867c-756f8c36bb0eid: d90290ec-3e61-4ebd-8649-bcafe0836803
subfeature_v2: id: ad602516-aca3-4247-9ae8-f393d958efa9
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2: id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dcid: c1579802-ddd4-4214-8a91-97b2066abe11id: ebde5b41-29c9-4f5e-9ef6-1197e85409e3
source-git-commit: 8ed5c9cb07c56b84b36ef56a55af8738989a6d3f
workflow-type: tm+mt
source-wordcount: 362
ht-degree: 0%

---

# 如何在DITA内容中添加、删除和管理标记

标记可用于对您的内容进行分类。 如果内容已正确标记，则它可以帮助您在ditamap中查找准确的主题，并且最终用户可以在已发布的输出中更快地找到相应的内容

> **_NOTE:_**&#x200B;以下文章适用于AEM Guides Build 4.2（内部部署）/2023年2月（云版本）或更高版本


## 创建标记

标记是AEM的本机功能，您的AEM管理员可以帮助您初始创建和配置这些标记。


## 添加、删除和管理DITA内容中的标记

**在AEM cq中创建的任何标记：可以为您的DITA内容添加、删除和管理标记**

可通过多种方式将标记添加到DITA内容中，但本文将重点介绍AEM Guides Web编辑器UI。

### 步骤：

1. 转到指南UI中的存储库视图
2. 双击ditamap并在映射视图中打开
3. 转到“管理”选项卡
4. 在管理选项卡中，转到元数据选项
5. 此处加载您的所有直接和间接ditamap文件列表。
6. 选择一个或多个文件并单击“管理”图标。 您可以在此处向所选文件添加标记。
也可以删除所选文件中常见的现有标记。

<img title="在AEM Guides中管理标记 " alt="管理DITA中的标记 " src="ManageTags.jpg">

## 疑难解答和常见问题解答

### 在管理 — >元数据中的列表为空或不完整

`If list is empty or  incomplete then you may need to run the indexing on your ditamap, You can refer` [升级说明（为您的内容编制索引）](https://experienceleague.adobe.com/docs/experience-manager-guides-learn/tutorials/install-guide/on-prem-ig/download-install-upgrade-aemg/upgrade-xml-documentation.html?lang=en#steps-to-index-the-existing-content-to-use-the-new-find-and-replace%3A)

### 自定义元数据未在列表中显示

`Only Tags present in cq:tags can be managed from here and custom metadata is not supported`




## 其他有用资源

- [使用映射功能板批量标记(Assets UI)](https://experienceleague.adobe.com/docs/experience-manager-guides-learn/tutorials/user-guide/manaege-metadata/map-editor-bulk-tagging.html?lang=en)
- [Web编辑器中的Ditamap报表](https://experienceleague.adobe.com/docs/experience-manager-guides-learn/tutorials/user-guide/reports-aem-guide/reports-web-editor.html?lang=en)
- [AEM中的标记](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/configuring/tagging.html?lang=en)


**有关任何其他查询，请与相应的CSM联系**
