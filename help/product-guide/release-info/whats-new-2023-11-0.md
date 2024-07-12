---
title: 发行说明 | Adobe Experience Manager Guides的新增功能（2023年11月版）
description: 在2023年11月版的Adobe Experience Manager Guidesas a Cloud Service中了解新增功能和增强功能。
exl-id: 83c04e01-92f1-41b0-8866-a202f4106b51
feature: What's New
role: Leader
source-git-commit: 6d8c01f20f7b59fed92c404561b647d9ebecb050
workflow-type: tm+mt
source-wordcount: '803'
ht-degree: 0%

---

# 2023年11月版的Adobe Experience Manager Guidesas a Cloud Service的新增功能

本文介绍2023年11月版本的Adobe Experience Manager Guides(以后称为&#x200B;*Experience Manager Guidesas a Cloud Service*)中的新增功能和增强功能。

有关升级说明、兼容性矩阵以及此版本中修复的问题的更多详细信息，请查看[发行说明](release-notes-2023-11-0.md)。

## 本机PDF增强功能

2023年11月版本中完成了以下本机PDF增强功能：

### 使用和复制现成的PDF模板

Experience Manager Guides提供开箱即用或出厂预装PDF模板。 复制工厂PDF模板以创建自定义PDF模板。

现在，您还可以在创建和复制模板时预览模板的缩略图图像。 您还可以编辑或删除此图像。 此功能对于标记或区分具有相似名称的模板很有用。
了解有关[PDF模板](../native-pdf/pdf-template.md)的更多信息。

![复制PDF模板对话框](assets/duplicate-template.png){width="550" align="left"}

*复制现有PDF模板。*


### 更改页面的顺序并发布每张页面的多个页面

除了根据源文档发布页面外，您还可以在发布多页文档时更改PDF中的页面顺序。  这让您能够灵活地按各种顺序发布页面，例如先发布所有奇数页面，或先发布所有偶数页面。 您还可以以小册子的形式发布，并像读书一样阅读页面。 您还可以决定要在单张纸上发布的页数。 有关更多详细信息，请查看[页面组织](../native-pdf/components-pdf-template.md#page-organization)部分。

### 根据排序键对术语进行排序

现在，您还可以根据排序键对术语表进行排序。 您可以使用标记“sort-as”来定义术语的排序键。 然后，您可以根据排序键来排序它们，而不是术语。 这允许您根据不同语言中使用的术语对术语表术语进行排序。 您还可以为具有短语或一组单词的术语定义单个排序键。
有关详细信息，请查看[高级PDF设置](../native-pdf/components-pdf-template.md#advanced-pdf-settings)。


### 改进了本机PDF模板的资源管理

Experience Manager Guides现在改进了本机PDF模板的资源管理。 您现在可以在多个本机PDF模板之间共享和重用资源，如图像、CSS文件和字体文件。 通过这种改进，管理大量模板的资源变得更加简单。 您无需为每个模板创建重复资源，可以将这些资源保存在共享文件夹中，并在所有本机PDF模板中使用它们。
有关详细信息，请查看[PDF模板](../native-pdf/pdf-template.md)。

## Web编辑器增强功能

2023年11月版本中完成了以下Web编辑器增强功能：


### 按标题或文件名查看文件

现在，您可以选择在Web编辑器中查看文件的默认方式。 您可以在“创作”视图中按各个面板的标题或文件名查看文件列表。

![用户首选项对话框](assets/user-preferences-2311.png){width="550" align="left"}

*从&#x200B;**用户首选项**对话框更改查看文件的默认方式。*


### 管理条件预设

您可以在DITA主题中定义条件属性。 然后，使用条件预设中的条件属性发布DITA映射中的内容。 Experience Manager Guides现在还允许您从Web编辑器创建和管理条件预设。 您还可以轻松地编辑、复制或删除它们。

Web编辑器](assets/web-editor-manage-condition-presets.png){width="550" align="left"}的“管理”选项卡中的![条件预设

有关详细信息，请查看[使用条件预设](../user-guide/generate-output-use-condition-presets.md)。

### 刷新浏览器时恢复文件选项卡

在刷新浏览器时，Experience Manager Guides将恢复Web编辑器中打开的文件选项卡的状态。 有关更多详细信息，请在Web编辑器中的[编辑主题](../user-guide/web-editor-edit-topics.md)下查看&#x200B;**在编辑文件时刷新浏览器**&#x200B;部分。

### 轻松展开元素

现在，您可以使用Web编辑器中元素上下文菜单中的选项轻松展开元素。 这有助于轻松地将元素的文本与其父元素合并。
有关更多详细信息，请在Web编辑器中查看[其他功能中的&#x200B;**取消包裹元素**&#x200B;部分](../user-guide/web-editor-other-features.md)。

### 用于移动光标的键盘快捷键

Experience Manager Guides现在还允许您使用键盘快捷键在Web编辑器中移动光标。 您可以使用键盘快捷键快速左右移动一个单词。 您还可以在键盘快捷键的帮助下移动到行的开头或结尾。
现在，您还可以使用键盘快捷键将光标移动到下一个元素的开头或上一个元素的结尾。
了解有关Web编辑器中的[键盘快捷键](../user-guide/web-editor-keyboard-shortcuts.md)的详细信息。
