---
title: 发行说明 | Adobe Experience Manager Guides 2026.09.0版本中的新增功能
description: 了解Adobe Experience Manager Guides 2026.09.0版本中的新增功能和增强功能
role: Leader
source-git-commit: 5d42c75d75b85b97fc3795c87004510eb43acd29
workflow-type: tm+mt
source-wordcount: '1077'
ht-degree: 0%
---
# 2026.09.0版（2026年9月）的新增功能

本文介绍Adobe Experience Manager Guides as a Cloud Service 2026.09.0版本中引入的新增功能和增强功能。

有关此版本中修复的问题列表，请查看[2026.09.0版本中的已修复问题](fixed-issues-2026-09-0.md)。

了解2026.09.0版本](../release-info/upgrade-instructions-2026-09-0.md)的[升级说明。

## 在AI Assistant中引入AI支持的智能标记

现在，您可以使用AI Assistant向内容建议标记和添加标记。 借助新的智能标记功能，作者可以要求AI助手为一个或多个主题建议标记，该功能由Adobe CX Enterprise Coworker提供的智能标记技能提供支持。 该技能将审核内容，生成标记推荐，并将它们呈现在您的审核中。 确认后，建议的标记将应用于映射中的相关主题。

有关详细信息，请查看[在代理模式下使用AI助手](../user-guide/ai-assistant-agentic.md)。

![](./assets/guides-ai-tags-review.png)

当前，在&#x200B;**代理**&#x200B;模式下配置AI助手时，智能标记功能可用。 管理员可以选择从实例的&#x200B;**Workspace设置**&#x200B;中启用&#x200B;**代理**&#x200B;或&#x200B;**标准**&#x200B;模式。

- **代理模式**&#x200B;为作者提供了用于标记推荐和应用程序的智能标记界面。
- **标准模式**&#x200B;通过AI助手面板中的&#x200B;**帮助**&#x200B;和&#x200B;**创作**&#x200B;选项卡提供现有的AI助手体验。

## 编辑器增强功能

### 在并发编辑期间防止内容被覆盖

当两个作者同时处理同一主题时，一个作者可能打开了主题，而另一个作者锁定主题，进行更改并保存较新版本。 然后，已打开的主题可能包含过时的内容，编辑此版本可能会覆盖最新更改。

为防止此类冲突，现在，当您锁定主题时，最新保存的版本会自动加载到编辑器中。 这样可以确保您使用最新的内容，并防止覆盖其他作者所做的更改。

当启用&#x200B;**禁用编辑而不锁定文件**&#x200B;设置时适用。

有关更多详细信息，请查看[在并发编辑期间阻止内容覆盖](../user-guide/web-editor-edit-topics.md#prevent-content-overwrite-during-concurrent-editing)。

### 预览选定静态基线的映射内容

当映射具有一个或多个静态基线时，您现在可以在编辑器中基于所选基线而不是当前工作副本预览映射。

与所选基线关联的主题、资产、图像和引用的所有版本都将显示在“预览”中，以便在创建基线时提供地图内容的准确视图。 有关更多详细信息，请查看主题](../user-guide/web-editor-views.md#preview-content-using-baseline)的[编辑器视图。

## 审核增强功能

### 在审阅任务中将单个主题标记为完成

Experience Manager Guides为审阅人引入了主题级进度跟踪，使具有多个主题任务的审阅进度更加可见。 作为审阅者，您现在可以将单个主题标记为已完成，并区分您已完成的主题和仍需要关注的主题。

![](./assets/mark-topics-done-review-ui.png)

为了支持此功能，审阅UI的文档视图中的主题被组织为折叠面板，其中具有&#x200B;**将主题标记为完成**&#x200B;复选框。 使用复选框标记为已审阅的主题显示在&#x200B;**主题**&#x200B;面板中，而顶部的&#x200B;**已审阅主题**&#x200B;计数器显示分配给您的主题的进度。 这些功能可让您清楚地了解您所覆盖的内容以及剩余内容，即使在休息后返回较长的审阅任务时也是如此。

有关更多详细信息，请查看[查看主题](../user-guide/review-topics.md#mark-individual-topics-as-done-in-a-review-task)。


### 在评论中标记时识别具有角色的用户

在评论或回复中标记某人时，审阅人和作者现在可以查看用户的角色（例如，审阅人、作者或所有者）及其用户名和电子邮件地址（如果可用）。 这使得快速识别要标记的正确用户变得更容易，尤其是在具有大量参与者的项目中。

了解有关[在评论中标记用户](../user-guide/review-topics.md#tag-task-users-in-a-comment)的详细信息。

### 选择要查看的主题时查看映射层次结构

当选择审核内容时，作为审核任务的作者或发起者，您现在可以在&#x200B;**内容**&#x200B;页面上查看其现有层次结构中的映射、子映射和主题，而不是以平面列表查看所有主题。 利用分层视图，可以更轻松地了解内容的结构，并选择单个主题或整个子映射以供审阅。

有关更多详细信息，在选择审核主题时查看[查看映射层次结构](../user-guide/review-send-topics-for-review.md#view-the-map-hierarchy-while-selecting-topics-for-review)。

![](assets/review-map-hierarchy.png)

## 发布增强功能

### 使用地图的语言发布本机PDF输出

本机PDF输出预设页面现在包含一个新的&#x200B;**使用映射语言**&#x200B;选项。 选中后，输出模板变量将从根映射的`xml:lang`属性中解析其语言，而不是从预设中显式选择的语言。 这意味着，在发布已翻译地图时，您不再需要为每种语言维护单独的输出预设。 如果映射未定义`xml:lang`，则输出默认为英语(en_US)。

有关更多详细信息，请查看[本机PDF预设配置](../web-editor/native-pdf-web-editor.md)和[在输出模板中使用语言变量](../native-pdf/native-pdf-language-variables.md#use-language-variables-in-the-output-templates)。

## 学习内容增强功能

### 在学习课程中启用H5P内容的全屏视图

现在，作者可以为学习课程中使用的每个H5P元素启用或禁用全屏显示。 使用&#x200B;**内容属性**&#x200B;面板中的&#x200B;**启用全屏**&#x200B;切换可控制此设置。 启用后，学习者可以将H5P内容展开到全屏。 禁用后，内容将内联保留在标准视图中。 此设置始终适用于预览模式和已发布的输出。

在产品培训和学习内容的“插入”菜单](../learning-content/lc-other-insert-options.md)中了解有关[其他选项的更多信息。

![](./assets/h5p-fullscreen.png)

## 性能提升

### 通过分页加载文件和文件夹提高了性能

Experience Manager Guides现在支持对文件和文件夹进行分页加载，以增强浏览体验，尤其是对于具有大量资源的文件夹。 文件夹不是一次加载所有内容，而是以50个资源的批量逐步加载，并在滚动或选择&#x200B;**加载更多**&#x200B;时检索其他资源，具体取决于面板或对话框。

排序是在服务器端执行的，因此应用排序顺序会获取最新排序的结果，而不是对浏览器中已加载的数据重新排序。 重命名、删除、添加和移动等常见操作不再重新加载整个文件夹。 相反，他们仅更新受影响的项目或刷新结果的第一页。

“主页存储库”表、“收藏集”、“资源管理器”、“搜索”和“模板”面板以及“选择路径”对话框中均提供分页加载。

有关详细信息，请查看[文件和文件夹的分页加载](../user-guide/paginated-loading-assets.md)。

文件夹导航面板的![页](../user-guide/images/home-tree-pagination.png){width="650"}









