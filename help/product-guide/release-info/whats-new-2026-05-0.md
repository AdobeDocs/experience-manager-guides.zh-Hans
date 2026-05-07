---
title: 发行说明 | Adobe Experience Manager Guides 2026.05.0版本中的新增功能
description: 了解Adobe Experience Manager Guides 2026.05.0版本中的新增功能和增强功能
role: Leader
source-git-commit: 2c9e91a85bb9cfbfec05dbe5c2e9eae9e240d571
workflow-type: tm+mt
source-wordcount: '1031'
ht-degree: 0%

---

# 2026.05.0版（2026年5月）的新增功能

本文介绍Adobe Experience Manager Guides as a Cloud Service 2026.05.0版本中引入的新增功能和增强功能。

有关此版本中修复的问题列表，请查看[2026.05.0版本中的已修复问题](fixed-issues-2026-05-0.md)。

了解2026.05.0版本[&#128279;](../release-info/upgrade-instructions-2026-05-0.md)的升级说明。

## Editor 2.0简介

Editor 2.0（又称“新编辑器”）提供了简化的创作过程，使您能够更直观地跨标记模式和非标记模式更高效地创建内容。 此版本提高了性能，页面加载速度更快，编辑更顺畅，即使对于大型复杂主题也是如此。 它还通过解决关键的创作差距（尤其是围绕导航和光标行为的差距）提供了增强的稳定性。 此外，现代化界面提供了更新后且用户友好的UI，实现了功能与易用性的平衡。 有关详细信息，请查看[编辑器简介](../user-guide/web-editor.md)。

以下是一段概述视频，重点介绍Editor 2.0的功能。

>[!VIDEO](https://video.tv.adobe.com/v/3484007)


>[!NOTE]
>
> 联系AEM Guides客户成功团队以在您的环境中启用编辑器2.0。

以下是使创作更容易、更高效的增强功能。

### 重新设计用户界面和体验

刷新的界面提高了整体可用性，使导航和内容创作更加直观和一致。

- **创作和预览模式下元素的CSS更丰富**：元素的默认CSS增强后，在创作和预览模式下样式更佳，视觉一致性更好。

  ![](assets/rich-css.png){width="650"}

- **深色主题支持**：支持内容编辑区域中的深色主题，可为喜欢使用深色界面的用户增强创作体验。

  ![](assets/dark-theme.png){width="650"}

- **统一的用户级编辑器设置**：新的集中式设置面板，它使作者更好地控制编辑器行为，允许用户从单个位置更轻松地管理首选项。 配置选项包括启用/禁用功能：

   - 创作模式中的不间断空格
   - 具有属性或不具有属性的标记可见性设置
   - 创作模式中的XML注释
   - 在编辑器中插入元素的快速插入菜单

  ![](assets/editor-settings-dialog.png){width="350"}


  有关如何配置编辑器设置的详细信息，请查看[编辑器设置](../user-guide/config-editor-settings.md)。

- **在创作模式下更好地表示条件内容**：在创作模式下可更清楚地显示条件内容，从而帮助作者更有效地识别和管理变体。 有关详细信息，请在编辑器的左侧面板中查看[条件](../user-guide/web-editor-left-panel.md#conditions)。

  ![](assets/multiple-conditions-applied_cs-editor-2-0.png){width="650"}

### 增强的创作功能

提供了改进的工具和灵活性，以简化内容创建和编辑工作流。

- **在标记模式下查看属性以及元素**：作者现在可以使用标记模式查看元素属性，从而更好地查看和控制结构化内容。 要配置此功能，请查看[编辑器设置](../user-guide/config-editor-settings.md)。

  ![](assets/config-tags-attributes.png){width="650"}

- **快速插入菜单**：在创作模式下编辑光标位置时可直接添加元素，而无需导航到工具栏。 也可以通过“编辑器”设置在“收藏夹”部分中配置常用元素，以便更快地进行访问。 有关详细信息，请查看[编辑主题](../user-guide/web-editor-edit-topics.md)。

  ![](assets/quick-insert-menu.png){width="650"}

- **在创作模式下查看、编辑和插入XML注释的功能**：使作者能够在创作模式下直接查看、编辑和插入XML注释，以便在内容中提高可见性。 要配置此功能，请查看[编辑器设置](../user-guide/config-editor-settings.md)。

  ![](assets/config-xml-comments.png){width="650"}

- **并排模式**：允许同时查看“创作”模式和“Source”模式，两个视图保持完全同步，以便更轻松地比较、编辑和验证内容更改。 有关详细信息，请查看[编辑器视图](../user-guide/web-editor-views.md)。

  ![](assets/side-by-side-editor-2-0.png){width="650"}

- **改进了表创作**：通过更直观、更高效的交互来创建和管理表，增强了整个表创作体验。

   - 流畅而直观的交互：可轻松插入行和列，并且支持拖放以重新排列行和列。
   - 上下文工具栏：直接在表中访问特定于表的操作，例如格式设置、对齐、合并和其他附加操作。
   - 配置表：在单个操作中添加多个行或列，从而减少重复步骤并提高效率。

  ![](assets/config-table.png){width="650"}

  有关详细信息，请查看[使用表](../user-guide/web-editor-other-features.md#work-with-tables-in-the-new-editor)。

### 改进了大型主题的性能

新编辑器通过提供更快的内容渲染、更可靠的撤消和重做功能以及脏标记来明确指示未保存的更改，增强了处理大型复杂主题的体验。

## 从内容属性面板访问文件中引用的路径和UUID

现在，您可以使用&#x200B;**Link path**&#x200B;查看所选引用的相对路径，使用&#x200B;**Link UUID**&#x200B;从“内容属性”面板查看其唯一标识符。 您还可以使用链接路径和链接UUID旁边的图标直接从界面复制完整的绝对路径和关联的UUID，从而更易于跟踪和重用链接资源。

有关详细信息，请查看[内容属性](../user-guide/web-editor-right-panel.md#content-properties)。

## 审核增强功能

此版本中包含以下审核增强功能：

- 您现在可以启用&#x200B;**自动提醒**，以便在审核任务的到期日之前和到期之后，为审核者安排AEM通知和电子邮件提醒。 您可以为每个案例配置多个提醒，根据配置的提醒计划，按定义的顺序发送预过期提醒，并在任务标记为过期后触发过期提醒。 有关详细信息，请查看[发送审阅主题](../user-guide/review-send-topics-for-review.md)。

- 查看者现在可以访问所查看主题的版本历史记录，从而允许他们在以前的查看任务中查看和比较同一主题的先前已查看版本和更新版本。 这有助于审阅人通过审阅当前审阅上下文中的注释、标签和其他相关详细信息，来验证自早期审阅周期以来所做的更改并保持连续性。 有关详细信息，请查看审阅者[&#128279;](../user-guide/review-topics.md#version-history-for-the-reviewer)的版本历史记录。

## Experience Manager Guides中引入的新基线体验

>[!NOTE]
>
> 联系AEM Guides客户成功团队以在您的环境中启用新基线。

借助基于重新设计的基线体系结构构建的&#x200B;**新基线体验**，管理大型复杂基线现在更快、更稳定且更易于扩展。 此更新解决了长期存在的性能和可靠性难题，同时保留了现有的工作流。

此更新作为测试版增强功能提供，通过增强对自动化和大规模基线操作的支持，可提供更快、更稳定和可预测的基线体验，从而为解决常见的棘手问题（如加载缓慢、基线状态不一致和可管理性受限）提供了解决方案。 主要改进包括：

- 改进的性能和可扩展性
- 更强的UI和后端一致性
- 扩展的筛选、导航和依赖项可见性

有关详细信息，请在Experience Manager Guides[&#128279;](../user-guide/web-editor-baseline-v2.md)中查看新的基线体验(Beta)。






