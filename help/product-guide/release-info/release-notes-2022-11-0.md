---
title: 发行说明 | Adobe Experience Manager Guidesas a Cloud Service，2022年11月版
description: 11月版的Adobe Experience Manager Guidesas a Cloud Service
exl-id: 9f329ec1-dd74-47cc-8567-3fadd962584a
feature: Release Notes
role: Leader
source-git-commit: 6d8c01f20f7b59fed92c404561b647d9ebecb050
workflow-type: tm+mt
source-wordcount: '1384'
ht-degree: 0%

---

# 11月版的Adobe Experience Manager Guidesas a Cloud Service

## 升级到11月版

请通过以下步骤升级当前的Adobe Experience Manager Guidesas a Cloud Service(以后称为&#x200B;*AEM Guidesas a Cloud Service*)安装程序：
1. 查看Cloud Service的Git代码，并切换到在Cloud Service管道中配置的与要升级的环境对应的分支。
1. 将Cloud ServiceGit代码的`/dox/dox.installer/pom.xml`文件中的`<dox.version>`属性更新为2022.11.198。
1. 提交更改并运行Cloud Service管道，以升级到AEM Guidesas a Cloud Service的11月版。

## 索引现有内容的步骤(仅当使用的版本早于9月份的AEM Guidesas a Cloud Service版本时)

执行以下步骤来索引现有内容，并在映射级别使用新的查找和替换文本：

* 对服务器运行POST请求（使用正确的身份验证） — `http://<server:port>/bin/guides/map-find/indexing`。
(可选：您可以传递映射的特定路径来对其进行索引，默认情况下，所有映射都将进行索引 || 示例：`https://<Server:port>/bin/guides/map-find/indexing?paths=<map_path_in_repository>`)

* 该API将返回作业ID。 要检查作业的状态，可以将带有作业ID的GET请求发送到同一终结点 — `http://<server:port>/bin/guides/map-find/indexing?jobId={jobId}`
(例如：http://&lt;_localhost：8080_>/bin/guides/map-find/indexing？jobId=2022/9/15/7/27/7dfa1271-981e-4617-b5a4-c18379f11c42_678)

* 作业完成后，上述GET请求将做出成功响应，并提及是否有任何映射失败。 可以从服务器日志中确认已成功编制索引的映射。

## 兼容性矩阵

本部分列出了AEM Guides as a Cloud Service 2022年11月版支持的软件应用程序的兼容性矩阵。

### FrameMaker和FrameMaker Publishing Server

| FMPS | FrameMaker |
| --- | --- |
| 不兼容 | 2020更新4及更高版本 |
| | |

*从2020.2开始的FMPS版本支持在AEM中创建的基线和条件。

### 氧气连接器

| AEM Guides as a Cloud | 氧气连接器窗口 | 氧气连接器Mac | 在氧气窗口中编辑 | 在氧气Mac中编辑 |
| --- | --- | --- | --- | --- |
| 2022.11.0 | 2.7.13 | 2.7.13 | 2.3 | 2.3 |
|  |  |  |  |


## 新增功能和增强功能

AEM Guidesas a Cloud Service在11月版本中提供了以下增强功能和新功能：


### 从存储库面板中删除文件

现在，您可以从存储库面板的选定文件的&#x200B;**选项**&#x200B;菜单中轻松删除文件（一次删除一个文件）。
<img src="assets/repository-delete-file.png" alt="从存储库中删除" width="500">

删除文件之前会显示确认提示。 如果文件未从任何其他文件引用，则会将其删除，并显示一条成功消息。

如果所选文件已签出，则无法删除该文件，并会显示一条错误消息。 如果所选文件已添加到收藏夹集合或引用自任何其他文件，AEM guides将检查您的确认，并为您提供强制删除它的选项。 如果删除了引用的主题并且打开了包含要编辑的引用的文件，则将显示被引用文件的断开链接。

**注意**：您也可以使用键盘的Delete键删除所选文件。


### 清除所选的文件版本

在创建和维护内容时，可能会为存储库中的DITA文件创建多个版本。 AEM Guides允许您从存储库中清除旧版本的DITA文件并释放磁盘空间。

<img src="assets/preview-purge-report.png" alt="预览清除报告" width="500">


AEM Guides不会删除文件的第一个版本，也不会删除基线中包含的某个版本，也不会删除应用于该文件的标签。 清除操作甚至不会删除翻译或审阅工作流中包含的文件。 您可以选择要保留的版本数量，也可以决定删除早于定义天数的文件。

在开始清除操作之前，您可以预览报表以查看要清除的版本。 然后，您可以决定是启动还是取消清除操作。

<img src="assets/download-purge-report.png" alt="PDownload清除报告" width="500">

清除操作完成后，您可以检查清除报表以查看已清除的文件。

### 管理全局和文件夹配置文件输出预设

AEM Guides提供了为全局和文件夹配置文件创建和管理输出预设的功能。 然后，您可以轻松地使用这些输出预设为与该全局或文件夹配置文件相关的所有映射生成输出。

<img src="assets/add-global-output-preset.png" alt="添加全局配置文件" width="400">

**注意**&#x200B;只有文件夹级别的管理用户可以创建全局和文件夹配置文件预设。

这些全局预设出现在所有相关映射的&#x200B;**输出**&#x200B;选项卡下。 您可以使用它们为所有相关映射生成输出。 您可以选择预设作为默认的PDF预设，以生成PDF输出。 您还可以从&#x200B;**选项**&#x200B;菜单&#x200B;**编辑**、**重命名**、**复制**&#x200B;或&#x200B;**删除**&#x200B;现有的输出预设。

### 已将“版本标签”列添加到翻译仪表板

在翻译仪表板中，您还可以看到版本标签列。 这将显示源文件的选定版本的标签。 这可以帮助您选择具有特定标签的所有文件并一次性翻译它们。

<img src="assets/send-translation.png" alt="发送以供翻译" width="600">


### 本机PDF | 带有显示文档版本之间差异的更改条的PDF

现在，您可以使用更改栏创建一个PDF，以显示两个版本之间的内容差异。 您可以选择将当前版本与先前版本的基线进行比较，或者将两个选定的基线版本进行比较。

<img src="assets/pdf-change-version.png" alt="spdf-change-version" width="600">

PDF中将显示一个更改栏，以指示已修改、已插入或删除的内容。 您还可以选择执行以下操作：
* 以绿色和带下划线的形式显示插入的内容
* 以红色显示删除的内容并标记删除线

### 本机PDF | 对输出路径和PDF文件名的变量支持

现在，您还可以使用以下现成的变量来定义输出路径和PDF文件。 您可以使用单个变量或变量组合来定义以下选项：
* `${map_filename}`
* `${map_title}`
* `${preset_name}`
* `${language_code}`
* `${map_parentpath}` （仅适用于输出路径）
* `${path_after_langfolder}` （仅适用于输出路径）


### 本机PDF | 为DITA映射生成目录并重新排序页面布局

现在还可以使用模板的高级PDF设置在DITA映射中生成目录。 您可以选择启用或禁用各种页面布局的显示，也可以重新排列它们的位置。

## 修复的问题

修复了多个区域中的错误如下：

* 本机PDF | 在生成的PDF输出中未解析`conkeyref`。 (10564)
* 本机PDF | 访问PDF输出中的映射元数据时出现问题。 (10556)
* 本机PDF | 使用内联样式而不是类名生成标记。  (10498)
* Web编辑器间歇性地加载空白页。 (10678)
* 如果我们通过复制现有预设来创建预设，则PDF发布失败。 (10584)
* 当预设的PDF生成失败时，**查看日志**&#x200B;按钮不起作用。 (10576)
* 预览中不会显示para标记内为conref的注释。 (10559)
* 在列表项末尾点击空格会删除整个列表。 (10540)
* 在使用本机PDF导出时，嵌套的`<indexterm>`未嵌套在索引中。 (10521)
* Source视图中缺少工具栏中的&#x200B;**自动缩进**&#x200B;按钮。 (10448)
* 在编辑器中创作列表时，列表项的第一个字符丢失。 (10447)
* 如果在基线编辑窗口中更改并保存了任何DITA资源版本，则会出现多个弹出窗口。 (10399)
* 从“快速生成”面板中选择所有输出预设后，单击&#x200B;**编辑**&#x200B;按钮时出现应用程序错误。 (10388)
* 从Assets UI执行复制粘贴操作时，不会保留DITA主题的自定义元数据。 (10367)
* 对于资产位于活动翻译项目中的整个语言文件夹，将阻止Post处理。 (10332)
* XML编辑器中的“模板”选项卡对文件夹配置文件管理员不可见。 (10266)
* 升级4.0后，Web编辑器中出现导航问题。 (10159)
* 在预览模式下不会显示SVG文件。 (10010)
* 如果编辑器的输出选项卡包含更多预设，则无法滚动预设部分，并且不会显示所有预设。 (9787)
* 图像的&#x200B;**编辑**&#x200B;和&#x200B;**注释**&#x200B;选项在列视图中无法正常工作。 (8758)
* 对等链接未解析并在生成的输出中显示为普通文本。 (7774)
