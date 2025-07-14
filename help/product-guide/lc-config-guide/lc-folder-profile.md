---
title: 配置文件夹配置文件
description: 了解如何在Experience Manager Guides中处理学习和培训内容时配置文件夹配置文件。
feature: Authoring
role: Admin
level: Experienced
source-git-commit: b114cbcc0f637a71a9d9b7458686a06070179983
workflow-type: tm+mt
source-wordcount: '1296'
ht-degree: 0%

---

# 配置文件夹配置文件

需要文件夹配置文件来分隔企业中不同部门或产品的配置。 对于学习和培训内容，您可以创建和配置文件夹级别的配置文件，以管理创作模板、输出模板、输出预设和其他文件夹级别的设置。

要开始使用学习和培训内容的文件夹配置文件配置，您需要：

1. [创建文件夹配置文件](../cs-install-guide/conf-folder-level.md#create-and-configure-a-folder-level-profile)。
2. **选择要配置的文件夹配置文件**：创建文件夹配置文件后，您需要在[用户首选项](../user-guide/intro-home-page.md#user-preferences)页面上选择文件夹配置文件，以确保作者和发布者可以访问正确的模板。

   ![](assets/folder-profile.png){width="650" align="left"}

3. **配置文件夹配置文件设置**：对于学习和培训内容，可以在文件夹级别配置以下设置：
   - [面板](#configure-panels)
   - [模板](#configure-templates)
   - [输出预设](#configure-output-presets)
   - [HTML编辑器](#html-editor-settings)
   - [发布配置文件](#manage-publish-profiles)

要访问这些设置，请切换到编辑器视图，然后从&#x200B;**选项**&#x200B;菜单中选择&#x200B;**设置**，如下所示：

![](assets/access-editor-settings.png)

## 配置面板

此设置控制在Experience Manager Guides中的&#x200B;**编辑器**&#x200B;和&#x200B;**映射控制台**&#x200B;的左右面板中显示的面板。 您可以切换按钮以显示或隐藏所需的面板。

对于学习和培训内容，请确保仅为“编辑器和映射”控制台启用以下功能。

![](assets/panels-settings.png){width="350" align="left"}


### 编辑器

**左侧面板**

- **收藏集**：允许您组织和保存常用文件，或快速访问共享文件。
- **存储库**：允许您查看和访问内容存储库中存储的所有地图、主题、图像和其他资源。
- **课程经理**：为创建和管理课程提供专用工作区。
- **片段**：允许您在学习课程的各个主题中创建和重复使用小型内容片段。
- **条件**：允许您在全局和文件夹级别配置条件属性。
- **变量**：允许您创建和管理要在学习内容中使用的变量。
- **语言变量**：允许您为模板中的已发布输出或静态文本定义本地化的字符串。
- **模板**：允许您创建和管理供作者使用的模板。
- **输出模板**：允许您创建和管理输出模板，以生成各种格式的输出。
- **查找和替换**：提供用于搜索并替换映射或存储库中文件夹中文件间的文本的选项。 

**右侧面板**

- **内容属性**：包含有关编辑器中当前选定元素的类型和属性的信息。
- **文件属性**：允许您查看和管理选定文件的属性。
- **样式**：显示用于学习内容的基于类的全局样式选项。
- **筛选器**：允许您在主题的预览模式下根据应用的条件筛选内容。

### 映射控制台

**左侧面板**

- **预设**：允许您配置用于发布学习课程的输出预设。
- **翻译**：提供将内容翻译成多种语言的选项。
- **报告**：允许您生成和管理报告，以便让有用的insight了解课程内容的整体运行状况。
- **条件预设**：提供为不同受众、部门等配置基于条件的输出预设的选项。

**右侧面板**

- **筛选器**：允许您在处理报告和翻译时使用筛选器。

## 配置模板

此设置允许您管理编辑器[中](../user-guide/web-editor-left-panel.md)左侧面板中存在的创作和发布模板。 您可以添加、删除或重新排序创作和输出模板，作者和发布者随后可以访问这些模板。

![](assets/templates-settings.png){width="350" align="left"}

创作模板分为四个类别 — 学习课程、学习内容、测验和问题库。 如果在实例中配置了任何预定义模板，则默认情况下将显示这些模板。

![](assets/templates-list.png){width="350" align="left"}

### 添加模板

执行以下步骤以添加新模板：

1. 导航到要添加模板的模板类别，然后选择&#x200B;**添加**。
2. 在选择路径对话框中，选择所需的模板。
3. 选择&#x200B;**选择**。

   ![](assets/add-templates.png){width="350" align="left"}

模板即添加到设置面板的相应类别中。

同样，您可以添加其他创作和输出模板。 添加后，作者和发布者可在各自的课程对话框中访问这些模板。 例如，管理员添加的学习课程模板可供作者创建新课程时使用。

![](assets/templates-added-course.png){width="350" align="left"}

### 使用新的创作和输出模板

要使用与&#x200B;**选择路径**&#x200B;对话框中所显示的模板不同的模板，请创建自定义创作或输出模板。

**创建新的创作模板**

要使用其他映射或主题模板，请从编辑器的“模板”面板中新建一个创作模板。 使用映射模板创建学习课程和主题模板，用于学习内容、测验或学习摘要。

有关详细信息，请查看[从编辑器创建自定义模板](../user-guide/create-maps-customized-templates.md)。

![](assets/authoring-templates-editor.png){width="350" align="left"}

**创建新输出模板**

执行以下步骤，为学习与培训内容创建新的输出模板：

1. 从编辑器的左侧面板中，选择&#x200B;**更多** > **输出模板**。

   此时将显示“输出模板”面板。

   ![](assets/output-templates-editor.png){width="350" height="" align="left"}
2. 在“输出模板”面板中，选择(+)以创建新的输出模板。

   ![](assets/create-new-output-template.png){width="350" align="left"}
3. 从下拉菜单中选择一个输出模板。


   ![](assets/output-template-types.png){width="650" align="left"}
4. 根据所选的输出模板类型，会显示一个对话框，您可以在其中基于可用模板创建新模板。

   ![](assets/new-scorm-template-dialog.png){width="350" align="left"}

5. 选择&#x200B;**创建**。

   将创建新的输出模板。

6. 要访问和添加发布者的输出模板，请导航到&#x200B;**设置** > **模板** > **输出模板**，然后选择&#x200B;**添加**。

   ![](assets/add-output-template-settings-panel.png){width="350" align="left"}

   输出模板显示在“选择路径”对话框中。
7. 选择模板并选择&#x200B;**确认**。

   ![](assets/select-scorm-template-dialog.png){width="350" align="left"}

   现在，选定的输出模板即添加到“设置”面板中。

   ![](assets/scorm-template-added.png){width="350" align="left"}

### 删除或重新排序模板

添加模板后，您可以从“设置”面板中删除或重新排序模板。

要删除模板，请选择模板旁边的&#x200B;**删除**&#x200B;图标。

![](assets/remove-teamplates.png){width="350" align="left"}

您还可以定义类别中存在的模板的显示顺序。 要更改模板的显示顺序，请选择虚线并将模板拖到所需位置。

![](assets/reorder-templates.png){width="350" align="left"}


## 配置输出预设

“输出预设”选项卡允许您定义哪些输出格式可用于发布课程。 它包含两个部分：**允许的输出预设类型**&#x200B;和&#x200B;**公共输出预设**。

![](assets/configure-course-output-presets.png){width="350" align="left"}

- **允许的输出预设类型**：此部分列出了Experience Manager Guides实例中支持的所有输出预设。 对于课程发布，仅&#x200B;**SCORM**&#x200B;和&#x200B;**PDF**&#x200B;格式适用。 您可以选择其中一个或两个选项。 生成课程输出时，发布者可以使用选定的预设。

  ![](assets/allowed-output-presets.png){width="350" align="left"}

- **常见输出预设**：此部分显示发布者通常创建并添加到特定文件夹配置文件的输出预设。 您还可以删除任何不再需要的预设。

  ![](assets/common-output-presets.png){width="350" align="left"}

## HTML编辑器设置

通过此设置，可为基于HTML的创作配置编辑器。 此设置中存在的关键配置选项如下：

![](assets/configure-html-editor-setting.png){width="350" align="left"}

- **隐藏内联样式**：启用此选项可阻止作者将内联格式应用于课程内容。 启用后，编辑器右侧面板中存在的所有内联样式选项（如“字体”、“边框”、“布局”、“背景”和“列”）对作者保持隐藏状态。 但是，作者仍可以使用&#x200B;**样式**&#x200B;面板中提供的基于类的全局样式选项。 这有助于保持与组织风格指南的一致性。
- **隐藏作者的Source视图**：启用此选项可限制对HTML源代码的访问。 当您希望简化编辑体验或避免意外更改基础代码时，这将很有用。

## 管理发布配置文件

在此部分中，您可以查看、创建和管理用于将课程发布到SCORM Cloud的发布配置文件。 每个配置文件定义将学习课程发布到特定SCORM云环境所需的连接设置和配置详细信息。

如果需要发布到不同的SCORM Cloud帐户，您可以创建多个配置文件，从而确保发布过程的灵活性和控制力。

提供服务器详细信息以及关联的SCORM云应用程序的客户端ID和客户端密码，以配置SCORM云的发布配置文件。

![](assets/configure-publish-profiles.png){width="350" align="left"}