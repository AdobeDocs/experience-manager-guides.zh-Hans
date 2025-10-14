---
title: Adobe Experience Manager Guides中的映射控制台
description: 了解地图控制台以及允许您在Adobe Experience Manager Guides中发布和管理地图的各种可用功能。
feature: Publishing
role: User
exl-id: b273b1ae-fbb2-4b35-abce-0df78eeb2e11
source-git-commit: e14b19ff7c128899b4536d5b8c4290c476991bef
workflow-type: tm+mt
source-wordcount: '767'
ht-degree: 0%

---

# 映射控制台概述

Adobe Experience Manager Guides提供了一个专用控制台（称为&#x200B;**地图控制台**），用于简化所有地图管理和发布任务。 此集中式界面通过提供用于生成输出、翻译内容、访问报告等功能的选项，提高了与地图相关活动的生产力和准确性 — 所有这些功能都在一处完成。

![文件属性选项选项卡](./images/map-console-screen.png){align="left"}

地图控制台界面主要分为两个部分 — **导航栏**&#x200B;和&#x200B;**左侧面板**。

![新建](images/map-console-sections.png){align="left"}

- (**A**) **导航栏**：导航栏会显示一些工具，用于切换导航、调整页面视图并显示所选映射文件的名称。

  导航栏中可用的功能说明如下：

   - **导航切换器**：允许无缝导航到其他页面 — 编辑器或主页：
   - **选定的映射文件**：显示当前选定映射文件的名称。 您可以在编辑器中打开它，或为“映射”控制台选择其他映射文件。
   - **更多操作**：提供用于导航到&#x200B;**Assets UI**&#x200B;和&#x200B;**Workspace设置**&#x200B;的选项。 有关详细信息，请查看[选项卡栏](./web-editor-tab-bar.md)。

  >[!NOTE]
  >
  > 如果在内部部署设置中使用Adobe Experience Manager Guides，则Workspace设置选项在“更多操作”菜单下继续显示为&#x200B;**设置**。

   - **展开视图**：允许您使用&#x200B;**展开**&#x200B;图标展开页面视图。 在此视图中，标题栏是隐藏的，从而最大化内容空间。 要返回到标准视图，请使用&#x200B;**退出扩展视图**&#x200B;图标。

  >[!NOTE]
  >
  > 如果使用Adobe Experience Manager Guides as a Cloud Service，则导航栏中会显示附加功能[AI助手](./ai-assistant.md)。

- (**B**) **左侧面板**：左侧面板允许您快速访问输出生成、报告创建和管理、基线、条件预设、内容翻译和Workfront（仅当已配置时）功能。

  有关更多详细信息，请参阅下面的[映射控制台功能](#map-console-features)部分。

## 映射控制台功能

当您[在映射控制台](./open-files-map-console.md)中打开DITA映射文件时，以下功能在左侧面板中可用。

**输出生成**

利用映射控制台，您可以通过DITA-OT、本机PDF发布和FMPS高效地生成各种格式的输出，包括AEM Sites、PDF、HTML5、EPUB、JSON和自定义输出。 可以为整个DITA映射生成输出，也可以只选择性地发布已更新的几个主题。 也可以使用基线发布功能有选择地发布DITA映射或主题的特定版本。

有关详细信息，请查看[输出生成](./generate-output.md)。

**报告创建和管理**

在组织设置中，您需要先验证技术文档的整体完整性，然后再开始处理技术文档或将文档推送到现场。 在多用户和大规模环境中，这种需求变得更加重要。 通过映射控制台，您可以访问Experience Manager Guides报表，这些报表为存储库中内容的整体运行状况以及文档过程中内容的使用方式提供了有用的insight。

有关更多详细信息，请在Experience Manager Guides中查看[报告](./reports-intro.md)。

**基线**

Experience Manager Guides提供基线功能，允许您创建随后可用于发布或翻译的主题和资产版本。 也可以并行发布同一DITA映射的多个输出预设。

了解如何[在Experience Manager Guides](./web-editor-baseline.md)中创建和管理基线。

**条件预设**

Experience Manager Guides允许您在DITA主题中定义属性，并使用条件预设指定在最终输出中属性会发生什么情况。 例如，您可以在内容中添加版本为1.0和版本为2.0的属性，并使用条件预设来包含版本1.0的版本1.0和排除版本2.0。同样，您可以将OS Windows和OS Linux等属性添加到内容中，然后根据操作系统在最终输出中包括或排除相关内容。

了解有关[条件预设](./generate-output-use-condition-presets.md)的更多信息。

**内容翻译**

Experience Manager Guides提供的强大功能使您能够将内容翻译成多种语言。 Experience Manager Guides同时支持人工翻译工作流和机器翻译工作流。

在映射控制台中，您可以访问开始使用翻译工作流所需的所有选项。 有关详细信息，请查看[翻译内容](./translation.md)。


**Workfront**

Workfront功能也存在于映射控制台中，允许您直接从Experience Manager Guides处理Adobe Workfront任务。

了解Experience Manager Guides[中的](./workfront-integration.md)Adobe Workfront集成。

仅当管理员在Experience Manager Guides实例中配置了&#x200B;**Adobe Workfront**&#x200B;集成时，您才可以访问此功能。
