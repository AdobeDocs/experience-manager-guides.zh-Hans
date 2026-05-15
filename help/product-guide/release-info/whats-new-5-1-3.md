---
title: 发行说明 | Adobe Experience Manager Guides 5.1.0 Service Pack 3版本中的新增功能
description: 了解Adobe Experience Manager Guides 5.1.0 Service Pack 3版本中的新增功能和增强功能
role: Leader
exl-id: 1b2e45a8-bea6-4b78-bd2e-cc02df86f40a
TQID: https://experienceleague.adobe.com/dXXQ1YvVduT11vvF5qyXHLqnuo1xMKkAb5I-EoD2JAA
product_v2:
  - id: fae5e35a-80c9-4b94-9352-1a060a6aab1d
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: a3bd6397-2eb2-4908-a61c-226e26855dca
subfeature_v2:
  - id: fd6cc9e1-e5e5-494e-b7b1-a32f2d6cd7c9
role_v2:
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
source-git-commit: 8ed5c9cb07c56b84b36ef56a55af8738989a6d3f
workflow-type: tm+mt
source-wordcount: 176
ht-degree: 0%

---

# 5.1.0 Service Pack 3版（2025年12月）的新增功能

本文介绍Adobe Experience Manager Guides版本5.1.0 Service Pack 3中引入的新增功能和增强功能。

有关此版本中已修复的问题的列表，请查看[5.1.0 Service Pack 3版本](fixed-issues-5-1-0-sp3.md)中已修复的问题。

了解5.1.0 Service Pack 3版本[&#128279;](../release-info/upgrade-instructions-5-1-0-sp3.md)的升级说明。


## 为特定输出预设配置自定义图像演绎版

您现在可以使用`renditionmapping.xml`中的`outputName`属性为同一输出类型下的各个输出预设配置不同的图像演绎版。 此增强功能让您在发布需要针对不同场景采用不同图像分辨率的内容时拥有更大的灵活性。 例如，您可能希望主HTML5输出使用高分辨率图像，同时为轻型预设使用较小的缩略图。

有关更多详细信息，请查看[处理输出生成](../install-guide/conf-output-generation.md#handle-image-rendition-during-output-generation)中的图像演绎版。
