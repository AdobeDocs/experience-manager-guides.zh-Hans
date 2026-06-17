---
title: 发行说明 | Adobe Experience Manager Guides 2026.06.0版本中的新增功能
description: 了解Adobe Experience Manager Guides 2026.06.0版本中的新增功能和增强功能
role: Leader
source-git-commit: f3f30400f776f746427e257e2c937ff3413aa9ac
workflow-type: tm+mt
source-wordcount: '943'
ht-degree: 0%

---

# 2026.06.0版本（2026年6月）的新增功能

本文介绍Adobe Experience Manager Guides as a Cloud Service 2026.06.0版本中引入的新增功能和增强功能。

有关此版本中修复的问题列表，请查看[2026.06.0版本中的已修复问题](fixed-issues-2026-06-0.md)。

了解2026.06.0版本](../release-info/upgrade-instructions-2026-06-0.md)的[升级说明。


## 新的地图收集(Beta)用于管理地图和发布输出

>[!NOTE]
>
> 此功能当前作为Beta功能提供，默认情况下处于禁用状态。 要在您的环境中启用该功能，请联系客户成功团队。

新的地图收集(Beta)将地图收集管理和输出生成活动整合到一个界面中。 您可以从一个位置管理映射和预设、生成和发布输出、视图生成和发布历史记录等。 通过将相关发布任务整合在一起，可以更轻松地处理地图收藏集并跟踪多个地图及其相关语言的输出活动。

![](assets/new-maps-collection.png)

有关更多详细信息，请查看[使用新的映射集合生成输出(Beta)](../user-guide/generate-output-use-new-map-collection-output-generation.md)。

## 为本机PDF引入新的发布引擎

新的发布引擎&#x200B;*原生PDF引擎v2*&#x200B;现在可用于Experience Manager Guides中的原生PDF。 其中包括渲染增强功能和原生PDF引擎v1问题的修复。 由于渲染行为已更新，因此使用&#x200B;*原生PDF引擎v2*&#x200B;生成的PDF输出可能与使用现有原生PDF发布引擎&#x200B;*原生PDF引擎v1*&#x200B;生成的输出不同。

例如，生成的PDF中的文本可能因&#x200B;*本机PDF引擎v2*&#x200B;使用的核心字体更新而略有不同。 同样，由于图像插值和渲染行为的改进，图像可能会显示得更清晰。

了解如何在您的环境中[启用Native PDF引擎v2](../native-pdf/conf-new-pdf-engine.md)。

有关&#x200B;**本机PDF引擎v2**&#x200B;的信息，请查看[使用本机PDF引擎v2](../native-pdf/new-pdf-engine.md)。


## 编辑器增强功能

### 支持AMA引用样式

Experience Manager Guides现在支持美国医学协会(AMA)的引文风格，并扩展了现有的引文框架，以满足医疗保健、监管和生命科学行业客户所要求的文档标准。

在&#x200B;**Workspace设置**&#x200B;中选择AMA作为引用样式时，引用将根据AMA准则自动设置格式，包括数字上标渲染、顺序编号和精确的引用列表排序。 编辑器中的&#x200B;**分析引文**&#x200B;选项仅在选择AMA时可用，允许作者添加和分析引文而不切换上下文。

本机PDF和AEM Sites输出格式支持AMA引文样式。 要配置引文样式，请转到&#x200B;**Workspace设置**，然后从引文样式选项中选择AMA。 有关详细信息，请查看[使用引文](../user-guide/web-editor-apply-citations.md)。


### 新编辑器中现在支持外部数据源和引文

新编辑器现在支持两种现有的Experience Manager Guides功能：与外部数据源连接以及在文档中使用引用的功能。

在新编辑器中创建或更新内容时，作者可以继续使用已配置的外部数据源。 由于还支持引用，因此作者可以在其内容中添加和管理引用，而无需切换编辑器。

## 审核增强功能

### 审核UI与AEM收件箱(Beta)之间同步审核任务完成

>[!NOTE]
>
> 此功能当前作为Beta功能提供，默认情况下处于禁用状态。 要在您的环境中启用该功能，请联系客户成功团队。

现在，您可以在审核UI和AEM收件箱之间保持审核任务完成的同步。 启用此功能后，在审核UI中完成任务会将其从AEM收件箱中删除，然后从AEM收件箱中完成该任务，这会在审核UI中将其标记为已完成。 这有助于避免两次完成同一任务，并使审阅工作流更加顺畅。 在需要额外审阅时，作者和任务发起者可以继续审阅反馈并重新分配任务。 重新分配任务后，将为审阅人生成新的AEM收件箱通知，从而允许审阅周期无缝继续。

有关更多详细信息，请查看[以审阅者身份完成审阅任务](../user-guide/review-complete-review-tasks.md)。

## 学习内容增强功能

此版本中的产品培训和学习内容功能提供了以下增强功能：

- 现在，作者可以在学习者参加课程之前强制他们进行知识检查。 为课程中的知识检查引入了新的&#x200B;**需要知识检查才能继续**&#x200B;选项。 启用后，学习者需要先尝试进行知识检查，然后再继续后续课程内容。 这有助于确保在课程的指定时刻完成所需的知识检查。 有关详细信息，请在“插入”菜单中查看[其他选项](../learning-content/lc-other-insert-options.md)。
- 创建学习内容时，您现在可以使用多行文本输入字段。 此增强功能支持在单个字段中使用换行符和文本换行，因此无需依赖自定义脚本，即可更轻松地捕获较长的学习者响应。 在“插入”菜单](../learning-content/lc-other-insert-options.md)中了解有关[其他选项的更多信息。
- 现在，SCORM输出模板支持将不同的页面布局分配给课程中的不同主题类型。 这允许您直接从输出模板设置为课程、测验、概览页面和其他主题类型配置专用布局。

  这允许每种主题类型使用适合其内容和结构的布局，而不是在所有课程页面上应用相同的布局。 有关为SCORM输出模板配置页面布局的详细信息，请查看[配置文件夹配置文件](../lc-config-guide/lc-folder-profile.md)。
- Experience Manager Guides现在支持将SCORM内容直接发布到Adobe Learning Manager (ALM)。 配置ALM发布配置文件后，作者可以生成SCORM输出并将其直接上传到Adobe Learning Manager，而无需下载和手动导入包。

  有关详细信息，请查看[配置SCORM预设](../learning-content/config-scorm-preset.md)。


