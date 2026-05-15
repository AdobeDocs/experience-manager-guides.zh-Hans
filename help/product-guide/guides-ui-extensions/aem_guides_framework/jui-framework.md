---
title: Jui框架
description: 了解Jui框架
role: User, Admin
exl-id: c193cf90-5916-4d8c-88f1-be5014beca1c
TQID: https://experienceleague.adobe.com/AQFEy2bHTDHXq6QH8KTBOEzUvtA3Hf2ojhxvD0dsI7o
product_v2: id: fae5e35a-80c9-4b94-9352-1a060a6aab1did: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2: id: a01bfd36-4ab8-4bf8-9dc0-5b45b890552eid: c6d09140-3c91-45d3-b7ed-b681af752f43id: cb8c6a2a-3c38-4e40-867c-756f8c36bb0e
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
source-git-commit: 8ed5c9cb07c56b84b36ef56a55af8738989a6d3f
workflow-type: tm+mt
source-wordcount: 268
ht-degree: 1%

---

# Jui框架

在开始了解如何编写扩展之前，我们将了解框架的结构。
以便我们能够有效地推广它。

## 简介

JUI是一个基于React和Adobe React Spectrum组件的MVC框架。 JUI是JSON用户界面。 它包含多个Git存储库。

JUI-Core是核心库，具有将JSON配置转换为工作react组件并将其链接到相关控制器类实例的所有逻辑。
JUI-React-Spectrum库具有Adobe React Spectrum组件的包装构件

## JUI核心设计

### MVC UI设计

![JUI MVC流](./imgs/jui-mvc-flow.png)

### 小组件

- 具有唯一ID。
- 具有要查看的单个JSON文件。
- 可以拥有自己的或共享的控制器。
- 可以使用父模型或新模型。
- 可以具有UI元素（React组件）
- 可以有其他构件
- 应用程序是一个小组件

![JUI小组件](./imgs/jui-widget.png)

### 元素

- 是HTML/React组件。
- 没有任何模型，它使用父构件模型。

### 事件处理程序

- 下一个(eventOpts)
   - 使用某些选项触发事件
- 订阅（回调）
   - 获取有关事件是通过配置触发的通知

### 应用程序/全局模型

- 下一个（新值）
   - 要发布新值
- 订阅（回调）
   - 获取值更改的通知
   - 首次获取旧值
- GetValue()
   - 获取当前值

### 控制器

- 它应从Controller类扩展
- API
- 创建模型
   - 要创建子小部件独立模型，请执行以下操作
- InitEventHandler
   - 创建子小部件单独事件处理程序
- RegisterCommand
   - 注册本地、父或应用程序事件
- 下一个(eventName， eventHandler)
   - 触发子构件事件处理程序、父构件事件处理程序或应用程序事件处理程序的事件
- Subscribe(callback， eventHandler)
- SubscribeAppModel(callback)

### 示例应用程序设计

![示例应用程序](./imgs/jui-sample-app.png)
