---
title: 发行说明 | Adobe Experience Manager Guides 4.6.0 Service Pack 4版本的升级说明
description: 了解如何升级到Adobe Experience Manager Guides的4.6.0 Service Pack 4版本
role: Leader
source-git-commit: f6d5b1abb9e9a50d2564e8199b04129e3bc0f256
workflow-type: tm+mt
source-wordcount: '531'
ht-degree: 1%

---

# 4.6.0 Service Pack 4版本（2025年4月）的升级说明

介绍Adobe Experience Manager Guides 4.6.0 Service Pack 4版本的升级说明和兼容性矩阵。

有关此版本中已修复的问题的列表，请查看[4.6.0 Service Pack 4版本](fixed-issues-4-6-0-sp4.md)中已修复的问题。

## 兼容性矩阵

本部分列出了Experience Manager Guides 4.6.0 Service Pack 4版本支持的软件应用程序的兼容性矩阵。

### Adobe Experience Manager

**4.6.0 Service Pack 4非UUID**
版本6.5 Service Pack 21、20和19

**4.6.0 Service Pack 4 UUID**
版本6.5 Service Pack 21、20和19

有关更多详细信息，请查看On-Premise Installation and Configuration Guide中的[技术要求](../install-guide/download-install-technical-requirements.md)部分。

### FrameMaker和FrameMaker Publishing Server

| 发行版本 | FMPS 2022 | FMPS 2020 | FM 2022 | FM 2020 |
| --- | --- | --- | --- | --- |
| 4.6.0 Service Pack 4（非UUID） | 2022或更高版本 | 2020.2或更高版本* | 2022或更高版本 | 2020.3或更高版本 |
| 4.6.0 Service Pack 4 (UUID) | 2022或更高版本 | 2020.2或更高版本* | 2022或更高版本 | 2020.4或更高版本 |
| | | | |

*从2020.2开始的FMPS版本支持在AEM中创建的基线和条件。

### 氧气连接器

| 发行版本 | 氧气连接器窗口 | 氧气连接器Mac | 在氧气窗口中编辑 | 在氧气Mac中编辑 |
| --- | --- | --- |--- |--- |
| 4.6.0 Service Pack 4（非UUID） | 2.8-regular-10 | 2.8-regular-10 | 1.6 | 1.6 |
| 4.6.0 Service Pack 4 (UUID) | 3.6-uuid.9 | 3.6-uuid.9 | 2.3 | 2.3 |
|  |  |   |

### 知识库模板版本

| 组件包名称 | 组件版本 | 模板版本 |
|---|---|---|
| 适用于Cloud Service的Experience Manager Guides组件内容包 | dxml-components.all-1.2.2 | aem-site-template-dxml.all-1.0.15 |

### 新的AEM站点模板版本

| 组件版本 | 站点版本 |
|---|---|
| guides-components.all-1.0.0 | aemg-docs.all-1.0.0 |

## 升级到Experience Manager Guides的4.6.0 Service Pack 4版本

您可以轻松地将最新版本的Guides升级到4.6.0 Service Pack 4。 在继续升级之前，您必须考虑以下几点：

- 如果您使用的是版本4.6.0、4.6.0 Service Pack 1或4.6.0 Service Pack 3，则可以直接升级到4.6.0 Service Pack 4。
- 如果您使用的是版本4.4、4.3.1或4.3.0 ，则需要升级到版本4.6.0。
- 如果您使用的是版本4.2、4.2.1（修补程序4.2.1.3）、4.1或4.1.x，则需要在升级到版本4.6.0之前升级到版本4.4。
- 如果您使用的是版本4.0，则需要先升级到版本4.2，然后再升级到版本4.3.x。
- 如果您使用的是版本3.8.5，则在升级到版本4.2之前需要升级到版本4.0。
- 如果您使用的版本低于3.8.5，请参阅[Adobe Experience Manager Guides帮助Experience Manager Guides存档](https://helpx.adobe.com/cn/xml-documentation-for-experience-manager/archive.html)上提供的产品特定安装指南中的“升级PDF”部分。

>[!NOTE]
>
>在升级AEM版本之前，必须安装Experience Manager Guides Service Pack。

4.6.0 Service Pack 4版本的升级过程与4.6.0版本遵循的步骤相同。 有关详细说明，请查看Experience Manager Guides内部部署版本[&#128279;](../install-guide/upgrade-xml-documentation.md)的升级说明。
