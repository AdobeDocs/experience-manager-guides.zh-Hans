---
title: 发行说明 |Adobe Experience Manager Guides 4.3.1.5版本的升级说明
description: 了解如何升级到Adobe Experience Manager Guides的4.3.1.5版本
role: Leader
exl-id: 856970ef-9f50-4452-b589-ba1f5ee73322
TQID: https://experienceleague.adobe.com/wN9EyxDaR5dSTnaUQIqKV-8jhbw2LUj36vpeUd8Obc4
product_v2: id: fae5e35a-80c9-4b94-9352-1a060a6aab1did: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2: id: a3bd6397-2eb2-4908-a61c-226e26855dcaid: afb45297-4313-4f67-818e-bc0b03abe086id: cb8c6a2a-3c38-4e40-867c-756f8c36bb0e
subfeature_v2: id: d5ea0417-7932-4688-a3e2-4d3b2e7076a3
role_v2: id: f8a45b24-4be7-4f1b-909b-60d06b483a20
source-git-commit: 8ed5c9cb07c56b84b36ef56a55af8738989a6d3f
workflow-type: tm+mt
source-wordcount: 434
ht-degree: 2%

---

# 4.3.1.5版本的升级说明

本文介绍Adobe Experience Manager Guides 4.3.1.5版本的升级说明和兼容性矩阵。


有关此版本中已修复的问题的列表，请查看4.3.1.5版本](../release-info/fixed-issues-4-3-1-5.md)中的[已修复问题。




## 兼容性矩阵

本节列出了Experience Manager Guides 4.3.1.5版本支持的软件应用程序的兼容性矩阵。

### Adobe Experience Manager

**4.3.1.5个非UUID**
版本6.5 Service Pack 18、17、16、15、14

**4.3.1.5UUID**
版本6.5 Service Pack 18、17、16、15、14

有关更多详细信息，请查看On-Premise Installation and Configuration Guide中的&#x200B;*技术要求*&#x200B;部分。

### FrameMaker和FrameMaker Publishing Server

| 发行版本 | FMPS 2022 | FMPS 2020 | Fm 2022 | Fm 2020 |
| --- | --- | --- | --- | --- |
| 4.3.1.5 （非UUID） | 2022或更高版本 | 2020.2或更高版本* | 2022或更高版本 | 2020.3或更高版本 |
| 4.3.1.5 (UUID) | 2022或更高版本 | 2020.2或更高版本* | 2022或更高版本 | 2020.4或更高版本 |
| | | | | |

*从2020.2开始的FMPS版本支持在AEM中创建的基线和条件。

### 氧气连接器

| 发行版本 | 氧气连接器窗口 | 氧气连接器Mac | 在氧气窗口中编辑 | 在氧气Mac中编辑 |
| --- | --- | --- |--- |--- |
| 4.3.1.5 （非UUID） | 2.3 — 常规–5 | 2.3 — 常规–5 | 1.6 | 1.6 |
| 4.3.1.5 (UUID) | 3.2-uuid-5 | 3.2-uuid-5 | 2.3 | 2.3 |
|  |  |   | | |



### 知识库模板版本

| 组件包名称 | 组件版本 | 模板版本 |
|---|---|---|
| 适用于Cloud Service的Experience Manager Guides组件内容包 | dxml-components.all-1.2.2 | aem-site-template-dxml.all-1.0.15 |



## 升级到Experience Manager Guides的4.3.1.5版本


您可以轻松地将指南的当前版本升级到版本4.3.1.5。 在继续升级到版本4.3.1.5的Experience Manager Guides之前，必须考虑以下几点：


- 如果您使用的是版本4.3.1或4.3.1.x ，则可以直接升级到版本4.3.1.5。
- 如果您使用的是版本4.3.0或4.2（修补程序4.2.1.3），则需要先升级到版本4.3.1，然后再升级到版本4.3.1.5。

- 如果您使用的是版本4.1或4.1.x，则需要升级到版本4.3.1后再升级到版本4.3.1.5。


- 如果您使用的是版本4.0，则需要先升级到版本4.2，然后再升级到版本4.3.x。
- 如果您使用的是版本3.8.5，则在升级到版本4.2之前需要升级到版本4.0。
- 如果您使用的版本低于3.8.5，请参阅[Adobe Experience Manager Guides帮助Experience Manager Guides存档](https://helpx.adobe.com/xml-documentation-for-experience-manager/archive.html)上提供的产品特定安装指南中的“升级PDF”部分。



>[!NOTE]
>
>在升级AEM版本之前，必须安装Experience Manager Guides Service Pack。

有关详细信息，请查看Experience Manager Guides内部部署版本](../install-guide/upgrade-xml-documentation.md)的[升级说明。
