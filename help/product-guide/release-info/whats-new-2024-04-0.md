---
title: 发行说明 | Adobe Experience Manager Guides 2024.4.0版本中的新增功能
description: 了解Adobe Experience Manager Guidesas a Cloud Service2024.4.0版本中的新增功能和增强功能。
exl-id: e9db535a-5ad5-4ff0-94af-b4425594316a
source-git-commit: 5d99274da8fdacbd255d426fa4913b5773ca45f8
workflow-type: tm+mt
source-wordcount: '1806'
ht-degree: 28%

---

# 2024.4.0版本中的新增功能

本文介绍Adobe Experience Manager Guides 2024.4.0版的新增功能和增强功能。

有关此版本中修复的问题列表，请查看 [2024.4.0 版本中已修复的问题](fixed-issues-2024-04-0.md)。

了解2024.4.0版本](upgrade-instructions-2024-04-0.md)的[升级说明。

## 能够使用预配置的语言组将内容翻译成多种语言

Experience Manager Guides 现在允许您创建语言组，并轻松地将您的内容翻译成多种语言。此功能可帮助您根据组织的需要组织和管理翻译内容。

例如，如果您需要将内容翻译成欧洲某些国家/地区的语言，则可以为欧洲语言创建一个语言组，例如英语 (EN)、法语 (FR)、德语 (DE)、西班牙语 (ES) 和意大利语 (IT)。



![翻译面板](assets/translation-languages-2404.png){width="300" align="left"}

*选择您想要将文档翻译成的语言组或语言。*

>[!NOTE]
>
>如果某个语言的目标文件夹缺失或目标语言与源语言相同，则它会变灰，并会显示警告标志。

作为管理员，您可以创建语言组并将其配置为多个文件夹配置文件。作为作者，您可以查看文件夹配置文件中配置的语言组。


总体而言，创建语言组可以提高翻译项目的效率和生产力，最终可以改善多种语言的本地化流程。


了解如何[从Web编辑器](../user-guide/translate-documents-web-editor.md)翻译文档。



## 在翻译后自动删除或禁用翻译项目

现在，作为管理员，您可以将翻译项目配置为在完成翻译后自动禁用或删除。 此功能可帮助您在完成翻译后高效地使用资源和管理文件。

删除项目将永久删除该项目中存在的所有文件和文件夹。 删除翻译项目还可以释放已占用的磁盘空间。

如果要稍后使用翻译项目，可以禁用这些项目。

![](assets/editor-setting-translation.png){width="550" align="left"}


*为翻译项目配置语言组和清理设置。*


详细了解如何[自动删除或禁用翻译项目](../user-guide/translate-documents-web-editor.md#automatically-delete-or-disable-a-completed-translation-project)。


## 在预览实例的批量激活集合中激活映射的输出

现在，除了在发布实例上激活批量激活集合的输出之外，Experience ManagerGuides as Cloud Service还提供了在&#x200B;**预览**&#x200B;实例上激活该集合的功能。


此功能可帮助您将内容激活到预览实例，允许您在将其激活到&#x200B;**Publish**&#x200B;实例之前查看内容的外观和工作方式。


![已创建批量激活集合审核历史记录选项卡](assets/bulk-collection-audit-history.png){width="800" align="left"}

*在&#x200B;**审核历史记录**选项卡中查看有关激活的映射输出的信息。*


了解有关[批量激活](../user-guide/conf-bulk-activation-publish-map-collection.md)的详细信息。

## 数据源连接器中的增强功能

2024.4.0 版本的数据源连接器具有以下增强功能：

### 连接到Salsify、Akeneo和Microsoft Azure DevOps Boards (ADO)数据源

除了现有的现成连接器之外，Experience Manager Guides 还为 Salsify、Akeneo 和 Microsoft Azure DevOps Boards (ADO) 数据源提供连接器。作为管理员，您可以下载并安装这些连接器。然后，配置已安装的连接器。

### 复制并粘贴示例查询以创建内容片段或主题

您可以轻松地在生成器中复制并粘贴样本数据查询，以创建内容片段或主题。有了这个功能，您无需再记忆语法或手动创建查询。您无需手动输入查询，而是可以复制并粘贴示例查询，对其进行编辑，然后使用它来根据您的要求获取数据。

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

## 使用新的用户首选项UI自定义您的Web编辑器体验

Web编辑器中的&#x200B;**用户首选项**&#x200B;对话框现在包含新的&#x200B;**外观**&#x200B;选项卡。 此新选项卡允许您在Web编辑器界面中方便地配置最常见的外观首选项。

您可以配置以按标题或文件名查看文件，并更改应用程序和源视图的主题。 它还有助于您配置设置，以便在存储库视图中查找打开的文件并处理不间断空格。

用户首选项的![外观选项卡](assets/user_preference_editor_appearance.png){width="550" align="left"}

*根据您的喜好自定义外观。*

在[左侧面板](../user-guide/web-editor-features.md#id2051EA0M0HS)部分中了解有关&#x200B;**用户首选项**&#x200B;功能说明的更多信息。

## 在Web编辑器的存储库视图中查找打开的文件

在&#x200B;**用户首选项**&#x200B;中选择&#x200B;**始终在存储库中查找文件**&#x200B;选项，以便在存储库视图中快速导航和查找文件。 您不必手动搜索它。

在编辑时，此功能还可帮助您轻松查看文件在存储库层次结构中的位置。

有关更多详细信息，请查看[在存储库视图](../user-guide/web-editor-edit-topics.md#locate-an-open-file-in-the-repository-view)中找到打开的文件。


## 改进了Web编辑器中不间断空格的处理

Experience Manager Guides允许您在Web编辑器中编辑文档时显示不间断空间指示器。 它还改进了不中断空间的处理。
它将多个连续的空格转换为单个空格，以在Web编辑器中保留文档的WYSIWYG视图。 此功能还有助于改进文档的整体外观和专业性。


有关详细信息，请查看Web编辑器的[其他功能](../user-guide/web-editor-other-features.md)。




## 在Adobe Experience Manager Assets上禁用选择性文件夹的后处理


作为管理员，您现在可以在Experience Manager Assets上为选择性文件夹禁用后处理和UUID生成。 此配置可能很有用，尤其是在处理许多资源或复杂的文件夹结构时。 它还有助于多个用户同时快速上传资产，而不会相互干扰。  

禁用文件夹的后处理也会影响其所有子文件夹。 但是，Experience Manager Guides现在支持选择性地为被忽略文件夹中的各个子文件夹启用后处理。

了解如何[禁用文件夹](../cs-install-guide/conf-folder-post-processing.md)的后处理。

## 在存储库视图中搜索和筛选文件的改进体验

现在，您在过滤文件时可以获得增强的体验。改进的文件过滤功能提供了一种能够更轻松地搜索和浏览文件的方法。


![在存储库视图中搜索文件](assets/repository-filter-search-2404.png){width="300" align="left"}

*搜索包含文本的文件`general purpose.`*

享受更快地访问相关文件和使用更直观的用户界面等益处，使您的搜索体验更加顺畅、高效。

![快速搜索筛选器](assets/repository-filter-search-quick.png) {width="300" align="left"}

*使用快速过滤器搜索 DITA 和非 DITA 文件。*

详细了解[左侧面板](../user-guide/web-editor-features.md#id2051EA0M0HS)部分中的&#x200B;**过滤搜索**&#x200B;功能。

## 用于根据元素的位置查看和插入有效元素的隔离列表

在Web编辑器中编辑文档时，您现在可以查看在当前位置以及在当前位置之外有效的元素的独立列表。 根据要求，您可以从以下选项中选择元素：

* **在当前位置**&#x200B;处可插入在当前光标位置本身的有效元素。
* **当前位置**&#x200B;之外的有效元素，您可以在元素层次结构中当前元素的任何父元素之后插入这些元素。

![插入元素对话框](assets/insert-element-dialog.png){width="300" align="left"}

*查看有效元素的隔离列表以在当前位置插入元素。*


此有效元素拆分列表可帮助您维护内容结构并遵循DITA标准。

了解有关[辅助工具栏](../user-guide/web-editor-features.md#2051ea0j0y4)部分中的&#x200B;**插入元素**&#x200B;功能的更多信息。


## 内容属性类型显示为下拉菜单

现在，内容属性&#x200B;**类型**&#x200B;显示为下拉菜单。 您可以查看并从下拉列表中为当前标记选择完整层次结构的标记。

此下拉菜单可帮助您快速访问层次结构中的相关标记。


内容属性中的![类型下拉菜单](assets/content-properties-type.png){width="300" align="left"}

*从层次结构中为当前标记选择一个标记。*

在[右侧面板](../user-guide/web-editor-features.md#id2051eb003yk)部分中了解有关&#x200B;**内容属性**&#x200B;功能的更多信息。



## 改进了从映射编辑器批量检查文件的性能

Experience Manager Guides改进了映射编辑器中批量文件签入功能的性能和体验。 这项改进可帮助您更快地批量签入文件。
您还可以从**另存为新版本和解锁**&#x200B;对话框中查看文件的签入操作的进度。 最后，在操作完成且所有选定的检出文件都已检入后，将显示成功消息。

![另存为新版本并解锁对话框](./assets/save-version-lock.png){width="300" align="left"}

*查看从映射编辑器批量签入的文件的列表和状态。*

了解如何[使用高级映射编辑器](../user-guide/map-editor-advanced-map-editor.md)

## 通过DITA-OT生成输出时下载临时文件

您还可以下载通过DITA-OT发布AEM Site、HTML、自定义、JSON或PDF输出时生成的临时文件。 此功能可帮助您分析输出生成过程中可能发生的任何问题并有效地进行故障排除。  
如果您选择了任何已传递到使用DITA-OT生成的输出的元数据属性，则也可以下载metadata.xml文件。 

有关预设的详细信息，请查看[了解输出预设](../user-guide/generate-output-understand-presets.md)。


## 使用IMS OAuth凭据替换IMS JWT凭据以进行基于微服务的发布


已弃用服务帐户(JWT)凭据，推荐使用&#x200B;**OAuth服务器到服务器**&#x200B;凭据。 使用服务帐户(JWT)凭据的应用程序将在2025年1月1日之后停止工作。 您必须在2025年1月1日之前迁移到新凭据，以确保您的应用程序继续运行。


Experience Manager Guides的云发布服务现在由基于Adobe IMS OAuth的身份验证来保护。 了解如何[使用OAuth身份验证](../knowledge-base/publishing/configure-microservices-imt-config.md)配置基于微服务的发布。
