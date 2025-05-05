---
title: 下载并安装AEM Sites模板
description: 了解如何下载和安装AEM Sites模板
feature: Installation
role: Admin
level: Experienced
source-git-commit: f6e34c0bc57603b4251abd4859b43c95042e8819
workflow-type: tm+mt
source-wordcount: '1130'
ht-degree: 0%

---


# 下载并安装AEM Sites模板

执行以下步骤，以Cloud Service身份在Experience Manager Guides上下载并安装AEM Sites模板：

## 软件包安装{#package-installation}

要使用模板，请通过云部署安装组件包：
- [guides-components-all.zip](https://github.com/adobe/aemg-sites-components/releases/tag/v1.0.0)



执行以下步骤以使用模板创建AEM Sites：


1. 使用模板创建AEM Sites：
1. 在站点UI中，单击右上角的&#x200B;**创建**&#x200B;按钮。
1. 从&#x200B;**创建**&#x200B;下拉列表中选择&#x200B;**从模板**&#x200B;创建站点。

1. 使用&#x200B;**导入**&#x200B;选项导入站点模板： [aemg-docs-1.0.0.zip](https://github.com/adobe/aemg-sites-template/releases/tag/v1.0.0)。
1. 选择`AEMG Docs 1.0.0`，然后单击&#x200B;**下一步**。
1. 输入`Site title`和`Site name`。
1. 单击&#x200B;**创建**。软件包已安装，并且创建了AEM Sites模板。

了解有关[将站点模板添加到AEM](https://experienceleague.adobe.com/zh-hans/docs/experience-manager-cloud-service/content/sites/administering/site-creation/site-templates#adding)的详细信息。


>[!NOTE]
>
>创建主页后，您可以将此路径用作&#x200B;**Publish路径**&#x200B;来生成AEM Sites预设的输出。 例如：`aemg-docs-en/docs/product-abc`。


## 配置要与AEM Sites预设一起使用的模板

安装包后，将在Sites UI中创建名为&#x200B;**AEMG**&#x200B;的站点。 此示例站点显示了如何设置站点结构以生成AEM Sites输出。 这只是个例子。 您可以根据自己的要求创建自定义站点。

![AEMG Sites示例页面](assets/aemg-sites-sample-pages.png)


**AEMG**&#x200B;包含以下组件。
- **AEMG**&#x200B;文件夹中存在英语(en)语言的文件夹。 您可以根据要求创建类似的语言副本。 例如，多语言网站包括英语(en)、德语(de)和法语(fr)语言副本。  了解有关如何使用[语言副本向导](https://experienceleague.adobe.com/zh-hans/docs/experience-manager-65/content/sites/administering/introduction/tc-wizard)创建语言副本的详细信息。
- 在English(en)语言文件夹中，Experience Manager Guides提供了许多现成的示例页面，如&#x200B;**搜索**、**登录**、**文档**&#x200B;和&#x200B;**支持**。

- **文档**&#x200B;是示例文档主页。 它是所有产品相关文档的中心位置
和显示其文档作为单个图块提供的每个产品。

- 除了文档主页之外，还有&#x200B;**搜索**、**登录**&#x200B;和&#x200B;**支持**&#x200B;的示例页面。 您可以根据需要自定义这些示例。
- 您可以拥有各个产品（如Product1）的主页。 **文档**&#x200B;下有一个示例页面&#x200B;**Product1**，该页面是文档主页。

- Experience Manager Guides还提供了以下预定义模板：

   - **内容页面**&#x200B;模板：使用此模板创建包含产品站点大部分内容的标准页面。 它们可以包括文本、图像、视频和其他内容元素。 此模板仅包含页眉和页脚。 根据您的要求，自定义并使用它来创建任何页面。 例如，您可以为产品创建支持页面或登录页面。
   - **主页**&#x200B;模板：网站的主登录页面，包括概述、关键元素和功能等关键部分以及导航链接。 例如，产品ABC的主页连接到其他内容或功能页面。
   - **主题页面**&#x200B;模板：用于组织和展示基于主题内容的页面。 例如，用户指南包含不同的主题页面，其中每个页面都包含与功能和故障诊断相关的特定主题。

  ![站点模板](assets/sites-ui-templates.png)

使用这些示例和模板生成AEM Sites输出：
- 产品主页对应于映射主页，并使用主页模板创建。 在AEM Sites预设中选择此路径以发布该路径下的映射内容。 产品主页可以包含其他主页。
- 例如，您拥有Experience Manager Guides等产品，并且需要为用户、管理员和开发人员编写三本手册。  使用“主页”模板为每个手册创建一个主页，然后在AEM Sites输出预设中选择对应的主页。

详细了解如何在Web编辑器中创建和配置[AEM Sites预设](../user-guide/generate-output-aem-site-web-editor.md)。

## 使用模板创建主页{#create-a-home-page-using-the-template}

执行以下步骤可为您的产品创建主页：
1. 安装包后，从全局导航中选择&#x200B;**站点**。
1. 选择安装在站点UI中的“AEMG文档”模板。
1. 在站点UI中，单击右上角的&#x200B;**创建**&#x200B;按钮。
1. 从&#x200B;**创建**&#x200B;下拉列表中选择&#x200B;**页面**。
1. 选择&#x200B;**主页**，然后单击&#x200B;**下一步**。
1. 输入站点标题和站点名称，然后单击右上角的&#x200B;**创建**。 使用&#x200B;**主页**&#x200B;站点模板创建AEM站点模板。 例如，您可以为产品`Product ABC`创建主页。


>[!NOTE]
>
>创建主页后，您可以将此路径用作&#x200B;**Publish路径**&#x200B;来生成AEM Sites预设的输出。 例如：`aemg-docs-en/docs/product-abc`。

## 编辑AEM Sites的主题模板

您还可以自定义AEM Sites的主题模板。 您可以在主题中编辑内容或配置不同AEM组件的属性。 例如，您可以根据要求添加或删除组件。\
执行以下步骤来编辑主题模板：
1. 选择要编辑的模板。
1. 选择顶部的&#x200B;**编辑**&#x200B;图标。

将打开AEM模板编辑器。 您可以编辑主题模板。 了解有关[创建页面模板](https://experienceleague.adobe.com/zh-hans/docs/experience-manager-65/content/sites/authoring/siteandpage/templates#editing-a-template-structure-template-author)的详细信息。


## 自定义现有AEM Sites模板 {#customize-existing-aem-sites-templates}

除了预定义模板之外，您还可以将现有模板与AEM Sites预设一起使用。 执行以下步骤可自定义现有AEM Sites模板：

### 模板设置

您需要以下两种类型的模板：

- 类别或登陆模板：此模板用于产品文档登陆页面，并与DITA映射相对应。  使用此模板生成DITA映射的AEM站点页面。 您可以在任何级别使用此模板。
 — 向现有模板中添加文本组件。 文本组件应具有强制属性`text="$category.html$"`。
 — 例如，您可以选择We-Retail模板，并使用区域页面模板作为DITA映射的登陆页面模板。 为此，请进行如下屏幕快照中所示的更改：
  ![节页面模板](assets/customize-existing-aem-templates-section.png)
   - 详细信息页面或主题页面模板：此模板用于地图主题的内容。 DITA/XML内容的所有“站点”页面都是使用主题页面模板创建的。 要创建这些模板，需满足两个先决条件：
      - 将文本组件添加到模板中（包含在容器组件中），该模板具有必需属性。`text="$topic.content$"`。

        ![容器页面模板](assets/customize-existing-aem-templates-container.png)
      - 在同一个模板的结构中反映相同的容器和文本组件，如下面的屏幕快照所示：

        ![容器模板的结构](assets/customize-existing-aem-templates-structure.png)

### 将类别页面标记为文档容器

假设使用以前的模板为文档页面创建了站点层次结构，请选择在该站点层次结构中创建的类别页面之一。 通过提供一个ID将类别页面标记为文档容器。
为此，请为其属性`id`分配值`category-page`。 请参阅以下屏幕截图：

![标记类别页面](assets/customize-existing-aem-templates-tagging.png)





