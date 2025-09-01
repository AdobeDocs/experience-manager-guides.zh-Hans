---
title: 为AEM Guides自定义现有AEM站点模板
description: 了解如何为AEM Guides自定义现有AEM站点模板
feature: Installation
role: Admin
level: Experienced
source-git-commit: 1cec8975e8aad56184793a023d066aa467d8cec5
workflow-type: tm+mt
source-wordcount: '937'
ht-degree: 1%

---

# 为AEM Guides自定义现有AEM站点模板

本指南提供了分步说明，用于自定义现有AEM站点模板以与AEM Guides一起使用以从DITA映射和主题生成AEM Sites。

如果您使用的是现成的AEM Guides (AEMG Docs)模板，则配置和组件已经就位，可以按原样使用它们来发布AEM Guides内容。 但是，如果您要将现有的AEM Sites模板与自定义品牌结合使用来发布AEM Guides内容，请按照以下步骤使您的站点模板与AEM Guides渲染要求保持一致。


## 先决条件

- 您拥有对AEM模板的适当权限和访问权限。
- 您了解AEM可编辑模板和AEM站点结构。
- 您已有使用可编辑模板构建的现有站点层次结构。
- 您现有项目中至少有两个模板：

   - **文档容器页面模板**，用于将DITA映射呈现为文档根。
   - **主题页模板**&#x200B;用于呈现各个DITA主题页。

## 模板命名注意事项

模板名称将因项目设置而异。 例如，在OOTB AEMG文档配置中：

- 文档容器页面： /conf/AEMG-Docs-Site/settings/wcm/templates/kb-content

- 主题页面： /conf/AEMG-Docs-Site/settings/wcm/templates/topic-content

**自定义：**&#x200B;自定义过程包含两个主要步骤：

1. 模板设置：标识并配置两个模板（容器和主题）。
2. 渲染指南组件：嵌入必需的AEM Guides组件以启用目录、导航和元数据显示等功能。

## 模板设置

从AEM站点中选择并配置两个可编辑的模板。

### 文档容器页面模板

文档容器页面模板用于创建呈现DITA映射内容的产品文档容器页面。

- 它用作一组特定文档（例如，产品手册或指南）的入口点或主页。
- 将id=&quot;category-page&quot;属性添加到模板初始节点的jcr:content。 这可确保AEM Guides会自动将从此模板创建的所有页面视为文档容器。

  ![正在添加id=&quot;category-page&quot;](/help/product-guide/knowledge-base/kb-articles/assets/publishing/add-id-category-page.png){width="650" align="left"}

- 添加具有必需属性的文本组件： text=&quot;$category.html$&quot;。

  ![正在添加文本组件](/help/product-guide/knowledge-base/kb-articles/assets/publishing/add-text-component.png){width="650" align="left"}

- 通常包括导航元素，例如指向文档中的部分或主题的链接。
- 它可以进行自定义以包含品牌、页眉、页脚和其他设计元素。

**示例用例：**
如果您有产品手册的DITA映射，则文档容器页面模板将为该手册生成主页，显示概述和各个主题的链接。

### 主题页面模板

- **主题页面模板**&#x200B;用于创建单个&#x200B;**DITA主题**&#x200B;的页面。
- DITA映射中的每个主题都使用此模板呈现为单独的页面。
- 包含具有强制属性&#x200B;**文本组件**： text=&quot;$topic.content$&quot;。

  ![正在添加具有强制属性的文本组件](/help/product-guide/knowledge-base/kb-articles/assets/publishing/add-text-component-mandatory-property.png){width="650" align="left"}

- 在站点生成期间，此占位符将替换为DITA主题的实际内容。
   - 文本组件通常置于&#x200B;**Container组件**&#x200B;中，以确保布局和样式正确。
   - 可以自定义以包含所有主题页面中一致的页眉、页脚和导航元素。

**示例用例：**
如果您有有关“安装说明”的DITA主题，则主题页面模板将生成一个显示该主题内容的页面。

**容器组件：**

![正在添加容器组件](/help/product-guide/knowledge-base/kb-articles/assets/publishing/add-container-component.png){width="650" align="left"}

>[!NOTE]
>
> 确保将wcm/foundation/components下使用sling:resourceType的组件迁移到相应的核心/wcm/components。

在同一模板的结构中添加相同的（容器和文本组件）：

![正在添加容器和文本组件](/help/product-guide/knowledge-base/kb-articles/assets/publishing/add-container-and-text-component.png){width="650" align="left"}

## 呈现自定义模板中的指南组件

要启用核心AEM Guides组件功能（如目录、页面重定向、导航和元数据显示），您需要在自定义模板中包含特定的AEM Guides组件。 必须将这些组件显式添加到相应的可编辑模板（文档容器页面或主题页面），以确保在站点生成和运行时提供所需的功能。

有关组件及其使用情况的列表，请参阅下表：

| 功能 | 组件名称 | 描述 | 推荐的模板 |
|---|---|---|---|
| 目录 | guidessidenavigation | 从DITA映射中呈现完整目录 | 文档容器 |
| 页面重定向 | childredirect | 重定向到地图中的第一个主题页面 | 文档容器 |
| 迷你目录 | minitoc | 显示当前主题的目录 | 主题页面 |
| 上次更新时间 | pageproperty | 显示上次修改日期 | 主题页面 |
| 传呼机 | 传呼机 | 允许在上一个主题页和下一个主题页之间进行导航 | 主题页面 |
| 语言导航 | 语言导航 | 支持在不同语言版本之间切换 | 任一模板 |


## 组件用例

- **重定向组件(childredirect)：**&#x200B;将此组件添加到文档容器页面模板，以便从DITA映射生成的产品主页自动重定向到第一个主题页面。 如果您的文档容器页面设计为具有自定义组件和布局的独立主页，则不需要此组件。

- **目录(guidessidenavigation)：**&#x200B;将此项添加到主题页面模板，以随主题内容呈现可导航的目录。 TOC派生自DITA映射，并帮助用户在同级主题之间导航。


## 启用Guides客户端库

默认情况下，AEM Guides组件包中提供的客户端库(clientlibs)不会应用于自定义模板。 要启用它们，请执行以下操作：

1. **编辑模板：**

   1. 在&#x200B;**编辑器模式**&#x200B;中打开&#x200B;**产品页**。
   2. 选择&#x200B;**编辑模板** (这将打开类似conf/settings/wcm/templates/structure.html的URL)。

      ![编辑模板](/help/product-guide/knowledge-base/kb-articles/assets/publishing/edit-template.png){width="650" align="left"}

2. **更新页面策略：**

   1. 转到&#x200B;**页面信息**&#x200B;按钮，然后选择&#x200B;**页面策略**。
   2. 添加以下客户端库：
      - **客户端库**
      - **客户端库JavaScript页头**

3. **保存更改：**&#x200B;添加所需的客户端库后保存模板。

   ![添加客户端库](/help/product-guide/knowledge-base/kb-articles/assets/publishing/add-client-libraries.png){width="650" align="left"}


>[!NOTE]
>
> 在部署到生产环境之前，请确保在非生产环境中测试模板。<br><br>有关更多详细信息，请参阅官方的[AEM Guides](https://experienceleague.adobe.com/en/docs/experience-manager-guides/using/overview)和[AEM Sites](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/get-started/authoring)文档。
