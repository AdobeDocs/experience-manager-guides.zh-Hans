---
title: 自定义应用程序
description: 自定义应用程序
role: User, Admin
exl-id: 3e454c48-2168-41a5-bbab-05c8a5b5aeb1
source-git-commit: 3615928117ce1be527dc3c6d2ec8ddd115b78b0a
workflow-type: tm+mt
source-wordcount: '486'
ht-degree: 0%

---

# 自定义应用程序

## 扩展框架下公开的功能

我们在`proxy`下公开了一组函数和getter，它们可用于访问数据、配置和触发事件。 以下是列表及其访问方式。

```typescript
interface EventData {
  key?: string,
  keys?: string[]
  view?: any,
  next?: any,
  error?: any,
  completed?: any,
  id?: any
}

* getValue(key)
* setValue(key, value)
* subject // getter
* subscribe(opts: EventData)
* subscribeAppEvent(opts: EventData)
* subscribeAppModel(key, next)
* subscribeParentEvent(opts: EventData)
* parentEventHandlerNext(eventName: string, opts: any)
* appModelNext(eventName:string, opts) 
* appEventHandlerNext(eventName:string, opts)
* next(eventName:string, opts, eventHandler?)
* viewConfig //getter
* args //getter
```

我们的应用程序遵循MVC（模型、视图、控制器）结构

## 模型

模型定义各种属性并存储其值。 可使用语法从控制器访问存储在模型中的各种属性的值

```typescript
this.getValue('attributeName')
```

对于在应用程序中自定义，所有新创建的属性都将添加到模型中的映射下。
要在模型中设置新属性，我们将在控制器中使用以下语法：

```typescript
// If a key is not already in model then it will be added to extraProps
this.setValue('key', value)
```

要访问添加到模型中的属性，我们将使用以下语法：

```typescript
const value = this.getValue("key")
```

## 查看

该视图定义应用程序的UI。 我们使用JSON文件来定义文件的视图。 在本例中，我们定义组件和css（如组件外的示例中所提供），并渲染存储在模型中的值。
在我们的应用程序中，每个视图都使用JSON进行定义。 JSON是使用其称为`id`的唯一ID引用的。

## 控制器

控制器用于处理事件和处理数据。 控制器用于从服务器获取和发送数据，是UI上显示的内容与存储在后端上的内容之间的接口。

- 要在初始化时设置值，我们使用`init`函数。
- 要将方法添加到控制器，请使用以下语法：

```typescript
methodName: function(args){
    // functionality
}
```

此处的`methodName`用作引用JSON（视图）或其他函数中的方法的`key`

- 要在控制器中调用方法，请使用语法

```typescript
this.next('methodName', args)
```

## 示例

现在，我们通过一个简单的示例来演示这3个组件如何彼此进行交互。
我们将添加一个按钮，该按钮可在单击时切换其标签值

### 查看示例

下面我们定义了一个按钮的JSON，该按钮显示在变量名称`buttonLabel`下存储在模型中的动态文本。
在此示例中，单击按钮将更改其标签。

```JSON
{
    "component": "button",
    "label": "@extraProps.buttonLabel",
    "variant": "cta",
    "on-click": "switchButtonLabel",
}
```

### 模型示例

在这种情况下，`extraProps.buttonLabel`保存按钮的标签

### 控制器示例

```typescript
  controller: {
    init: function () {
      this.setValue("buttonLabel", "Submit")
    },

    switchButtonLabel(){
        const buttonLabel = this.getValue("buttonLabel") === "Submit"? "Cancel" : "Submit"
        this.setValue("buttonLabel", buttonLabel)
    }
  }
```

以下GIF显示了正在运行的上述代码
![basic_customization](imgs/basic_customisation.gif "基本自定义按钮")


### 查看配置示例

在此情况下，我们使用`viewConfig`访问搜索模式事件并触发事件以更新它

```typescript
  { 
    id: 'repository_panel', 
    controller: {
      init: function () {
        console.log('Logging view config ', this.viewConfig)
        this.next(this.viewConfig.items[1].searchModeChangedEvent, { searchMode: true })
      }
    }
  }
```

### 订阅示例

在这种情况下，我们将在单击文件重命名选项时将有关文件重命名的订阅添加到控制台日志中

```typescript
  { 
    id: 'repository_panel', 
    controller: {
      init: function () {
        this.subscribe({
          key: 'rename',
          next: () => { console.log('rename using extension') }
        })
      }
    }
  }
```

### 订阅应用程序事件示例

在本例中，我们控制台登录已更改的活动文档（更改编辑器UI中的选项卡）

```typescript
  { 
    id: 'repository_panel', 
    controller: {
      init: function () {
        this.subscribeAppEvent({
          key: 'app.active_document_changed',
          next: () => { console.log('Extension: active document changed') }
        })
      }
    }
  }
```

### 订阅应用程序模型事件示例

订阅应用程序模型事件的示例，例如`app.mode`

```typescript
  { 
    id: 'repository_panel', 
    controller: {
      init: function () {
        this.subscribeAppModel('app.mode',
          () => { console.log('app mode subs') }
        )
      }
    }
  }
```

### 父控制器事件示例

在此内容中，我们为`tabChange`事件添加订阅，该事件是`left_panel_container`控制器的事件，将起作用
作为`repository_panel`的父控制器

```typescript
  { 
    id: 'repository_panel', 
    controller: {
      init: function () {
        this.subscribeParentEvent({
          key: 'tabChange',
          next: () => { console.log('tab change subs') }
        })
        this.parentEventHandlerNext('tabChange', {
          data: 'map_panel'
        )
      }
    }
  }
```

### 下一页App模型和应用控制器

它们可以通过知道要触发的正确事件及其数据直接触发

```typescript
  { 
    id: 'file_options', 
    controller: {
      init: function () {
        this.appModelNext('app.mode', 'author')
        this.appEventHandlerNext('app.active_document_changed', 'active doc changed')   
      }
    }
  } 
```
