---
title: 发行说明 | Adobe Experience Manager Guides 4.3.1.5版的升级说明
description: 了解如何升级到Adobe Experience Manager Guides的4.3.1.5版本
role: Leader
exl-id: 856970ef-9f50-4452-b589-ba1f5ee73322
source-git-commit: e40ebf4122decc431d0abb2cdf1794ea704e5496
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 2%

---

# 4.3.1.5版本的升级说明

介绍Adobe Experience Manager Guides 4.3.1.5版的升级说明和兼容性矩阵。


有关此版本中已修复的问题的列表，请查看[4.3.1.5版本中已修复的问题](../release-info/fixed-issues-4-3-1-5.md)。




## 兼容性矩阵

本部分列出了Experience Manager Guides 4.3.1.5版本支持的软件应用程序的兼容性矩阵。

### Adobe Experience Manager

**4.3.1.5非UUID**
版本6.5 Service Pack 18、17、16、15、14

**4.3.1.5 UUID**
版本6.5 Service Pack 18、17、16、15、14

有关更多详细信息，请查看On-Premise Installation and Configuration Guide中的&#x200B;*技术要求*&#x200B;部分。

### FrameMaker和FrameMaker Publishing Server

| 发行版本 | FMPS 2022 | FMPS 2020 | Fm 2022 | Fm 2020 |
| --- | --- | --- | --- | --- |
| 4.3.1.5（非UUID） | 2022或更高版本 | 2020.2或更高版本* | 2022或更高版本 | 2020.3或更高版本 |
| 4.3.1.5 (UUID) | 2022或更高版本 | 2020.2或更高版本* | 2022或更高版本 | 2020.4或更高版本 |
| | | | |

*从2020.2开始的FMPS版本支持在AEM中创建的基线和条件。

### 氧气连接器

| 发行版本 | 氧气连接器窗口 | 氧气连接器Mac | 在氧气窗口中编辑 | 在氧气Mac中编辑 |
| --- | --- | --- |--- |--- |
| 4.3.1.5（非UUID） | 2.3 — 常规–5 | 2.3 — 常规–5 | 1.6 | 1.6 |
| 4.3.1.5 (UUID) | 3.2-uuid-5 | 3.2-uuid-5 | 2.3 | 2.3 |
|  |  |   |



### 知识库模板版本

| 组件包名称 | 组件版本 | 模板版本 |
|---|---|---|
| 适用于Cloud Service的Experience Manager Guides组件内容包 | dxml-components.all-1.2.2 | aem-site-template-dxml.all-1.0.15 |



## 升级到Experience Manager Guides的4.3.1.5版


您可以轻松地将指南的当前版本升级到4.3.1.5版。在继续升级到版本4.3.1.5的Experience Manager Guides之前，必须考虑以下几点：


- 如果您使用的是版本4.3.1或4.3.1.x ，则可以直接升级到版本4.3.1.5。
- 如果您使用的是版本4.3.0或4.2（修补程序4.2.1.3），则需要在升级到版本4.3.1.5之前升级到版本4.3.1。

- 如果您使用的是版本4.1或4.1.x ，则需要先升级到版本4.3.1，然后再升级到版本4.3.1.5。


- 如果您使用的是版本4.0，则需要先升级到版本4.2，然后再升级到版本4.3.x。
- 如果您使用的是版本3.8.5，则在升级到版本4.2之前需要升级到版本4.0。
- 如果您使用的版本低于3.8.5，请参阅[Adobe Experience Manager Guides帮助PDF存档](https://helpx.adobe.com/xml-documentation-for-experience-manager/archive.html)上提供的产品特定安装指南中的“升级Experience Manager Guides”部分。



>[!NOTE]
>
>在升级Experience Manager Guides版本之前，必须安装AEM Service Pack。

有关详细信息，请查看Experience Manager Guides内部部署版本[&#128279;](../install-guide/upgrade-xml-documentation.md)的升级说明。
