---
title: 根据自定义模板创建映射
description: 了解如何创建自定义模板，使用它们创建新映射文件，并将定义的标题传递给AEM Guides中的DITA映射。
feature: Authoring, Map Editor
role: User
source-git-commit: 76c731c6a0e496b5b1237b9b9fb84adda8fa8a92
workflow-type: tm+mt
source-wordcount: '1103'
ht-degree: 0%

---

# 根据自定义模板创建映射 {#id225VF0808MP}

您可以创建自定义的映射模板，并使用它们创建DITA映射以及映射模板中引用的主题模板和映射模板

您可以从自定义的映射模板中引用其他映射模板和主题模板。 引用的映射模板可以引用各种映射模板、主题模板、主题、映射、图像、视频和其他资源。 自定义的映射模板可以帮助您非常轻松地复制映射模板和整个引用的文件夹结构。 这些自定义模板对于创建和重新创建具有递归结构和引用的多个映射特别有用。

>[!NOTE]
>
> 主题模板不是递归创建的。 只生成直接位于映射模板中的主题模板，而主题模板中的任何主题模板都只是在父项中直接引用。

## 创建自定义模板

AEM Guides允许您从dita-templates文件夹创建自定义映射和主题。 您可以使用这些自定义模板来创建映射和主题。 您还可以与作者共享这些模板，他们可以使用这些模板创建自己的文件。 使用这些模板，您可以允许作者保留模板文件夹中特定资源的单独副本。

>[!NOTE]
>
> 任何仅在中引用和维护的资源都必须保留在templates文件夹之外。


可通过以下方式创建映射和主题模板：
1. [左侧面板](./web-editor-features.md#left-panel-id2051ea0m0hs)的模板窗格
1. [Assets UI中的模板](#templates-assets-ui)
1. [“选项”菜单](#templates-in-assets-ui)

### Assets UI中的模板 {#templates-assets-ui}

**主题模板**

执行以下步骤可创建主题模板：

1. 在&#x200B;**Assets UI**&#x200B;中，导航到dita-templates文件夹。

   ![](images/dita-templates.png){width="800" align="left"}

1. 单击&#x200B;**主题**&#x200B;文件夹以将其打开。单击&#x200B;**创建\> DITA模板**。
1. 在Blueprint页面上，选择&#x200B;**主题**，然后单击&#x200B;**下一步。**
1. 在“属性”页面上，指定主题模板&#x200B;**标题**。
1. 指定文件&#x200B;**名称**

   >[!NOTE]
   >
   > 文件名必须具有.dita扩展名。

1. \（可选\）添加说明。
1. 单击&#x200B;**创建**。此时将显示主题模板创建消息。 然后，您可以打开主题模板并对其进行编辑。

**映射模板**

执行以下步骤可创建映射模板：

1. 在&#x200B;**Assets UI**&#x200B;中，导航到dita-templates文件夹。
1. 单击&#x200B;**映射**&#x200B;文件夹以将其打开。
1. 单击&#x200B;**创建\> DITA模板。**

   ![](images/create-dita-template.png){width="300" align="left"}

1. 在Blueprint页面上，选择&#x200B;**映射**&#x200B;并单击&#x200B;**下一步**。
1. 在“属性”页面上，指定映射模板&#x200B;**标题**。
1. 指定文件&#x200B;**名称**。

   >[!NOTE]
   >
   > 文件名必须具有.ditamap扩展名。

1. （可选\）添加说明。单击&#x200B;**创建**。 出现“map template created（已创建映射模板）”消息。 然后，您可以打开映射模板并对其进行编辑。 您可以在映射模板中添加对主题模板、映射模板以及其他资源的引用。

### “选项”菜单 {#options-menu}

要创建映射或主题模板，请执行以下步骤：

1. 选择当前模板文件夹中的&#x200B;**Map**&#x200B;或&#x200B;**Topic**&#x200B;文件夹。 例如，`dita-templates` 文件夹。
1. 从&#x200B;**选项**&#x200B;菜单中，选择&#x200B;**创建映射模板**&#x200B;或&#x200B;**创建主题模板**。

   将打开&#x200B;**创建新映射模板**&#x200B;或&#x200B;**创建新主题模板**&#x200B;对话框。
1. 输入新模板的标题和名称。
1. 从&#x200B;**模板**&#x200B;下拉列表中选择要创建的模板类型。

出现“map template created（已创建映射模板）”消息。 您可以将模板添加到全局或文件夹级别的配置文件中。 然后，新模板会出现在主题或映射创建过程中，您可以使用它来创建映射或主题。


管理员还可以创建一个文件夹，并将其配置为可在其中创建和保存模板的文件夹。

根据您的设置，了解如何配置自定义DITA模板文件夹路径：

+++ Cloud Service

了解如何在Cloud Service安装和配置指南中[配置自定义DITA模板文件夹路径](/help/product-guide/install-guide/conf-template-tags-custom-dita-topic-template.md#configure-custom-dita-template-folder-path-id191lcf0095z){target="_blank"}。

+++

+++ 内部部署软件

了解如何在On-premise Installation and Configuration指南中[配置自定义DITA模板文件夹路径](/help/product-guide/cs-install-guide/conf-template-tags-custom-dita-topic-template.md#configure-custom-dita-template-folder-path-id191lcf0095z)。

+++

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
> 映射模板必须配置并可由管理员进行创作。 有关更多详细信息，请参阅安装和配置Adobe Experience Manager Guidesas a Cloud Service中的&#x200B;*配置创作模板*&#x200B;部分。

执行以下步骤以使用自定义映射模板创建映射：

1. 在&#x200B;**Assets UI中，**&#x200B;导航到要创建映射的文件夹。
1. 单击&#x200B;**创建\> DITA映射**。
1. 在Blueprint页面上，选择要使用的映射模板并单击&#x200B;**下一步**。 例如，如果您已创建映射模板“test-template”，请选择它。
1. 在“属性”页面上，指定映射&#x200B;**标题**。
1. 指定文件&#x200B;**名称**。

   >[!NOTE]
   >
   > 文件名必须具有.ditamap扩展名。

1. 单击&#x200B;**创建**。此时将显示映射创建消息。


映射会生成在模板文件夹中引用的所有资源。 地图中引用的某些资源类型如下所示：

- 如果映射包含对主题模板的引用，则会在文件夹中创建主题模板的副本，其层次结构与`dita-templates`文件夹中主题文件夹中的层次结构相同。
- 如果映射包含对映射模板的引用，则会在文件夹中创建映射模板的副本，其层次结构与`dita-templates`文件夹中的映射文件夹相同。
- 如果映射包含对`dita-templates/topics`或`dita-templates/maps`文件夹外部的主题或映射的泛型引用，则仅引用该泛型引用，并且不创建任何副本。

  >[!NOTE]
  >
  > `dita-templates/topics`和`dita-templates/maps`是指南中的默认路径，可以对其进行配置。


  如果映射模板中有主题模板键定义，则会创建一个新键\（因此是新主题\），并在映射中引用该键。

- 如果在文件夹的同一级别创建另一个映射或主题，则新创建的资源的名称将附加0、1、2等。 您可以选择打开映射进行编辑，或将映射文件保存到存储库中。

**父主题：**[&#x200B;使用映射编辑器](map-editor.md)
