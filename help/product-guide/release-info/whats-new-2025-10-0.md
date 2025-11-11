---
title: 发行说明 | Adobe Experience Manager Guides 2025.10.0版本中的新增功能
description: 了解Adobe Experience Manager Guides 2025.10.0版本中的新增功能和增强功能
role: Leader
source-git-commit: bf08a48cd00170bdbe8cde312aac9776f871dbf9
workflow-type: tm+mt
source-wordcount: '521'
ht-degree: 3%

---

# 2025.10.0版（2025年10月）的新增功能

本文介绍Adobe Experience Manager Guides as a Cloud Service 2025.10.0版本中引入的新增功能和增强功能。

有关此版本中修复的问题列表，请查看 [2025.10.0 版本中已修复的问题](fixed-issues-2025-10-0.md)。

了解2025.10.0版[的](../release-info/upgrade-instructions-2025-10-0.md)升级说明。


## 编辑器设置现已重命名为Workspace设置，可从主页访问

为了提高导航和可用性，已引入以下增强功能：

- Experience Manager Guides中的&#x200B;**编辑器设置**&#x200B;已重命名为&#x200B;**Workspace设置**。
- 现在，可以从&#x200B;**主页**&#x200B;访问[更多操作](../user-guide/intro-home-page.md)菜单（三点菜单），该菜单以前只能在“编辑器”和“映射”控制台界面中使用。

  ![](assets/workspace-settings.png)

## 在创作视图的主题和映射中轻松识别和修复重复ID

Experience Manager Guides现在在编辑器中包含&#x200B;**重复ID**&#x200B;按钮，以帮助您快速识别和修复单个主题或映射中存在的重复ID。 检测到重复的ID时，此按钮将出现在&#x200B;**创作**&#x200B;视图的编辑器界面的左下角。 选择按钮后，弹出框中会显示具有重复ID的所有实例的列表。 选择实例会突出显示主题或地图中的相应内容，使您能够从右侧面板中查找和修复重复的ID。

有关更多详细信息，请在编辑器中查看[其他功能](../user-guide/web-editor-other-features.md)。

![](assets/duplicate-element-IDs.png){width="350" align="left"}

## 增强存储库和报告过滤器

存储库高级筛选器下的&#x200B;**锁定者**&#x200B;筛选器和DITA map报表中的&#x200B;**作者**&#x200B;筛选器现在会在您滚动时逐渐加载用户列表，而不是一次加载所有列表。 这种分页加载提高了速度，并使处理大型用户数据集更加高效和无缝。

## 直接从审阅面板访问审阅任务的状态

作为审阅任务的发起者，您现在可以直接从“审阅”面板检查审阅任务的状态。 通过最新的增强功能，“审阅”面板中的&#x200B;**更新任务**&#x200B;对话框包含一个新的&#x200B;**检查审阅状态**&#x200B;选项。 选择此选项将直接转到审阅仪表板，可在其中查看每个审阅者的任务状态，从而无需切换上下文即可更快地访问任务进度。

有关更多详细信息，请查看[请求重新审阅或关闭审阅任务作为作者](../user-guide/review-close-review-task.md)。

![](assets/check-review-status-icon.png){width="350" align="left"}



## 用于跟踪文件夹或资产的后处理状态的API

新API现在可用于跟踪单个资源和文件夹的后处理状态。 这对于使用自动化工作流的团队特别有用，因为在这些团队中，发布需要仅在内容经过完全处理之后进行。 API提供了一种确认就绪性的可靠方式，从而降低了因处理不完整而导致发布失败的风险。

此外，通过引入此API，资产后处理事件将不会自动触发。 管理员现在可以通过`fmdita config manager`中的设置启用此事件。

有关详细信息，请查看：

- [用于跟踪单个资源和文件夹后处理状态的API](../api-reference/track-post-processing-status.md)
- [fmdita配置管理器中的后处理事件处理程序设置](../api-reference/post-process-event.md)

