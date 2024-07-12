---
title: 用于创作内容的AI支持的智能建议
description: 了解如何在Web编辑器中查看和利用AI支持的智能建议。
exl-id: 23c5285e-0d4f-484a-a062-fe1ba1608b8d
source-git-commit: 75425d82ee55485503ea6678030c5e919e50a691
workflow-type: tm+mt
source-wordcount: '789'
ht-degree: 0%

---

# 用于创作内容的AI支持的智能建议

Experience Manager Guides提供了&#x200B;**智能建议**&#x200B;功能，可帮助您创建一致且准确的内容。

在您创作内容时，**智能建议**&#x200B;功能可以使用AI进行搜索并显示语义上与您的内容类似的现有内容。 然后，您可以选择要在当前主题中包含的最佳匹配内容作为引用。

这可帮助您重用文档存储库中的现有内容并创建一致的内容。 例如，您正在创建的文档包含有关&#x200B;**Adobe Firefly**&#x200B;的信息，其中包括有关&#x200B;**Adobe**&#x200B;的段落。 在这种情况下，您可以快速查看和添加来自其他主题(如&#x200B;**Adobe Photoshop**)的内容引用，该主题包含相同的段落。





在Web编辑器中打开主题时，**智能建议**&#x200B;面板将显示在右侧。

>[!NOTE]
>
> 您的管理员必须配置&#x200B;**智能建议**&#x200B;功能。 有关更多详细信息，请查看Cloud Service的《安装和配置指南》中的[为创作配置AI支持的智能建议](../cs-install-guide/conf-smart-suggestions.md)部分。

![智能建议面板](images/smart-suggestions-panel.png){width="300" align="left"}

*查看&#x200B;**智能建议**面板。*

执行以下步骤，查看有关向主题添加相应内容引用的智能建议：

1. 选择&#x200B;**智能建议** ![智能建议图标](images/smart-suggestions-icon.svg)以打开面板。



   >[!NOTE]
   >
   > 在[全局或文件夹级别配置文件](../cs-install-guide/conf-folder-level.md#conf-ai-smart-suggestions)中，管理员需要定义要索引的文件或文件夹以获取智能建议，需要输入的最小字符数以及可在列表中查看的最大建议数。

1. 在主题中键入内容以查看相关建议。 确保内容的字符长度超过管理员在文件夹配置文件中为显示内容建议而设置的长度。

1. 选择&#x200B;**当前标记的建议** ![智能建议当前标记图标](images/smart-suggestions-current-tag-icon.svg)以查看您放置鼠标指针的当前标记的创作建议。  根据当前标记中的内容，显示从索引文件中查看和添加内容引用的建议。

   键盘快捷键： **Windows** (*Ctrl* + *K*)、**macOS** (*Command* + *K*)
1. 选择&#x200B;**完整文档的建议** ![智能建议完整文档图标](images/smart-suggestions-complete-document-icon.svg)以根据完整文档中存在的内容查看建议。  智能建议![智能建议图标](images/smart-suggestions-complete-document-icon.svg)图标显示在找到合适匹配项的内容旁边。

   键盘快捷键： **Windows** (*Ctrl* + *Shift* + *K* )、**macOS** (*Command* + *Shift* + *K* )

   >[!NOTE]
   >
   > 您只能查看有关当前视区（屏幕上显示的内容）的建议。 要查看文档中任何其他内容的建议，请向上或向下滚动以在视区中显示该内容，然后选择![智能建议图标](images/smart-suggestions-complete-document-icon.svg)图标。

1. 选择您添加到文档的标记旁边的&#x200B;**智能建议** ![智能建议图标](images/smart-suggestions-complete-document-icon.svg)图标以查看智能建议。
1. 您可以在&#x200B;**内容重用**&#x200B;建议框中查看智能建议。  Experience Manager Guides为完全匹配具有相同含义的内容和内容提供了建议。 例如，您可以搜索包含确切版本号的主题，如“发行版本2023.03.12”。 您还可以搜索“Adobe的总部在加利福尼亚州的圣何塞”，并找到类似“圣何塞拥有像Adobe这样的许多软件公司的季度”的内容。
1. 选择&#x200B;**内容信息** ![内容信息](images/smart-suggestions-content-info-icon.svg)以查看详细信息。
   ![内容信息面板](images/smart-suggestions-content-information.png){width="300" align="left"}

   *查看有关内容引用的详细信息。*

   1. 包含内容引用的主题的标题显示为超链接。
   1. 包含内容引用的文件的路径。
   1. 引用了内容的引用类型。
   1. 引用主题的DITA文件的名称显示为超链接。
1. 选择&#x200B;**建议的内容预览** ![智能建议预览图标](images/smart-suggestions-preview-icon.svg)以将当前内容与建议的内容进行比较。 这有助于您比较差异，并确定您是要为建议的内容添加内容引用并使它保持一致，还是要保留当前内容。

   ![建议的内容预览](images/smart-suggestions-suggested-content-preview.png){width="800" align="left"}

   *预览当前内容与建议内容之间的比较。*

1. 单击&#x200B;**接受**&#x200B;在&#x200B;**建议的内容预览**&#x200B;对话框中添加建议的内容引用。
1. 您还可以在&#x200B;**内容重用**&#x200B;建议框中选择&#x200B;**接受**&#x200B;或&#x200B;**拒绝**&#x200B;以获取相应的建议。


此智能功能非常方便，最大程度地减少了手动内容搜索的工作量，让您能够将更多精力集中在生成新内容上。 它还有助于更好地进行团队协作，并帮助保持由不同作者创建的内容的一致性。

>[!NOTE]
>
>智能建议不会保留当前会话之外的数据。 对于响应，智能建议仅依赖于基于内部数据库中驻留的内容创建的索引。 不使用外部AI工具，确保您的数据保留在系统中。
