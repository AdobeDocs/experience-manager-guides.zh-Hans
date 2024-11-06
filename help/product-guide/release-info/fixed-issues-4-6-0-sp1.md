---
title: 发行说明 | 修复了Adobe Experience Manager Guides 4.6.0 Service Pack 1版本中的问题
description: 了解Adobe Experience Manager Guides 4.6.0 Service Pack 1版本中的错误修复
role: Leader
source-git-commit: 2362870e0e3e6c08df03e8c547bb77de7faa0a02
workflow-type: tm+mt
source-wordcount: '316'
ht-degree: 0%

---


# 修复了4.6.0 Service Pack 1版本（2024年10月）中的问题


本文介绍Adobe Experience Manager Guides 4.6.0 Service Pack 1版本中修复的各个方面的错误。

了解4.6.0 Service Pack 1版本](upgrade-instructions-4-6-0-sp1.md)的[升级说明。

## 创作

- 在`XMLEditorConfig`中启用`xmleditor.uniquefilenames`时，在UUID实例上创建DITA映射失败。 (21201)
- 关闭文件时，在&#x200B;**保存更改和解锁文件**&#x200B;对话框中添加的注释和标签未使用新版本保存在版本历史记录中。 这特定于在`XMLEditorConfig`中启用了&#x200B;**Ask for Check in Close**&#x200B;或&#x200B;**Ask for New Version on Close**&#x200B;的使用案例。 (20065)
- 在保存新版本之前，标记为&#x200B;**Done**&#x200B;的文档状态将还原为&#x200B;**Draft**，从而导致&#x200B;**Done**&#x200B;状态不会在任何文档版本中持续存在。 (20006)
- 无法在Web编辑器的主题中将PDF文件添加为图像引用。 (21206)
- 在Assets UI中选择DITA文件会显示&#x200B;**在FrameMaker中打开**&#x200B;选项，即使在配置中禁用也是如此。 (20082)


## 发布

- 如果附件路径超过允许的长度，则将附件上传到Salesforce失败。 (19420)
- 将主题发布到Salesforce时，无法解析PDF文件链接。 (19304)
- 尝试在Salesforce中重新发布现有文章时，`DUPLICATE_VALUE`错误间歇性地出现。 (17932)
- 在本机PDF输出中，目录中的章节标题缺失，导致层次结构不正确。 (21840)
- 在发布AEM Sites时，目录中可包含的属性数量有限。 (7483)

## 管理

- 由于日志中出现未关闭的&#x200B;**ResourceResolver**&#x200B;错误，因此发生资源泄漏。 (18488)
- 创建新基线或复制基线时，标签以随机顺序显示。 (19307)









