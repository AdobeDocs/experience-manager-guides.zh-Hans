---
title: 创建和管理DITA映射的分支 |Experience Manager Guides
description: 了解如何在Experience Manager Guides中创建、切换、存档和重新激活DITA映射的分支。
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
source-wordcount: '1167'
ht-degree: 0%
---

# 创建和管理DITA映射的分支

在Experience Manager Guides中，您可以创建DITA映射的多个分支来管理不同版本、功能或修复的文档。 您可以在分支之间切换以处理关联的内容，存档不再需要的分支，并在需要时恢复它们。

您也可以从同一DITA映射的任何现有分支创建分支。

## 创建分支

您可以创建DITA映射的分支以处理文档更改，而不影响其他分支中的相应内容。

执行以下步骤可创建分支：

1. 打开要为其创建分支的DITA映射。

   >[!NOTE]
   >
   > 如果已在编辑器中打开另一个映射，则会显示确认对话框。 选择&#x200B;**打开**&#x200B;以打开当前分支中的选定映射。 有关详细信息，请查看[打开当前映射上下文之外的内容](#open-content-outside-the-current-map-context)。

1. 选择&#x200B;**main**&#x200B;分支下拉列表，并验证是否已选择所需的DITA映射。

   ![](./images/map-context-change.png)

1. 选择&#x200B;**新建分支**&#x200B;以创建选定映射的分支。

1. 在&#x200B;**新建分支**&#x200B;对话框中，输入新分支的名称，然后选择要从中创建分支的父分支。

   ![](./images/new-branch-creation.png)

1. 选择&#x200B;**创建**。

将为所选DITA映射创建新分支。 您现在可以切换到新分支并开始处理其关联内容。

## 在分支之间切换

执行以下步骤以切换分支：

1. 选择编辑器顶部的&#x200B;**分支下拉列表**（默认显示`main`）。 此时将显示选定DITA映射的可用分支列表。
1. 选择要使用的分支。

   ![](./images/switch-branches.png)

   选定分支随即打开，其名称将显示在编辑器顶部的分支下拉列表中，取代&#x200B;**main**。

   ![](./images/branch-switched.png)

您现在可以在选定分支内处理映射及其关联内容。

![](./images/branch-switched.png)

>[!NOTE]
>
>如果切换分支时某个主题具有未保存的更改，则会出现一个对话框，提示您先保存更改，然后再切换到所选分支。

您现在可以在选定分支内处理映射及其关联内容。

## 分支中的独立编辑

当您在DITA映射的分支中工作时，对其内容所做的更改将保留在选定分支中，并且不会影响其他分支中的相应内容。 这允许多位作者跨地图的不同分支独立处理相同的主题。

默认情况下，未更改的主题从源分支或`main`中读取。 在选定分支中编辑主题时，该主题将变成该分支的一部分。 随后对该主题所做的任何更改都会保留在所选分支中。

可以在同一DITA映射的分支之间切换以查看和编辑其各自的内容。

### 编辑分支中的主题

您可以编辑所选分支中与DITA映射关联的主题，而不会影响它们在其他分支中的内容。

执行以下步骤来编辑主题：

1. 在编辑器中打开DITA映射。
2. 从分支下拉列表中，选择要编辑主题的分支。
3. 从映射中打开要修改的主题。
4. 对主题进行所需的更改。
5. 保存更改。

   已修改主题的副本将保存在所选分支中。 其他分支中的相应主题保持不变。

您可以继续编辑所选分支中的主题，或切换到另一个分支以处理其内容。

### 在当前映射上下文之外打开映射

在Experience Manager Guides中，**映射上下文**&#x200B;引用编辑器中当前打开的DITA映射。

如果尝试打开不属于当前映射上下文的映射、主题或资源，将出现一个包含以下选项的确认对话框：

- **打开：**&#x200B;将当前映射上下文替换为选定内容。
- **在编辑器中打开：**&#x200B;在不更改当前映射上下文的情况下在新选项卡中打开内容。
- **取消：**&#x200B;取消操作并保留当前映射上下文。

例如，假定当前在&#x200B;**主**&#x200B;分支中选择了`master_map.ditamap`。

![](./images/map-context-selection.png)

如果尝试打开另一个DITA映射，将出现以下确认对话框：

![](./images/open-map-context-dialog.png)

选择&#x200B;**打开**&#x200B;以切换到所选映射。

`main`分支的映射上下文已更新为新选择的映射，允许您使用其关联内容。

![](./images/map-context-change.png)

### 打开或编辑当前映射上下文以外的主题

映射未引用的主题不会在分支中自动可用。

![](./images/edit-topic-current-branch.png)

选择&#x200B;**在当前分支**&#x200B;中编辑，使此类主题可在所选分支中编辑。

您现在可以编辑主题，而不影响其在`main`中的内容。 但是，该主题不会自动添加到关联的DITA映射中，并且不会包含在已发布的输出中。 要在输出中包括主题，请将其添加到DITA映射。

## 管理分支

您可以从“映射”控制台的&#x200B;**分支**&#x200B;面板中管理DITA映射的分支。 您可以查看可用的分支、创建新分支、合并或重命名现有分支以及存档不再主动使用的分支。

**分支**&#x200B;面板列出了选定DITA映射的所有可用分支。

![](./images/branches-panel.png)

要管理分支，请将鼠标悬停在所需分支上，然后选择&#x200B;**选项**&#x200B;菜单。 以下操作可用：

![](./images/options-menu-branch.png)

- **新分支：**&#x200B;从所选分支创建新分支。
- **合并到主分支：** [将选定分支中的更改](./merge-branches.md)合并到`main`分支中。
- **重命名分支：**&#x200B;更改所选分支的名称。
- **合并历史记录：**&#x200B;显示合并活动的历史记录。 此选项仅在创建合并请求后可用。
- **存档分支：**&#x200B;存档不再使用的分支。

  >[!NOTE]
  >
  > Experience Manager Guides不支持删除分支。 您可以存档不再主动使用的分支。

您还可以使用&#x200B;**分支**&#x200B;面板顶部的选项来搜索分支、刷新分支列表或创建新分支。

### 存档分支

您可以存档不再主动使用的DITA映射的分支，并在需要时恢复它们。

>[!NOTE]
>
> 无法存档默认分支(`main`)。

要存档分支，请执行以下步骤：

1. 在&#x200B;**分支**&#x200B;面板中，选择&#x200B;**管理**&#x200B;图标。

   ![](./images/manage-branches-icon.png)

   显示&#x200B;**管理分支**&#x200B;对话框。

   ![](./images/manage-branches-dialog.png)

   该对话框包含以下选项卡：

   - **活动：**&#x200B;列出选定DITA映射的所有活动分支。
   - **已存档：**&#x200B;列出选定DITA映射的所有已存档分支。

2. 在&#x200B;**活动**&#x200B;选项卡中，将鼠标悬停在要存档的分支上，然后选择&#x200B;**存档**。

   ![](./images/archive-branch.png)

   所选分支已存档并移至&#x200B;**已存档**&#x200B;选项卡。

### 恢复已存档的分支

当您需要继续处理DITA映射的内容时，可以恢复其存档的分支。

要恢复已存档的分支，请执行以下步骤：

1. 在&#x200B;**分支**&#x200B;面板中，选择&#x200B;**管理**&#x200B;图标。
2. 在&#x200B;**管理分支**&#x200B;对话框中，选择&#x200B;**已存档**&#x200B;选项卡。
3. 找到要还原的分支，然后选择&#x200B;**还原**。

   分支已恢复并出现在&#x200B;**活动**&#x200B;选项卡中。


