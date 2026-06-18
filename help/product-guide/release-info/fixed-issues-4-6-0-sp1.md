---
title: 发行说明 |修复了Adobe Experience Manager Guides 4.6.0 Service Pack 1版本中的问题
description: 了解Adobe Experience Manager Guides 4.6.0 Service Pack 1版本中的错误修复
role: Leader
exl-id: ab45ac10-8a97-4ade-accc-2b884da0e973
TQID: https://experienceleague.adobe.com/-PGxudGeachzaYoru1fHTObZcwRuXzle5s7KRRJlfBA
product_v2: id: fae5e35a-80c9-4b94-9352-1a060a6aab1did: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2: id: a3bd6397-2eb2-4908-a61c-226e26855dcaid: ab01a588-7dea-43f2-a699-0b3f128465d6id: cb8c6a2a-3c38-4e40-867c-756f8c36bb0e
subfeature_v2: id: ad602516-aca3-4247-9ae8-f393d958efa9id: d4f22c6d-7923-41e5-9da3-527ff8df4bc8id: f89f75b0-cf2e-4e96-aec8-fe8c39cbd0ef
role_v2: id: f8a45b24-4be7-4f1b-909b-60d06b483a20
source-git-commit: cc73b81787a3c3dbe8390d93e558064327e59965
workflow-type: tm+mt
source-wordcount: 311
ht-degree: 4%

---

# 修复了4.6.0 Service Pack 1版本（2024年10月）中的问题


本文介绍Adobe Experience Manager Guides 4.6.0 Service Pack 1版本中修复的各个方面的错误。

了解4.6.0 Service Pack 1版本](upgrade-instructions-4-6-0-sp1.md)的[升级说明。

## 创作

- 在`XMLEditorConfig`中启用`xmleditor.uniquefilenames`时，在UUID实例上创建DITA映射失败。 (21201)
- 关闭文件时，在&#x200B;**保存更改和解锁文件**&#x200B;对话框中添加的注释和标签未使用新版本保存在版本历史记录中。 这特定于在`XMLEditorConfig`中启用了&#x200B;**Ask for Check in Close**&#x200B;或&#x200B;**Ask for New Version on Close**&#x200B;的使用案例。 (20065)
- 在保存新版本之前，标记为&#x200B;**Done**&#x200B;的文档状态将还原为&#x200B;**Draft**，从而导致&#x200B;**Done**&#x200B;状态不会在任何文档版本中持续存在。 (20006)
- 无法将PDF文件作为图像引用添加到编辑器中的主题中。 (21206)
- 在Assets UI中选择DITA文件会显示&#x200B;**在FrameMaker中打开**&#x200B;选项，即使在配置中禁用也是如此。 (20082)


## 发布

- 如果附件路径超过允许的长度，则将附件上传到Salesforce失败。 (19420)
- 将主题发布到Salesforce时，无法解析PDF文件链接。 (19304)
- 尝试在Salesforce中重新发布现有文章时，`DUPLICATE_VALUE`错误间歇性地出现。 (17932)
- 在本机PDF输出中，目录中的章节标题缺失，导致层级不正确。 (21840)
- 在发布AEM Sites时，目录中可包含的属性数量有限。 (7483)

## 管理

- 由于日志中出现未关闭的&#x200B;**ResourceResolver**&#x200B;错误，因此发生资源泄漏。 (18488)
- 创建新基线或复制基线时，标签以随机顺序显示。 (19307)
