---
title: 使用DITA-OT生成PDF
description: 了解如何从映射控制台和映射仪表板中使用DITA-OT创建PDF预设。 在AEM Guides中配置PDF输出预设。
feature: Publishing
role: User
exl-id: 6ac82dad-34af-4f9e-8b52-4e4f2eb982a4
source-git-commit: 9ae2690c52ab5408a9d17e9a40a89fe1f902042f
workflow-type: tm+mt
source-wordcount: '1349'
ht-degree: 0%

---

# 创建DITA-OT PDF输出预设 {#id205BE600HAH}

可通过两种方式创建DITA-OT PDF输出预设：

- [从“映射”控制台创建DITA-OT PDF预设](#create-the-dita-ot-pdf-preset-from-the-map-console)
- [从“映射”仪表板创建DITA-OT PDF预设](#create-the-dita-ot-pdf-preset-from-the-map-dashboard)

## 从“映射”控制台创建DITA-OT PDF预设

执行以下步骤，从“地图”控制台中创建PDF预设：

1. [在映射控制台](./open-files-map-console.md)中打开DITA映射文件。

   您还可以从[概述部分](./intro-home-page.md#overview)中的&#x200B;**最近使用的文件**&#x200B;构件访问映射文件。 选定的映射文件将在映射控制台中打开。
1. 在&#x200B;**输出预设**&#x200B;选项卡中，选择+图标以创建输出预设。
1. 从&#x200B;**新建输出预设**&#x200B;对话框的“类型”下拉列表中选择&#x200B;**PDF**。
1. 在&#x200B;**名称**&#x200B;字段中，提供此预设的名称。
1. 在&#x200B;**使用**&#x200B;生成PDF字段中，选择&#x200B;**DITA-OT**。
1. 选择&#x200B;**添加到当前文件夹配置文件**&#x200B;选项可在当前文件夹配置文件中创建输出预设。 ![文件夹配置文件图标](images/global-preset-icon.svg)表示文件夹配置文件级别的预设。

   了解有关[管理全局和文件夹配置文件输出预设](./web-editor-manage-output-presets.md)的更多信息。

1. 选择&#x200B;**添加**。

   将创建PDF的预设。

   ![](./images/pdf-preset-map-console.png){width="350" align="left"}

在映射控制台中，DITA-OT的预设配置选项组织在“映射”控制台中的&#x200B;**常规**&#x200B;和&#x200B;**高级**&#x200B;选项卡下。

![](./images/dita-ot-preset-config.png){width="350" align="left"}

**常规**

**常规**&#x200B;选项卡包含以下配置选项：

- 输出路径
- DITA-OT命令行参数
- PDF文件名
- 条件筛选\（如果为映射定义了条件\）
- 使用基线\（如果为映射创建了基线\）
- 后期生成工作流

**高级**

**高级**&#x200B;选项卡包含以下配置选项：

- 启用版本控制
- 保留临时文件
- 文件属性

有关预设配置选项的详细信息，请参阅[PDF预设配置](#pdf-preset-configuration)部分。


## 从“映射”仪表板创建DITA-OT PDF预设

执行以下步骤，从地图仪表板创建PDF预设：

1. 在Assets UI中，导航到DITA映射并选择DITA映射以在映射仪表板中将其打开。
1. 确保已选择&#x200B;**输出预设**&#x200B;选项卡。
1. 在工具栏中选择&#x200B;**创建**。

   此时将显示一个新的输出预设创建表单。

1. 输入PDF预设所需的配置详细信息。
1. 选择&#x200B;**完成**&#x200B;以保存预设设置。

## PDF预设配置

根据是从“地图”控制台还是从“地图”仪表板配置预设，配置选项会略有不同。 某些选项仅适用于“映射”仪表板，而其他选项则同时适用于这两个仪表板。

如果同一配置具有两个不同的字段标签，则&#x200B;**/**&#x200B;会在下表中将它们分开。 第一个表示映射控制台中的标签，第二个表示映射仪表板中的标签。

例如，**输出路径/目标路径** — 在此，**输出路径**&#x200B;是映射控制台中使用的标签，而&#x200B;**目标路径**&#x200B;是映射仪表板中为相同配置使用的标签。

| PDF选项 | 描述 |
| --- | --- |
| 输出类型（*仅适用于Map仪表板*） | 要生成的输出类型。 要生成PDF输出，请选择PDF选项。 |
| 设置名称（*仅适用于地图仪表板*） | 为您正在创建的PDF输出设置提供一个描述性名称。 例如，您可以指定&#x200B;_内部客户输出_&#x200B;或&#x200B;_最终用户输出_。 |
| 使用生成PDF （*仅适用于地图仪表板*） | 选择&#x200B;**DITA-OT**&#x200B;以生成PDF输出。 如果您的管理员已配置此选项，请选择&#x200B;**FrameMaker Publishing Server**。 选择FMPS时，某些配置选项会有所不同。 此外，FMPS配置选项仅在Map功能板中可用。 |
| 输出路径/目标路径 | AEM存储库中存储PDF的路径。<br><br>您还可以在设置目标路径时使用变量。 有关使用变量的更多详细信息，请查看[使用变量设置目标路径、站点名称或文件名选项](generate-output-use-variables.md#id18BUG70K05Z)。 |
| DITA-OT命令行参数 | 指定在生成输出时希望DITA-OT处理的其他参数。 有关DITA-OT中支持的命令行参数的详细信息，请查看[DITA-OT文档](https://www.dita-ot.org/)。 |
| 转换名称 | 指定要生成的输出类型。 如果您要使用自己的自定义插件（该插件集成在DITA-OT插件中）生成输出，则需要使用此插件。 例如，如果要生成XHTML输出，请指定`xhtml`。 有关DITA-OT中可用的转换列表，请查看OASIS DITA-OT用户指南中的[DITA-OT转换（输出格式）](http://www.dita-ot.org/2.3/user-guide/AvailableTransforms.html)。 |
| PDF文件名 | 指定要用于保存PDF的文件名。<br><br>您还可以在设置PDF文件名时使用变量。 有关使用变量的更多详细信息，请查看[使用变量设置目标路径、站点名称或文件名选项](generate-output-use-variables.md#id18BUG70K05Z)。<br><br>**注意**：如果未提供文件名，则使用DITA映射的标题生成最终的PDF文件名。 如果映射没有标题，则使用DITA映射的文件名来命名最终的PDF。 使用系统中配置的规则清理文件名，以处理任何无效字符。 |
| 条件筛选/应用条件，使用 | 选择以下选项之一：<br><br>* **未应用任何项**：如果不想对已发布的输出应用任何条件，请选择此选项。<br>* **DITAVal文件**：选择DITAVal文件以生成个性化内容。 可使用浏览对话框或键入文件路径来选择多个DITAVal文件。 使用文件名旁边的交叉图标可将其删除。 DITAVal文件将按指定的顺序进行计算，因此第一个文件中指定的条件优先于后续文件中指定的匹配条件。 您可以通过添加或删除文件来维护文件顺序。 如果将DITAVal文件移动到其他位置或将其删除，则不会从映射操控板中自动将其删除。 如果移动或删除了文件，则需要更新位置。 您可以将鼠标悬停在文件名上以查看存储该文件的AEM存储库中的路径。 您只能选择DITAVal文件，如果已选择任何其他文件类型，则会显示错误。 FrameMaker Publishing Server不支持多个DITAVAL文件。<br>* **条件预设**：从下拉列表中选择条件预设，以在发布输出时应用条件。 如果您在DITA映射控制台的条件预设选项卡中添加了条件，则该选项可见。 要了解有关条件预设的更多信息，请查看[使用条件预设](generate-output-use-condition-presets.md#id1825FL004PN)。 |
| 运行后期生成工作流 | 选择此选项时，将显示一个新的生成后工作流下拉列表，其中包含在AEM中配置的所有工作流。 必须选择要在输出生成工作流完成后执行的工作流。<br><br>**注意**：有关创建自定义输出后生成工作流的详细信息，请在安装和配置Adobe Experience Manager Guides as a Cloud Service中查看自定义输出后生成工作流程。 |
| 使用基线 | 如果已为所选DITA映射创建了基线，请选择此选项以指定要发布的版本。<br><br>查看[使用基线](generate-output-use-baseline-for-publishing.md#id1825FI0J0PF)以了解更多详细信息。 |
| 保留临时文件 | 选择此选项可保留由DITA-OT生成的临时文件。 如果在通过DITA-OT生成输出时遇到错误，请选择此选项以保留临时文件。 然后，您可以使用这些文件来排查输出生成错误。<br> <br>生成输出后，选择&#x200B;**下载临时文件** ![下载临时文件图标](images/download-temp-files-icon.png)图标以下载包含临时文件的ZIP文件夹。 下载的文件还将包括`system_config.json`文件，该文件为您提供了有关作者URL、本地URL和发布URL的信息。<br><br> **注意**：如果在生成期间添加文件属性，则输出临时文件还包括包含这些属性的&#x200B;*metadata.xml*&#x200B;文件。 |
| 文件属性 | 选择要作为元数据处理的属性。 这些属性是从DITA映射或书签文件的属性页面设置的。 您从下拉列表中选择的属性显示在&#x200B;**文件属性**&#x200B;字段下。 选择资产旁边的交叉图标以将其删除。 <br><br>注意：您还可以使用DITA-OT发布将元数据传递到输出。 有关更多详细信息视图，[使用DITA-OT](pass-metadata-dita-ot.md#id21BJ00QD0XA)将元数据传递到输出。 |


**父主题：**[&#x200B;了解输出预设](generate-output-understand-presets.md)
