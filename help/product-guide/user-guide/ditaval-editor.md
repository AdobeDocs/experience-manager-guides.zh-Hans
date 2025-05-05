---
title: 使用DITAVAL编辑器
description: 了解如何使用Adobe Experience Manager Guides中的DIVATAL编辑器创建和编辑DITAVAL文件。 了解DITAVAL编辑器如何在创作视图和源视图中支持DITAVAL文件。
exl-id: f3901a4f-1925-42aa-b773-0d6f18175ce8
feature: Authoring, DITAVAL Editor
role: User
source-git-commit: ac83f613d87547fc7f6a18070545e40ad4963616
workflow-type: tm+mt
source-wordcount: '1039'
ht-degree: 0%

---

# DITAVAL编辑器 {#ditaval-editor}

DITAVAL文件用于生成条件输出。 在单个主题中，您可以使用元素属性添加条件以条件化内容。 然后，创建一个DITAVAL文件，在该文件中指定应选取以生成内容的条件，以及应从最终输出中排除哪些条件。

Adobe Experience Manager Guides允许您使用DITAVAL编辑器轻松创建和编辑DITAVAL文件。 DITAVAL编辑器将检索系统中定义的属性\（或标记\），您可以使用它们来创建或编辑DITAVAL文件。 有关在Adobe Experience Manager中创建和管理标记的更多详细信息，请查看Adobe Experience Manager文档中的[管理标记](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/sites/authoring/features/tags.html?lang=zh-Hans)部分。

以下各节介绍了Experience Manager Guides中可用于DITAVAL文件的选项。

- [创建DITAVAL文件](#create-ditaval-file)
- [编辑DITAVAL文件](#edit-ditaval-file)
- [DITAVAl文件编辑器视图](#ditaval-editor-views)
- [在Assets UI中使用DITAVAL文件](#working-with-ditaval-files-in-the-assets-ui)

## 创建DITAVAL文件

执行以下步骤以创建DITAVAL文件：

1. 在“存储库”面板中，选择&#x200B;**新建文件**&#x200B;图标，然后从下拉菜单中选择&#x200B;**主题**。

   ![](images/new-file-option.png){align="left"}

   您还可以从[Experience Manager Guides主页](./intro-home-page.md)以及存储库视图中文件夹的选项菜单访问此选项。

2. 显示&#x200B;**新建主题**&#x200B;对话框。

3. 在&#x200B;**新建主题**&#x200B;对话框中，提供以下详细信息：
   - 主题的标题。
   - \（可选\）*主题的文件名。 根据主题“标题”自动建议文件名。 如果管理员启用了基于UUID设置的自动文件名，则您将不会查看名称字段。
   - 主题所基于的模板。 对于DITAVAL文件，请从下拉列表中选择&#x200B;**Ditaval**。
   - 要保存主题文件的路径。 默认情况下，存储库中当前选定文件夹的路径将显示在路径字段中。

   ![](images/new-topic-dialog-ditaval.png){width="300" align="left"}


4. 选择&#x200B;**创建**。

该主题在指定的路径中创建。 此外，该主题将在编辑器中打开以进行编辑。

![](images/ditaval-file-editor.png){align="left"}

## 编辑DITAVAL文件

创建DITAVAL主题时，将在编辑器中打开该主题以进行编辑。 要编辑现有的DITAVAL主题，请导航到DITAVAL主题所在的文件夹或映射，然后从&#x200B;**选项**&#x200B;菜单中选择&#x200B;**编辑**。

DITAVAL编辑器允许您执行以下任务：

- 切换左侧面板

  切换左侧面板视图。 如果您已通过DITA映射打开DITAVAL文件，则映射和存储库将显示在此面板中。 有关通过DITA映射打开文件的详细信息，请查看[通过DITA映射编辑主题](map-editor-advanced-map-editor.md#id17ACJ0F0FHS)。

- 保存

  保存您在文件中进行的更改。 所有更改都保存在文件的当前版本中。

- 添加属性

  在DITAVAL文件中添加单个属性。

  ![](images/ditaval-editor-props-new.png)

  第一个下拉列表列出了可以在DITAVAL文件中使用的允许DITA属性。 有五个受支持的属性 — `audience`、`platform`、`product`、`props`和`otherprops`。

  第二个下拉列表显示为所选属性配置的值。 然后，下一个下拉列表显示了您可以对选定属性配置的操作。 操作下拉列表中允许的值是 — `include`、`exclude`、`passthrough`和`flag`。 有关这些值的详细信息，请查看OASIS DITA文档中[prop](http://docs.oasis-open.org/dita/dita/v1.3/errata01/os/complete/part3-all-inclusive/langRef/ditaval/ditaval-prop.html#ditaval-prop)元素的定义

- 添加所有属性

  如果要通过单击添加系统中定义的所有条件属性或属性，请使用“添加全部属性”功能。

  >[!NOTE]
  >
  > 如果DITAVAL文件中已存在所有已定义的条件属性，则无法添加更多属性。 在这种情况下，您会收到一条错误消息。

  ![](images/ditaval-all-props-new.png)

编辑完DITAVAL文件后，选择&#x200B;**保存**。

>[!NOTE]
>
> 如果关闭文件而不保存，更改将丢失。 如果不希望将更改提交到Adobe Experience Manager存储库，请选择&#x200B;**关闭**，然后在&#x200B;**未保存的更改**&#x200B;对话框中选择&#x200B;**关闭而不保存**。

## DITAVAL编辑器视图

Adobe Experience Manager Guides的DITAVAL编辑器支持以两种不同的模式或视图查看DITAVAL文件：

**作者**：   这是DITAVAL编辑器的典型“所见即所得”视图。 您可以使用简单的用户界面添加或删除属性，该界面在下拉列表中显示属性、属性值和操作。 在“创作”视图中，您可以选择通过一次单击插入单个属性和所有属性。

通过将指针悬停在文件名上，还可以找到当前正在处理的DITAVAL文件的版本。

**Source**：   Source视图显示构成DITAVAL文件的基础XML。 除了在此视图中编辑常规文本外，作者还可以使用智能目录添加或编辑属性。

要调用智能目录，请将光标放在任何属性定义的末尾并输入“&lt;”。 该编辑器将显示可以在该位置插入的所有有效XML元素的列表。

![](images/ditaval-source-view-new.png)


## 在Assets UI中使用DITAVAL文件

您还可以从Assets UI创建DITAVAL文件。 创建新DITAVAL主题的步骤如下：

1. 在Assets UI中，导航到要创建DITAVAL文件的位置。

1. 选择&#x200B;**创建** \> **DITA主题**。

1. 在Blueprint页面上，选择DITAVAL文件模板并选择&#x200B;**下一步**。

1. 在“属性”页面上，为DITAVAL文件指定&#x200B;**标题**&#x200B;和&#x200B;**名称**。

   >[!NOTE]
   >
   > 根据文件的标题自动建议名称。 如果要手动指定文件名，请确保“名称”不包含任何空格、撇号或大括号，且以.ditaval结尾。

1. 选择&#x200B;**创建**。

   此时将显示“创建的主题”消息。

您可以选择打开DITAVAL文件以便在DITAVAL编辑器中编辑，或者将主题文件保存到Adobe Experience Manager存储库中。

执行以下步骤来编辑现有DITAVAL文件：

1. 在Assets UI中，导航到要编辑的DITAVAL文件。

1. 若要获得对文件的独占锁定，请选择该文件并选择&#x200B;**签出**。

1. 选择该文件并选择&#x200B;**编辑**&#x200B;以在Adobe Experience Manager Guides DITAVAL编辑器中打开该文件。



