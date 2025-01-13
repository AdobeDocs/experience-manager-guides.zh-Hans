---
title: 发行说明 | 修复了Adobe Experience Manager Guides 2024.12.0版本中的问题
description: 了解Adobe Experience Manager Guidesas a Cloud Service2024.12.0版本中的错误修复。
source-git-commit: f643a4a22151af2ff14288ab3885c1a6657a80ca
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 1%

---

# 修复了2024.12.0版本中的问题

本文介绍Adobe Experience Manager Guides as a Cloud Service 2024.12.0版本中修复的各个方面的错误。

了解2024.12.0版本](./upgrade-instructions-2024-12-0.md)的[升级说明。

## 创作

- 在`XMLEditorConfig`中启用`xmleditor.uniquefilenames`时，在UUID实例上创建DITA映射失败。 (21201)
- 关闭文件时，在&#x200B;**保存更改和解锁文件**&#x200B;对话框中添加的注释和标签未使用新版本保存在版本历史记录中。 这特定于在`XMLEditorConfig`中启用了&#x200B;**Ask for Check in Close**&#x200B;或&#x200B;**Ask for New Version on Close**&#x200B;的使用案例。 (20065)
- 在保存新版本之前，标记为&#x200B;**Done**&#x200B;的文档状态将还原为&#x200B;**Draft**，从而导致&#x200B;**Done**&#x200B;状态不会在任何文档版本中持续存在。 (20006)
- 无法在Web编辑器的主题中将PDF文件添加为图像引用。 (21206)
- 在Assets UI中选择DITA文件会显示&#x200B;**在FrameMaker中打开**&#x200B;选项，即使在配置中禁用也是如此。 (20082)

## 发布

- 在本机PDF输出中，目录中的章节标题缺失，导致层次结构不正确。 (21840)


## 管理

- 由于日志中存在&#x200B;**未关闭的ResourceResolver**&#x200B;错误，因此发生资源泄漏。 (18488)
- 创建新基线或复制基线时，标签以随机顺序显示。 (19307)


## 基准线

- 如果基线具有大量主题或地图，则编辑1分钟后在云设置上保存基线会超时。 (19558)

## 翻译

- 使用基线的映射转换变得缓慢，最终无法加载所有关联主题和映射文件的列表。 (19733)
