---
title: 在AEM Guides中分支 |Adobe Experience Manager Guides`
description: 了解如何在AEM Guides中创建和管理DITA映射的分支以支持并行创作、独立发布和文档更改的合并。
TQID: https://experienceleague.adobe.com/pg9zeEg8m3NeDbN-j945SqPbaMX0GgBmuquAsQcrjOM
product_v2:
  - id: fae5e35a-80c9-4b94-9352-1a060a6aab1d
    internal-label: Experience Manager Guides
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
feature_v2:
  - id: ab01a588-7dea-43f2-a699-0b3f128465d6
    internal-label: Authoring
  - id: ec4263d9-bf7c-44c7-b3f1-3e664861c8f2
    internal-label: Generative AI
subfeature_v2:
  - id: ad602516-aca3-4247-9ae8-f393d958efa9
    internal-label: Editor
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
topic_v2:
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
    internal-label: Security
  - id: f5c2a4bb-71ca-4d7e-8efd-442250e6ba48
    internal-label: Content reuse
source-git-commit: 3f0d8e31537ade58a4eab5ddf73eb6d263d3dd96
workflow-type: tm+mt
source-wordcount: '747'
ht-degree: 0%
---
# 概述

>[!NOTE]
>
> 分支和合并功能在2026.11.0版的Experience Manager Guides as a Cloud Service中引入，默认情况下处于禁用状态。 要为您的环境启用该功能，请联系您的客户成功团队。

Adobe Experience Manager Guides中的分支允许您从&#x200B;**main**&#x200B;分支创建和管理多个分支，以便DITA映射并行处理不同的文档发布。 每个分支允许作者独立管理内容更改，而不影响其他分支中的相应内容。

通过分支，多个团队可以同时处理与同一DITA map关联的不同版本、功能或修复。 您可以在更新准备就绪时将分支中的更改合并到默认分支(`main`)中。

## 分支的工作方式

您可以从&#x200B;**main**&#x200B;或DITA映射的任何现有分支创建分支。 创建分支后，您可以切换到分支并开始编辑映射及其内容。 您还可以在准备就绪时发布所选分支的内容或将更改合并到`main`中。

例如，考虑一个名为`install-the-lift.ditamap`的DITA映射，其中包含产品的安装说明。 您的文档团队可以从`main`创建此映射的两个分支：

- **版本1：**&#x200B;团队A维护现有的安装说明和地址修复。
- **版本2：**&#x200B;团队B为新功能开发安装说明。

两个团队可以在各自的地图分支上独立工作，而不会影响彼此的更改。

>[!NOTE]
>
>根据DITA映射创建分支。 您还可以添加和编辑所选分支中的映射未引用的主题。 有关详细信息，请查看[打开或编辑当前映射](./create-manage-branch.md#open-or-edit-topics-outside-the-current-map-context)之外的主题。

创建DITA映射的分支时，Experience Manager Guides不会自动将映射的引用主题复制到新分支中。 从源分支或默认分支（主分支）中读取未更改的主题。 仅当编辑主题并将其保存到新分支中时，才会将主题复制到该分支中。

例如，DITA映射引用了100个主题，而存储库包含50个未被映射引用的其他主题。 创建新分支（版本1.0）时，所有100个引用的主题都会自动成为版本1.0的一部分，即使不编辑任何主题也是如此。 50个未引用的主题不会自动成为新分支的一部分。 如果编辑其中10个，则只有这10个会成为1.0版的一部分。 其余40个未更改的主题将继续从默认分支（主分支）使用。

>[!NOTE]
>
> 主题版本控制将继续与分支一起使用。 您可以在DITA映射的选定分支中创建和管理主题版本。 每个分支都维护其自己的版本历史记录，独立于其他分支。

## 主要优势

使用Experience Manager Guides中的分支具有以下优势：

- **隔离编辑：**&#x200B;在选定的映射分支中进行更改，而不影响其他分支中的相应内容。
- **并行创作：**&#x200B;使多个团队能够同时处理各自映射分支中的不同版本、功能或修复。
- **独立发布：**&#x200B;从各个映射分支发布文档，无需等待其他分支中的更改完成。
- **受控合并：**&#x200B;将映射分支中的更改合并到默认分支(`main`)，并可以查看和解决冲突。

## 分支与基线

>[!NOTE]
>
> 基线和分支是互斥的特征。 启用分支后，基线功能将不可用。 但是，现有基线将保持不变，并且不会被删除。 如果以后禁用分支，则现有基线将再次可用。

**基线**&#x200B;标识DITA映射的主题版本的特定组合，允许您使用这些选定的版本生成输出。

**分支**&#x200B;为DITA映射及其内容提供了单独的编辑环境，允许作者进行更改而不影响同一映射的其他分支。

| 基线 | 分支 |
|---|---|
| 在DITA映射中选择特定版本的主题。 | 创建DITA映射的单独分支以独立管理更改。 |
| 用于发布主题版本的特定组合。 | 用于并行开发和发布不同的版本。 |
| 不提供单独的编辑上下文。 | 支持独立的编辑和合并。 |

## 即将推出的功能

以下功能当前仅受默认分支(`main`)支持，并计划在将来版本的Experience Manager Guides中受DITA映射的其他分支支持：

- 搜索
- 查找并替换
- 审核工作流

