---
title: Experience Manager Guides文档
description: 查找Adobe Experience Manager Guides的文档。 了解Experience Manager中的本机DITA支持、结构化创作和多渠道发布。
feature: AEM Guides Tutorials
role: User
TQID: https://experienceleague.adobe.com/S4wTM-7gfU7D-JfKVbb9nK3qoQIG6PdiY7jtpsc6kDs
product_v2:
  - id: fae5e35a-80c9-4b94-9352-1a060a6aab1d
    internal-label: Experience Manager Guides
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
feature_v2:
  - id: a3bd6397-2eb2-4908-a61c-226e26855dca
    internal-label: Publishing
  - id: ab01a588-7dea-43f2-a699-0b3f128465d6
    internal-label: Authoring
  - id: cb8c6a2a-3c38-4e40-867c-756f8c36bb0e
    internal-label: Configuration
  - id: d90290ec-3e61-4ebd-8649-bcafe0836803
    internal-label: Reports
  - id: f59890ff-de81-47d5-9ef8-7ab2dd10c6c3
    internal-label: Authoring and publishing content
subfeature_v2:
  - id: aad65a09-20cc-4780-ad44-329d14dc8481
    internal-label: Workflows
  - id: ad602516-aca3-4247-9ae8-f393d958efa9
    internal-label: Editor
  - id: f89f75b0-cf2e-4e96-aec8-fe8c39cbd0ef
    internal-label: Web Editor
  - id: f901afa4-5613-4581-add5-219fa5f03fb5
    internal-label: Publishing
  - id: fd6cc9e1-e5e5-494e-b7b1-a32f2d6cd7c9
    internal-label: Output generation
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
    internal-label: Troubleshooting
  - id: f5c2a4bb-71ca-4d7e-8efd-442250e6ba48
    internal-label: Content reuse
source-git-commit: 411756129e6ce756f8674d6d3feb27a1cd9a2f19
workflow-type: tm+mt
source-wordcount: '311'
ht-degree: 5%
---
# Experience Manager Guides文档

Experience Manager Guides是一款企业级CCMS，它在本机DITA中支持结构化创作、多渠道发布和内容生命周期管理。

**部署：** [!BADGE Cloud Service]{type=Positive} [!BADGE 内部部署]{type=Informative}

## 由您的角色开始

::::landing-cards-container
:::card
![管理员图标](./user-guide/images/admin.png)

管理员

配置文件夹配置文件、权限、工作流设置和输出模板。

[管理指南](./install-conf-guide/introduction.md)
:::

:::card
![作者图标](./user-guide/images/author.png)

作者

创建和管理DITA主题、映射、内容重用和审阅工作流。

[创作概述](./user-guide/authoring-content.md)
:::

:::card
![发布者图标](./user-guide/images/publish.png)

发布者

设置输出预设、管理基线并生成跨渠道输出。

[地图管理和发布](./user-guide/map-console-overview.md)
:::

::::


<!--
:::card
![Architects icon](./user-guide/images/architect.svg)

Architects

Design DITA specializations, schemas, and content architecture for your implementation.

[DITA specialization](./install-conf-guide/dita-ot-specialization.md)
:::

::::
-->

## 按功能区域浏览

<!-- Author note: Six cards will wrap to two rows of three in production. Same beta caveat as the role cards above applies here. -->

::::landing-cards-container

:::card
![创作图标](./user-guide/images/author.svg)

创作

Web编辑器、FrameMaker集成、可重用内容和审核周期。

[创作您的内容](./user-guide/web-editor.md)
:::

:::card
![审阅图标](./user-guide/images/review.svg)

审阅

审阅主题、管理审阅任务和审阅通知。

[评论简介](./user-guide/review.md)
:::

:::card
![发布图标](./user-guide/images/publish.svg)

发布

PDF、AEM Sites、HTML5、EPUB和JSON输出类型。

[发布您的内容](./user-guide/generate-output.md)
:::

:::card
![翻译图标](./user-guide/images/Smock_GlobeGrid_18_N.svg)

翻译

多语言内容的人工翻译和机器翻译工作流。

[翻译内容](./user-guide/translation.md)
:::

:::card
![报告图标](./user-guide/images/Smock_Report_18_N.svg)

报告

主题列表、多媒体、断开的链接和元数据报表。

[生成报表](./user-guide/reports-intro.md)
:::

:::card
![配置图标](./user-guide/images/config.svg)

配置

文件夹配置文件、DITA-OT自定义和输出模板。

[配置文件夹配置文件](./install-conf-guide/conf-profiles.md)
:::

::::

## 新增功能

<!-- Author note: Badges render correctly in markdown table cells per ExL spec. <br> is supported within cells. Update release version, links, and descriptions each release cycle. The What's new table is the primary update touchpoint on this page — aim to refresh it within one week of each cloud service release. -->
::::landing-cards-container

:::card
![管理员图标](https://cdn.experienceleague.adobe.com/icons/admin.svg)

Git连接器

直接从Git存储库将内容导入指南。

[使用Git连接器导入内容](./user-guide/web-editor-git-connector.md)
:::

:::card
![疑难解答图标](https://cdn.experienceleague.adobe.com/icons/atomic-search-troubleshoot.svg)

新建地图收藏集

用于管理映射和发布输出的统一界面。

[新建地图收藏集](./user-guide/web-editor-git-connector.md)
:::

:::card
![书图标](https://cdn.experienceleague.adobe.com/icons/book.svg)

委派审核任务

审阅人可以将审阅任务委派给其他审阅人。

[委派审核任务](./user-guide/review-complete-review-tasks.md#delegate-a-review-task-to-another-reviewer)
:::

::::

<!--
<table>
<tr>
<td>

[!BADGE Feature]{type=Neutral} <br> [**Import content using Git Connector**](./user-guide/web-editor-git-connector.md)<br> Import content into Guides directly from Git repositories.

</td>
<td>

[!BADGE Feature]{type=Neutral} <br> [**New map collection**](./user-guide/generate-output-use-new-map-collection-output-generation.md)<br> Unified interface for managing maps and publishing outputs

</td>
<td>

[!BADGE Enhancement]{type=Neutral} <br> [**Delegate a review task**](./user-guide/review-complete-review-tasks.md#delegate-a-review-task-to-another-reviewer) <br> Reviewers can delegate a review task to another reviewer

</td>
</tr>
</table>
-->


## 其他资源

* [Cloud Service发行说明](./release-info/latest-release-info-cs.md)
* [On-Premise发行说明](./release-info/latest-release-info.md)
* [AEM Guides社区](https://experienceleaguecommunities.adobe.com/adobe-experience-manager-guides-11){target="_blank"}
* [GitHub存储库](https://github.com/AdobeDocs/experience-manager-guides.en){target="_blank"}
* [支持](https://experienceleague.adobe.com/support/v2/en/){target="_blank"}
* [视频教程](https://experienceleague.adobe.com/en/docs/experience-manager-guides-learn/videos/getting-started/overview){target="_blank"}
