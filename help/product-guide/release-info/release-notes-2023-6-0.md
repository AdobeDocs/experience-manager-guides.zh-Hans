---
title: 发行说明 | Adobe Experience Manager Guides 2023年6月版中的升级说明和修复的问题
description: 了解错误修复以及如何升级到Adobe Experience Manager Guides as a Cloud Service 2023年6月版
exl-id: df17ee33-9f50-4223-ab9f-a57a31097d22
feature: Release Notes
role: Leader
source-git-commit: 6d8c01f20f7b59fed92c404561b647d9ebecb050
workflow-type: tm+mt
source-wordcount: '1170'
ht-degree: 1%

---

# 2023年6月版的Adobe Experience Manager Guidesas a Cloud Service

此发行说明涵盖了升级说明、兼容性矩阵，以及Adobe Experience Manager Guides版本2023年6月(以后称为&#x200B;*AEM Guidesas a Cloud Service*)中修复的问题。

有关新增功能和增强功能的更多信息，请参阅[AEM Guides as a Cloud Service 2023年6月版的新增功能](whats-new-2023-6-0.md)。

## 升级到2023年6月版

请通过以下步骤升级当前的AEM Guidesas a Cloud Service设置：

1. 查看Cloud Service的Git代码，并切换到在Cloud Service管道中配置的与要升级的环境对应的分支。
2. 将Cloud ServiceGit代码的`/dox/dox.installer/pom.xml`文件中的`<dox.version>`属性更新为2023.6.297。
3. 提交更改并运行Cloud Service管道，以升级到AEM Guidesas a Cloud Service的2023年6月版。

## 通过servlet启用脚本触发器的步骤

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

(仅限您使用的版本低于2023年6月版本的AEM Guidesas a Cloud Service)

执行以下步骤后处理现有内容并使用新的断开链接报表：

1. （可选）如果系统中有超过100,000个dita文件，请将`org.apache.jackrabbit.oak.query.QueryEngineSettingsService`下的`queryLimitReads`更新为更大的值（任何大于现有资产数的值，例如200,000），然后重新部署。

   - 按照安装和配置Adobe Experience Manager Guides中&#x200B;*配置覆盖*部分中提供的说明进行操作
as a Cloud Service，以创建配置文件。
   - 在配置文件中，提供以下（属性）详细信息以配置queryLimitReads选项：

     | PID | 属性键 | 属性值 |
     |---|---|---|
     | org.apache.jackrabbit.oak.query.QueryEngineSettingsService | queryLimitRead | 值：200000默认值：100000 |

1. 对服务器运行POST请求（使用正确的身份验证） — `http://<server:port>//bin/guides/reports/upgrade`。

1. 该API将返回作业ID。 要检查作业的状态，可以将带有作业ID的GET请求发送到同一终结点 — `http://<server:port>/bin/guides/reports/upgrade?jobId= {jobId}`
（例如： `http://localhost:8080/bin/guides/map-find/indexing?jobId=2022/9/15/7/27/7dfa1271-981e-4617-b5a4-c18379f11c42_678`）

1. 作业完成后，先前的GET请求将做出成功响应。 如果作业由于某个原因失败，则可以从服务器日志中看到失败。

1. 如果您在步骤1中更改了`queryLimitReads`的值，请恢复为默认或以前的现有值。

## 为现有内容编制索引以使用“报表”选项卡下的新查找和替换以及主题列表的步骤：

(仅限您使用的版本低于2022年9月发行的AEM Guidesas a Cloud Service)

执行以下步骤来索引现有内容，并在报表选项卡下的映射级别和主题列表中使用新的查找和替换文本：

1. 对服务器运行POST请求\（使用正确的身份验证\） - `http://<server:port\>/bin/guides/map-find/indexing`。 (可选：您可以传递映射的特定路径以对其进行索引，默认情况下，所有映射都将进行索引\|\| 例如：`https://<Server:port\>/bin/guides/map-find/indexing?paths=<map\_path\_in\_repository\>`)

1. 您还可以传递根文件夹来索引特定文件夹（及其子文件夹）的DITA映射。 例如，`http://<server:port\>/bin/guides/map-find/indexing?root=/content/dam/test`。请注意，如果同时传递了路径参数和根参数，则只考虑路径参数。

1. 该API将返回作业ID。 要检查作业的状态，可以将带有作业ID的GET请求发送到同一终结点 — `http://<server:port\>/bin/guides/map-find/indexing?jobId=\{jobId\}`\（例如： `http://localhost:8080/bin/guides/map-find/indexing?jobId=2022/9/15/7/27/7dfa1271-981e-4617-b5a4-c18379f11c42`\）


1. 作业完成后，先前的GET请求将做出成功响应，并提及是否有任何映射失败。 可以从服务器日志中确认已成功编制索引的映射。

## 兼容性矩阵

本部分列出了AEM Guides as a Cloud Service 2023年6月版支持的软件应用程序的兼容性矩阵。

### FrameMaker和FrameMaker Publishing Server

| AEM Guides as a Cloud | FMPS | FrameMaker |
| --- | --- | --- |
| 2023.06.0 | 不兼容 | 2022或更高版本 |
| | | |


### 氧气连接器

| AEM Guides as a Cloud | 氧气连接器窗口 | 氧气连接器Mac | 在氧气窗口中编辑 | 在氧气Mac中编辑 |
| --- | --- | --- | --- | --- |
| 2023.06.0 | 2.9-uuid-2 | 2.9-uuid-2 | 2.3 | 2.3 |
|  |  |  |  |


## 修复的问题

修复了多个区域中的错误如下：

### 创作

- 从布局视图切换到创作视图或源视图时，Navtitle将从content33中删除。 (12174)
- 有时，单击DITA映射时出现应用程序错误。 (11842)
- Web编辑器 | 编辑主题时，会在XML编辑器中添加不间断的空间。 (11786)
- 资产UI | 在“列表”视图中，叠加的可用列不可合并。 (11528)
- 未在映射视图中解析Keyref。 (11490)
- 通过XML编辑器导航时，顶部菜单不显示。 (10868)
- ph标记中的`conref` | 显示的浏览对话框不正确。 (9481)
- 在Web编辑器中不会解析指向其他元素的本地链接。 (8790)
- Matches()函数在架构功能中不起作用。 (11224)


### 管理

- Web编辑器UI中的“报表”选项卡不显示4.2升级之前创建的旧DITA映射的主题列表。 (11708)

- Assets UI中的“上传文件”按钮功能在4.2版本中中断。 (11633)

### 发布

- 从可能刷新或重新启动的面板中读取临时文件时，发布到AEM站点失败。 (12113)
- 本机PDF | 如果发布的内容具有带brackets()的输出类，则会导致发布冻结。 (11936)
- JSON输出 | 将属性值映射为`"value in spaces and double quotes"`的元数据会导致发布错误。 (11933)
- Web编辑器 | 无法在AEM预设中选择输出路径和模板。 (11530)
- 本机PDF | 自定义属性不会传播到临时HTML或PDF引擎。 (DXML-12005)
- 本机PDF |  发布大型内容时出现Java OutOfMemoryError。 (11789)
- JSON输出 | JSON的jcr：content节点上的`fmUuid`属性不同于JSON中的“id”。 (11564)
- JSON输出 | 如果存在具有相同文件名的映射和主题，则将删除映射的JSON。 (11524)
- 本机PDF | Xref正在打印href主题标题的内容而不是Xref标签。 (11322)
- 本机PDF | 无法保存PDF模板设置。 (10751)
- 本机PDF | 文本在包含多个xref时超出列宽。 (10876)
- 本机PDF | `<note>` `</note>`元素未生成其类型的额外范围标题。 (10549)
- 本机PDF | 无法将生成的PDF中的语言元数据设置为符合WCAG 2.0。 (12296)



### 翻译

- Post 2月云版本(2302)，所有翻译内容显示“不同步”或“缺少副本”。 (11834)

### 审查

- 新建审核UI | 这些条件会高亮显示，并且显示隐藏的工作方式与它们在Web编辑器中的工作方式有所不同。 (11628)
