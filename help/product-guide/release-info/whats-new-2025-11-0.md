---
title: 发行说明 | Adobe Experience Manager Guides 2025.11.0版本中的新增功能
description: 了解Adobe Experience Manager Guides 2025.11.0版本中的新增功能和增强功能
role: Leader
source-git-commit: a13fdb36efb5cfb548f8e128977469763836537a
workflow-type: tm+mt
source-wordcount: '510'
ht-degree: 3%

---

# 2025.11.0版（2025年11月）的新增功能

本文介绍Adobe Experience Manager Guides as a Cloud Service 2025.11.0版本中引入的新增功能和增强功能。

有关此版本中修复的问题列表，请查看 [2025.11.0 版本中已修复的问题](fixed-issues-2025-11-0.md)。

了解2025.11.0版本[的](../release-info/upgrade-instructions-2025-11-0.md)升级说明。


## 在主页中引入新存储库并增强搜索体验

存储库现在可直接从主页访问，它用作集中空间，以改善文件夹和文件的可发现性。 它具有专用的&#x200B;**文件夹导航面板**&#x200B;以及可自定义的存储库&#x200B;**的**&#x200B;表格视图。 改版后的搜索和筛选体验使查找和查找文件变得非常容易。 有关详细信息，请查看[了解存储库界面](../user-guide/home-page-repository-view.md)。

![](assets/repository-view-home.png){align="left"}

在编辑器中，文件的搜索和筛选体验现在与主页一致。 在编辑器界面底部引入了新的[搜索面板](../user-guide/search-panel-explorer.md)以显示搜索结果。 此外，存储库现在在编辑器中重命名为&#x200B;**资源管理器**，允许您像以前一样浏览文件夹和文件。

![](assets/search-panel-explorer.png){align="left"}


## AI助手中智能建议的增强索引

现在，您可以使用新的状态指示器在AI Assistant中轻松跟踪智能建议的每次索引尝试的状态：索引已完成、不同步、正在进行中，以及索引失败。 现在，在文件夹配置文件级别记录上次索引时间戳，以便更好地进行跟踪。 此外，在为索引指定文件夹或文件路径时，会强制实施父子文件夹限制。

有关更多详细信息，请查看[为智能帮助和创作配置AI助手](../cs-install-guide/conf-folder-level.md#configure-ai-assistant-for-smart-help-and-authoring)。

## 性能改进

### 自动B树清理以获得最佳性能

为了保持系统效率并防止资源拥塞，一个新的后台进程定期清理系统级别的B树。 这可确保不再存在或临时添加的资产不会占用不必要的空间。

系统智能地识别要清理的候选者，并执行自动删除。 此外，此功能是可配置的，可让管理员根据操作需求控制其行为。

有关详细信息，请查看[配置B树清理](../cs-install-guide/configure-btree-cleanup-cs.md)。

### 改进了对具有大量键的DITA映射的处理

现在，您可以无缝地处理包含大量密钥的DITA映射。 此增强功能可确保更快的加载和改进的性能，从而更轻松地管理复杂的地图而不会出现中断。

在版本升级后，系统可能会遇到负载临时增加的情况，从而导致新上传数据的后处理出现延迟。 这是由于后台运行的一次性自动脚本(OTS)造成的。 脚本完成后，系统性能将恢复正常。

### 改进了资产处理

引入了自动流程以使`/content/dam`中的资产保持最新。 系统每15分钟触发一次资产重新处理。 在每个周期中，都会提取并重新处理最近的15分钟间隔内新添加或未处理的资产，从而提高内容存储库的效率和一致性。

有关更多详细信息，请查看[处理资源](../user-guide/asset-processor.md)。




