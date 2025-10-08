---
title: 发行说明 | Adobe Experience Manager Guides 5.1.0版本的升级说明
description: 了解兼容性矩阵以及如何升级到Adobe Experience Manager Guides的5.1.0版本。
exl-id: 4b7b6756-d260-4baf-a9cb-d99fc02f020f
source-git-commit: 6bcfed792036a51aa0c11498e4cb489199280a56
workflow-type: tm+mt
source-wordcount: '520'
ht-degree: 7%

---

# 5.1.0版（2025年9月）的升级说明

本文介绍5.1.0版本的Adobe Experience Manager Guides的升级说明和兼容性矩阵。

有关新功能和增强功能的更多信息，请查看 [5.1.0 版本中的新增功能](../release-info/whats-new-5-1-0.md)。

有关此版本中已修复的问题的列表，请查看[5.1.0版本](../release-info/fixed-issues-5-1-0.md)中已修复的问题。

## 兼容性矩阵

本部分列出了Experience Manager Guides 5.1.0版本支持的软件应用程序的兼容性矩阵。

| AEM Guides | AEM 版本 | 服务包 |
| --- | --- | --- |
| 5.1.0 (UUID) | 6.5 LTS | 1 |
| 5.1.0 (UUID) | 6.5 | 23、22、21 |

有关更多详细信息，请查看On-Premise Installation and Configuration Guide中的[技术要求](../install-guide/download-install-technical-requirements.md)部分。

### FrameMaker和FrameMaker Publishing Server

| 发行版本 | FMPS | FM |
| --- | --- | --- |
| 5.1.0 (UUID) | 支持 | 2022或更高版本 |

### 氧气连接器

| 发行版本 | 氧气连接器窗口 | 氧气连接器Mac | 在氧气窗口中编辑 | 在氧气Mac中编辑 |
| --- | --- | --- |--- |--- |
| 5.1.0 (UUID) | 3.8-uuid.1 | 3.8-uuid.1 | 2.3 | 2.3 |

### 知识库模板版本

| 组件包名称 | 组件版本 | 模板版本 |
|---|---|---|
| 适用于Cloud Service的Experience Manager Guides组件内容包 | dxml-components.all-1.3.0 | aem-site-template-dxml.all-1.0.4 |

### 新的AEM站点模板版本


| AEM Guides | AEM 版本 | 组件版本 | 站点版本 |
|---|---|---| ---|
| 5.1.0 UUID | 6.5 LTS | guides-components.all-1.4.1 | aemg-docs.all-1.2.0 |
| 5.1.0 UUID | 6.5 | guides-components.all-1.4.0 | aemg-docs.all-1.2.0 |

## 升级到Experience Manager Guides 5.1.0

您可以在&#x200B;**Experience Manager Guides 6.5**&#x200B;或&#x200B;**AEM 6.5 LTS**&#x200B;上轻松将AEM的当前版本升级到版本5.1.0。

>[!NOTE]
>
> 如果您当前使用AEM 6.5，并计划迁移到AEM 6.5 LTS，请确保先完成AEM升级，然后再继续进行Experience Manager Guides 5.1.0升级。 有关详细信息，请查看[升级到Adobe Experience Manager (AEM) 6.5 LTS](https://experienceleague.adobe.com/zh-hans/docs/experience-manager-65-lts/content/implementing/deploying/upgrading/upgrade)。

在继续升级到版本5.1.0的Experience Manager Guides之前，必须考虑以下几点：

- 如果您使用的是版本4.6.3、4.6.4、5.0.0或5.0.0 Service Pack 1，则可以直接升级到版本5.1.0。
- 如果您使用的是版本4.6.0、4.6.1，则需要在升级到版本5.1.0之前升级到版本4.6.3、4.6.4或5.0.0。
- 如果您使用的是版本4.3.x、4.2、4.2.1（修补程序4.2.1.3）、4.1或4.1.x，则需要在升级到版本5.1.0之前升级到版本4.4。
- 如果您使用的是版本4.0，则需要先升级到版本4.2，然后再升级到版本4.3.x。
- 如果您使用的是版本3.8.5，则在升级到版本4.2之前需要升级到版本4.0。
- 如果您使用的版本低于3.8.5，请参阅[Adobe Experience Manager Guides帮助Experience Manager Guides存档](https://helpx.adobe.com/cn/xml-documentation-for-experience-manager/archive.html)上提供的产品特定安装指南中的“升级PDF”部分。

>[!NOTE]
>
>在升级AEM版本之前，必须安装Experience Manager Guides Service Pack。

有关详细信息，请查看Experience Manager Guides内部部署版本[的](../install-guide/upgrade-xml-documentation.md)升级说明。


