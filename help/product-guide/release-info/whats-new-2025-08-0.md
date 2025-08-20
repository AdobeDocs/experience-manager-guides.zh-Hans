---
title: 发行说明 | Adobe Experience Manager Guides 2025.08.0版本中的新增功能
description: 了解Adobe Experience Manager Guides 2025.08.0版本中的新增功能和增强功能
role: Leader
source-git-commit: d418ffb254b11430509609b91e0174690815cf73
workflow-type: tm+mt
source-wordcount: '843'
ht-degree: 2%

---

# 2025.08.0版（2025年8月）的新增功能

本文介绍Adobe Experience Manager Guides as a Cloud Service 2025.08.0版本中引入的新增功能和增强功能。

有关此版本中修复的问题列表，请查看 [2025.08.0 版本中已修复的问题](fixed-issues-2025-08-0.md)。

了解2025.08.0版本[的](../release-info/upgrade-instructions-2025-08-0.md)升级说明。


## 增强的审核工作流程

在此版本中，审阅工作流程已得到显着改进，可更好地支持作者和审阅者之间的无缝通信。 关键更新包括：

- 包含可操作通知的任务管理工作流
- 能够标记用户以立即引起注意
- 从审核面板访问项目和任务详细信息以方便使用

有了这些增强功能，用户现在可以预期：

- 高效、及时的审查周期
- 减少反馈交换过程中的手动操作

有关更多详细信息，请查看[简介](../user-guide/review.md)

## 编辑器设置中的可配置AI助手操作

最新更新为AI Assistant中的&#x200B;**创作快速操作**&#x200B;引入了增强的配置，使管理员能够根据特定工作流和首选项自定义创作环境。

启用&#x200B;**AI助手**&#x200B;切换后，管理员可以选择在&#x200B;**创作**&#x200B;选项卡下显示哪些快速操作，从而帮助简化作者交互。 这些可见性设置特定于每个文件夹配置文件。

在Experience Manager Guides的编辑器设置[中了解有关](../user-guide/web-editor-settings.md#general)AI助手的详细信息。

![](assets/authoring-quick-actions.png){width="350" align="left"}


## 改进了创建和使用DITAVAL文件的体验

此更新引入了几项增强功能，可简化创建、管理和应用DITAVAL文件，从而更好地控制条件内容和跨输出设置样式。

主要亮点如下：

- **创作DITAVAL文件时增强的标记支持：** Experience Manager Guides通过DITAVAL文件中的增强标记支持，为自定义内容发布提供了新的功能。 您现在可以应用特定内容（包括图像）的开始和结束标记，并使用粗体、斜体等格式选项扩充标记的部分。 若要处理条件重叠，可以配置&#x200B;**样式冲突**，包括设置默认背景和文本颜色，以确保输出清晰一致。 本机PDF生成完全支持这些标志，并且生成的输出准确而全面地反映了所有应用的样式元素。
有关详细信息，请查看[使用DITAVAL编辑器](../user-guide/ditaval-editor.md)。

  ![](assets/ditaval-flag-style-new.png){width="350" align="left"}

- **本机PDF支持多个DITAVAL文件：**&#x200B;对于本机PDF，现在可以添加多个DITAVAL文件，每个文件都显示为标记条目，以便于识别和删除，从而在PDF输出中提供更大的灵活性和条件内容控制

  此外，此更新通过启用跨格式的可编辑DITAVAL字段来增强输出预设创建，允许用户手动指定DITAVAL路径。

  有关详细信息，请查看[了解Experience Manager Guides中的输出预设](../user-guide/generate-output-understand-presets.md)。

## 改进的输出生成日志过滤

此版本引入了UI改进以生成输出日志过滤功能。 您现在可以更好地筛选所有四个不同级别的输出生成日志： **信息**、**警告**、**错误**（包括错误和异常）以及&#x200B;**致命**；使用经过改进和直观的颜色编码指示器以简化分析并锐化日志流的可见性。 这项改进使您能够更有效地浏览日志并准确找到关键问题。

有关详细信息，请查看[基本疑难解答](../user-guide/generate-output-basic-troubleshooting.md)。

![](./assets/log-file-new.png){align="left"}


## 发布输出的临时文件现在包含新配置文件中的作者和发布URL

Experience Manager Guides的最新发布增强功能现在将新的`system_config.xml`文件添加到使用DITA-OT以及本机PDF输出发布HTML、PDF和JSON输出时生成的临时文件中。 此文件会自动包含在发布作业中，并且在为预设启用&#x200B;**保留临时文件**&#x200B;选项并生成输出时，还可以通过临时文件访问该文件。

`system_config.xml`文件包含AEM实例详细信息，包括创作URL、本地URL和发布URL，它们提供了更清晰的上下文，并提高了下载URL的可跟踪性。

有关详细信息，请查看[了解输出预设](../user-guide/generate-output-understand-presets.md)。

## 新的输出路径变量支持输出生成

此更新引入了输出预设的动态`output path`配置，如Native PDF、DITA-OT PDF、JSON、HTML5和Custom。 用户现在可以在安装期间使用`${base_output_path}`变量定义输出位置，而不是使用固定路径，从而提供了更大的灵活性。 以前的默认路径`/content/dam/fmdita-outputs`不再是必需的。

与全局文件夹配置文件预设关联的所有输出路径将自动迁移以利用新的基本输出路径变量。 但是，对于自定义文件夹配置文件，不会自动迁移；建议您联系客户成功团队以获取帮助。

有关详细信息，请查看[了解输出预设](../user-guide/generate-output-understand-presets.md)。

## 编辑器工具栏和用户首选项中的用户界面改进

在此版本中，“常规”和“外观”选项卡的主页上的&#x200B;**用户首选项**&#x200B;中的设置已重新构建。 它包括重命名标签&#x200B;**打开映射的首选项**&#x200B;以及将不间断空格切换开关移动到编辑器工具栏。

此外，在编辑器工具栏中，一些用于启用或禁用跟踪更改、标记和不中断空格的快速访问切换现已分组到菜单下拉列表中的&#x200B;**显示**&#x200B;选项下，以提高可用性。

有关详细信息，请在编辑器[中查看](../user-guide/web-editor-toolbar.md#menu-dropdown)工具栏。






