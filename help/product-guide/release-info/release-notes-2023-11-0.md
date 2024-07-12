---
title: 发行说明 | Adobe Experience Manager Guides 2023年11月版中的升级说明和修复的问题
description: 了解错误修复以及如何升级到Adobe Experience Manager Guidesas a Cloud Service的2023年11月版
exl-id: 80839890-075f-4187-a167-444c73215496
feature: Release Notes
role: Leader
source-git-commit: 6d8c01f20f7b59fed92c404561b647d9ebecb050
workflow-type: tm+mt
source-wordcount: '1673'
ht-degree: 1%

---

# 2023年11月版的Adobe Experience Manager Guidesas a Cloud Service

此发行说明涵盖了升级说明、兼容性矩阵，以及2023年11月版Adobe Experience Manager Guidesas a Cloud Service(以后称为&#x200B;*Experience Manager Guidesas a Cloud Service*)中修复的问题。

有关新增功能和增强功能的详细信息，请查看[Experience Manager Guides as a Cloud Service 2023年11月版的新增功能](whats-new-2023-11-0.md)。

## 升级到2023年11月版

请通过以下步骤升级当前的Experience Manager Guidesas a Cloud Service设置：

1. 查看Cloud Service的Git代码，并切换到在Cloud Service管道中配置的与要升级的环境对应的分支。
2. 将Cloud ServiceGit代码的`/dox/dox.installer/pom.xml`文件中的`<dox.version>`属性更新为2023.11.0.406。
3. 提交更改并运行Cloud Service管道，以升级到Experience Manager Guidesas a Cloud Service的2023年11月版。

## 通过servlet启用脚本触发器的步骤

(仅限您使用的版本低于2023年6月发行的Experience Manager Guidesas a Cloud Service)

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

## 后处理现有内容以使用断开链接报表的步骤

(仅限您使用的版本低于2023年6月发行的Experience Manager Guidesas a Cloud Service)

执行以下步骤对现有内容进行后处理，并使用新的断开链接报表：

1. （可选）如果系统中有超过100,000个DITA文件，请将`org.apache.jackrabbit.oak.query.QueryEngineSettingsService`下的`queryLimitReads`和`queryLimitInMemory`更新为更大的值（任何大于现有资产数的值，例如200,000），然后重新部署。

   - 按照安装和配置Adobe Experience Manager Guides as a Cloud Service中的&#x200B;*配置覆盖*&#x200B;部分提供的说明创建配置文件。
   - 在配置文件中，提供以下（属性）详细信息以配置`queryLimitReads`和`queryLimitInMemory`选项：

     | PID | 属性键 | 属性值 |
     |---|---|---|
     | org.apache.jackrabbit.oak.query.QueryEngineSettingsService | queryLimitRead | 值：200000默认值：100000 |
     | org.apache.jackrabbit.oak.query.QueryEngineSettingsService | queryLimitInMemory | 值：200000默认值：100000 |

1. 对服务器运行POST请求（使用正确的身份验证） — `http://<server:port>//bin/guides/reports/upgrade`。

1. API返回jobId。 要检查作业的状态，可以将带有作业ID的GET请求发送到同一终结点 — `http://<server:port>/bin/guides/reports/upgrade?jobId= {jobId}`
（例如： `http://localhost:8080/bin/guides/map-find/indexing?jobId=2022/9/15/7/27/7dfa1271-981e-4617-b5a4-c18379f11c42_678`）

1. 作业完成后，先前的GET请求会成功响应。 如果作业由于某个原因失败，则可以从服务器日志中看到失败。

1. 如果您在步骤1中更改了`queryLimitReads`的值，请恢复为默认或以前的现有值。

## 为现有内容编制索引以使用“报表”选项卡下的新查找和替换以及主题列表的步骤：

(仅限您使用的版本低于2023年6月发行的Experience Manager Guidesas a Cloud Service)

执行以下步骤来索引现有内容，并在报表选项卡下的映射级别和主题列表中使用新的查找和替换文本：

1. 对服务器运行POST请求（使用正确的身份验证） — `http://<server:port>/bin/guides/map-find/indexing`。 (可选：您可以传递映射的特定路径来对其进行索引，默认情况下，所有映射都将进行索引 || 例如：`https://<Server:port>/bin/guides/map-find/indexing?paths=<map_path_in_repository>`)

1. 您还可以传递根文件夹来索引特定文件夹（及其子文件夹）的DITA映射。 例如，`http://<server:port>/bin/guides/map-find/indexing?root=/content/dam/test`。请注意，如果同时传递了路径参数和根参数，则只考虑路径参数。

1. API返回jobId。 要检查作业的状态，可以将带有作业ID的GET请求发送到同一终结点 — `http://<server:port>/bin/guides/map-find/indexing?jobId={jobId}`（例如： `http://localhost:8080/bin/guides/map-find/indexing?jobId=2022/9/15/7/27/7dfa1271-981e-4617-b5a4-c18379f11c42`）


1. 作业完成后，先前的GET请求会做出成功响应，并提及是否有任何映射失败。 可以从服务器日志中确认已成功编制索引的映射。

## 处理`'fmdita rewriter'`冲突的步骤

Experience Manager Guides有一个&#x200B;[**自定义sling重写器**](../cs-install-guide/conf-output-generation.md#custom-rewriter)&#x200B;模块，用于处理在交叉映射（两个不同映射的主题之间的链接）情况下生成的链接。

如果您的代码库中有另一个自定义sling重写器，请使用大于50的`'order'`值，因为Experience Manager Guides sling重写器使用`'order'` 50。  要覆盖此值，您需要一个大于50的值。 有关详细信息，请查看[输出重写管道](https://sling.apache.org/documentation/bundles/output-rewriting-pipelines-org-apache-sling-rewriter.html)。

在此升级过程中，由于`'order'`值从1000更改为50，因此您需要将现有的自定义重写器（如果有）与`'fmdita-rewriter'`合并。


## 兼容性矩阵

本部分列出了Experience Manager Guides as a Cloud Service 2023年11月版支持的软件应用程序的兼容性矩阵。

### FrameMaker和FrameMaker Publishing Server

| Experience Manager Guides Guides as a Cloud版本 | FMPS | FrameMaker |
| --- | --- | --- |
| 2023.11.0 | 不兼容 | 2022或更高版本 |
| | | |


### 氧气连接器

| Experience Manager Guides as a Cloud | 氧气连接器窗口 | 氧气连接器Mac | 在氧气窗口中编辑 | 在氧气Mac中编辑 |
| --- | --- | --- | --- | --- |
| 2023.11.0 | 3.2-uuid 5 | 3.2-uuid 5 | 2.3 | 2.3 |
|  |  |  |  |


### 知识库模板版本

| 组件包名称 | 组件版本 | 模板版本 |
|---|---|---|
| 适用于Cloud Service的Experience Manager Guides组件内容包 | dxml-components.all-1.2.2 | aem-site-template-dxml.all-1.0.15 |

## 修复的问题

修复了多个区域中的错误如下：



### 创作

- 保存主题时，conref `<ph>`元素后的空格消失。 (13642)
- 在后处理完成之前尝试保存DITA文件时出现应用程序错误。 (13571)
- 如果主题的标题包含斜杠`/`，则编辑器中的选项卡仅显示其后面的字母。 (13455)
- 在编辑器中显示预览后，图像预览未消失。 (13454)
- 在其他主题中使用根映射定义的键时，不会出现插入关键字弹出窗口。 (12950)
- 在“版本历史记录”面板中预览高度很高的图形时，不会显示关闭图标。 (12867)
- 无法为基线修改在&#x200B;**列上创建的**&#x200B;版本的时区。 (12711)
- Assets UI中的&#x200B;**版本历史记录**&#x200B;面板显示&#x200B;**当前**&#x200B;字段的时间戳不正确。 (12624)
- 从文件名以数字字符开头的模板创建DITA文件会导致命名空间错误。 (12188)
- 在Web编辑器中，插入`varname`标记时会打开&#x200B;**键引用**&#x200B;窗口。 (10940)
- 在Web编辑器中无法识别Zip文件，并且您不能拖放它们。 (12709)
- 应用了某些属性的内容在“创作”或“预览”模式下不会突出显示。 (11063)
- 在编辑某个主题后关闭该主题时，您将被重定向到AEM主页，而不是返回到文件夹视图。 (13306)
- 对已复制并粘贴到云服务中的文件进行后处理时出现延迟。 (12457)
- 即使用户未从“用户首选项”中明确设置rootmap设置，Web编辑器中仍会保留该设置。 (11551)


### 发布

- Publish作为内容片段功能不适用于搜索结果中列出的文件。 (14090)
- 在本机PDF发布中，模板布局上的背景颜色选择要求在恢复为`None`时重新加载页面。 (13621)
- 在AEM站点发布中，提交具有范围对等链接的大型DITA映射的数据存储时出现问题。 (13530)
- 在本机PDF发布中，由于页眉和页脚中的图像不显示替换文本，因此辅助功能会受损。 (12829)
- 使用本机PDF复制页面布局时，无法自动添加扩展。 (12534)
- 使用本机PDF发布生成PDF输出时，文件名将在句点后截断。 (13620)
- 在本机PDF发布中使用的“模板”的“页面布局”工具栏中，**编辑内容**&#x200B;选项的图标和工具提示显示不正确。 (13492)
- 自定义元数据在最终输出中不可用。 (12116)
- fmdita重写器与用户的重写器配置冲突，并导致显示长URL而不是链接。 (12076)
- 在AEM网站预设中，**为每个主题**&#x200B;生成单独PDF的选项不起作用。 (11555)
- 本机PDF发布不支持CMYK色彩空间转换。 (10754)
- 动态基线调用使用名称而不是标题，从而导致导出DITA映射API失败。 (14268)

### 管理

- 复制粘贴具有不带GUID的自引用链接的DITA文件时会破坏内容引用。 (13540)
- 在Web编辑器中，基线显示DITA文件的先前版本（而非所选版本）的标题。 (13444)
- Web编辑器UI中的&#x200B;**报表**&#x200B;选项卡无法显示在2023年7月升级Experience Manager Guidesas a Cloud Service之前创建的旧DITA映射的主题列表。 (11852)
- 未创建大型DITA映射的条件预设。 (10936)
- 自引用链接显示在报表中的断开链接列表下方。 (13539)

### 审查

- 在2023年10月版的Experience Manager Guidesas a Cloud Service中，Web编辑器中以前版本和当前版本的并排审核面板不正确。 (14156)
- **审阅**&#x200B;工作流的电子邮件模板自定义不适用于覆盖节点。 (13954)
- Experience Manager Guides中“审阅”页面上的&#x200B;**关闭**&#x200B;按钮会将用户转到AEM主页。 (13535)
- 以朝鲜语创建代码片段时，会出现字符损坏。 (13489)
- Experience Manager Guides Review屏幕中的韩文附件不可点击。 (13436)
- 在审核和协作屏幕中，地图标题被切断，没有查看完整标题的选项。 (13012)

### 翻译

- 自动批准有时不起作用，如果在&#x200B;**翻译状态**&#x200B;上设置的值不正确，则会发生异常。 (13607)
- 从翻译仪表板导出的基线会失败，并且不会以目标语言打开。 (12993)

## 已知问题

Adobe已为2023年11月版本发现以下已知问题。

- AEM Site输出的选择性主题重新生成失败。
