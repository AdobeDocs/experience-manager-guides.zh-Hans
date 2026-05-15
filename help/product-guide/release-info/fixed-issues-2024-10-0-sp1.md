---
title: 发行说明 |修复了Adobe Experience Manager Guides 2024.10.0 Service Pack 1版本中的问题
description: 了解Adobe Experience Manager Guides as a Cloud Service 2024.10.0 Service Pack 1版本中的错误修复。
exl-id: d5fa200b-1f15-4ec2-adf9-a29382afc3de
TQID: https://experienceleague.adobe.com/ziRAAFKf5Dl-6Hd7ziXwSJepbiVzkXLGz5jDWIILPkU
product_v2: id: fae5e35a-80c9-4b94-9352-1a060a6aab1did: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2: id: a3bd6397-2eb2-4908-a61c-226e26855dcaid: ab01a588-7dea-43f2-a699-0b3f128465d6id: cb8c6a2a-3c38-4e40-867c-756f8c36bb0e
subfeature_v2: id: ad602516-aca3-4247-9ae8-f393d958efa9id: d4f22c6d-7923-41e5-9da3-527ff8df4bc8id: f89f75b0-cf2e-4e96-aec8-fe8c39cbd0ef
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554
source-git-commit: 8ed5c9cb07c56b84b36ef56a55af8738989a6d3f
workflow-type: tm+mt
source-wordcount: 299
ht-degree: 5%

---

# 修复了2024.10.0 Service Pack 1版本中的问题

本文介绍Adobe Experience Manager Guides as a Cloud Service 2024.10.0 Service Pack 1版本中各个方面修复的错误。

## 创作

- 在`XMLEditorConfig`中启用`xmleditor.uniquefilenames`时，在UUID实例上创建DITA映射失败。 (21201)
- 关闭文件时，在&#x200B;**保存更改和解锁文件**&#x200B;对话框中添加的注释和标签未使用新版本保存在版本历史记录中。 这特定于在`XMLEditorConfig`中启用了&#x200B;**Ask for Check in Close**&#x200B;或&#x200B;**Ask for New Version on Close**&#x200B;的使用案例。 (20065)
- 在保存新版本之前，标记为&#x200B;**Done**&#x200B;的文档状态将还原为&#x200B;**Draft**，从而导致&#x200B;**Done**&#x200B;状态不会在任何文档版本中持续存在。 (20006)
- 无法在Web编辑器的主题中添加PDF文件作为图像引用。 (21206)
- 在Assets UI中选择DITA文件会显示&#x200B;**在FrameMaker中打开**&#x200B;选项，即使在配置中禁用也是如此。 (20082)

## 发布

- 在本机PDF输出中，目录中的章节标题缺失，导致层级不正确。 (21840)


## 管理

- 由于日志中存在&#x200B;**未关闭的ResourceResolver**&#x200B;错误，因此发生资源泄漏。 (18488)
- 创建新基线或复制基线时，标签以随机顺序显示。 (19307)


## 基准线

- 如果基线具有大量主题或地图，则编辑1分钟后在云设置中保存基线会超时。 (19558)

## 翻译

- 使用基线的映射转换变得缓慢，最终无法加载所有关联主题和映射文件的列表。 (19733)
