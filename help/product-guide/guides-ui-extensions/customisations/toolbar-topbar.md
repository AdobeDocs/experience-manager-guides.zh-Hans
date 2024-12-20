---
title: 顶部栏和工具栏
description: 自定义标题栏和工具栏
role: User, Admin
exl-id: 7065c9b8-67ac-4f6d-8124-daa547f2dc3b
source-git-commit: 4f41609368b64415993b93be27162b069e7b2e32
workflow-type: tm+mt
source-wordcount: '75'
ht-degree: 0%

---

# 自定义标题栏和工具栏

要自定义`topbar`和`toolbar`，我们将使用ID： `topbar`或`toolbar`，并遵循相同的视图、控制器结构。

以下是工具栏自定义的简单示例。 此处，我们删除了`Insert Numbered List`按钮，并使用自定义的单击处理程序将`Insert Paragraph`按钮替换为我们自己的组件。

要访问`proxy`对象下公开的功能，我们需要使用`this.proxy.getValue`来访问它，以表示用于获取值。

```js title = toolbar_customisation.js
const toolbarExtend = {
    id: "toolbar",
    view: {
        items: [
            {
                component: "div",
                target: {
                    key:"title",value: "Insert Numbered List",                    
                    viewState: VIEW_STATE.REPLACE
                }
            },
            {
                {
                    "component": "button",
                    "icon": "textParagraph",
                    "variant": "action",
                    "quiet": true,
                    "title": "Insert Paragraph",
                    "on-click": "INSERT_P"
                },

                target: {
                    key:"title",value: "Insert Paragraph",                    
                    viewState: VIEW_STATE.REPLACE
                }
            },
        ]
    },
    controller: {
        init: function() {
            console.log(this.proxy.getValue("canUndo"))
            this.proxy.subscribeAppEvent({
              key: "editor.preview_rendered",
              next: async function (e) {
                console.log(this.proxy.getValue("canUndo"))
              }.bind(this)
            })
        },
        INSERT_P(){
            this.next("AUTHOR_INSERT_ELEMENT",  "p" )
        }
    }
}
```
