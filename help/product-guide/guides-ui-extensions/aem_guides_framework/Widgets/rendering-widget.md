---
title: 渲染构件
description: 呈现如何在JUI小组件中工作
role: User, Admin
exl-id: 381cc7b9-c957-40be-9db4-8347eefe2fa7
TQID: https://experienceleague.adobe.com/-VznRFHuyxLqumy55MssEvPMMHIIt2BelCe7C6zBqR8
product_v2:
  - id: fae5e35a-80c9-4b94-9352-1a060a6aab1d
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
source-git-commit: 8ed5c9cb07c56b84b36ef56a55af8738989a6d3f
workflow-type: tm+mt
source-wordcount: 86
ht-degree: 0%

---

# 渲染构件

我们可以通过使用小部件的`id`引用它来呈现该小部件

要在应用程序中的任意位置呈现构件`widget_languages`，可以使用简单语法：

```json
{
    "component": "widget",
    "id": "widget_languages"
}
```

小组件也可用于呈现复杂的项目，例如，我想呈现每个文件的参与者列表。
在这里，构件可以构造为：

```js title="fileContributorsWidget.js"
const widgetJSON =  {
    component: "div", 
    id: "file_contributors", 
    items: [ // adding components to the widget
        {
            component: "div",
            items: [
                {
                    component: "icon",
                    icon: "file"
                },
                {
                    component: "label",
                    label: "@fileName"
                }
            ]
        },
        {
            component: "list",
            data: "@contributors",
            itemConfig: {
                component: "label"
            }
        }
    ]
},
```

现在，为了呈现每个文件的参与者列表，我们将该列表编写为：

```js title="fileContributorsList.js"
const listJSON = {
    component: "list"
    data: "@files"
    itemConfig: {
        component: "widget",
        id: "file_contributors"
    }
}
```

此处`@files`是包含字段的文件对象列表

```typescript
- fileName: string
- contributors: Array<String>
```
