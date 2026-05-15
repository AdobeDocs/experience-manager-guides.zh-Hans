---
title: 向“参考线”编辑器添加自定义样式
description: 了解如何添加自定义样式以更改指南编辑器的外观。
exl-id: 03143fb2-d05d-4103-b172-8b91880b7f9e
feature: Web Editor
role: User, Admin
TQID: https://experienceleague.adobe.com/uQc8TTz7dHxbN6-zbin-esQevLoJR-IMR1hchrwEs8M
product_v2:
  - id: fae5e35a-80c9-4b94-9352-1a060a6aab1d
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: ab01a588-7dea-43f2-a699-0b3f128465d6
  - id: cb8c6a2a-3c38-4e40-867c-756f8c36bb0e
subfeature_v2:
  - id: ad602516-aca3-4247-9ae8-f393d958efa9
  - id: b1ef4d86-3917-4b76-a0bc-4a4771f9b3b0
  - id: f89f75b0-cf2e-4e96-aec8-fe8c39cbd0ef
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
source-git-commit: 8ed5c9cb07c56b84b36ef56a55af8738989a6d3f
workflow-type: tm+mt
source-wordcount: 300
ht-degree: 0%

---

# 向“参考线”编辑器添加自定义样式

在本文中，我们将了解如何添加自定义样式以更改浏览器默认外观。

这将涉及以下步骤：
- 通过文件夹配置文件XML编辑器配置添加自定义样式
- 在浏览器中选择相应的文件夹配置文件并测试更改


## 以示例实施

让我们通过一个示例来了解这一点，我们希望在编辑器中将简短描述和标题显示为具有某些样式方面的单独块。

![使用自定义样式预览Webeditor](../../../assets/authoring/webeditor-customstyles-preview.png)


## 实施此功能


### 将自定义CSS添加到文件夹配置文件

使用文件夹配置文件检查“XML编辑器配置”选项卡下的&#x200B;*css_layout.css*，并添加具有自定义样式的CSS

[使用此链接可了解有关文件夹配置文件和配置CSS模板布局的更多信息](https://experienceleague.adobe.com/docs/experience-manager-guides-learn/videos/advanced-user-guide/editor-configuration.html?lang=en#customize-the-css-template-layout)

使用以下内容在编辑器中设置上述样式：
- 使用[css_layout.css](../../../assets/authoring/webeditor-customstyles-css_layout.css)并将其上载到您选择的文件夹配置文件
- 使用AEM包管理器安装附加的包[webeditor-styles-resources.zip](../../../assets/authoring/webeditor-styles-resources.zip)，以安装上述CSS文件中使用的资源

```
This will install the resources at path "/content/dam/resources" which will include sub-folders "fonts" and "images"
```


### 测试

- 打开Web编辑器
- 在“用户首选项”中，选择添加自定义样式的文件夹配置文件。 如果您将其添加到全局配置文件，则您可能已在使用它。
- 打开一个主题，您会注意到编辑区域应具有自定义UI

```
Please note this is compatible to AEM Guides version 4.2 and AEM Guides cloud version 2303 (March)
```


## 引用

您也可能对有关webeditor配置和自定义的专家会话感兴趣，该会话包含在[Webeditor专家会话](https://experienceleague.adobe.com/docs/experience-manager-guides-learn/tutorials/knowledge-base/expert-session/webbased-authoring-jan2023.html?lang=en)中
