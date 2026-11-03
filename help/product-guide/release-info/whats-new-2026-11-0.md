---
title: 发行说明 | Adobe Experience Manager Guides 2026.11.0版本中的新增功能
description: 探索Adobe Experience Manager Guides 2026.11.0版本中的新功能，包括地图级别分支和AI助手内容创建。
role: Leader
source-git-commit: ef5e433214f15b12102af7c9e38031536183ca72
workflow-type: tm+mt
source-wordcount: '1512'
ht-degree: 0%
---

# 2026.11.0版（2026年11月）的新增功能

本文介绍Adobe Experience Manager Guides as a Cloud Service 2026.11.0版本中引入的新增功能和增强功能。

有关此版本中修复的问题列表，请查看[2026.11.0版本中的已修复问题](fixed-issues-2026-11-0.md)。

了解2026.11.0版本[&#128279;](../release-info/upgrade-instructions-2026-11-0.md)的升级说明。

## 引入映射级别的分支和合并

Adobe Experience Manager Guides引入了映射级别的分支和合并功能，使创作者能够在不影响主内容的情况下并行处理多个文档版本、功能更新和关键修复。 作者可以创建DITA映射及其依赖项的独立分支，确保编辑、锁定和预览始终特定于每个分支。

此功能可帮助文档团队管理并行工作流、高效协作以及维护主文档版本的稳定性。 您可以：

- **从DITA映射的主版本创建分支**&#x200B;以单独处理功能、增强功能或关键修复。
- 在编辑器中的&#x200B;**在分支之间切换**&#x200B;以管理多个文档版本。
- **管理内容版本**&#x200B;以通过分支和合并来组织更改。
- **使用引导式比较工作流解决合并冲突**，该工作流具有三向合并功能。
- **将更改**&#x200B;合并到主版本。
- **使用标准发布直接从分支**&#x200B;发布，而不修改主版本。

了解有关[分支和合并](../user-guide/branching-overview.md)的详细信息。

![](./assets/branching.png){width="650"}


## AI支持的内容创建和在AI Assistant中导入技能

>[!NOTE]
>
>要在代理模式下使用AI助手，您的组织必须已载入Adobe CX Enterprise Coworker并具有所需的积分。

现在，您可以使用&#x200B;**AI助手**&#x200B;使用自然语言提示创建和导入DITA内容。 由&#x200B;**Adobe CX Enterprise Coworker**&#x200B;提供支持的，全新&#x200B;**创建**&#x200B;和&#x200B;**导入**&#x200B;技能可简化结构化内容的创建，并帮助作者处理DITA内容而无需广泛的DITA专业知识。

- **创建：**&#x200B;使用存储库模板从自然语言提示、参考文档或现有内容生成DITA主题和映射。 您可以在保存之前查看生成的内容，并反复优化新内容或现有内容以满足您的要求。
- **导入：**&#x200B;将现有PDF、DOCX或Markdown文件转换为结构化DITA主题和映射。 在将转换后的内容保存到存储库之前，您可以预览和查看这些内容。
- **智能标记：**&#x200B;根据您组织的分类获取内容的相关标记推荐。 增强型体验允许文件夹配置文件管理员在Workspace设置中配置分类命名空间，以确保推荐的一致性和可控性。

**AI助手**&#x200B;面板还引入了全屏模式和&#x200B;**活动对话**&#x200B;部分，以增强对话体验。

有关详细信息，请查看[在代理模式下使用AI助手](../user-guide/ai-assistant.md#agentic-mode)。

![](./assets/preview-import.png){width="650"}


## Experience Manager Guides中新的帮助助手面板

创作AI支持的&#x200B;**智能帮助**&#x200B;功能可通过专用的&#x200B;**帮助助手**&#x200B;面板使用，该面板可从“主页”、“编辑器”和“地图”控制台界面访问。 该面板提供了对话式搜索体验，允许您以自然语言提问，并快速从Experience Manager Guides文档中找到相关信息。 这有助于在不离开编辑器的情况下访问上下文指南和解决查询，从而简化您的创作工作流。

管理员可以通过Workspace设置管理帮助助手面板的可用性。 **AI帮助助手**&#x200B;部分包含为用户启用或禁用面板的切换开关。

有关详细信息，请查看[帮助助手](../user-guide/ai-based-smart-help.md)。

![](./assets/help-assistant.png){width="650"}

## 创作增强功能

### 新编辑器中的“跟踪更改”面板

现在，新编辑器中提供了&#x200B;**跟踪更改**&#x200B;面板，允许您查看主题中所有跟踪的插入和删除操作。 您可以跟踪多个用户所做的编辑，并直接从面板接受或拒绝更改。

您还可以使用&#x200B;**显示内嵌跟踪删除**&#x200B;设置控制已删除内容在编辑器中的显示方式，该设置允许您以删除线文本显示已删除的内容，或者使用链接到相应更改的铅笔图标替换已删除内容。 了解有关[跟踪更改](../user-guide/config-editor-settings.md#track-changes)的详细信息。

![编辑器设置](./assets/track-changes-all.png){width="650"}

### 在资源管理器面板中排序文件和文件夹

编辑器中的&#x200B;**资源管理器**&#x200B;面板允许您使用&#x200B;**排序**&#x200B;按钮按升序或降序对文件和文件夹进行排序。 默认情况下，根据&#x200B;**用户首选项**&#x200B;中的&#x200B;**编辑器文件显示**&#x200B;设置，项按标题或文件名升序排序。 这样可更轻松地在编辑器中导航和查找内容。

有关详细信息，请在文件和文件夹的分页加载中查看[资源管理器](../user-guide/paginated-loading-assets.md#explorer)部分。

### 从编辑器管理非DITA文件的版本和标签

Experience Manager Guides允许您直接从编辑器查看非DITA文件（如图像、多媒体、ZIP、PDF和DOCX文件）的版本历史记录和管理版本标签。 您可以预览这些文件、查看其版本历史记录、比较版本以及还原到早期版本，而无需导航到Assets UI。 您还可以为现有文件版本应用或更新版本标签，以简化版本标识和管理。

有关详细信息，请查看[使用媒体和其他非DITA文件](../user-guide/authoring-file-management.md#work-with-media-and-other-non-dita-files)。


![编辑器设置](./assets/version-management-non-dita-files.png){width="650"}


## 审核增强功能

### 通过发起者注释增强审阅协作

审阅发起者可以使用审阅UI向审阅任务中的主题添加内联注释和批注。 这使得审阅人能够提供额外的上下文，突出显示特定内容，并提请审阅人注意需要反馈的领域。

这些评论与其他审阅人的反馈一起显示在&#x200B;**评论**&#x200B;面板中，提供了审阅讨论的综合视图。 发起者添加评论时，审阅者还会收到AEM通知，这有助于简化整个审阅过程中的协作和通信。 有关详细信息，请查看[为审阅人添加注释](../user-guide/review-send-topics-for-review.md#add-comments-for-reviewers)。

## 发布增强功能

### 从映射控制台查看和管理输出历史记录

Experience Manager Guides中的地图控制台现在包括&#x200B;**输出历史记录**&#x200B;选项卡，允许您直接从编辑器查看和管理输出生成任务，而无需导航到地图仪表板。

选项卡提供了输出生成任务的统一视图，包括其状态、预设详细信息、生成日期和持续时间。 您可以搜索和筛选任务，取消正在进行的生成，访问生成的输出和日志，以及从历史记录中删除已完成的条目。 您还可以将输出历史记录导出为CSV文件，以供进一步分析。 输出生成状态使用与“地图”仪表板一致的颜色指示器。

有关详细信息，请查看[管理输出生成进程](../user-guide/generate-output-manage-process.md#view-and-manage-output-generation-tasks-from-the-editor)。

![编辑器设置](./assets/output-history-editor-view.png){width="650"}


### 增强的输出历史记录清除选项

您可以按时间&#x200B;**清除输出历史记录**（删除超过指定天数的条目）或&#x200B;**按计数**（仅保留指定数量的最近条目）。

您还可以选择只清除输出日志，同时保留历史记录条目以供审核，或者同时删除日志及其相关条目。 这些选项有助于优化存储库存储，同时更好地控制输出历史记录清除。

有关详细信息，请查看[为输出历史记录](../install-conf-guide/conf-output-generation.md#configure-auto-purging-period-for-output-history-id19aai070v8q)配置自动清除时段。

### 对Edge Delivery Services发布配置文件的GitLab支持

Edge Delivery Services发布支持与GitHub一起托管GitLab的存储库，从而提供更大的灵活性和发布DITA内容。 要发布到GitLab托管的站点，请在创建Edge Delivery Services发布配置文件时选择GitLab作为服务器类型，并在访问令牌字段中提供存储库的项目访问令牌。

发布预设还包括子文件夹的字段，因此您可以将内容发布到配置文件指定的根文件夹中的子文件夹。

有关详细信息，请查看[配置Edge Delivery Services](../knowledge-base/publishing/configure-eds.md)。

### Salesforce发布的增强功能

Experience Manager Guides通过提高安全性、性能和发布效率增强了Salesforce发布。 这些增强功能包括支持Proof Key for Code Exchange (PKCE)、刷新基于令牌的身份验证、文章级发布状态、详细发布日志、输出历史记录和优化资产发布，以减少冗余上传。

有关详细信息，请查看[使用后端处理的增强Salesforce发布](../user-guide/web-editor-article-publishing.md#enhanced-salesforce-publishing-using-backend-processing)。


### 在本机PDF中支持来自映射元数据的图像

本机PDF发布支持动态显示在DITA映射、书映射和自定义映射的元数据中定义的图像。 您可以在多个地图中使用单个PDF模板，同时在生成的输出中显示特定于地图的图像，例如产品封面图像。

通过在页面布局中添加图像占位符，您可以在发布期间自动使用映射元数据中引用的图像填充该占位符。 这消除了为不同映像维护单独模板的需要，并简化了模板管理。

有关详细信息，请查看[从地图元数据](../native-pdf/design-page-layout.md#add-an-image-from-map-metadata-add-image-map-metadata)添加图像。

### 在旧编辑器中通过内容运行状况检查验证内容质量

内容运行状况检查在旧编辑器中可用（已受新编辑器支持），这有助于在发布之前验证跨DITA映射的内容质量。 管理员可以通过组合检查断开的链接、重复的ID和架构验证来创建可重用的运行状况检查预设。

作者可以对DITA映射或旧编辑器中的选定基线运行运行状况检查，以生成跨相关主题和映射的合并问题报告。 有关详细信息，请查看[对映射](../user-guide/map-editor-other-features.md#run-health-check-on-a-map)运行运行状况检查。

## 更新插入API以进行旧版内容迁移

此API允许您通过单个API创建或更新内容及其元数据。 它支持在请求中指定主题内容、元数据和GUID。 Swagger API文档中的`/bin/guides/v1/asset/upsert/`提供了该API。