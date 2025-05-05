---
title: 使用标签
description: 了解如何在Adobe Experience Manager Guides中为不同版本的文件使用标签。 了解如何在主题版本中添加或删除标签。
exl-id: d116906d-b469-4a97-b0af-4fadbe15222b
feature: Authoring, Features of Web Editor, Publishing
role: User
source-git-commit: ac83f613d87547fc7f6a18070545e40ad4963616
workflow-type: tm+mt
source-wordcount: '536'
ht-degree: 0%

---

# 使用标签 {#id164JBG0M0T1}

Adobe Experience Manager Guides允许您将标签添加到文件的不同版本。 您可以使用这些标签指定要包含在要发布的基线中的版本。 有关使用标签创建基线的详细信息，请查看[使用基线](generate-output-use-baseline-for-publishing.md#)。

例如，如果要在&#x200B;*版本2.0*&#x200B;中使用同一主题的&#x200B;*版本1.0*&#x200B;和&#x200B;*版本1.1*&#x200B;中的&#x200B;*版本1.0*，则可以在&#x200B;*版本1.0*&#x200B;上添加&#x200B;*版本1.0*&#x200B;标签，在&#x200B;*版本1.1*&#x200B;上添加&#x200B;*版本2.0*&#x200B;标签。

添加标签后，即可创建基线，并指定要使用该基线发布时包含的主题版本。 要查看基线中应包含或排除的版本，可以使用“版本历史记录”选项。

## 从编辑器添加标签

执行以下步骤，从编辑器向主题添加标签：

1. 在“存储库”面板中，导航到主题并在编辑器中将其打开。
1. 从&#x200B;**菜单**&#x200B;下拉列表中选择&#x200B;**版本标签**。

   ![](images/version-label-option.png){width="400" align="left"}

   显示&#x200B;**版本标签管理**&#x200B;对话框。

1. 在&#x200B;**版本标签管理**&#x200B;对话框中，选择要添加标签的版本。
1. 为所选版本选择标签，然后选择&#x200B;**添加标签**。

   ![](images/version-label-management-dialog-new.png){width="650" align="left"}

   >[!NOTE]
   >
   > 不能将同一标签添加到主题的不同版本。 但是，您可以向主题的同一版本添加多个标签。
1. 确认以在确认提示中应用标签。

   标签将显示在所选主题的“版本历史记录”中。

   ![](images/label-comparison-version-history.png){width="650" align="left"}

   >[!NOTE]
   >
   > 使用基线，可以向多个主题添加标签。 有关使用基线添加标签的详细信息，请查看[向基线添加标签](generate-output-use-baseline-for-publishing.md#id184KD0T305Z)。

要从主题中删除版本标签，请使用针对在版本标签管理对话框中添加的每个标签提供的&#x200B;**删除**&#x200B;图标。

![](images/remove-version-label.png){align="left"}


## 从Assets UI使用标签

您还可以向主题添加标签，并根据需要从Assets UI中删除它们。

执行以下步骤，从Assets UI向主题添加标签：

1. 在Assets UI中，选择一个主题，然后将其打开。
1. 选择左边栏选择器图标并选择&#x200B;**版本历史记录**。
1. 在版本历史记录下拉列表中，选择要添加标签的版本。
1. 输入所选版本的标签，然后按Enter键。 例如，*2.6版本*。

   >[!NOTE]
   >
   > 不能将同一标签添加到主题的不同版本。 但是，您可以向主题的同一版本添加多个标签。

   标签将显示在所选主题的“版本历史记录”中。 以下屏幕截图显示了已添加到高亮显示的主题版本中的标签&#x200B;*x.x版本*&#x200B;和&#x200B;*用户指南*。

   ![](images/labels.png){width="300" align="left"}

>[!NOTE]
>
> 使用基线，可以向多个主题添加标签。 有关使用基线添加标签的详细信息，请查看[向基线添加标签](generate-output-use-baseline-for-publishing.md#id184KD0T305Z)。

要从主题中删除版本标签，请使用“版本历史记录”面板中针对每个标签提供的&#x200B;**删除**&#x200B;按钮。

![](images/delete-labels.png){width="300" align="left"}


**父主题：**&#x200B;[&#x200B;编辑器简介](web-editor.md)
