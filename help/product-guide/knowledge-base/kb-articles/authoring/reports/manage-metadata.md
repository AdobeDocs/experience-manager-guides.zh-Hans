---
title: 在AEM Guides中管理DITA文件的标记
description: 关于在AEM Guides中管理cq：tags的简短文章
exl-id: 2d805c26-df9b-405a-81ca-7aa84c6f86c8
feature: Metadata Management
role: User, Admin
source-git-commit: be06612d832785a91a3b2a89b84e0c2438ba30f2
workflow-type: tm+mt
source-wordcount: '280'
ht-degree: 1%

---

# 如何在DITA内容中添加、删除和管理标记

标记可用于对您的内容进行分类。 如果内容已正确标记，则它可以帮助您在ditamap中查找准确的主题，并且最终用户可以在已发布的输出中更快地找到相应的内容

> **_注意：_**&#x200B;以下文章适用于AEM Guides Build 4.2（内部部署）/2023年2月（云版本）或更高版本


## 创建标记

标记是本机AEM功能，AEM管理员可以帮助您初始创建和配置这些标记。


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

- [使用映射仪表板(Assets UI)批量标记](https://experienceleague.adobe.com/docs/experience-manager-guides-learn/tutorials/user-guide/manaege-metadata/map-editor-bulk-tagging.html?lang=en)
- 在Web编辑器中[个Ditamap报告](https://experienceleague.adobe.com/docs/experience-manager-guides-learn/tutorials/user-guide/reports-aem-guide/reports-web-editor.html?lang=en)
- 在AEM中标记[](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/configuring/tagging.html?lang=en)


**有关任何其他查询，请与相应的CSM联系**
