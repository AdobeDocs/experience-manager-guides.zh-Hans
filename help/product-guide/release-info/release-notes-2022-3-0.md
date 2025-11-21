---
title: ' [!DNL AEM Guides]的发行说明，2022年3月版'
description: ' [!DNL Adobe Experience Manager Guides] as a Cloud Service的3月版本'
exl-id: 885edbb5-dfe4-4bdc-bb66-0df64addb094
feature: Release Notes
role: Leader
source-git-commit: 6e23f52fc9124d0f07f8108da1b5fe574f553469
workflow-type: tm+mt
source-wordcount: '777'
ht-degree: 0%

---

# [!DNL Adobe Experience Manager Guides] as a Cloud Service的3月版

## 升级到3月版

请通过执行以下步骤升级当前[!DNL Adobe Experience Manager Guides] as a Cloud Service(以后称为&#x200B;*[!DNL AEM Guides]as a Cloud Service*)安装程序：
1. 检查云服务的Git代码，并切换到在云服务管道中配置的与您要升级的环境对应的分支。
1. 将云服务Git代码的`<dox.version>`文件中的`/dox/dox.installer/pom.xml`属性更新为2022.3.123。
1. 提交更改并运行云服务管道以升级到[!DNL AEM Guides] as a Cloud Service的3月版本。

## 兼容性矩阵

本部分列出了[!DNL AEM Guides] as a Cloud Service 2022年3月版支持的软件应用程序的兼容性矩阵。

### FrameMaker和FrameMaker Publishing Server

| FMPS | FrameMaker |
| --- | --- |
| 不兼容 | 2020更新4及更高版本 |
| | |


### 氧气连接器

| [!DNL AEM Guides]云版本 | 氧气连接器窗口 | 氧气连接器Mac |
| --- | --- | --- |
| 2022.3.0 | 2.4.0 | 2.4.0 |
|  |  |  |

*从2020.2开始的FMPS版本支持在AEM中创建的基线和条件。

## 新增功能和增强功能

### 新建基线仪表板

[!DNL AEM Guides] as a Cloud Service 3月版提供了集成在Web编辑器中的基线功能。 您现在可以从Web编辑器创建基线，并使用它们发布或翻译不同版本的主题。

注意：对于已升级的系统，请更新文件夹配置文件的最新&#x200B;**ui_config.json**。

使用此功能可使用特定日期和时间提供的主题的特定版本创建基线。 此外，您还获得API支持，可使用为主题版本定义的标签创建或更新基线。

![基线管理选项卡](assets/baseline-manage.png)

您可以根据文件名或文件位置搜索文件。 您还可以过滤要在基线编辑窗口中显示的主题，并根据特定列对它们进行排序。

![基线管理选项卡](assets/baseline-filter.png)

基线创建过程的性能已得到进一步改进。 创建基线的过程是异步的，因此，在创建基线时，您可以继续在Web编辑器中编辑其他文件。 有关更多详细信息，请参阅用户指南中的&#x200B;*从Web编辑器创建和管理基线*。

注意：默认情况下，映射操控板上的“基线”选项卡处于隐藏状态。 您的管理员可以在映射仪表板上启用基线选项卡。

### 改进了Web编辑器刷新行为

现在，Web编辑器中的浏览器刷新操作提供了以下增强功能：

* 现在，您可以在编辑时获得刷新浏览器的支持
Web编辑器中的内容。 如果在显示一个或多个文件的同时点击浏览器刷新图标，
未保存的更改将打开进行编辑，系统会提示您保存文件或取消刷新操作。

* 即使刷新浏览器时，左侧面板和右侧面板的视图也会保留。

* 活动主题或DITA映射将在内容编辑区域中重新打开。

### 发布增强功能

发布过程已通过[!DNL AEM Guides] as a Cloud Service的3月版本进一步改进：

* AEM站点输出的元数据已遵循基线。 您还可以将基线版本的属性作为元数据处理。 如果未定义基线，则最新版本的属性将作为元数据处理。

* 已为HTML5、EPUB和自定义输出预设添加&#x200B;**文件名**&#x200B;和&#x200B;**DITA-OT命令行参数**&#x200B;选项。 现在，您可以指定要用来保存输出的文件名。 您还可以指定在生成输出时希望DITA-OT处理的其他参数。

## 修复的问题

修复了多个区域中的错误如下：

* 无法使用Web编辑器的“作者”视图在书签中添加前置内容、后置内容元素。 (7652)
* 在删除主题并执行移动操作后，引用树断开。 (8804)
* 上传资源后查看内容时收到异常。 (3638)
* 当其父文件夹的文件名中有特殊字符的文件在氧气中打开时（使用&#x200B;**在氧气中编辑**&#x200B;按钮），会发生错误。 (8918)
* **在存储库中定位**&#x200B;选项未在XML编辑器中定位并突出显示DITA映射。 (8796)
* 将多个属性添加到XML编辑器中的内容时，筛选不会显示相应的结果。 (8795)
* 当用户ID为数字时，在文件夹配置文件中将用户添加为管理员时出错。 (8908)

## 已知问题

Adobe已在[!DNL AEM Guides] as a Cloud Service 3月版本中识别出以下已知问题。

* 删除直接引用上的标签也会从间接引用中删除标签。

* 如果不手动刷新基线面板，则无法反映更新的基线标题。

* “版本历史记录”面板中的版本预览功能不显示选定主题的预览。
