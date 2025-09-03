---
title: 发行说明 | Adobe Experience Manager Guides 5.1.0版本中的新增功能
description: 了解Adobe Experience Manager Guides 5.1.0版本中的新增功能和增强功能
role: Leader
source-git-commit: f6617b727d385d31ba66d575ee48f29e77ac716f
workflow-type: tm+mt
source-wordcount: '1398'
ht-degree: 0%

---

# 5.1.0版本的新增功能（2025年9月）

本文介绍Adobe Experience Manager Guides版本5.1.0中引入的新增功能和增强功能。

有关此版本中已修复的问题的列表，请查看[5.1.0版本](fixed-issues-5-1-0.md)中已修复的问题。

了解5.1.0版本的[升级说明](../release-info/upgrade-instructions-5-1-0.md)。


## 增强的审核工作流程

在此版本中，审阅工作流程已得到显着改进，可更好地支持作者和审阅者之间的无缝通信。 关键更新包括：

- 包含可操作通知的任务管理工作流
- 能够标记用户以立即引起注意
- 从审核面板访问项目和任务详细信息以方便使用

有了这些增强功能，用户现在可以预期：

- 高效、及时的审查周期
- 减少反馈交换过程中的手动操作

有关更多详细信息，请查看[简介](../user-guide/review.md)

## 改进了创建和使用DITAVAL文件的体验

此更新引入了几项增强功能，可简化创建、管理和应用DITAVAL文件，从而更好地控制条件内容和跨输出设置样式。

主要亮点如下：

- **创作DITAVAL文件时增强的标记支持：** Experience Manager Guides通过DITAVAL文件中的增强标记支持，为自定义内容发布提供了新的功能。 您现在可以应用特定内容（包括图像）的开始和结束标记，并使用粗体、斜体等格式选项扩充标记的部分。 若要处理条件重叠，可以配置&#x200B;**样式冲突**，包括设置默认背景和文本颜色，以确保输出清晰一致。 本机PDF生成完全支持这些标志，并且生成的输出准确而全面地反映了所有应用的样式元素。
有关详细信息，请查看[使用DITAVAL编辑器](../user-guide/ditaval-editor.md)。

  ![](assets/ditaval-flag-style-new.png){width="350" align="left"}

- **本机PDF支持多个DITAVAL文件：**&#x200B;对于本机PDF，现在可以添加多个DITAVAL文件，每个文件都显示为标记条目，以便于识别和删除，从而在PDF输出中提供更大的灵活性和条件内容控制

  此外，此更新通过启用跨格式的可编辑DITAVAL字段来增强输出预设创建，允许用户手动指定DITAVAL路径。

  有关详细信息，请查看[了解Experience Manager Guides中的输出预设](../user-guide/generate-output-understand-presets.md)。

## 发布增强功能

作为新版本的一部分，做出了以下发布增强：

### 改进的输出生成日志过滤

此版本引入了UI改进以生成输出日志过滤功能。 您现在可以更好地筛选所有四个不同级别的输出生成日志： **信息**、**警告**、**错误**（包括错误和异常）以及&#x200B;**致命**；使用经过改进和直观的颜色编码指示器以简化分析并锐化日志流的可见性。 这项改进使您能够更有效地浏览日志并准确找到关键问题。

有关详细信息，请查看[基本疑难解答](../user-guide/generate-output-basic-troubleshooting.md)。

![](./assets/log-file-new.png){align="left"}


### 发布输出的临时文件现在包含新配置文件中的作者和发布URL

Experience Manager Guides的最新发布增强功能现在将新的`system_config.xml`文件添加到使用DITA-OT以及本机PDF输出发布HTML、PDF和JSON输出时生成的临时文件中。 此文件会自动包含在发布作业中，并且在为预设启用&#x200B;**保留临时文件**&#x200B;选项并生成输出时，还可以通过临时文件访问该文件。

`system_config.xml`文件包含AEM实例详细信息，包括创作URL、本地URL和发布URL，它们提供了更清晰的上下文，并提高了下载URL的可跟踪性。

有关详细信息，请查看[了解输出预设](../user-guide/generate-output-understand-presets.md)。

### 新的输出路径变量支持输出生成

此更新引入了输出预设的动态`output path`配置，如Native PDF、DITA-OT PDF、JSON、HTML5和Custom。 用户现在可以在安装期间使用`${base_output_path}`变量定义输出位置，而不是使用固定路径，从而提供了更大的灵活性。 以前的默认路径`/content/dam/fmdita-outputs`不再是必需的。

与全局文件夹配置文件预设关联的所有输出路径将自动迁移以利用新的基本输出路径变量。 但是，对于自定义文件夹配置文件，不会自动迁移；建议您联系客户成功团队以获取帮助。

有关详细信息，请查看[了解输出预设](../user-guide/generate-output-understand-presets.md)。

### 导出的基线现在包括文档状态

导出基线功能现在包括&#x200B;**文档状态**&#x200B;以及基线快照中的标题、文件名、文件类型和版本号等键详细信息。 此增强功能通过提供对基线的更全面概述来改进基线管理。

有关详细信息，请查看[从映射控制台创建和管理基线](../user-guide/web-editor-baseline.md#manage-baselines)。

### 使用旧版组件映射，通过用于AEM Sites输出的映射仪表板支持基线驱动的增量发布

增量输出生成流程已得到增强，可支持使用旧版组件映射为AEM站点发布选定基线中定义的主题的特定版本，从而确保输出内容的准确传播。

有关详细信息，请查看[增量输出生成](../user-guide/generate-output-aem-site.md)。

## 编辑器增强功能

作为新版本的一部分，进行了以下编辑器增强：

### 可重用内容面板的增强搜索体验

Experience Manager Guides在可重用内容面板中引入了增强的搜索体验。 通过此更新，搜索任何关键字现在会扫描作为可重用内容添加的所有文件，而不只是打开的文件，从而确保您在所有匹配项（无论容器是打开还是折叠）中都能找到关键字的精确位置。 此外，当您清除搜索栏时，所有容器的原始状态都会保留，从而提供更加高效和用户友好的搜索功能。

有关更多详细信息，请查看[可重复使用的内容](../user-guide/web-editor-features.md#reusable-content)。

### 为引用链接添加了“格式”属性

Adobe Experience Manager Guides现在为编辑器中的引用链接添加&#x200B;**format**&#x200B;属性。 此属性显示在&#x200B;**Source视图**&#x200B;中，并清楚地指示文件类型，例如：

- 对于扩展名为&#x200B;**.pdf**&#x200B;的文件，格式将设置为&#x200B;**pdf**
- 对于扩展名为&#x200B;**.html**&#x200B;的文件，格式将设置为&#x200B;**html**
- 对于具有&#x200B;**.dita**&#x200B;或&#x200B;**.ditamap**&#x200B;文件的文件，格式将设置为&#x200B;**dita**

此外，扩展名为&#x200B;**.xml**&#x200B;的文件还将格式设置为&#x200B;**dita**。 对于没有任何扩展名的文件，格式将保留为空。 此外，对于范围设置为&#x200B;**external**&#x200B;的任何引用链接，格式将设置为&#x200B;**html**，而不管引用链接中的文件扩展名如何。

### 编辑器中的增强映射下载选项

Experience Manager Guides在&#x200B;**下载映射**&#x200B;对话框中引入了新的&#x200B;**使用实际文件名**&#x200B;选项。 现在，当您下载映射文件时，您可以选择保留其原始文件名而不是默认UUID，从而更易于识别和管理您的文件。 仅当您选择&#x200B;**保留文件层次结构**&#x200B;时，此选项才可用，当您选择&#x200B;**拼合文件层次结构**&#x200B;时，此选项将禁用，这样您就可以在组织下载的映射时更加灵活。

有关详细信息，请查看[下载文件](../user-guide/authoring-download-assets.md#download-a-dita-map-file-from-the-editor)。

![](assets/download-map-dialog-new.png){width="300" align="left"}

### 会话超时提示以防止意外内容丢失

现在，当Adobe Experience Manager会话过期且您因非活动状态而注销时，系统会弹出一条消息通知您。 会话结束后，当您尝试在Experience Manager Guides中编辑内容时，将触发此消息。 该功能有助于降低丢失未保存工作的风险，并提高体验的整体可靠性和流动性，即使是在不活动期间。

![](assets/sign-out-prompt.png)

了解有关Experience Manager Guides中[会话超时提示](../user-guide/session-timeout-prompt.md)的更多信息。

### 在编辑器中增强了`navref`处理

对编辑器的最新增强功能改进了对DITA映射中`navref`元素的处理。 现在，当您将`navref`元素添加到地图时，**选择路径**&#x200B;对话框打开，允许您轻松选择要作为导航链接包含在地图中的地图引用。 添加后，所添加地图的标题会同时显示在创作视图和布局视图中，这样可在创作期间更好地显示包含的导航。  此外，添加的`navref`元素会自动解析以在编辑器中显示引用的映射。

有关详细信息，请查看[添加导航引用](../user-guide/map-editor-other-features.md#add-navigation-references)。


### 编辑器工具栏和用户首选项中的用户界面改进

在此版本中，“常规”和“外观”选项卡的主页上的&#x200B;**用户首选项**&#x200B;中的设置已重新构建。 它包括重命名标签&#x200B;**打开映射的首选项**&#x200B;以及将不间断空格切换开关移动到编辑器工具栏。

此外，在编辑器工具栏中，一些用于启用或禁用跟踪更改、标记和不中断空格的快速访问切换现已分组到菜单下拉列表中的&#x200B;**显示**&#x200B;选项下，以提高可用性。

有关详细信息，请在编辑器[中查看](../user-guide/web-editor-toolbar.md#menu-dropdown)工具栏。







