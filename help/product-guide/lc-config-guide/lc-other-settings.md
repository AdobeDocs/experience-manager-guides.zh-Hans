---
title: 配置其他设置
description: 了解如何在Experience Manager Guides中为不同的部门配置文件夹、资源文件夹、变量、代码片段、条件等。
feature: Authoring
role: Admin
level: Experienced
source-git-commit: 5f42540a32da6e85a5c8aa0831582ce871c9088a
workflow-type: tm+mt
source-wordcount: '360'
ht-degree: 0%

---

# 配置其他设置

作为管理员，您还可以为学习课程作者和发布者配置以下设置：

- **文件夹设置**
   - **创建不同的文件夹**：您可以为企业中不同部门或产品中工作的作者和发布者创建文件夹。 这些文件夹可以映射到特定的文件夹配置文件，每个文件夹都配置了不同的创作和输出模板，以支持特定于部门的学习课程创建和分散管理。

     您可以从“存储库”面板创建新文件夹。

     ![](assets/create-new-folder.png){width="350" align="left"}
   - **创建语言文件夹**：如果将内容翻译成不同的语言，则必须创建与每种语言对应的文件夹。 其中每个语言文件夹都将包含与该语言对应的内容。

     有关详细信息，请查看[内容翻译的最佳实践](../user-guide/translation-first-time.md)。
   - **Assets管理**：与文件夹类似，您也可以创建其他Assets文件夹以满足不同部门的需求。 通过这种方式，您还可以确保作者和发布者有权访问其模板、图像和其他资产中配置的正确CSS。

     ![](assets/configure-assets-folder.png){width="350" align="left"}
- **代码片段**：您可以在文件夹级别配置代码片段，以确保作者可以访问正确的代码片段。 只有管理员可以在Experience Manager Guides中创建代码片段，然后作者可以在编辑器中使用该代码片段。

  您可以从编辑器的左侧面板访问代码片段。

  ![](assets/create-snippets.png){width="350" align="left"}
- **条件**：作为管理员，您可以在全局或文件夹级别配置标准DITA支持的条件属性。 然后，作者只需将所需条件拖放到其内容中，即可使用已配置的条件。

  您可以从编辑器的左侧面板访问条件。

  ![](assets/create-conditions.png){width="350" align="left"}
- **变量**：您可以定义变量，以使内容更可移植、一致且更易于更新。 在输出生成期间，变量将被所选变量集中的值替换，从而允许您高效地生成自定义输出。

  有关详细信息，请查看[创建新变量](../native-pdf/native-pdf-variables.md#create-a-new-variable)

- **编辑器工具栏**：您可以根据组织需要自定义编辑器工具栏。 例如，您可能希望更改工具栏按钮的名称、更改其位置等等。

  有关详细信息，请查看[配置和自定义XML编辑器](../cs-install-guide/conf-folder-level.md#configure-and-customize-the-xml-editor-id2065g300o5z)。
