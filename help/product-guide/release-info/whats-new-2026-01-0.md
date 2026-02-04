---
title: 发行说明 | Adobe Experience Manager Guides 2026.01.0版本中的新增功能
description: 了解Adobe Experience Manager Guides 2026.01.0版本中的新增功能和增强功能
role: Leader
source-git-commit: cb3b06e18391fdfc53eb5abd4096553781eab0b8
workflow-type: tm+mt
source-wordcount: '1551'
ht-degree: 1%

---

# 2026.01.0版（2026年2月）的新增功能

本文介绍Adobe Experience Manager Guides as a Cloud Service 2026.01.0版本中引入的新增功能和增强功能。

有关此版本中修复的问题列表，请查看 [2026.01.0 版本中已修复的问题](fixed-issues-2026-01-0.md)。

了解2026.01.0版本[的](../release-info/upgrade-instructions-2026-01-0.md)升级说明。


## 在“查找和替换”中引入Source模式搜索

Experience Manager Guides在编辑器界面的左侧面板中提供的查找和替换功能中引入了几项增强功能。 除了改进用户界面以提高可用性外，此版本还在&#x200B;**查找和替换**&#x200B;面板中引入了新的&#x200B;**使用源模式**&#x200B;切换开关。

启用此模式后，您不仅可以对可见内容执行全局搜索，还可以对搜索字符串的基础源内容（XML结构，包括元素、标记和属性值）执行全局搜索。 此模式可确保跨整个内容进行全面的搜索。

![](assets/map-find-replace-with-source-mode.png){width="650" align="left"}

在此模式下，您可以应用过滤器以按文件类型、文档状态、上次修改日期等缩小搜索范围。 您还可以选择在执行“全部替换”操作后下载详细的CSV报表，该操作提供所执行的所有替换操作及其成功和失败状态的快照。

有关更多详细信息，请在编辑器[的](../user-guide/web-editor-left-panel.md#find-and-replace)左侧面板中查看&#x200B;_查找和替换_&#x200B;部分。

>[!NOTE]
>
> 对于“查找和替换”面板中的&#x200B;**使用源模式**&#x200B;功能，必须首先完成自定义索引部署。 建立索引后，请联系您的客户成功团队以启用此功能。

## 增强的文件和文件夹浏览体验

此版本引入了更清晰、更直观的界面，用于浏览Experience Manager Guides中的文件和文件夹路径。

浏览文件时，改版的&#x200B;**选择文件**&#x200B;对话框现在具有带两个视图的选项卡式布局 — **存储库**&#x200B;用于以表格格式导航整个内容存储库，以及&#x200B;**收藏集**&#x200B;用于快速访问常用主题、映射和图像。

![](assets/select-file.png){width="650" align="left"}

关键增强功能包括：

- 用于有组织导航的文件和文件夹的表格视图。
- 痕迹导航和文件夹导航面板，可轻松地在文件夹中移动。
- 支持对可重用内容、主题引用、架构、输出预设（使用DITAVAL）和Workfront进行多文件选择。
- 预览所选文件以便于查看；对于多个选择，根据需要预览所有文件并从“预览”面板中删除任何文件。
- 搜索和筛选选项可按名称、标题、文件类型、文档状态和标记缩小结果的范围。

**选择路径**&#x200B;对话框还为文件夹导航提供了改进的树状结构视图，从而确保在内容存储库中选择路径的方式更加有组织和高效。

![](assets/select-path-dialog-new.png){width="350" align="left"}

有关更多详细信息，请在编辑器的[其他功能](../user-guide/web-editor-other-features.md#browse-files-and-folders-in-experience-manager-guides)中查看&#x200B;_浏览Experience Manager Guides_&#x200B;中的文件和文件夹。

## 存储库搜索和过滤器增强功能

### 支持文档状态过滤器

现在，根据文件的当前文档状态筛选存储库搜索结果。 通过新的&#x200B;**文档状态**&#x200B;筛选器，您可以使用文件夹配置文件内`ui_config.json`文件中定义的可用筛选器值来缩小搜索范围。

![](assets/document-state-filter-repository.png){align="left"}

“文档”状态可用的默认筛选器值为：“草稿”、“编辑”、“正在审阅”、“已批准”、“已审阅”和“完成”。 有关自定义默认文档状态筛选器值的详细信息，请查看[配置文档状态筛选器](../cs-install-guide/config-doc-state-filters.md)。

>[!NOTE]
>
> 如果您正在为`ui_config.json`使用自定义设置，请确保在升级之前对这些设置进行备份。 更新后，查看并调整您的设置，以与最新版本中引入的更改保持一致。

### 多媒体的缩略图图标

现在，所有多媒体文件都显示有缩略图图标，以便更轻松地在&#x200B;**存储库**&#x200B;中直观地识别和查找图像。 在&#x200B;**搜索面板**&#x200B;中搜索文件时，此增强功能也适用，可帮助您快速区分多媒体资源和其他文件类型。

![](assets/thumbnail-repository.png){align="left"}

## 编辑器增强功能

作为此版本的一部分，进行了以下编辑器增强：

### 在预览模式下刷新主题或映射

为已在预览模式下打开的映射引入新的&#x200B;**刷新**&#x200B;功能。 通过此新功能，您可以轻松刷新整个映射的内容或其中存在的单个主题。

- 为了刷新整个映射（包括所有主题），在编辑器的左上角引入了一个新的&#x200B;**刷新**&#x200B;按钮。

  ![](assets/refresh-map.png){width="600" align="left"}

- 为了刷新单个主题的内容，在上下文菜单中引入了新的&#x200B;**刷新主题**&#x200B;选项。

  ![](assets/refresh-topic.png){width="600" align="left"}

有关详细信息，请查看[映射编辑器功能](../user-guide/map-editor-advanced-map-editor.md)。

### 元数据更改的工作副本指示器

对&#x200B;**文件属性**&#x200B;下可用的元数据字段所做的任何更改现在都将触发工作副本指示器。 添加、删除或修改任何默认或自定义元数据字段时，文档版本被标记为&#x200B;_已修改(*)_。 此增强功能可确保准确跟踪所有元数据更改，从而增强对文档版本的可视性和控制能力。

### 主题和地图的字数

您现在可以跟踪映射或主题文件中出现的字数。 右侧面板中新增的&#x200B;**单词数**&#x200B;字段将显示主题（或地图）中存在的单词总数，其中以空格分隔的单词将计为单个单词。 每次保存更改时，它都会自动刷新。 对于交叉引用，只包含显示文本，而排除键。

![](assets/file-properties-new.png){width="350" align="left"}

有关详细信息，请在编辑器[中查看](../user-guide/web-editor-right-panel.md#file-properties)右侧面板。

### 改进了对只读文件的处理

现在，对于处于&#x200B;**只读**&#x200B;模式的文件，编辑文件属性受到限制。 如果文件被其他用户锁定（在只读模式下可用），则您无法更改任何元数据属性，无论是从右面板[更改属性](../user-guide/web-editor-right-panel.md#file-properties)、更改文件&#x200B;**的**&#x200B;上下文菜单中的[属性](../user-guide/web-editor-other-features.md#context-menu-functions-on-a-files-tab)选项更改属性还是更改元数据报表[。 &#x200B;](../user-guide/reports-web-editor.md#metadata-report)这有助于防止意外更改只读文件。

## 审核增强功能

### 在正在进行的审阅任务中添加或删除主题

现在，您可以向正在进行的审阅任务添加新主题（如果先前未发送这些主题以供审阅），或从正在进行的审阅任务中删除主题，而不会影响审阅工作流。

在&#x200B;**任务详细信息**&#x200B;页面上，您只需选择或取消选择主题以修改主题列表即可。 查看者会通过AEM和电子邮件收到通知，告知其通过AEM和电子邮件通知所分配的主题有任何变化。 有关更多详细信息，请查看[发送审核主题](../user-guide/review-send-topics-for-review.md)。

![](assets/modify-review-topics.png){width="650" align="left"}

## 翻译增强功能

### 已发送以进行翻译的无版本化资产的指示器

在管理翻译时，请务必确保在发送内容以进行处理之前对所有内容进行版本控制。 为了帮助解决此问题，Experience Manager Guides现在为已保存更改但尚未进行版本控制的主题提供明确的指示符。

如果文件包含不带版本的更改（未在地图中另存为新版本），则文件旁边会显示一个&#x200B;_信息_&#x200B;图标，指示存在更新。 要快速关注这些文件，请在“筛选器”面板中启用&#x200B;**仅显示具有无版本更改的资源**&#x200B;选项。

有关更多详细信息，请从映射控制台查看[翻译文档](../user-guide/translate-documents-web-editor.md)。

![](assets/unversioned-changes-translation.png){width="650" align="left"}

## 发布增强功能

### 特定输出预设的自定义图像演绎版

您现在可以使用`outputName`中的`renditionmapping.xml`属性为同一输出类型下的各个输出预设配置不同的图像演绎版。 此增强功能让您在发布需要针对不同场景采用不同图像分辨率的内容时拥有更大的灵活性。 例如，您可能希望主HTML5输出使用高分辨率图像，同时为轻型预设使用较小的缩略图。

有关更多详细信息，请查看[处理输出生成](../cs-install-guide/conf-output-generation.md#handle-image-rendition-during-output-generation)中的图像演绎版。


### 下载生成的输出的日志

通过Assets UI生成输出时，现在有新的&#x200B;**下载日志**&#x200B;按钮可用，通过该按钮可以将日志下载到本地设备，以便更轻松地访问和查看。


### 本机PDF输出中交叉引用的语言变量

发布本机PDF输出时，您可以使用[语言变量](../native-pdf/native-pdf-language-variables.md)来翻译静态交叉引用文本，如&#x200B;_参阅章节_&#x200B;或&#x200B;_参阅页面_。 变量通过`xml:lang`属性使用主题中定义的语言。

有关配置Native PDF输出预设和交叉引用设置的详细信息，请查看[Native PDF输出预设](../web-editor/native-pdf-web-editor.md)。


### 在新AEM Sites（使用复合组件映射）发布中支持元素级组件映射

Experience Manager Guides现在支持AEM Sites输出中的元素级别组件映射（使用复合组件映射），从而让团队能够精确控制DITA元素使用`componentmapping.json`呈现的方式。 通过将`topicref`、标题、图像、表等映射到适当的AEM核心组件，您可以获得更简洁的结构，而不是默认使用文本组件的所有内容。 这可以提高性能，并解锁更丰富、更现代的Sites体验。

有关详细信息，请在AEM Sites[中查看](../cs-install-guide/component-mapping.md)组件映射。

## 资产处理增强功能

此版本引入了以下资产处理增强功能：

- 在文件夹和单个文件级别运行资产处理
- 通过选择特定的资源类型(如主题、映射、Markdown、HTML/CSS、DITAVAL或其他支持的文件)来筛选资源，以仅处理您需要的文件。
- 应用基于日期的筛选器以限制指定时间范围内的处理范围。
- 使用“存储库”视图和“资源管理器”面板中文件和文件夹的上下文菜单中提供的新选项（**重新处理资源**）直接重新处理资源。

有关处理资产的更多详细信息，请查看[处理资产](../user-guide/asset-processor.md)。

## API增强功能

作为此版本的一部分，进行了以下API增强：

- 引入新API以创建新翻译项目并跟踪其状态。 这些API有助于自动化翻译过程，减少手动工作并提高效率。 有关详细信息，请查看[创建翻译项目](../api-reference/translation-project.md)
- 增强了资源处理API，提高了文件和文件夹的过滤能力。 有关详细信息，请查看[处理资源](../api-reference/bulk-assets-processing.md)。
















