---
title: 发行说明 |Adobe Experience Manager Guides 5.2.0版本的升级说明
description: 了解兼容性矩阵以及如何升级到Adobe Experience Manager Guides的5.2.0版本。
source-git-commit: a2d4731af4f4996c87dd177a6e45f1d8ebabd6cf
workflow-type: tm+mt
source-wordcount: '859'
ht-degree: 4%

---

# 5.2.0版（2026年5月）的升级说明

本文介绍Adobe Experience Manager Guides 5.2.0版的升级说明和兼容性矩阵。

有关新增功能和增强功能的详细信息，请查看[5.2.0版本中的新增功能](../release-info/whats-new-5-2-0.md)。

有关此版本中已修复的问题的列表，请查看[5.2.0版本](../release-info/fixed-issues-5-2-0.md)中已修复的问题。

## 兼容性矩阵

本部分列出了Experience Manager Guides 5.2.0版本支持的软件应用程序的兼容性矩阵。

| AEM Guides | AEM 版本 | 服务包 |
| --- | --- | --- |
| 5.2.0 (UUID) | 6.5 LTS | 2 |
| 5.2.0 (UUID) | 6.5 | 24, 23, 22 |

有关更多详细信息，请查看On-Premise Installation and Configuration Guide中的[技术要求](../install-guide/download-install-technical-requirements.md)部分。

### FrameMaker和FrameMaker Publishing Server

| 发行版本 | FMPS | FM |
| --- | --- | --- |
| 5.2.0 (UUID) | 支持 | 2026或更高版本 |

### 氧气连接器

| 发行版本 | 氧气连接器窗口 | 氧气连接器Mac | 在氧气窗口中编辑 | 在氧气Mac中编辑 |
| --- | --- | --- |--- |--- |
| 5.2.0 (UUID) | 3.8-uuid.1 | 3.8-uuid.1 | 2.3 | 2.3 |

### 知识库模板版本

| 组件包名称 | 组件版本 | 模板版本 |
|---|---|---|
| 适用于Cloud Service的Experience Manager Guides组件内容包 | guides-components.all-1.4.0 | aem-site-template-dxml-1.0.17 |

### 新的AEM站点模板版本


| AEM Guides | AEM 版本 | 组件版本 | 站点版本 |
|---|---|---| ---|
| 5.2.0 UUID | 6.5 LTS | guides-components.all-1.4.1 | NA |
| 5.2.0 UUID | 6.5 | guides-components.all-1.4.0 | aemg-sites-template-1.3.0 |

## 先决条件

在开始Experience Manager Guides 5.2.0升级过程之前，请确保您具有：

1. 已升级到Experience Manager Guides版本5.0.0、5.0.3、5.1.0、5.1.3或5.1.4。
1. （可选）已关闭所有翻译任务。
1. 已将`com.adobe.fmdita.translationservices.TranslationMapUpgradeScript`类的日志级别更改为&#x200B;**INFO**，并将这些日志附加到新的日志文件中，例如`logs/translation_upgrade.log`。

## Experience Manager Guides 5.2.0升级路径

您可以在&#x200B;**Experience Manager Guides 6.5**&#x200B;或&#x200B;**AEM 6.5 LTS**&#x200B;上轻松将AEM的当前版本升级到版本5.2.0。

>[!IMPORTANT]
>
> - **对于AEM 6.5 LTS**：只有Experience Manager Guides 6.5 LTS Service Pack 2支持AEM 5.2.0。
> - **对于AEM 6.5**：只有Experience Manager Guides 6.5 Service Pack 24、23和22支持AEM 5.2.0。
> - 如果您当前使用AEM 6.5，并计划迁移到AEM 6.5 LTS，请确保先完成AEM升级，然后再继续进行Experience Manager Guides 5.2.0升级。 有关详细信息，请查看[升级到Adobe Experience Manager (AEM) 6.5 LTS](https://experienceleague.adobe.com/en/docs/experience-manager-65-lts/content/implementing/deploying/upgrading/upgrade)。

在继续升级到版本5.2.0的Experience Manager Guides之前，必须考虑以下几点：

- 如果您使用的是版本5.0.0、5.0.3、5.1.0、5.1.3或5.1.4，则可以直接升级到版本5.2.0。
- 如果您使用的是版本4.6.3、4.6.4、5.0.x，则可以直接升级到版本5.1.0。
- 如果您使用的是版本4.6.0、4.6.1，则需要在升级到版本5.1.0之前升级到版本4.6.3、4.6.4或5.0.0。
- 如果您使用的是版本4.3.x、4.2、4.2.1（修补程序4.2.1.3）、4.1或4.1.x，则需要在升级到版本5.1.0之前升级到版本4.4。
- 如果您使用的是版本4.0，则需要先升级到版本4.2，然后再升级到版本4.3.x。
- 如果您使用的是版本3.8.5，则在升级到版本4.2之前需要升级到版本4.0。
- 如果您使用的版本低于3.8.5，请参阅[Adobe Experience Manager Guides帮助Experience Manager Guides存档](https://helpx.adobe.com/xml-documentation-for-experience-manager/archive.html)上提供的产品特定安装指南中的“升级PDF”部分。

## Experience Manager Guides 5.2.0升级过程

>[!IMPORTANT]
>
> 后处理并编制索引可能需要几个小时。 我们建议您在非高峰时间启动升级过程。

1. 从[Adobe软件分发门户](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html)下载5.2.0版本包。
1. 安装要升级的版本包，然后等待包安装完毕。
1. *（可选）*&#x200B;随要升级到的版本一起发布的升级氧气连接器插件。
1. 安装包后清除浏览器缓存。
1. 如果已启用设置`Enable markup find and replace`来访问先前捕获内容的源视图中的查找和替换功能，则必须重新索引`guidesAssetLucene`索引。 有关详细信息，请查看[重新索引以查找和替换](../install-conf-guide/custom-indexing-on-prem.md)。
1. 更新系统配置以纳入5.2.0版中引入的新设置，从而确保支持以下增强功能：


| 已添加配置 | 配置文件 | 显示设置的标签 | 设置的名称 |
|-----|-----|------|-----|
| 启用或禁用“新建编辑器” | `com.adobe.fmdita.config.ConfigManager` | 启用编辑器2.0 | `enable.markup.editor` |
| 启用或禁用“新建基线” | `com.adobe.fmdita.config.ConfigManager` | 启用更快的基线(v2) | `enable.baseline.v2` |
| 忽略元数据属性以将版本标记为已修改 | `com.adobe.fmdita.xmleditor.config.XmlEditorConfig` | 忽略已更新版本的元数据属性 | `xmleditor.dirtychecker.ignoremetadata` |
| Source视图中的查找和替换功能 | `com.adobe.fmdita.config.ConfigManager` | 启用标记查找和替换 | `enable.markup.findreplace` |
| 启用或禁用跳过旧基线的对等链接 | `com.adobe.fmdita.config.ConfigManager` | 跳过基线V1的对等链接 | `guides.baseline.v1.skip.peer.links` |
| 启用或禁用在翻译工作流中使用源内容初始化目标副本。仅当禁用旧版翻译工作流时，此选项才适用。  | `com.adobe.fmdita.config.ConfigManager` | 使用源内容初始化目标语言副本 | `translation.workflow.propagate.source.content` |
| 引用存储清理 | `com.adobe.fmdita.config.ConfigManager` | 指南树删除已启用 | `btree.deletion.enabled` |
| DITA资产复制 | `com.adobe.fmdita.config.ConfigManager` | 复制DITA资产 | `publish.replicate` |
| 资产处理 | `com.adobe.fmdita.config.ConfigManager` | 启用Guides资产处理计划作业 | `enable.asset.processing.scheduler` |

有关这些配置设置的详细信息，请查看[配置更新](../install-conf-guide/configuration-on-prem.md)。







