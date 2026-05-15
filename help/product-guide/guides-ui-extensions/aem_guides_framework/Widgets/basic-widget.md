---
title: 小组件
description: 了解小组件
role: User, Admin
exl-id: 96e960df-d595-4d58-8ad4-27057f857bac
TQID: https://experienceleague.adobe.com/SssVShlzFB3kjQCV-cNAOZVYb0TYSQ1CjtWoax2Q-LU
product_v2: id: fae5e35a-80c9-4b94-9352-1a060a6aab1did: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
source-git-commit: 8ed5c9cb07c56b84b36ef56a55af8738989a6d3f
workflow-type: tm+mt
source-wordcount: 86
ht-degree: 0%

---

# 小组件

可以组合多个基本组件（如组件部分中所述）来构成构件。
小组件可用于制作新的“更复杂”组件，或为组件的项目提供结构。

让我们深入了解小部件的概念！

我们首先制作一个简单的构件来显示语言列表。

```js title="basicWidget.js"
const widgetJSON =  {
    "component": "div", 
    "id": "widget_languages", 
    "items": [ // adding components to the widget
        {
            "component": "div",
            "items": [
                {
                    "component": "icon",
                    "icon": "info"
                },
                {
                    "component": "label",
                    "label": "List of some languages"
                }
            ]
        },
        {
            "component": "list",
            "data": "@languages"
        }
    ]
},
```

此处，`@languages`是在`widget_languages`的模型中定义的数组： [&quot;English&quot;、&quot;French&quot;、&quot;Hindi&quot;、&quot;Spanish&quot;、&quot;Urdu&quot;]

呈现的基本构件将如下所示：

![basic_widget](imgs/basic_widget.png "基本构件")
