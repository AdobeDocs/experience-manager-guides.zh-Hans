---
title: 发行说明 | 修复了Adobe Experience Manager Guides 5.0.0 Service Pack 1版本中的问题
description: 了解Adobe Experience Manager Guides 5.0.0 Service Pack 1版本中的错误修复
role: Leader
source-git-commit: 083a8e16b9d3cd6c3894d7eaa2fee489b1dc0bb8
workflow-type: tm+mt
source-wordcount: '293'
ht-degree: 1%

---


# 修复了5.0.0 Service Pack 1版本（2025年6月）中的问题


本文介绍Adobe Experience Manager Guides 5.0.0 Service Pack 1版本中修复的各个方面的错误。

了解5.0.0 Service Pack 1版本[&#128279;](upgrade-instructions-5-0-0-sp1.md)的升级说明。

## 创作

- 将内容粘贴到`codeblock`中或在`codeblock`中添加空格并切换视图时，间距将丢失。 (指南 — 29347)
- 在&#x200B;**Source**&#x200B;视图的元素中添加XML注释时，切换视图时注释周围的前导和尾随空格将丢失。 (指南 — 28188)

## 资产管理

- 在浏览器刷新后在&#x200B;**创作**&#x200B;视图中打开主题时，**文件属性**&#x200B;面板中先前应用的标记不会保留，添加新标记会覆盖现有标记，尤其是当大量标记可供选择时。 (指南 — 29078)
- 在为包含大量资源的DITA映射生成元数据报告时，**管理**&#x200B;按钮变得无响应或显示延迟响应。 (指南 — 29778)

## 翻译

- 从Experience Manager Guides发送要翻译的资源时，这些资源不会添加到翻译作业中，这会阻止显示&#x200B;**开始**&#x200B;按钮，并阻止您启动翻译作业。 (指南 — 28237)

## 发布

- 在文件夹配置文件中修改输出预设的设置并选择&#x200B;**应用预设更改**&#x200B;时，更改不会传播到DITA映射中存在的输出预设。 (指南 — 26694)

## 审查

- 尝试通过AEM工作流创建审核任务总是失败，因为未创建审核节点。 (指南 — 28214)
