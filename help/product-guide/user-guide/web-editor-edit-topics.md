---
title: 在编辑器中编辑主题
description: 了解如何在编辑器中编辑主题。 了解各种编辑功能，以便在AEM Guides中修改主题文件。
exl-id: 8da37a81-e8c3-434f-b3f4-4723d87c2ade
feature: Authoring, Web Editor
role: User
TQID: https://experienceleague.adobe.com/Ln0JE2F8klsmIZJqtpy3Idi3VHdh1U900sfMrD0xpEU
product_v2: id: fae5e35a-80c9-4b94-9352-1a060a6aab1did: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2: id: ab01a588-7dea-43f2-a699-0b3f128465d6
subfeature_v2: id: ad602516-aca3-4247-9ae8-f393d958efa9id: f89f75b0-cf2e-4e96-aec8-fe8c39cbd0ef
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554
source-git-commit: 8ed5c9cb07c56b84b36ef56a55af8738989a6d3f
workflow-type: tm+mt
source-wordcount: 1409
ht-degree: 0%

---

# 在编辑器中编辑主题 {#id2056B040VUI}

>[!INFO]
>
>本主题适用于新编辑器和旧编辑器。 虽然核心功能保持一致，但内容中使用适用的选项卡和标注，指出用户界面、术语和交互中的差异。

该编辑器附带了一系列编辑功能，可让您轻松创建或修改主题文件。 概括地说，您可以执行以下步骤以在编辑器中编辑主题。

>[!IMPORTANT]
>
> 如果在使用编辑器时遇到应用程序错误，请刷新页面以继续工作。

>[!BEGINTABS]

>[!TAB 新编辑器]

1. 要在主题中编辑或插入元素，请单击所需元素的文本边界以进行更改，或将光标置于要添加新元素的元素末尾，然后从工具栏中选择所需元素（或按Alt+1打开“插入元素”弹出窗口），这会在主题中智能地仅列出和插入该位置的有效元素。

1. 此外，可以使用“快速插入”菜单在光标位置处方便地插入允许的元素。 选择&#x200B;**Control + /** for Windows或&#x200B;**Command + /** for Mac以访问这些元素。

   ![快速插入菜单](./images/quick-insert-menu-in-editor.png){width="650"}

   使用“快速插入”菜单搜索新元素或从收藏夹中选择一个元素，然后将其插入到当前光标位置。 收藏夹包括最常用的元素，并且只显示对当前光标位置有效的元素。 您可以通过[编辑器设置](./config-editor-settings.md)中的“快速插入”菜单来启用或禁用此功能并配置收藏夹元素以进行插入。


>[!TAB 旧编辑器]

1. 要在主题中进行更改，请单击所需元素的文本边界并开始进行编辑。

1. 要插入特定元素，请将光标移动到要在其后插入新元素的元素的元素末尾，然后在工具栏中选择所需的元素图标。 您还可以使用键盘快捷键`Alt+1`调用&#x200B;**插入元素**&#x200B;弹出窗口。

   将显示可用于主题中的元素列表。 Experience Manager Guides会根据元素在主题中的有效位置对其进行智能放置。

   >[!NOTE]
   >
   > 您还可以通过配置位于 — `/etc/designs/fmdita/clientlibs/xmleditor/`的`ui_config.json`文件来选择要在工具栏中显示的图标。 有关自定义功能的详细信息，请与系统管理员联系。

1. 编辑完文档后，选择&#x200B;**全部保存**。

   >[!NOTE]
   >
   > 如果不希望将更改提交到Adobe Experience Manager存储库，请选择&#x200B;**关闭**，然后在“未保存的更改”对话框中选择&#x200B;**关闭而不保存**。

>[!ENDTABS]

## 跨元素的部分内容选择

Experience Manager Guides还允许您跨元素选择内容。 选择内容后，您可以执行以下操作：

- 格式化：与编辑器1.0相比，在新编辑器中格式化选定内容要容易得多，如下图所示。

>[!BEGINTABS]

>[!TAB 新编辑器]

您可以使用上下文工具栏将选定内容设置为粗体、斜体或下划线格式。 选择内容，然后在显示的菜单中单击相应的格式设置图标。 将所选内容变为粗体、斜体或下划线。 然后，将合并有效开放标记中的内容，并将其显示在单个元素下。

![格式化选项](./images/formatting-options.png){width="650"}

>[!TAB 旧编辑器]

将所选内容变为粗体、斜体，并将所选内容加下划线。 然后，将合并有效开放标记中的内容，并将其显示在单个元素下。 例如，您可以选择段落中的内容并将所选内容扩展到另一个段落。 然后，如果您将选定内容变为粗体，则会合并开放标记中的所有粗体内容，并显示在单个段落元素下。

>[!ENDTABS]

- 删除：如果删除选定内容，则合并开放标记中删除后的剩余内容。

- 使用有效元素括起内容：执行以下步骤以使用有效元素括起内容：

   - 选择元素中的内容。
   - 从顶部的工具栏中选择![添加](images/Add_icon.svg)图标以查看&#x200B;**插入元素**&#x200B;对话框。 该对话框列出了选定内容的有效元素。

     >[!NOTE]
     >
     > 您还可以通过选择所选内容的上下文菜单来查看“插入元素”对话框。

   - 从对话框中选择元素。 选定的内容将封装在该元素下。 例如，如果您在段落中选择内容，然后从&#x200B;**插入元素**&#x200B;对话框中选择`<note>`元素，则所选内容将显示在注释下。

     ![插入元素对话框](./images/insert-element-editor.png) {width="300"}

## 编辑文件时刷新浏览器

Experience Manager Guides支持您在编辑器中编辑内容时刷新浏览器。 此功能可帮助您继续编辑内容，以防您在工作时遇到应用程序错误。 如果在打开一个或多个具有未保存更改的文件进行编辑时点击浏览器刷新，系统会警告您未保存的更改可能会丢失。 您可以选择取消刷新操作并保存文件以保留更改。

即使刷新浏览器时，编辑器中也会保留左侧和右侧面板的视图。 当您刷新浏览器时，Experience Manager Guides将恢复编辑器中打开的文件上次保存的状态。 例如，在“存储库”面板中打开的文件将再次打开。 映射面板与先前打开的映射一起保留。

活动主题或DITA映射将在内容编辑区域中重新打开。

右侧面板也会重新打开，并显示与刷新之前相同的视图。

## 工作副本指示器

Experience Manager Guides提供工作副本指示器，用于显示文件的当前\（工作副本\）是否与保存的版本同步。 如果您对当前副本进行了任何更改并且尚未保存文件，则会在主题的文件选项卡上显示一个\*标记以及标题。 此指示器用于提醒您保存所做的更改，并在保存文件时消失。

>[!BEGINTABS]

>[!TAB 新编辑器]

此视图显示内容在新编辑器中的呈现方式。

![工作副本指示器](images/working-copy-text-update-indicator-new-editor-2-0.png){width="550"}

>[!TAB 旧编辑器]

此视图显示内容在旧编辑器中呈现的方式。

![工作副本指示器](images/working-copy-text-update-indicator.png){width="550"}

>[!ENDTABS]

Experience Manager Guides还指示文件的最后保存的\(working\)副本是否与保存的版本同步。 如果在工作副本和上次保存的版本之间有一些未保存的更改，则会在主题文件选项卡右上角显示一个\*标记以及版本信息。 此指示器用于提醒您保存并从文件的当前\(working\)副本创建版本。

>[!NOTE]
>
> 对[文件属性](./web-editor-right-panel.md#file-properties)下可用或在后端应用的元数据字段的任何更改也会在文档版本上触发星号`(*)`。  要防止系统生成的元数据更新影响此指示器，管理员可以为元数据属性配置忽略列表。 有关如何配置元数据属性的详细信息，请查看[配置元数据属性的忽略列表](../install-conf-guide/conf-metadata-prop.md)。

>[!BEGINTABS]

>[!TAB 新编辑器]

![版本更新指示器](images/version-update-indicator-editor-2-0.png){width="650"}

>[!TAB 旧编辑器]

![版本更新指示器](images/version-update-indicator.png){width="650"}


>[!ENDTABS]

## 在创作和Source模式下访问锁定的文件

当DITA或Markdown文件被其他用户锁定或检出时，无法编辑或修改内容。 但是，除&#x200B;**预览**&#x200B;模式外，您仍然可以在&#x200B;**创作**&#x200B;和&#x200B;**Source**&#x200B;模式下以只读格式查看文件。

在只读模式下，您可以查看&#x200B;**创作**&#x200B;或&#x200B;**Source**&#x200B;模式中的内容、标记和属性。 您还可以修改文件属性。

>[!NOTE]
>
> 作为管理员，您可以访问&#x200B;**强制解锁**&#x200B;功能，该功能允许您解锁被其他人锁定的文件。

<!-- This is no more available -->
<!--
The toolbar displays the following icons for read-only access:

- Toggle Tags view
- Version History
- Version Label

Experience Manager Guides also displays a **Read only access** indicator near the version number.
 
![view read only file in author mode](images/locked-file-editor.png)

You can access the **Layout** view for read-only DITA maps. This view lets you see the DITA map and its properties but prevents edits.

>[!NOTE]
>
> Your folder-level administrative users must update *ui_config.json* so that you can harmoniously access the read-only files in the  Author, Source, and Layout modes.

 -->

## 在资源管理器中找到打开的文件

在编辑器中打开文件时，Experience Manager Guides提供在资源管理器中查找文件的功能。 例如，在编辑当前主题时，它会找到该主题。

您可以关闭此功能以通过&#x200B;**用户首选项**&#x200B;的&#x200B;**外观**&#x200B;选项卡中的&#x200B;**始终在资源管理器**&#x200B;中查找文件选项来查找文件。

>[!NOTE]
>
>从2025.11.0版本开始，**始终查找存储库中的文件**&#x200B;设置重命名为&#x200B;**始终查找资源管理器中的文件**。 对于内部部署设置，在Experience Manager Guides 5.1版发布之前，它将继续在存储库中作为始终定位文件提供。

**父主题：**[&#x200B;使用编辑器](web-editor.md)
