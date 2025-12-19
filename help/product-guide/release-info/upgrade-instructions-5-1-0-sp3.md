---
title: 发行说明 | Adobe Experience Manager Guides 5.1.0 Service Pack 3版本的升级说明
description: 了解兼容性矩阵以及如何升级到Adobe Experience Manager Guides的5.1.0 Service Pack 3版本。
source-git-commit: 7ecf29537ddfbfcff644c4f6e3dff32750868282
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 1%

---

# 5.1.0 Service Pack 3版本（2025年12月）的升级说明

本文介绍了适用于Adobe Experience Manager Guides 5.1.0 Service Pack 3版本的升级说明和兼容性矩阵。

有关此版本中已修复的问题的列表，请查看[5.1.0 Service Pack 3版本](../release-info/fixed-issues-5-1-0-sp3.md)中已修复的问题。

## 兼容性矩阵

本部分列出了Experience Manager Guides 5.1.0版本支持的软件应用程序的兼容性矩阵。

### Adobe Experience Manager

**5.1.0 Service Pack 3 UUID**

版本6.5 Service Pack 23、Service Pack 22和Service Pack 21

有关更多详细信息，请查看On-Premise Installation and Configuration Guide中的[技术要求](../install-guide/download-install-technical-requirements.md)部分。

### FrameMaker和FrameMaker Publishing Server

| 发行版本 | FMPS | FM |
| --- | --- | --- |
| 5.1.0 Service Pack 3 (UUID) | 支持 | 2022或更高版本 |

### 氧气连接器

| 发行版本 | 氧气连接器窗口 | 氧气连接器Mac | 在氧气窗口中编辑 | 在氧气Mac中编辑 |
| --- | --- | --- |--- |--- |
| 5.1.0 Service Pack 3 (UUID) | 3.8-uuid.1 | 3.8-uuid.1 | 2.3 | 2.3 |

### 知识库模板版本

| 组件包名称 | 组件版本 | 模板版本 |
|---|---|---|
| 适用于Cloud Service的Experience Manager Guides组件内容包 | dxml-components.all-1.3.0 | aem-site-template-dxml.all-1.0.4 |

### 新的AEM站点模板版本


| 组件版本 | 站点版本 |
|---|---|
| guides-components.all-1.4.0 | aemg-docs.all-1.2.0 |


## 升级到Experience Manager Guides的5.1.0 Service Pack 3版本

您可以轻松地将最新版本的Guides升级到5.1.0 Service Pack 3版。 在继续升级到Experience Manager Guides的5.1.0版Service Pack 3之前，您必须考虑以下几点：

- 如果您使用的是版本5.1.0或5.1.x ，则可以直接升级到版本5.1.0 Service Pack 3。
- 如果您使用的是版本4.6.0、4.6.x、5.0.0或5.0.x，则需要升级到版本5.1.0。
- 如果您使用的是版本4.6.3、4.6.1、4.6或4.4，则需要升级到版本5.0.0。
- 如果您使用的是版本4.3.x、4.2、4.2.1（修补程序4.2.1.3）、4.1或4.1.x，则需要在升级到版本5.0.0之前升级到版本4.4。
- 如果您使用的是版本4.0，则需要先升级到版本4.2，然后再升级到版本4.3.x。
- 如果您使用的是版本3.8.5，则在升级到版本4.2之前需要升级到版本4.0。
- 如果您使用的版本低于3.8.5，请参阅[Adobe Experience Manager Guides帮助Experience Manager Guides存档](https://helpx.adobe.com/xml-documentation-for-experience-manager/archive.html)上提供的产品特定安装指南中的“升级PDF”部分。

>[!NOTE]
>
>在升级AEM版本之前，必须安装Experience Manager Guides Service Pack。

有关详细信息，请查看Experience Manager Guides内部部署版本[的](../install-guide/upgrade-xml-documentation.md)升级说明。
