---
title: 发行说明 | Adobe Experience Manager Guides 4.4.0版本中的新增功能
description: 了解Adobe Experience Manager Guides 4.4.0版本中的新增功能和增强功能
role: Leader
source-git-commit: 57c3b39f0ab0fde5b18e4d4ae0e1501738997e68
workflow-type: tm+mt
source-wordcount: '3050'
ht-degree: 15%

---

# 4.6.0版本的新增功能（2024年9月）

本文介绍Adobe Experience Manager Guides版本4.6.0中引入的新增功能和增强功能。

有关此版本中已修复的问题的列表，请查看[4.6.0版本](../release-info/fixed-issues-4-6-0.md)中已修复的问题。

了解4.6.0版本](../release-info/upgrade-instructions-4-6-0.md)的[升级说明。


## 发布增强功能

4.6.0版本中进行了以下内容发布增强：



### 将主题或其元素添加到Publish体验片段

体验片段是Adobe Experience Manager中的一个模块化内容单元，它集成了内容和布局。 体验片段有助于创建一致且引人入胜的体验，这些体验可以跨多个渠道进一步重复使用。 例如，您可以为页眉或页脚创建体验片段，其中具有品牌元素、促销横幅、客户口号和事件促销活动。

![文件属性选项选项卡](./assets/file-properties-outputs-4-6.png) {width="300" align="left"}

*Publish并从&#x200B;**文件属性**.*&#x200B;的&#x200B;**输出**&#x200B;部分中查看主题的体验片段

Experience Manager Guides现在允许您将主题或其元素发布到体验片段。 您可以在主题或其元素与体验片段模板之间创建基于JSON的映射。 您还可以使用条件过滤器创建体验片段变量。

详细了解如何[Publish体验片段](../user-guide/publish-experience-fragment.md)。



### 内容片段发布中的增强

Experience Manager Guides在内容片段中还提供了一些有用的增强功能：

- Experience Manager Guides允许您将主题或其元素发布到内容片段。

- 您可以从&#x200B;**文件属性**&#x200B;的&#x200B;**输出**&#x200B;部分发布和查看主题的内容片段。


- 您可以在发布到内容片段时，通过用条件筛选内容来轻松创建内容片段变体。

- 使用新的映射界面轻松选择元素并将其发布到内容片段。

现在，内容片段发布仅替换映射的内容，而不是覆盖完整的内容片段。 此功能允许内容片段包含来自多个源的数据，如多个主题或内容片段编辑器。

![在Publish中添加片段模型和映射详细信息作为内容片段对话框](assets/content-fragment-mapping.png)

有关详细信息，请查看[Publish内容片段](../user-guide/publish-content-fragment.md)。

### 为方便使用，重新组织了AEM Sites预设

这些设置已重新组织，以帮助您快速配置输出预设并生成AEM Sites输出。
您可以通过在**新建输出预设**&#x200B;对话框中选择&#x200B;**使用旧版组件映射**&#x200B;选项来创建现有的AEM Sites预设。

查看AEM Sites预设中的&#x200B;**常规**、**内容**&#x200B;和&#x200B;**交叉映射引用**&#x200B;选项卡：
- **常规**：包含用于生成输出的常规配置。 您可以指定站点和输出路径，删除或覆盖现有的输出页面，删除已删除主题的先前生成的页面，选择设计模板，保留临时文件，以及指定生成后工作流。
- **内容**：包含适用于生成输出的内容的设置。 您可以选择筛选器、DITA映射基线以及要发布的元数据属性。
- **交叉映射引用**：此列表包含主题包含作用域=&quot;peer&quot;的交叉映射引用。 您可以为其他DITA映射中可用的主题的scope=&quot;peer&quot;的交叉映射引用列表指定发布上下文。 如果您使用Experience Manager Guides (UUID)版本，将显示此选项卡。



### Web编辑器中来自AEM Sites预设的交叉映射引用

Experience Manager Guides的最新增强功能在Web编辑器的AEM Sites预设中引入了跨映射引用。
Experience Manager Guides中的交叉映射引用有助于改进内容导航、提高内容重用性和增强用户体验。


您可以为对具有scope=&quot;peer&quot;的其他DITA映射中可用的主题的交叉映射引用列表指定发布上下文。 例如，映射A中的主题1包含对主题2的引用。 主题2可以出现在单个或多个映射中。  您可以选择父映射和特定预设，也可以为每个链接选择最近发布的输出。

如果同一主题在文件中被引用多次，则可以为每个实例添加不同的发布上下文。 这提供了更大的灵活性和对其内容的控制。 例如，主题3同时存在于映射B和映射C中。主题1包含两个对主题3的引用。 您可以选择映射B作为第一个链接的父映射，选择映射C作为第二个链接的父映射。

![旧版AEM Sites预设](assets/aem-sites-legacy.png)

*从&#x200B;**AEM Sites**预设的&#x200B;**交叉映射引用**选项卡中为链接的主题指定发布上下文。*






### 能够将元数据从主题文件属性传递到本机PDF输出

现在，通过Experience Manager Guides可在生成本机PDF输出时将元数据从主题的文件属性添加到页面布局。 使用此功能可向页面布局添加特定主题的元数据，例如标题、标记和描述。 您还可以根据主题的元数据自定义已发布的PDF，例如根据主题的文档状态向主题背景添加水印。

![添加元数据本机pdf](./assets/add-metadata-native-pdf.png) {width="300" align="left"}

*将元数据添加到页面布局中的字段。*

了解如何在页面布局中[添加字段和元数据](../native-pdf/design-page-layout.md#add-fields-metadata)。





### 在本机PDF发布中支持Markdown文档

Experience Manager Guides还支持在本机PDF发布中使用Markdown文档。 此功能非常方便，可帮助您为DITA映射中的Markdown文件生成PDF。

有关更多详细信息，请查看[对Markdown文档的支持](../web-editor/native-pdf-web-editor.md#support-for-markdown-documents)。


### 通过DITA-OT生成输出时下载临时文件

您还可以通过DITA-OT下载发布AEM Sites、HTML、自定义、JSON或PDF输出时生成的临时文件。 此功能可帮助您分析输出生成过程中可能发生的任何问题并有效地进行故障排除。  
如果您选择了任何已传递到使用DITA-OT生成的输出的元数据属性，则也可以下载metadata.xml文件。 

有关预设的详细信息，请查看[了解输出预设](../user-guide/generate-output-understand-presets.md)。


### 用于为HTML5输出选择平面或嵌套文件层次结构的选项

现在，通过Experience Manager Guides可保留临时文件的平面文件夹层次结构，其中整个内容以HTML5输出格式发布并保存在单个文件夹中。
如果不选择拼合文件层次结构，则会在嵌套文件夹层次结构中生成HTML5输出。 这意味着内容的原始文件夹结构（其中包含组织到子文件夹中的文件）将在输出中进行复制。 这种嵌套文件夹层次结构使文件的组织和分类更加复杂，更易于管理和导航大量数据。


详细了解如何[生成HTML5输出](../user-guide/generate-output-html5.md)


## 编辑器增强功能

4.6.0版本中添加了以下编辑器增强功能：

### 对锁定文件的创作和Source模式的只读访问权限

如果DITA或Markdown文件被其他用户锁定或签出，则无法编辑或更改内容。 除了预览之外，您还可以在“创作”或“Source”模式下以只读文件的形式查看它。
在只读模式下，您可以在**创作**&#x200B;或&#x200B;**Source**&#x200B;模式下查看内容以及标记和属性，并编辑文件属性。

您还可以访问只读DITA映射的&#x200B;**布局**&#x200B;视图。
>[!NOTE]
>
> 您的文件夹配置文件管理员必须更新&#x200B;*ui_config.json*，以便您可以在“创作”、“Source”和“布局”模式下协调访问只读文件。

![锁定的文件编辑器](./assets/locked-file-editor.png)
*在“创作”和“Source”模式下查看锁定的文件。*


了解如何[在创作和Source模式中打开锁定的文件](../user-guide/web-editor-edit-topics.md#open-locked-files-in-author-and-source-modes)。



### 在操作的元素间选择部分内容

Experience Manager Guides可增强您在Web编辑器中跨元素选择内容的体验。 您可以轻松地跨不同元素选择内容并执行操作，如使其变为粗体、斜体和加下划线。

此功能允许您为部分选定的内容无缝地应用或删除格式。 您还可以快速删除跨元素选择的内容。 删除内容后，如有必要，其余内容会自动合并到单个有效元素下。 您还可以跨元素选择部分内容，然后使用有效的DITA元素环绕该内容。

总体而言，这些增强功能提供了更好的体验，并帮助您在编辑文档时提高效率。
有关更多详细信息，请查看[跨元素](../user-guide/web-editor-edit-topics.md#partial-selection-of-content-across-elements)的部分内容选择。



### 用于根据元素的位置查看和插入有效元素的隔离列表

在Web编辑器中编辑文档时，您现在可以查看在当前位置以及在当前位置之外有效的元素的独立列表。 根据要求，您可以从以下选项中选择元素：

- **在当前位置**&#x200B;处可插入在当前光标位置本身的有效元素。
- **当前位置**&#x200B;之外的有效元素，您可以在元素层次结构中当前元素的任何父元素之后插入这些元素。

![插入元素对话框](assets/insert-element-dialog.png){width="300" align="left"}

*查看有效元素的隔离列表以在当前位置插入元素。*


此有效元素拆分列表可帮助您维护内容结构并遵循DITA标准。

了解有关[辅助工具栏](../user-guide/web-editor-features.md#2051ea0j0y4)部分中的&#x200B;**插入元素**&#x200B;功能的更多信息。


### 在存储库视图中搜索和筛选文件的改进体验

现在，您在过滤文件时可以获得增强的体验。改进的文件过滤功能提供了一种能够更轻松地搜索和浏览文件的方法。


![在存储库视图中搜索文件](assets/repository-filter-search-2404.png){width="300" align="left"}

*搜索包含文本的文件`general purpose.`*

享受更快地访问相关文件和使用更直观的用户界面等益处，使您的搜索体验更加顺畅、高效。

![快速搜索筛选器](assets/repository-filter-search-quick.png) {width="300" align="left"}

*使用快速过滤器搜索 DITA 和非 DITA 文件。*


>[!NOTE]
>
> 您的文件夹配置文件管理员必须更新&#x200B;*ui_config.json*，以便您可以协调地访问此功能。

详细了解[左侧面板](../user-guide/web-editor-features.md#id2051EA0M0HS)部分中的&#x200B;**过滤搜索**&#x200B;功能。

### 增强的内容组织的分组条件

Experience Manager Guides现在允许您对条件进行分组，并在嵌套层次结构中显示它们，从而允许您向单个组添加多个条件。 通过分组条件，您可以更好地在内容中组织和应用这些条件。

以嵌套层次结构组织的![条件](assets/conditions-nested-hierarchy.png){width="300" align="left"}

在[左侧面板](../user-guide/web-editor-features.md#id2051EA0M0HS)部分中了解有关&#x200B;**条件**&#x200B;功能说明的更多信息。

### 使用新的用户首选项用户界面自定义您的Web编辑器体验

Web编辑器中的&#x200B;**用户首选项**&#x200B;对话框现在包含新的&#x200B;**外观**&#x200B;选项卡。 此新选项卡允许您在Web编辑器界面中方便地配置最常见的外观首选项。

您可以配置以按标题或文件名查看文件，并更改应用程序和源视图的主题。 它还有助于您配置设置，以便在存储库视图中查找打开的文件并处理不间断空格。

用户首选项的![外观选项卡](assets/user_preference_editor_appearance.png){width="550" align="left"}

*根据您的喜好自定义外观。*

在[左侧面板](../user-guide/web-editor-features.md#id2051EA0M0HS)部分中了解有关&#x200B;**用户首选项**&#x200B;功能说明的更多信息。


### 在Web编辑器的存储库视图中查找打开的文件

选择&#x200B;**用户首选项**&#x200B;中的&#x200B;**始终在存储库中查找文件**&#x200B;选项可快速导航并在存储库视图中查找文件。 您不必手动搜索它。

在编辑时，此功能还可帮助您轻松查看文件在存储库层次结构中的位置。

有关更多详细信息，请查看[在存储库视图](../user-guide/web-editor-edit-topics.md#locate-an-open-file-in-the-repository-view)中找到打开的文件。

### 改进了Web编辑器中不间断空格的处理

Experience Manager Guides允许您在Web编辑器中编辑文档时显示不间断空间指示器。 它还改进了不中断空间的处理。
它将多个连续的空格转换为单个空格，以在Web编辑器中保留文档的WYSIWYG视图。 此功能还有助于改进文档的整体外观和专业性。


有关详细信息，请查看Web编辑器的[其他功能](../user-guide/web-editor-other-features.md)。


### 能够从元素层次结构中查看任何元素的属性

现在，内容属性&#x200B;**类型**&#x200B;显示为下拉菜单。 您可以查看并从下拉列表中为当前标记选择完整层次结构的标记。

此下拉菜单可帮助您快速访问所选标记的内容属性。


内容属性中的![类型下拉菜单](assets/content-properties-type.png){width="300" align="left"}

*从层次结构中为当前标记选择一个标记。*

在[右侧面板](../user-guide/web-editor-features.md#id2051eb003yk)部分中了解有关&#x200B;**内容属性**&#x200B;功能的更多信息。



### 提高了从映射编辑器批量签入文件的性能

Experience Manager Guides改进了映射编辑器中批量文件签入功能的性能和体验。 这项改进可帮助您更快地批量签入文件。
您还可以从**另存为新版本和解锁**&#x200B;对话框中查看文件的签入操作的进度。 最后，在操作完成且所有选定的检出文件都已检入后，将显示成功消息。

![另存为新版本并解锁对话框](./assets/save-version-lock.png){width="300" align="left"}

*查看从映射编辑器批量签入的文件的列表和状态。*

了解如何[使用高级映射编辑器](../user-guide/map-editor-advanced-map-editor.md)





## 内容生命周期管理增强功能

内容生命周期管理在以下方面得到了增强：

### 能够使用预配置的语言组将内容翻译成多种语言

Experience Manager Guides 现在允许您创建语言组，并轻松地将您的内容翻译成多种语言。此功能可帮助您根据组织的需要组织和管理翻译内容。

例如，如果您需要将内容翻译成欧洲某些国家/地区的语言，则可以为欧洲语言创建一个语言组，例如英语 (EN)、法语 (FR)、德语 (DE)、西班牙语 (ES) 和意大利语 (IT)。



![翻译面板](assets/translation-languages-2404.png){width="300" align="left"}

*选择要翻译文档的语言组或语言。*

>[!NOTE]
>
>如果某个语言的目标文件夹缺失或目标语言与源语言相同，则它会变灰，并会显示警告标志。

作为管理员，您可以创建语言组并将其配置为多个文件夹配置文件。作为作者，您可以查看文件夹配置文件中配置的语言组。


总体而言，创建语言组可以提高翻译项目的效率和生产力，最终可以改善多种语言的本地化流程。


了解如何[从Web编辑器](../user-guide/translate-documents-web-editor.md)翻译文档。


### 提高了大型翻译项目的性能和可扩展性

翻译功能比以往更快、更可扩展。 它随附提供增强性能的新架构。 项目创建时间现在比以前快，在此过程中几乎不存在冲突。 这种改进的性能可帮助您更快地翻译，确保即使对于大型翻译项目也能顺利操作。

这种改进非常有益，因为它提高了生产率和整体体验。

详细了解如何[从Web编辑器](../user-guide/translate-documents-web-editor.md)翻译文档。

### 在翻译后自动删除或禁用翻译项目

现在，作为管理员，您可以将翻译项目配置为在完成翻译后自动禁用或删除。 此功能可帮助您在完成翻译后高效地使用资源和管理文件。

删除项目将永久删除该项目中存在的所有文件和文件夹。 删除翻译项目还可以释放已占用的磁盘空间。

如果要稍后使用翻译项目，可以禁用这些项目。

![](assets/editor-setting-translation.png){width="550" align="left"}


*为翻译项目配置语言组和清理设置。*


详细了解如何[自动删除或禁用翻译项目](../user-guide/translate-documents-web-editor.md#automatically-delete-or-disable-a-completed-translation-project)。


### 在Adobe Experience Manager Assets上禁用选择性文件夹的后处理


作为管理员，您现在可以在Experience Manager Assets上为选择性文件夹禁用后处理和UUID生成。 此配置可能很有用，尤其是在处理许多资源或复杂的文件夹结构时。 它还有助于多个用户同时快速上传资产，而不会相互干扰。  

禁用文件夹的后处理也会影响其所有子文件夹。 但是，Experience Manager Guides现在支持选择性地为被忽略文件夹中的各个子文件夹启用后处理。

了解如何[禁用文件夹](../cs-install-guide/conf-folder-post-processing.md)的后处理。


## 数据源连接器中的增强功能

2024.4.0 版本的数据源连接器具有以下增强功能：

### 连接到Salsify、Akeneo和Microsoft Azure DevOps Boards (ADO)数据源

除了现有的现成连接器之外，Experience Manager Guides 还为 Salsify、Akeneo 和 Microsoft Azure DevOps Boards (ADO) 数据源提供连接器。作为管理员，您可以下载并安装这些连接器。然后，配置已安装的连接器。

### 复制并粘贴示例查询以创建内容片段或主题

您可以轻松地在生成器中复制并粘贴样本数据查询，以创建内容片段或主题。使用此功能，您无需记住语法或手动创建查询。 您无需手动输入查询，而是可以复制并粘贴示例查询，对其进行编辑，然后使用它来根据您的要求获取数据。

![插入内容片段对话框](assets/insert-content-snippet.png){width="800" align="left"}

*复制并编辑示例查询，以创建内容片段。*

### 使用文件连接器连接到JSON数据文件


现在，作为管理员，您可以配置 JSON 文件连接器，以使用 JSON 数据文件作为数据源。使用连接器从您的计算机或 Adobe Experience Manager Assets 中导入 JSON 文件。然后，作为作者，您可以使用生成器创建内容片段或主题。

此功能可帮助您使用存储在 JSON 文件中的数据，并在各个代码片段中重复使用它。每当您更新 JSON 文件时，内容也会动态更新。

### 为连接器配置多个资源URL以创建内容片段或主题

作为管理员，您可以为某些连接器(如Generic REST Client、Salsify、Akeneo和Microsoft Azure DevOps Boards (ADO))配置多个资源URL。

然后，作为作者，通过连接数据源来使用生成器创建内容片段或主题。此功能非常方便，因为您不必为每个 URL 创建数据源。它可帮助您从单个内容片段或主题中特定数据源的任何资源快速获取数据。

查看有关数据源连接器的更多详细信息，以及如何[从用户界面](../cs-install-guide/conf-data-source-connector-tools.md)配置数据源连接器。

了解如何[使用数据源中的数据](../user-guide/web-editor-content-snippet.md)。

