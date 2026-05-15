---
title: 发行说明 |修复了Adobe Experience Manager Guides 4.3.1.5版本中的问题
description: 了解Adobe Experience Manager Guides 4.3.1.5版本中的错误修复
role: Leader
exl-id: 082dca28-15da-417c-b511-74eb5ac68078
TQID: https://experienceleague.adobe.com/ujQFyhAp5bIB1OJnmqvbHCaiDip7T2qsjlVAWevykK8
product_v2: id: fae5e35a-80c9-4b94-9352-1a060a6aab1did: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2: id: a3bd6397-2eb2-4908-a61c-226e26855dcaid: ab01a588-7dea-43f2-a699-0b3f128465d6
role_v2: id: f8a45b24-4be7-4f1b-909b-60d06b483a20
source-git-commit: 8ed5c9cb07c56b84b36ef56a55af8738989a6d3f
workflow-type: tm+mt
source-wordcount: 130
ht-degree: 6%

---

# 修复了4.3.1.5版本中的问题


本文介绍Adobe Experience Manager Guides 4.3.1.5版本中各个方面修复的错误。



了解4.3.1.5版本](../release-info/upgrade-instructions-4-3-1-5.md)的[升级说明。


## 创作

- 在`<codeblock>`中的内联元素之间添加空格会导致生成的输出中出现换行符。 (15247)
- 从“插入元素”对话框添加元素时出现体验问题。 (15108)

## 发布

- 错误日志显示有关使用外部范围发布内容的信息不正确。 (15242)
- 指向以`HTTP`开头的DITA文件的内部链接被视为外部链接，并导致范围错误。 (15155)
- DITA映射的AEM站点重新生成失败。 (14369)

## 管理

- **fmditaTopicrefs**&#x200B;属性显示相对路径而非绝对路径。 (15341)
