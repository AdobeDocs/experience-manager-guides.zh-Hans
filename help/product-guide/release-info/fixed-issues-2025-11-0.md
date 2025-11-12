---
title: 发行说明 | 修复了Adobe Experience Manager Guides 2025.11.0版本中的问题
description: 了解Adobe Experience Manager Guides as a Cloud Service 2025.11.0版本中的错误修复。
source-git-commit: d9a46a009477b1110208a509d4ad8c0616139661
workflow-type: tm+mt
source-wordcount: '704'
ht-degree: 3%

---

# 修复了2025.11.0版本中的问题

本文介绍Adobe Experience Manager Guides as a Cloud Service 2025.11.0版本中修复的各个方面的错误。

有关新功能和增强功能的更多信息，请查看 [2025.11.0 版本中的新增功能](whats-new-2025-11-0.md)。

了解2025.11.0版本[的](upgrade-instructions-2025-11-0.md)升级说明。

## 创作

- 如果将没有属性或值的空`prop`元素添加到DITAVAL文件中，则无法添加其他`prop`元素。 (指南 — 33597)
- 将Experience Manager Guides升级到2025.08.0版本后，**Workspace设置**&#x200B;中不再显示启用或禁用自定义&#x200B;**Acrolinx**&#x200B;选项卡的选项。 (指南 — 35261)
- 在浏览器刷新时，在主题或映射的文件夹级别配置文件中应用的自定义CSS将恢复到预览模式中的默认样式。 (指南 — 31098)
- **撤消**&#x200B;和&#x200B;**重做**&#x200B;操作在DITA文件编辑器的Source视图中无法按预期工作。 (GUIDES-24914和GUIDES-25034)
- 使用`Xref`元素在主题中引用DITA映射时，将显示引用的映射的文件名而不是映射标题。 (指南 — 21759)
- 通过编辑器界面的右侧面板添加多个Schematron文件进行验证时，即使添加的文件有效且没有错误，也会显示错误&#x200B;**Schematron文件不存在或存在错误**。 (指南 — 33731)
- 大型或复杂的MathML公式无法在编辑器中显示。 (指南 — 29095)

## 资产管理

- 当您通过Experience Manager Guides UI重新上传编辑后的图像时，图像的原始演绎版会更新，但关联的DITA内容会继续显示图像的先前版本。 (指南 — 33693)
- 当尝试将两个或更多文件夹从它们的源位置移动到不同的位置时（使用批量移动工具），如果文件夹名称以相同的字符串开头（例如Product和ProductImages），则操作失败。 (指南 — 29096)
- 从Omnisearch Assets UI中删除搜索出的资源时，会绕过&#x200B;**强制删除**&#x200B;警告对话框并直接删除该资源，即使它在现有DITA内容中被引用也是如此。 (指南 — 17232)

## 发布

- 在AEM Sites上使用基线（使用旧版组件映射）发布DITA映射时，也会发布属性为`processing-role = resource-only`的映射元素。 (指南 — 37649)
- 在某些情况下，发现AEM Sites输出页面（具有旧版组件映射）中缺少`jcr:content/fmUuidOfSource`属性，导致新创建的内容页面不可发现。
- 通过DITAVal过滤器和条件预设进行内容过滤不适用于Salesforce发布。 (指南 — 33515)
- 如果地图内容层次结构中存在同名文件夹，则无法为地图创建本机PDF预设。 (指南 — 33012)
- 使用动态基线生成本机PDF输出时，术语&#x200B;**PDFProject**&#x200B;显示为PDF标题，而不是实际的映射标题。 (指南 — 31102)
- 在主题引用中生成具有某些`print`属性值的本机PDF输出无法按预期工作。 (指南 — 31101)
- 使用Assets UI或&#x200B;**批量移动**&#x200B;选项移动包含DITA映射的文件夹时，无法加载引用这些映射的现有映射集合和批量激活集合。 (指南 — 28355)
- 移动包含带有条件预设的映射的文件夹时，移动后生成的输出中不应用条件。 (指南 — 28352)
- 使用旧版组件映射生成AEM Sites输出时，使用`copy-to`属性的主题将通过`copy-from`主题的名称（而不是`copy-to`属性中设置的名称）发布。 (指南 — 22155)
- 从&#x200B;**批量发布仪表板**&#x200B;激活一个或多个DITA映射会生成超大日志。 (指南 — 20746)

## 平台

- 通过Assets UI上传资源或从编辑器界面创建新文件时生成的错误日志，在日志消息中错误地使用术语`predecessor`而不是`successor`。 (指南 — 35607)

## 已知问题

Adobe发现了2025.11.0版本的以下已知问题：

- 使用`copy-to`属性创建重复主题并使用`scope=peer`属性引用该主题会导致AEM Sites输出中出现重定向问题，其中链接会从AEM Sites（使用复合组件映射）重定向到AEM Sites（使用旧版组件映射），反之亦然。 (指南 — 37656)











