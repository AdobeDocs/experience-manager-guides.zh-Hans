---
title: 发行说明 | Adobe Experience Manager Guides 2024.04.0版本中的升级说明和修复的问题
description: 了解兼容性矩阵以及如何升级到Adobe Experience Manager Guidesas a Cloud Service的2024.04.0版本。
exl-id: deca46e5-12cc-497f-84af-61ee02da3d65
source-git-commit: 989f1628adf417167525a068845203380573b077
workflow-type: tm+mt
source-wordcount: '916'
ht-degree: 4%

---

# 2024.04.0版的升级说明

本文介绍Adobe Experience Manager Guides as a Cloud Service 2024.04.0版的升级说明和兼容性矩阵。

有关新功能和增强功能的更多信息，请查看 [2024.04.0 版本中的新增功能](whats-new-2024-04-0.md)。

有关此版本中修复的问题列表，请查看 [2024.04.0 版本中已修复的问题](fixed-issues-2024-04-0.md)。

## 兼容性矩阵

本部分列出了2024.04.0版Experience Manager Guidesas a Cloud Service支持的软件应用程序的兼容性矩阵。

### FrameMaker和FrameMaker Publishing Server

| Experience Manager Guides as a Cloud | FMPS | FrameMaker |
| --- | --- | --- |
| 2024.04.0 | 不兼容 | 2022或更高版本 |
| | | |


### 氧气连接器

| Experience Manager Guides as a Cloud | 氧气连接器窗口 | 氧气连接器Mac | 在氧气窗口中编辑 | 在氧气Mac中编辑 |
| --- | --- | --- | --- | --- |
| 2024.04.0 | 3.5-uuid 1 | 3.5-uuid 1 | 2.3 | 2.3 |
|  |  |  |  |


### 知识库模板版本

| 组件包名称 | 组件版本 | 模板版本 |
|---|---|---|
| 适用于Cloud Service的Experience Manager Guides组件内容包 | dxml-components.all-1.2.2 | aem-site-template-dxml.all-1.0.15 |

## 升级到2024.04.0版

Experience Manager Guides会在升级当前（最新）版本的Experience Manageras a Cloud Service时自动升级。

>[!NOTE]
>
> 开始使用当前（最新）版本后，将任何覆盖的配置与最新配置进行比较，以获取最新功能：
>- ui_config.json（可能已在文件夹配置文件中设置）



如果您之前尚未对现有版本实施Experience Manager Guidesas a Cloud Service，请对其执行以下步骤：

### 通过servlet启用脚本触发器的步骤

(仅当使用的版本早于2023年6月的Experience Manager Guidesas a Cloud Service版本时)

完成安装后，您可以选择点击触发器以启动翻译作业：

POST：

```
http://localhost:4503/bin/guides/script/start?jobType=translation-map-upgrade
```

响应：

```
{
"msg": "Job is successfully submitted and lock node is created for future reference",
"lockNodePath": "/var/dxml/executor-locks/translation-map-upgrade/1683190032886",
"status": "SCHEDULED"
}
```

在上一个响应JSON中，键`lockNodePath`保存指向在存储库中创建的指向已提交作业的节点的路径。 作业完成后会自动将其删除，然后您可以引用此节点来了解作业的状态。

请等待此作业完成，然后再继续后续步骤。

>[!NOTE]
>
> 您应该检查节点是否仍然存在，以及作业的状态。

```
GET
http://<aem_domain>/var/dxml/executor-locks/translation-map-upgrade/1683190032886.json
```

### 后处理现有内容以使用断开链接报表的步骤

(仅当使用的版本早于2023年6月的Experience Manager Guidesas a Cloud Service版本时)

执行以下步骤对现有内容进行后处理，并使用新的断开链接报表：

1. （可选）如果系统中有超过100,000个DITA文件，请将`org.apache.jackrabbit.oak.query.QueryEngineSettingsService`下的`queryLimitReads`和`queryLimitInMemory`更新为更大的值（任何大于现有资产数的值，例如200,000），然后重新部署。

   - 按照安装和配置Adobe Experience Manager Guides as a Cloud Service中的&#x200B;*配置覆盖*&#x200B;部分提供的说明创建配置文件。
   - 在配置文件中，提供以下（属性）详细信息以配置`queryLimitReads`和`queryLimitInMemory`选项：

     | PID | 属性键 | 属性值 |
     |---|---|---|
     | org.apache.jackrabbit.oak.query.QueryEngineSettingsService | queryLimitRead | 值：200000默认值：100000 |
     | org.apache.jackrabbit.oak.query.QueryEngineSettingsService | queryLimitInMemory | 值：200000默认值：100000 |

1. 对服务器运行POST请求（使用正确的身份验证） — `http://<server>//bin/guides/reports/upgrade`。

1. API返回jobId。 要检查作业的状态，可以将带有作业ID的GET请求发送到同一终结点 — `http://<server>/bin/guides/reports/upgrade?jobId= {jobId}`
（例如： `http://localhost:8080/bin/guides/reports/upgrade?jobId=2022/9/15/7/27/7dfa1271-981e-4617-b5a4-c18379f11c42_678`）

1. 作业完成后，先前的GET请求会成功响应。 如果作业由于某个原因失败，则可以从服务器日志中看到失败。

1. 如果您在步骤1中更改了`queryLimitReads`的值，请恢复为默认或以前的现有值。

### 为现有内容编制索引以使用“报表”选项卡下的新查找和替换以及主题列表的步骤：

(仅当使用的版本早于2023年6月的Experience Manager Guidesas a Cloud Service版本时)

执行以下步骤来索引现有内容，并在报表选项卡下的映射级别和主题列表中使用新的查找和替换文本：

1. 对服务器运行POST请求（使用正确的身份验证） — `http://<server:port>/bin/guides/map-find/indexing`。 (可选：您可以传递映射的特定路径以对其进行索引，默认情况下，所有映射都会被索引|| 例如：`https://<Server:port>/bin/guides/map-find/indexing?paths=<path of the MAP in repository>`)

1. 您还可以传递根文件夹来索引特定文件夹（及其子文件夹）的DITA映射。 例如，`http://<server:port\>/bin/guides/map-find/indexing?root=/content/dam/test`。请注意，如果同时传递了路径参数和根参数，则只考虑路径参数。

1. API返回jobId。 要检查作业的状态，可以将带有作业ID的GET请求发送到同一终结点 — `http://<server:port>/bin/guides/map-find/indexing?jobId={jobId}`（例如： `http://localhost:8080/bin/guides/reports/upgrade?jobId=2022/9/15/7/27/7dfa1271-981e-4617-b5a4-c18379f11c42_678`）

1. 作业完成后，先前的GET请求会成功响应。 如果作业由于某个原因失败，则可以从服务器日志中看到该失败。

### 处理`'fmdita rewriter'`冲突的步骤

Experience Manager Guides有一个&#x200B;[**自定义sling重写器**](../cs-install-guide/conf-output-generation.md#custom-rewriter)&#x200B;模块，用于处理在交叉映射（两个不同映射的主题之间的链接）情况下生成的链接。

如果您的代码库中有另一个自定义sling重写器，请使用大于50的`'order'`值，因为Experience Manager Guides sling重写器使用`'order'` 50。 要覆盖此值，您需要一个大于50的值。 有关详细信息，请查看[输出重写管道](https://sling.apache.org/documentation/bundles/output-rewriting-pipelines-org-apache-sling-rewriter.html)。

在此升级过程中，由于`'order'`值从1000更改为50，因此您需要将现有的自定义重写器（如果有）与`fmdita-rewriter`合并。
