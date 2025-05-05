---
title: 发行说明 | Adobe Experience Manager Guides 2025.04.0版本中的新增功能
description: 了解Adobe Experience Manager Guides 2025.04.0版本中的新增功能和增强功能
role: Leader
source-git-commit: 2d0be1a3b3d4b625333e5b8c93e6b01f38e00b39
workflow-type: tm+mt
source-wordcount: '570'
ht-degree: 2%

---

# 2025.04.0版（2025年4月）的新增功能

本文介绍Adobe Experience Manager Guides as a Cloud Service 2025.04.0版本中引入的新增功能和增强功能。

有关此版本中修复的问题列表，请查看 [2025.04.0 版本中已修复的问题](fixed-issues-2025-04-0.md)。

了解2025.04.0版本[&#128279;](../release-info/upgrade-instructions-2025-04-0.md)的升级说明。

## 为引用链接添加了“格式”属性

Adobe Experience Manager Guides现在为编辑器中的引用链接添加&#x200B;**format**&#x200B;属性。 此属性显示在&#x200B;**Source视图**&#x200B;中，并清楚地指示文件类型，例如：

- 对于扩展名为&#x200B;**.pdf**&#x200B;的文件，格式将设置为&#x200B;**pdf**
- 对于扩展名为&#x200B;**.html**&#x200B;的文件，格式将设置为&#x200B;**html**
- 对于具有&#x200B;**.dita**&#x200B;或&#x200B;**.ditamap**&#x200B;文件的文件，格式将设置为&#x200B;**dita**

此外，扩展名为&#x200B;**.xml**&#x200B;的文件还将格式设置为&#x200B;**dita**。 对于没有任何扩展名的文件，格式将保留为空。 此外，对于范围设置为&#x200B;**external**&#x200B;的任何引用链接，格式将设置为&#x200B;**html**，而不管引用链接中的文件扩展名如何。


## 在编辑器中准确传输大文件

Experience Manager Guides现在会通知您某个文件被分类为大文件，并且某些功能（例如撤消、重做、大纲面板和脏标记）可能无法按预期工作。 如下面的代码片段所示，大型文件的界面顶部会显示一条警报消息，用于指示基于&#x200B;**uiconfig.json**&#x200B;文件中&#x200B;**largeFileTagCount**&#x200B;参数的元素数量。

此外，标记计数显示在底部栏中，当您将鼠标悬停在该栏上时，将会显示工具提示。 选择&#x200B;**了解详情**&#x200B;选项卡提供了有关处理大型文件的详细信息。 此警报仅适用于DITA文件，并且在所有视图(创作、Source和布局)中都可见。

有关更多详细信息，请查看[在编辑器中处理大文件](../user-guide/web-editor-other-features.md#handling-large-files-in-the-editor)。

![](assets/add-toast-tag-count.png){width="800" align="left"}

## 导出的基线现在包括文档状态

导出基线功能现在包括&#x200B;**文档状态**&#x200B;以及基线快照中的标题、文件名、文件类型和版本号等键详细信息。 此增强功能通过提供对基线的更全面概述来改进基线管理。

有关详细信息，请查看[从映射控制台创建和管理基线](../user-guide/web-editor-baseline.md#manage-baselines)。

## 可重用内容面板的增强搜索体验

Experience Manager Guides在可重用内容面板中引入了增强的搜索体验。 通过此更新，搜索任何关键字现在会扫描作为可重用内容添加的所有文件，而不只是打开的文件，从而确保您在所有匹配项（无论容器是打开还是折叠）中都能找到关键字的精确位置。 此外，当您清除搜索栏时，所有容器的原始状态都会保留，从而提供更加高效和用户友好的搜索功能。

有关更多详细信息，请查看[可重复使用的内容](../user-guide/web-editor-features.md#reusable-content)。


## 微服务容器的DITA OT版本更新

对于启用了微服务的云环境，我们将过渡到使用Java 21，确保现有DITA-OT和本机PDF生成流程不受影响。 现有的DITA-OT 3工作流将继续与Java 21无缝配合使用。  此外，DITA-OT 4将完全可操作，允许用户使用DITA-OT和本机PDF生成PDF，以及生成本机AEM站点和其他格式的输出。