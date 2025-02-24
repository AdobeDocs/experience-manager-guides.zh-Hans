---
title: 根据自定义模板创建映射
description: 了解如何创建自定义模板，使用它们创建新映射文件，并将定义的标题传递给Experience Manager Guides中的DITA映射。
exl-id: 9cb0035f-bf81-4ab5-a575-53851bbff494
feature: Authoring, Map Editor
role: User
source-git-commit: 594e348fc1188e66cf2f4648702ed2b17f1f8f33
workflow-type: tm+mt
source-wordcount: '1541'
ht-degree: 0%

---

# 根据自定义模板创建映射 {#id225VF0808MP}

您可以创建自定义的映射模板，并使用它们创建DITA映射以及映射模板中引用的主题模板和映射模板

您可以从自定义的映射模板中引用其他映射模板和主题模板。 引用的映射模板可以引用各种映射模板、主题模板、主题、映射、图像、视频和其他资源。 自定义的映射模板可以帮助您非常轻松地复制映射模板和整个引用的文件夹结构。 这些自定义模板对于创建和重新创建具有递归结构和引用的多个映射特别有用。

>[!NOTE]
>
> 主题模板不是递归创建的。 只生成直接位于映射模板中的主题模板，而主题模板中的任何主题模板都只是在父项中直接引用。

## 创建自定义模板

Adobe Experience Manager Guides允许您从dita-templates文件夹创建自定义映射和主题。 您可以使用这些自定义模板来创建映射和主题。 您还可以与作者共享这些模板，他们可以使用这些模板创建自己的文件。 使用这些模板，您可以允许作者保留模板文件夹中特定资源的单独副本。

>[!NOTE]
>
> 任何仅在中引用和维护的资源都必须保留在templates文件夹之外。


可通过以下方式创建映射和主题模板：
- [从编辑器创建自定义模板](#create-customized-templates-from-the-editor)
- [从Assets UI创建自定义模板](#create-customized-templates-from-the-assets-ui)


### 从编辑器创建自定义模板

**模板**&#x200B;功能在编辑器](./web-editor-features.md#left-panel)界面的[左侧面板中存在，并且仅对管理员可用。 使用此面板，管理员可以轻松创建和管理随后可供作者使用的模板。 默认情况下，模板在&#x200B;*映射*&#x200B;和&#x200B;*主题*&#x200B;类型模板下分类。

![](images/templates-panel_cs.png){width="300" align="left"}

默认情况下，您可以按标题查看文件。 当您将鼠标悬停在模板上时，可以像工具提示一样查看文件标题和文件名。

>[!NOTE]
>
> 作为管理员，您还可以选择在编辑器中查看文件列表。 在&#x200B;**用户首选项**&#x200B;中选择&#x200B;**编辑器文件显示配置**&#x200B;节的&#x200B;**文件名**&#x200B;选项。

执行以下步骤以从编辑器创建主题或映射模板：

1. 在编辑器中打开&#x200B;**模板**&#x200B;面板，然后选择&#x200B;**创建DITA模板**&#x200B;图标。

   ![](images/create-dita-template-option.png){width="500" align="left"}

1. 根据要创建的模板类型，从下拉菜单中选择&#x200B;**主题模板**&#x200B;或&#x200B;**映射模板**。
1. 如果选择&#x200B;**主题模板**，则会显示&#x200B;**新建主题模板**&#x200B;对话框。

   ![](images/new-topic-template-dialog.png){width="300" align="left"}

   如果选择&#x200B;**映射模板**，则会显示&#x200B;**新建映射模板**&#x200B;对话框。

   ![](images/map-template-dialog.png){width="300" align="left"}

   如果要先在&#x200B;**主题**&#x200B;或&#x200B;**映射**&#x200B;文件夹内创建文件夹，则还可以从下拉列表中选择&#x200B;**文件夹**。

1. 在&#x200B;**新主题模板**/**新映射模板**&#x200B;对话框中，提供出现在&#x200B;**模板**&#x200B;面板中的&#x200B;**标题**。 根据标题自动建议模板的&#x200B;**名称**，但您可以提供其他文件名。
另外，从**模板**&#x200B;下拉列表中选择要创建的模板类型。

   >[!NOTE]
   >
   > 如果管理员启用了基于UUID设置的自动文件名，则您将不会查看名称字段。

1. 选择&#x200B;**创建**。

创建模板后，您需要将其添加到全局或文件夹级别的配置文件。 添加模板后，您的作者将在主题/地图创建过程中开始查看新模板。

使用现有模板上的&#x200B;**选项**&#x200B;菜单，您可以选择&#x200B;**编辑**&#x200B;或&#x200B;**复制**。 如果出现重复，将保留模板的结构及类型\(document\)，您可以重复使用它以从中创建另一个模板。

![](images/template-options-menu-editor.png){width="500" align="left"}

### 从Assets UI创建自定义模板

执行以下步骤，从Assets UI创建映射或主题模板：

1. 在&#x200B;**Assets UI**&#x200B;中，导航到dita-templates文件夹。

   ![](images/dita-templates.png){width="800" align="left"}

1. 如果要创建&#x200B;**主题**&#x200B;模板，请打开&#x200B;**主题**&#x200B;文件夹。 如果要创建&#x200B;**映射**&#x200B;模板，请打开&#x200B;**映射**&#x200B;文件夹。
1. 选择&#x200B;**创建\> DITA模板**。

   ![](images/create-dita-template.png){width="300" align="left"}
1. 在Blueprint页面上，选择&#x200B;**主题\>下一步**&#x200B;以创建主题模板。 否则，选择&#x200B;**映射\>下一步**&#x200B;以创建映射模板。
1. 在“属性”页面上，指定模板&#x200B;**标题**。
1. 指定文件&#x200B;**名称**。

   >[!NOTE]
   >
   > 文件名必须具有.dita扩展名。

1. \（可选\）添加说明。
1. 选择&#x200B;**创建**。

   此时将显示主题模板创建消息。 然后，您可以打开模板并对其进行编辑。 对于映射模板，还可以在映射模板中添加对主题模板、映射模板以及其他资源的引用。


Assets UI中的&#x200B;**选项菜单**

要使用Assets UI中的选项菜单创建映射或主题模板，请执行以下步骤：

1. 选择当前模板文件夹中的&#x200B;**Map**&#x200B;或&#x200B;**Topic**&#x200B;文件夹。 例如，`dita-templates` 文件夹。
1. 从&#x200B;**选项**&#x200B;菜单中，选择&#x200B;**创建映射模板**&#x200B;或&#x200B;**创建主题模板**。

   将打开&#x200B;**创建新映射模板**&#x200B;或&#x200B;**创建新主题模板**&#x200B;对话框。
1. 输入新模板的标题和名称。
1. 从&#x200B;**模板**&#x200B;下拉列表中选择要创建的模板类型。

出现“map template created（已创建映射模板）”消息。 您可以将模板添加到全局或文件夹级别的配置文件中。 然后，新模板会出现在主题或映射创建过程中，您可以使用它来创建映射或主题。

管理员还可以创建一个文件夹，并将其配置为可在其中创建和保存模板的文件夹。

根据您的设置，了解如何配置自定义DITA模板文件夹路径：
<details>
    <summary> Cloud Service </summary>

了解如何在Cloud Services安装和配置指南中[配置自定义DITA模板文件夹路径](../install-guide/conf-template-tags-custom-dita-topic-template.md#configure-custom-dita-template-folder-path-id191lcf0095z)。
</details>

<details>
    <summary> 内部部署软件</summary>

了解如何在On-premise Installation and Configuration指南中[配置自定义DITA模板文件夹路径](../cs-install-guide/conf-template-tags-custom-dita-topic-template.md#configure-custom-dita-template-folder-path-id191lcf0095z)。
</details>

## 传递模板中定义的标题

如果要将模板内使用的主题或映射的标题传递到使用该模板创建的DITA映射，请在标题周围使用大括号。

示例

```XML
<pubtitle>
   <mainpubtitle outputclass="booktitle">
   {title}
   </mainpubtitle>
   <subtitle>Subtitle</subtitle>
</pubtitle>

The resultant DITA map with title "Rootmap1" will look like as follows:
<pubtitle>
   <mainpubtitle outputclass="booktitle">Rootmap1
   </mainpubtitle>
   <subtitle>Subtitle</subtitle>
</pubtitle>
```

>[!NOTE]
> 只有第一个出现的花括号会被替换为标题。

如果您不在标题周围使用大括号，则仅会选取生成的DITA映射的第一个元素，并且不会从模板中选取标题的嵌套，其将如下所示：

```XML
<pubtitle> Rootmap1 </pubtitle>
```

>[!NOTE]
> 也可以使用文本周围的大括号将其嵌套结构从自定义模板传递到DITA映射。

示例

```XML
<title>    
    <sub>        
        <b>{title}</b>    
    </sub>
</title>
```

## 使用映射模板创建新映射

>[!NOTE]
>
> 映射模板必须配置并可由管理员进行创作。 有关更多详细信息，请参阅安装和配置Adobe Experience Manager Guides as a Cloud Service中的&#x200B;*配置创作模板*&#x200B;部分。

在&#x200B;**编辑器**&#x200B;中，执行以下步骤以使用自定义映射模板创建映射：

1. 在&#x200B;**编辑器**&#x200B;中，导航到要创建映射的文件夹。
1. 从文件夹的“选项”菜单中，选择&#x200B;**新建\> DITA映射**。

   ![](images/add-custom-template-dita-map.png){width="500" align="left"}
1. 显示&#x200B;**新建映射**&#x200B;对话框。
1. 在&#x200B;**新建映射**&#x200B;对话框中，指定映射&#x200B;**标题**，文件&#x200B;**名称**，然后选择要使用的映射模板。

   例如，如果您已创建映射模板“test-template”，请选择它。

1. 选择&#x200B;**创建**。

   此时将显示映射创建消息。

在&#x200B;**Assets UI**&#x200B;中，执行以下步骤以使用自定义映射模板创建映射：

1. 在&#x200B;**Assets UI中，**&#x200B;导航到要创建映射的文件夹。
1. 选择&#x200B;**创建\> DITA映射**。
1. 在Blueprint页面上，选择要使用的映射模板并选择&#x200B;**下一步**。 例如，如果您已创建映射模板“test-template”，请选择它。
1. 在“属性”页面上，指定映射&#x200B;**标题**。
1. 指定文件&#x200B;**名称**。

   >[!NOTE]
   >
   > 文件名必须具有.ditamap扩展名。

1. 选择&#x200B;**创建**。此时将显示映射创建消息。

## 有关使用自定义模板创建的DITA映射的附加说明


映射会生成在模板文件夹中引用的所有资源。 地图中引用的某些资源类型如下所示：

- 如果映射包含对主题模板的引用，则会在文件夹中创建主题模板的副本，其层次结构与`dita-templates`文件夹中主题文件夹中的层次结构相同。
- 如果映射包含对映射模板的引用，则会在文件夹中创建映射模板的副本，其层次结构与`dita-templates`文件夹中的映射文件夹相同。
- 如果映射包含对`dita-templates/topics`或`dita-templates/maps`文件夹外部的主题或映射的泛型引用，则仅引用该泛型引用，并且不创建任何副本。

  >[!NOTE]
  >
  > `dita-templates/topics`和`dita-templates/maps`是指南中的默认路径，可以对其进行配置。


  如果映射模板中有主题模板键定义，则会创建一个新键\（因此是新主题\），并在映射中引用该键。

- 如果在文件夹的同一级别创建另一个映射或主题，则新创建的资源的名称将附加0、1、2等。 您可以选择打开映射进行编辑，或将映射文件保存到存储库中。

**父主题：**[&#x200B;映射编辑器简介](map-editor.md)
