---
title: 使用标签
description: 了解如何在AEM Guides中为不同版本的文件使用标签。 了解如何在主题版本中添加或删除标签。
feature: Authoring, Features of Web Editor, Publishing
role: User
hide: true
exl-id: bd488298-57d7-46fb-9820-cec8d0db8bd5
TQID: https://experienceleague.adobe.com/e0RaL-brcNFr-xeegnXVtpTjgxN84Np-g5rw-0ONQDs
product_v2: id: fae5e35a-80c9-4b94-9352-1a060a6aab1did: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2: id: a3bd6397-2eb2-4908-a61c-226e26855dcaid: ab01a588-7dea-43f2-a699-0b3f128465d6
subfeature_v2: id: ad602516-aca3-4247-9ae8-f393d958efa9id: d4f22c6d-7923-41e5-9da3-527ff8df4bc8id: f89f75b0-cf2e-4e96-aec8-fe8c39cbd0ef
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554
source-git-commit: 8ed5c9cb07c56b84b36ef56a55af8738989a6d3f
workflow-type: tm+mt
source-wordcount: 396
ht-degree: 0%

---

# 使用标签 {#id164JBG0M0T1}

AEM Guides允许您将标签添加到文件的不同版本。 您可以使用这些标签指定要包含在要发布的基线中的版本。 有关使用标签创建基线的详细信息，请参阅[使用基线](generate-output-use-baseline-for-publishing.md#)。

例如，如果要在&#x200B;*版本2.0*&#x200B;中使用同一主题的&#x200B;*版本1.0*&#x200B;和&#x200B;*版本1.1*&#x200B;中的&#x200B;*版本1.0*，则可以在&#x200B;*版本1.0*&#x200B;上添加&#x200B;*版本1.0*&#x200B;标签，在&#x200B;*版本1.1*&#x200B;上添加&#x200B;*版本2.0*&#x200B;标签。

添加标签后，即可创建基线，并指定要使用该基线发布时包含的主题版本。 要查看基线中应包含或排除的版本，可以使用“版本历史记录”选项。

## 添加标签

执行以下步骤可向主题添加标签：

1. 在Assets UI中，选择一个主题
1. 单击左边栏选择器图标并选择&#x200B;**版本历史记录**。
1. 在“版本历史记录”中，单击要添加标签的版本。

1. 输入所选版本的标签，然后按Enter键。 例如，*2.6版本*。

   >[!NOTE]
   >
   > 不能将同一标签添加到主题的不同版本。 但是，您可以向主题的同一版本添加多个标签。

   标签将显示在所选主题的“版本历史记录”中。 以下屏幕截图显示了已添加到高亮显示的主题版本中的标签&#x200B;*x.x版本*&#x200B;和&#x200B;*用户指南*。

   ![](images/labels.png){width="300"}

>[!NOTE]
>
> 使用基线，可以向多个主题添加标签。 有关使用基线添加标签的详细信息，请参阅[将标签添加到基线](generate-output-use-baseline-for-publishing.md#id184KD0T305Z)。

## 删除标签

执行以下步骤可删除标签：

1. 在Assets UI中，选择添加了标签的主题。
1. 单击左边栏选择器图标并选择&#x200B;**版本历史记录**。

   在版本历史记录中，您将看到主题的所有版本以及附加到这些版本的标签。 下图显示了不同版本主题的一个示例，其中有一个版本添加了标签。

   ![](images/labels.png){width="300"}

1. 单击“删除”按钮\(**X**\)可删除标签。

   ![](images/delete-labels.png){width="300"}


**父主题：**[&#x200B;使用Web编辑器](web-editor.md)
