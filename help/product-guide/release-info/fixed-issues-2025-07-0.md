---
title: 发行说明 |修复了Adobe Experience Manager Guides 2025.07.0版本中的问题
description: 了解Adobe Experience Manager Guides as a Cloud Service 2025.07.0版本中的错误修复。
exl-id: 0744e821-5aee-432b-a6c8-7ed6538935db
TQID: https://experienceleague.adobe.com/xzYzEvtyVvvIpq3tfLftkCDuiC08hahdNhr5ZXcQPo8
product_v2: id: fae5e35a-80c9-4b94-9352-1a060a6aab1did: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2: id: a3bd6397-2eb2-4908-a61c-226e26855dcaid: ab01a588-7dea-43f2-a699-0b3f128465d6
subfeature_v2: id: ad602516-aca3-4247-9ae8-f393d958efa9
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2: id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dcid: ce44533e-8ec8-4e11-a9e9-78b0fe561832
source-git-commit: 8ed5c9cb07c56b84b36ef56a55af8738989a6d3f
workflow-type: tm+mt
source-wordcount: 520
ht-degree: 4%

---

# 修复了2025.07.0版本中的问题

本文介绍Adobe Experience Manager Guides as a Cloud Service 2025.07.0版本中修复的各个方面的错误。

有关新功能和增强功能的更多信息，请查看 [2025.07.0 版本中的新增功能](whats-new-2025-07-0.md)。

了解2025.07.0版本](upgrade-instructions-2025-07-0.md)的[升级说明。

## 创作

- 在Source视图的元素中添加XML注释时，切换视图时注释周围的前导和尾随空格会丢失。 （指南 — 29781）
- 当位于工具栏中的省略号图标（**更多**&#x200B;菜单）内时，多媒体选项不起作用。 （指南 — 29583）
- 通过Assets UI或编辑器创建新主题时，如果在`XMLEditorConfig`中将`xmleditor.uniquefilenames`设置设置为true，则不会在编辑器中自动打开该主题。 （指南 — 28171）
- 切换编辑器视图时，不会保留在Source视图的MathML公式中添加的空格。 （指南 — 26111）

## 资产管理

- 在浏览器刷新后在“创作”视图中打开主题时，先前在“文件属性”面板中应用的标记不会保留，添加新标记会覆盖现有标记，尤其是当大量标记可供选择时。 （指南 — 29078）
- 在为包含大量资源的DITA映射生成元数据报告时，**管理**&#x200B;按钮变得无响应或显示延迟响应。 （指南 — 28443）

## 审阅

- 尝试通过AEM工作流创建审核任务失败，因为未创建审核节点。 （指南 — 28214）

## 发布

- 通过Cloud Manager部署AEM Sites发布组件包`guides-components.all-1.3.0.zip`时出现代码质量错误。 （指南 — 28873）
- 发布具有`chunk=to-content`属性的DITA映射会在新的AEM Sites输出中创建重复的JCR节点，从而导致AEM Sites中存在冗余的内容结构。 （指南 — 28104）
- 使用新的AEM Sites输出发布DITA映射时，如果主题具有`chunk =to-content`属性并且输出设置为使用主题标题作为页面名称，则生成的页面名称错误地显示单词&#x200B;**区块**，而不是保留原始主题名称。 （指南 — 28102）
- 在新AEM Sites发布的AEM Guides主题模板中设置的`cq:template`属性显示不正确的值，这将影响模板结构和内容渲染。 （指南 — 27789）


## 平台

- 处理大型收藏集时，发现加载时间较长以及间歇性超时等性能问题。 （GUIDES-29065和GUIDES-28793）
- 与在Experience Manager Guides上传的AEM Guides组件中使用的已弃用Guava库相关的漏洞。(GUIDES-27402)

## 已知问题

Adobe发现了2025.07.0版本的以下已知问题：

- 使用Markdown主题时，“编辑器”工具栏中会显示&#x200B;**主题引用**&#x200B;按钮，但该按钮无法正常工作。 （指南 — 31038）
- 在编辑器中，文件夹节点名称无法正确代替文件夹标题显示。 （指南 — 30909）
- 在&#x200B;**合并**&#x200B;对话框中，下拉列表错误地显示&#x200B;**主内容**，而不是显示所选主题的可用版本。 （指南 — 30820）
- 在启用Unified Shell的情况下打开DITA映射时，编辑器会间歇性地刷新。(GUIDES-26919)
