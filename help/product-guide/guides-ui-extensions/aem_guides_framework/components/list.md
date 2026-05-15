---
title: 列表
description: 列表
role: User, Admin
exl-id: 333b5e24-efba-4a51-8f68-83b5d1d7daec
TQID: https://experienceleague.adobe.com/2mjVuKodk-Jn7tGoiF1fNpCnTd1VqK57oATMiN2gd0o
product_v2:
  - id: fae5e35a-80c9-4b94-9352-1a060a6aab1d
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
source-git-commit: 8ed5c9cb07c56b84b36ef56a55af8738989a6d3f
workflow-type: tm+mt
source-wordcount: 58
ht-degree: 5%

---

# 列表

要显示列表，我们使用组件列表。

```js title="list.js"
const listJSON =  {
    "component": "list", //tells the component name
    "data": "@languages", // an array of list items
},
```

在这里，语言是一个简单的字符串数组。 `languages = ["English", "Hindi", "French"]`
如果要呈现对象列表，可以使用项目配置指定结构。

```js title="list.js"
const listJSON =  {
    "component": "list", //tells the component name
    "data": "@projects", // an array of list items
    "itemConfig": { // used to define the structure of the list items.
    "component": "widget",
    "id": "checkbox_label"
    }
},
```

itemConfig通常为`widget`。 若要了解有关小组件的更多信息，请转到[小组件](../Widgets/basic-widget.md)

渲染的列表将如下所示：

![列表](./imgs/list.png "列表")
