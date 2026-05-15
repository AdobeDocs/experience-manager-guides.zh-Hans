---
title: 原生PDF发布功能 |使用自定义更改条样式
description: 了解如何在更改条中应用样式。
exl-id: a81ec56c-ccbb-4599-a696-8edef7a73cdd
feature: Output Generation
role: Admin
level: Experienced
TQID: https://experienceleague.adobe.com/O-pFWUkHhojZiran3297cK58G5WDGvkGU5ooHJwZWeA
product_v2: id: fae5e35a-80c9-4b94-9352-1a060a6aab1did: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2: id: a3bd6397-2eb2-4908-a61c-226e26855dca
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
source-git-commit: 8ed5c9cb07c56b84b36ef56a55af8738989a6d3f
workflow-type: tm+mt
source-wordcount: 348
ht-degree: 0%

---

# 使用自定义更改条样式

更改条是一条垂直线，用于直观地标识新内容或修订的内容。 AEM Guides允许您在标题中更改的内容左侧显示更改栏，并且允许您在PDF输出的目录中显示更改的主题。

有关显示更改栏的更多详细信息，请参阅[发布PDF输出](../web-editor/native-pdf-web-editor.md)中的&#x200B;*创建发布版本间具有更改栏的PDF*&#x200B;设置。

## 更改的主题内容

更改栏显示在已插入、更改或删除的主题的内容左侧。

您可以修改以下样式以显示更改的内容以及更改栏。


>[!NOTE]
>
>这些样式是`layout.css`文件的一部分，您可以根据需要编辑它们。

例如，您可以使用`.inserted-block`样式中的color属性来定义插入内容在已发布的PDF输出中的显示方式。


```css
...
.inserted-block { 
  color: #2ECC40; 
  display: inline; 
  -ro-comment-content: " "; 
  -ro-comment-style: underline; 
  -ro-comment-title: "Inserted"; 
  -ro-comment-date: attr(data-time); 
  -ro-comment-dateformat: "yyyy/dd/MM HH:mm:ss"; 
} 
...
```

同样，您可以使用`.deleted-block`样式定义已删除内容在已发布PDF输出中的显示方式。

```css
...
.deleted-block { 
  display: inline; 
  color: #FF6961; 
  text-decoration: line-through; 
  -ro-comment-content: " "; 
  -ro-comment-style: strikeout; 
  -ro-comment-title: "Deleted"; 
  -ro-comment-date: attr(data-time); 
  -ro-comment-dateformat: "yyyy/dd/MM HH:mm:ss"; 
} 
...
```

您可以使用`.inserted-change-bar`和`.deleted-change-bar`样式来修改更新内容左侧的更改条的外观。

例如，您可以使用`.inserted-change-bar`样式中的`-ro-change-bar-color`属性以绿色显示插入的更改栏。 您还可以使用`.deleted-change-bar`样式中的`-ro-change-bar-color`属性以红色显示已删除的更改栏。

```css
...
.inserted-change-bar { 
  -ro-change-bar-color: #2ECC40; 
} 

.deleted-change-bar { 
  -ro-change-bar-color: #FF6961; 
  } 
...
```

<img src="./assets/changed-bar-content.png" alt="更改了条形图主题内容" width="500">

## 更改了目录(TOC)中的主题

您还可以在PDF输出的目录中已更改的主题左侧添加更改栏。 您可以使用`.changed-topic`样式中的`-ro-change-bar-color`特性，以所选颜色为目录列表中的更新主题添加更改栏。

例如，可以添加绿色更改栏。

```css
...
.changed-topic { 
 -ro-change-bar-color: #2ECC40; 
}  
...
```


该选项会针对目录中所有已完成更新的主题显示绿色更改栏。 您可以单击目录中已更改的主题并查看详细更改。

<img src="./assets/changed-bar-TOC.png" alt="更改条目录" width="500">
