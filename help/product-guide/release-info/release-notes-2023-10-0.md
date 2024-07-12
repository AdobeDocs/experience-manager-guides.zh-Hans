---
title: 发行说明 | Adobe Experience Manager Guides 2023年10月版中的升级说明和修复的问题
description: 了解错误修复以及如何升级到Adobe Experience Manager Guidesas a Cloud Service的2023年10月版
exl-id: 536d2ec2-31a0-4533-9c29-16a27525acca
feature: Release Notes
role: Leader
source-git-commit: 6d8c01f20f7b59fed92c404561b647d9ebecb050
workflow-type: tm+mt
source-wordcount: '1045'
ht-degree: 1%

---

# 2023年10月版的Adobe Experience Manager Guidesas a Cloud Service

此发行说明涵盖了升级说明、兼容性矩阵，以及Adobe Experience Manager Guides版本2023年10月中修复的问题(后称为&#x200B;*AEM Guidesas a Cloud Service*)。

有关新增功能和增强功能的更多信息，请参阅[AEM Guides as a Cloud Service 2023年10月版的新增功能](whats-new-2023-10-0.md)。

## 升级到2023年10月版

请通过以下步骤升级当前的AEM Guidesas a Cloud Service设置：

1. 查看Cloud Service的Git代码，并切换到在Cloud Service管道中配置的与要升级的环境对应的分支。
2. 将Cloud ServiceGit代码的`/dox/dox.installer/pom.xml`文件中的`<dox.version>`属性更新为2023.10.0.373。
3. 提交更改并运行Cloud Service管道，以升级到AEM Guidesas a Cloud Service的2023年10月版。

## 通过servlet启用脚本触发器的步骤

(仅限您使用的版本低于2023年6月发行的AEM Guidesas a Cloud Service)

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

在上一个响应JSON中，键`lockNodePath`保存指向在存储库中创建的指向已提交作业的节点的路径。 作业完成后该节点会被自动删除，在此之前，您可以引用此节点以获取作业的当前状态。

请等待此作业完成，然后再继续后续步骤。

>[!NOTE]
>
> 您应该检查节点是否仍然存在，以及作业的状态。

```
GET
http://<aem_domain>/var/dxml/executor-locks/translation-map-upgrade/1683190032886.json
```

## 后处理现有内容以使用断开链接报表的步骤

(仅限您使用的版本低于2023年6月发行的AEM Guidesas a Cloud Service)

执行以下步骤对现有内容进行后处理，并使用新的断开链接报表：

1. （可选）如果系统中有超过100,000个DITA文件，请将`org.apache.jackrabbit.oak.query.QueryEngineSettingsService`下的`queryLimitReads`更新为更大的值（任何大于现有资产数的值，例如200,000），然后重新部署。

   - 按照安装和配置Adobe Experience Manager Guides as a Cloud Service中的&#x200B;*配置覆盖*&#x200B;部分提供的说明创建配置文件。
   - 在配置文件中，提供以下（属性）详细信息以配置queryLimitReads选项：

     | PID | 属性键 | 属性值 |
     |---|---|---|
     | org.apache.jackrabbit.oak.query.QueryEngineSettingsService | queryLimitRead | 值：200000默认值：100000 |

1. 对服务器运行POST请求（使用正确的身份验证） — `http://<server:port>//bin/guides/reports/upgrade`。

1. API返回jobId。 要检查作业的状态，可以将带有作业ID的GET请求发送到同一终结点 — `http://<server:port>/bin/guides/reports/upgrade?jobId= {jobId}`
（例如： `http://localhost:8080/bin/guides/map-find/indexing?jobId=2022/9/15/7/27/7dfa1271-981e-4617-b5a4-c18379f11c42_678`）

1. 作业完成后，先前的GET请求会成功响应。 如果作业由于某个原因失败，则可以从服务器日志中看到失败。

1. 如果您在步骤1中更改了`queryLimitReads`的值，请恢复为默认或以前的现有值。

## 为现有内容编制索引以使用“报表”选项卡下的新查找和替换以及主题列表的步骤：

(仅限您使用的版本低于2023年6月发行的AEM Guidesas a Cloud Service)

执行以下步骤来索引现有内容，并在报表选项卡下的映射级别和主题列表中使用新的查找和替换文本：

1. 对服务器运行POST请求\（使用正确的身份验证\） - `http://<server:port\>/bin/guides/map-find/indexing`。 (可选：您可以传递映射的特定路径以对其进行索引，默认情况下，所有映射都将进行索引\|\| 例如：`https://<Server:port\>/bin/guides/map-find/indexing?paths=<map\_path\_in\_repository\>`)

1. 您还可以传递根文件夹来索引特定文件夹（及其子文件夹）的DITA映射。 例如，`http://<server:port\>/bin/guides/map-find/indexing?root=/content/dam/test`。请注意，如果同时传递了路径参数和根参数，则只考虑路径参数。

1. API返回jobId。 要检查作业的状态，可以将带有作业ID的GET请求发送到同一终结点 — `http://<server:port\>/bin/guides/map-find/indexing?jobId=\{jobId\}`\（例如： `http://localhost:8080/bin/guides/map-find/indexing?jobId=2022/9/15/7/27/7dfa1271-981e-4617-b5a4-c18379f11c42`\）


1. 作业完成后，先前的GET请求会做出成功响应，并提及是否有任何映射失败。 可以从服务器日志中确认已成功编制索引的映射。

## 兼容性矩阵

本部分列出了AEM Guides as a Cloud Service 2023年10月版支持的软件应用程序的兼容性矩阵。

### FrameMaker和FrameMaker Publishing Server

| AEM Guides as a Cloud | FMPS | FrameMaker |
| --- | --- | --- |
| 2023.10.0 | 不兼容 | 2022或更高版本 |
| | | |


### 氧气连接器

| AEM Guides as a Cloud | 氧气连接器窗口 | 氧气连接器Mac | 在氧气窗口中编辑 | 在氧气Mac中编辑 |
| --- | --- | --- | --- | --- |
| 2023.10.0 | 3.2-uuid 5 | 3.2-uuid 5 | 2.3 | 2.3 |
|  |  |  |  |


### 知识库模板版本

| 组件包名称 | 组件版本 | 模板版本 |
|---|---|---|
| 适用于Cloud Service的AEM Guides组件内容包 | dxml-components.all-1.2.2 | aem-site-template-dxml.all-1.0.15 |

## 修复的问题

修复了多个区域中的错误如下：

### 创作

- 没有为创建基线在&#x200B;**日期**&#x200B;设置下午时间。 (12712)
- 无法在Web编辑器的`<codeblock>`元素中粘贴JSON代码。 (12326)
- 未保存的版本更改，大型文件不会显示更改后的指示符。 (11784)
- 以韩语编辑时，第一个字符会更改为默认字符。 (10049)


### 发布

- 本机PDF | 生成PDF输出时，主题的顺序未固定。 (13157)
- 本机PDF| `<p>`元素没有可用的默认样式标记。 (12559)
- 本机PDF | 应用于内容区域的内联样式不会应用于前件和后件主题。 (13510)
- 生成AEM Site输出时未传播`DeliveryTarget`特性。  (13132)
- 为包含某些错误的内容生成AEM站点输出时，**Publish**&#x200B;工作流卡住。 (12000)

### 管理

- 即使资产的`dc:format`属性不存在，版本历史记录也不会显示。 (10463)


### 审查

- 有关主题的“复查”显示不正确的注释。 (13453)



### 翻译

- 从&#x200B;**翻译**&#x200B;仪表板导出的基线失败，且未以目标语言打开。 (13466)

- 将创建新的翻译项目，而不是向选定的现有翻译项目添加新作业。  (10214)

## 已知问题

Adobe已发现2023年10月版本的以下已知问题。

- 内容片段重新发布失败。
