---
title: 发行说明 | 修复了Adobe Experience Manager Guides 4.3.1.5版本中的问题
description: 了解Adobe Experience Manager Guides 4.3.1.5版本中的错误修复
role: Leader
exl-id: 082dca28-15da-417c-b511-74eb5ac68078
source-git-commit: e40ebf4122decc431d0abb2cdf1794ea704e5496
workflow-type: tm+mt
source-wordcount: '135'
ht-degree: 2%

---

# 修复了4.3.1.5版本中的问题


本文介绍Adobe Experience Manager Guides 4.3.1.5版本中修复的各个方面的错误。



了解4.3.1.5版本的[升级说明](../release-info/upgrade-instructions-4-3-1-5.md)。


## 创作

- 在`<codeblock>`中的内联元素之间添加空格会导致生成的输出中出现换行符。 (15247)
- 从“插入元素”对话框添加元素时出现体验问题。 (15108)

## 发布

- 错误日志显示有关使用外部范围发布内容的信息不正确。 (15242)
- 指向以`HTTP`开头的DITA文件的内部链接被视为外部链接，并导致范围错误。 (15155)
- DITA映射的AEM站点重新生成失败。 (14369)

## 管理

- **fmditaTopicrefs**&#x200B;属性显示相对路径而非绝对路径。 (15341)
