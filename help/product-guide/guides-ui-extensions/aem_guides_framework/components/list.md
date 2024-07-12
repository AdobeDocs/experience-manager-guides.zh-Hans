---
title: 列表
description: 列表
role: User, Admin
exl-id: 333b5e24-efba-4a51-8f68-83b5d1d7daec
source-git-commit: e40ebf4122decc431d0abb2cdf1794ea704e5496
workflow-type: tm+mt
source-wordcount: '59'
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
