---
title: 发行说明 |修复了Adobe Experience Manager Guides 4.6.0 Service Pack 4版本中的问题
description: 了解Adobe Experience Manager Guides 4.6.0 Service Pack 4版本中的错误修复
role: Leader
exl-id: ad69ea47-7880-43d1-8567-cd608fedb462
TQID: https://experienceleague.adobe.com/4ILARUO5umX41xE3Lcie-FsP396sgSqfbrWlMqdjsQ4
product_v2:
  - id: fae5e35a-80c9-4b94-9352-1a060a6aab1d
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: a3bd6397-2eb2-4908-a61c-226e26855dca
  - id: ab01a588-7dea-43f2-a699-0b3f128465d6
subfeature_v2:
  - id: d6596f3f-92a7-43ec-b444-237db6adad05
role_v2:
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
source-git-commit: 8ed5c9cb07c56b84b36ef56a55af8738989a6d3f
workflow-type: tm+mt
source-wordcount: 234
ht-degree: 4%

---

# 修复了4.6.0 Service Pack 4版本（2025年4月）中的问题


本文介绍Adobe Experience Manager Guides 4.6.0 Service Pack 4版本各个方面修复的错误。

了解4.6.0 Service Pack 4版本[&#128279;](upgrade-instructions-4-6-0-sp4.md)的升级说明。

## 创作

- 在&#x200B;**作者**&#x200B;视图的主题中拖放图像会导致图像引用中断，从而导致数据丢失。 (25769)
- 在&#x200B;**作者**&#x200B;视图的映射中拖放`topicref`无法执行预期操作，并删除被拖动`topicref`旁边的`topicref`。 (19460)
- 在更新或创建主题时无法关闭JCR会话连接，会导致内存泄漏和服务停机。 (26282)

## 发布

- 如果DITA内容具有Weblink且范围不为`external`，则本机PDF发布将无限期继续。 (26434)
- 创建具有大量标签的新基线时，会导致标签加载器失败并阻止获取标签。 (16232)
- 当内容中出现错误时，原生PDF和AEM站点的发布会停止并排队等候。 (26516)

## 已知问题

Adobe已发现此版本的以下已知问题：

- 当DITA内容包含不包含`scope`属性的外部链接时，Windows上的本机PDF发布会遇到失败。
