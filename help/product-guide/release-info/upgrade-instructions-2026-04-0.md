---
title: 发行说明| 2026.04.0版Adobe Experience Manager Guides中的升级说明和修复问题
description: 了解兼容性矩阵以及如何升级到Adobe Experience Manager Guides as a Cloud Service的2026.04.0版本。
source-git-commit: ce2c9da0d9beb05a15f7cefcf9483e0c93abbf37
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 11%

---

# 2026.04.0版的升级说明

本文介绍Adobe Experience Manager Guides as a Cloud Service 2026.04.0版的升级说明和兼容性矩阵。

有关新功能和增强功能的更多信息，请查看 [2026.04.0 版本中的新增功能](whats-new-2026-04-0.md)。

有关此版本中修复的问题列表，请查看 [2026.04.0 版本中已修复的问题](fixed-issues-2026-04-0.md)。

## 兼容性矩阵

本节介绍Experience Manager Guides as a Cloud Service 2026.04.0版本支持的软件应用程序的兼容性矩阵。

### FrameMaker和FrameMaker Publishing Server

| Experience Manager Guides as a Cloud | FMPS | FrameMaker | 氧气作者 |
| --- | --- | --- | --- |
| 2026.04.0 | 不兼容 | 2022或更高版本 | 26.1 |


### 氧气连接器

| Experience Manager Guides as a Cloud | 氧气连接器窗口 | 氧气连接器Mac | 在氧气窗口中编辑 | 在氧气Mac中编辑 |
| --- | --- | --- | --- | --- |
| 2026.04.0 | 3.8 -uuid 1 | 3.8 -uuid 1 | 2.3 | 2.3 |


### AEM站点模板版本

| 组件版本 | 站点版本 |
|---|---|
| guides-components.all-1.4.0 | aemg-sites-template-1.3.0 |

### 知识库模板版本

| 组件包名称 | 组件版本 | 模板版本 |
|---|---|---|
| 适用于Cloud Service的Experience Manager Guides组件内容包 | guides-components.all-1.4.0 | aem-site-template-dxml-1.0.17 |

## 升级到2026.04.0版

Experience Manager Guides在升级到最新版本的Experience Manager as a Cloud Service时自动升级。

>[!IMPORTANT]
>
> 此版本包括对文件夹配置文件设置(ui_config.json)的更新。 如果您使用的是自定义设置，请确保在升级之前备份这些设置。 更新后，查看并调整您的设置，以与最新版本中引入的更改保持一致。

查看并验证您的设置配置，以确认它们已正确实施。 如果您已引入任何自定义配置更改，请查看[升级Cloud Service的其他配置](../cs-install-guide/additional-config-for-cloud-service.md)，了解适用于您从中升级版本的任何其他过程。
