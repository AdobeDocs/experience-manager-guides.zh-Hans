---
title: AEM Sites
description: 在Web编辑器中创建和配置AEM Sites预设，并为DITA映射、选定主题和链接主题生成AEM Sites输出。
feature: Publishing
role: User
source-git-commit: 324b9b1364c14117740a924e825395f7c9d5c424
workflow-type: tm+mt
source-wordcount: '2732'
ht-degree: 0%

---

# Web编辑器中的AEM Sites预设


您可以从Web编辑器创建AEM Sites预设，并将其配置为生成AEM Sites输出。 AEM Sites输出基于复合组件映射以及`guides-components`，有助于高效的内容创建和管理。

Experience Manager Guides提供了用于创建AEM Sites的预定义模板。 这些预设可帮助您确保内容布局和结构的一致性。
- [根据这些预定义的模板创建主页](/help/product-guide/cs-install-guide/download-install-aem-sites-templates-cs.md#create-a-home-page-using-the-template)。
- 您可以[编辑主题模板](/help/product-guide/cs-install-guide/download-install-aem-sites-templates-cs.md#package-installation)并根据您的要求应用样式。
- 您也可以[自定义现有AEM Sites模板](/help/product-guide/cs-install-guide/download-install-aem-sites-templates-cs.md#customize-existing-aem-sites-templates)。



## 创建AEM Sites预设

执行以下步骤，从Web编辑器创建AEM Sites预设：

1. 在“存储库”面板中，在“映射视图”中打开DITA映射文件。
1. 在&#x200B;**输出**&#x200B;选项卡中，选择+图标以创建输出预设。
1. 从&#x200B;**新建输出预设**&#x200B;对话框的&#x200B;**类型**&#x200B;下拉列表中选择&#x200B;**AEM Sites**。
1. 从&#x200B;**新输出预设**&#x200B;对话框中取消选择&#x200B;**使用旧组件映射**&#x200B;选项。

![新](images/new-aem-sites-dialog-box.png)





>[!NOTE]
>
>在为Experience Manager Guides配置AEM Sites预设之前，管理员需要使用模板创建AEM Sites结构。
- **内部部署软件**：了解有关如何[下载并安装内部部署软件的AEM Sites模板](/help/product-guide/install-guide/download-install-aem-sites-templates.md)的详细信息。
- **Cloud Service**：了解有关如何[下载和安装AEM Sites模板](/help/product-guide/cs-install-guide/download-install-aem-sites-templates-cs.md)以进行Cloud Service的更多信息。




### 将预设添加到当前文件夹配置文件

作为管理员，Experience Manager Guides允许您为全局和文件夹配置文件创建和管理输出预设。 从&#x200B;**新建输出预设**&#x200B;对话框中选择&#x200B;**添加到当前文件夹配置文件**&#x200B;选项，以创建当前文件夹配置文件的输出预设。 ![文件夹配置文件图标](images/global-preset-icon.svg)图标表示文件夹配置文件级别预设。  了解有关[管理全局和文件夹配置文件输出预设](./web-editor-manage-output-presets.md)的更多信息。

### 基于旧版组件映射的AEM Sites预设

您也可以使用旧版组件映射来创建AEM Sites预设。 要基于旧组件映射创建AEM Sites预设，请从&#x200B;**新建输出预设**&#x200B;对话框中选择&#x200B;**使用旧组件映射**&#x200B;选项。

使用旧版组件映射的预设的某些选项可能有所不同。



## 配置AEM Sites预设

配置在&#x200B;**常规**、**内容**、**主题列表**&#x200B;和&#x200B;**交叉映射引用**&#x200B;选项卡下组织。

![aem sites预设设置](images/aem-sites-new-config.png)
**常规**

**常规**&#x200B;选项卡包含以下与生成输出相关的配置：

- 使用站点路径
- 站点路径
- 站点
- Publish路径
- 主题页面模板
- 根据生成页面名称
   - 主题文件名
   - 主题标题
- 清理以前生成的页面
   - 为从映射中删除的主题删除以前生成的页面
   - 删除此路径下由其他源创建的所有页面：
- 后期生成工作流



**内容**

**Content**&#x200B;选项卡包含以下配置：

- 使用基线
- 条件筛选
- 其他DITA-OT命令行参数
- 元数据
   - 文件(Assets)属性
   - 使用映射属性作为回退


有关详细信息，请参阅[AEM Sites配置](#aem_sites_config)。

**主题列表**

**主题列表**&#x200B;显示DITA映射的当前工作副本中存在的主题列表。 默认情况下，包含所有主题。 您可以选择特定主题，并仅为其生成AEM Sites输出。 例如，您已更新了某些主题，因此您可以仅发布这些主题，而不是发布整个DITA映射。

未基于旧版映射创建的AEM预设中存在&#x200B;**主题列表**&#x200B;选项卡。

**交叉映射引用**
此列表包含的主题包含`scope ="peer"`的交叉映射引用。 您可以为其他DITA映射中可用的主题的`scope="peer"`交叉映射引用列表指定发布上下文。 如果您使用Experience Manager Guides (UUID)版本，将显示此选项卡。



详细了解如何[发布链接的主题](#publish-linked-topics)。





## AEM Sites配置 {#aem_sites_config}

以下选项可用于AEM Sites输出：

| AEM Sites选项 | 描述 |
| --- | --- |
| 使用站点路径 | 使用此选项可将您的内容发布到Experience Manager站点。 如果您知道要将输出发布到的确切站点路径，请选择此选项。 此外，在站点路径字段中提及完整路径。 |
| 站点路径 | 如果选择&#x200B;**使用站点路径**&#x200B;选项，则会显示此选项。 浏览您希望发布输出的确切Experience Manager站点路径。 |
| 站点 | 要将内容发布到的Experience Manager Sites的名称。 下拉列表中的选项会根据AEM Sites中可用的站点列表进行填充。 <br>选择&#x200B;**刷新** ![刷新图标](images/navtitle-refresh-icon.svg)以获取新选项列表并反映更新的数据。 |
| Publish路径 | AEM存储库中存储输出的路径。 Publish路径会填充为包含根据主页模板创建的页面的所有路径。 DITA映射的AEM Sites输出在此路径下生成。  例如，如果您将站点指定为`AEMG-Docs`，将Publish路径指定为`aemg-docs-en/docs/product-abc.`，则将在`crx/de`中的`aemg-docs-en/docs/product-abc/`节点下生成AEM Sites输出。 |
| 主题页面模板 | 可用于在多个文档间以一致的方式组织内容的结构组件。 这些模板是在Adobe Experience Manager站点模板中预定义的。 这些选项中填充了可用于所选站点的所有主题页面模板。 选择要应用于所有输出主题的模板。 |
| 根据生成页面名称 | **主题文件名**：使用DITA主题的文件名创建站点URL。<br> **主题标题**：使用DITA主题的标题创建Experience Manager站点名称。 |
| 清理以前生成的页面 | - **删除从映射中删除的主题先前生成的页面**：如果DTIA映射的结构发生更改，则可以使用此选项为已删除的主题删除先前生成的页面。 此功能仅适用于完全映射发布。<br><br>假设您已发布一个DITA映射，其中包含主题a.dita、b.dita和c.dita。 再次发布映射之前，您已从映射中删除了b.dita主题。 现在，如果您选择了此选项，则与b.dita相关的所有内容都将从AEM Sites输出中删除，并且仅发布a.dita和c.dita。<br><br>**注意**：输出生成日志中还捕获了有关已删除页面的信息。 有关访问日志文件的详细信息，请[查看并检查日志文件](generate-output-basic-troubleshooting.md#id1821I0Y0G0A__id1822G0P0CHS)。 <br><br>**警告**：删除主题时，已发布站点中的页面将不可用。 因此，在删除主题之前，会出现警告。 您必须确认删除它们。<br><br>- **删除此路径上其他源创建的所有页面**：如果选择此选项，则将从其他映射、单个主题或任何其他源中删除此路径上发布的所有页面。 已发布的站点中的页面也将不可用。 因此，在删除主题之前，会出现警告。 您必须确认删除它们。 |
| 后期生成工作流 | 选择此选项时，将显示一个新的后期生成工作流下拉列表，其中包含在AEM中配置的所有工作流。 必须选择要在输出生成工作流完成后执行的工作流。 |
| 使用基线 | 如果已为所选DITA映射创建了基线，请选择此选项以指定要发布的版本。<br><br>**重要信息**：当您为AEM Site生成增量输出时，将使用当前版本的文件而不是附加的基线创建输出。<br><br>查看[使用基线](generate-output-use-baseline-for-publishing.md#id1825FI0J0PF)以了解更多详细信息。 |
| 条件筛选 | 选择以下选项之一：<br><br>**无**：如果不想对已发布的输出应用任何条件，请选择此选项。<br>**使用DITAVAL**：选择DITAVal文件以生成条件化内容。 可使用浏览对话框或键入文件路径来选择多个DITAVal文件。 使用文件名旁边的交叉图标可将其删除。 DITAVal文件将按指定的顺序进行计算，因此第一个文件中指定的条件优先于后续文件中指定的匹配条件。 您可以通过添加或删除文件来维护文件顺序。 如果将DITAVal文件移动到其他位置或将其删除，则不会从映射操控板中自动将其删除。 如果移动或删除了文件，则需要更新位置。 您可以将鼠标悬停在文件名上以查看存储该文件的AEM资料档案库中的路径。 您只能选择DITAVal文件，如果选择了任何其他文件类型，则会显示错误。<br>**条件预设**：从下拉列表中选择条件预设，以在发布输出时应用条件。 如果为DITA映射文件添加了条件，则此选项可见。 条件设置在DITA映射控制台的条件预设选项卡中可用。 要了解有关条件预设的更多信息，请查看[使用条件预设](generate-output-use-condition-presets.md#id1825FL004PN)。 |
| 其他DITA-OT命令行参数 | 指定在生成输出时希望DITA-OT处理的其他参数。 有关DITA-OT中支持的命令行参数的详细信息，请查看[DITA-OT文档](https://www.dita-ot.org/)。 |
| 元数据<br> <br>文件(Assets)属性 | 选择要作为元数据处理的属性。 这些属性是从DITA映射或书签文件的属性页面设置的。 您从下拉列表中选择的属性显示在&#x200B;**文件属性**&#x200B;字段下。 选择资产旁边的交叉图标以将其删除。 <br><br>**注意**：元数据属性区分大小写。<br><br>*如果已选择基线，则属性的值将基于所选基线的版本。<br>*&#x200B;如果您未选择基线，则属性的值将基于最新版本。<br><br>您还可以使用DITA-OT发布将元数据传递到输出。 有关更多详细信息视图，[使用DITA-OT](pass-metadata-dita-ot.md#id21BJ00QD0XA)将元数据传递到输出。<br><br>**注意**：如果您尚未在“属性”选项中定义`cq:tags`，那么即使您选择了基线进行发布，也会从当前工作副本中提取`cq:tags`的值。 |
| 元数据<br> <br>使用映射属性作为回退 | 如果选中，为映射文件定义的属性也会复制到未定义此类属性的主题中。 使用此选项时，请考虑以下几点：<br><br>*只能将字符串、日期或长（单值和多值）属性传递到AEM站点页面。<br>*&#x200B;字符串类型属性的元数据值不支持任何特殊字符（如`@, #, " "`）。<br>*此选项应与`Properties`选项一起使用。 |
| 保留临时文件 | 选择此选项可保留由DITA-OT生成的临时文件。 如果在通过DITA-OT生成输出时遇到错误，请选择此选项以保留临时文件。 然后，您可以使用这些文件来排查输出生成错误。<br> <br>生成输出后，选择&#x200B;**下载临时文件** ![下载临时文件图标](images/download-temp-files-icon.png)图标以下载包含临时文件的ZIP文件夹。<br><br> **注意**：如果在生成期间添加文件属性，则输出临时文件还包括包含这些属性的&#x200B;*metadata.xml*&#x200B;文件。 |


### 使用模板生成AEM Sites输出

Experience Manager Guides允许您使用现成的模板或添加您自己的AEM Sites模板。

在配置AEM Sites预设之前，请确保使用模板创建AEM Sites结构。\
有关详细信息，请查看[下载并安装AEM Sites模板](/help/product-guide/install-guide/download-install-aem-sites-templates.md)。



执行以下步骤创建和配置AEM Sites预设：
1. 打开要发布的DITA映射的&#x200B;**输出预设**&#x200B;选项卡。
1. 选择&#x200B;**AEM Sites**&#x200B;输出预设。
1. （可选）取消选中&#x200B;**使用旧版组件映射**&#x200B;选项来创建非旧版AEM Sites预设。
1. 单击&#x200B;**添加**。将创建AEM Sites的预设。
1. 您可以通过两种方式配置现成的站点模板：
   1. 选择&#x200B;**站点**，然后从填充的选项中选择发布路径和主题页面模板：
      1. 选择站点。
      1. 选择&#x200B;**站点**。 例如：`AEMG Docs`。
      1. 在下拉列表中自动设置&#x200B;**Publish路径**&#x200B;和&#x200B;**主题页面模板**&#x200B;选项。 您还可以选择选项。 例如，`AEMG-Docs-Site/en/docs/product1`和`Topic page`分别设置。
   1. 选择完整的站点路径：
      1. 选择&#x200B;**使用站点路径**&#x200B;选项。
      1. 选择完整的站点路径。 例如：`/content/AEMG-Docs-Site/en/docs/product1`。
      1. “主题页面模板”自动设置为`Topic Page`。


1. 保存对预设所做的更改。
1. 选择&#x200B;**生成**&#x200B;选项。
1. 为相应的映射生成AEM Sites。 例如：`/content/AEMG-Docs-Site/en/docs/product`。


   >[!NOTE]
   >
   > 如果您是首次将内容发布到AEM站点，则建议在站点级别发布页面。 这将确保输出在&#x200B;**Publish**&#x200B;实例上正确显示，不会出现任何CSS中断。



### Publish链接的主题

通过允许您使用`peer @scope`创建主题引用，Experience Manager Guides简化了复杂文档的发布。 然后，您可以从AEM Sites预设中定义这些引用的发布上下文，最后生成链接主题的输出。
有关更多详细信息，请查看[从其他映射生成链接主题的输出](../user-guide/generate-output-aem-site.md#generate-output-linking-topics-from-other-maps)。




执行以下步骤可指定交叉链接文件的发布上下文：
1. 打开要发布的DITA映射的&#x200B;**输出预设**&#x200B;选项卡。
1. 选择&#x200B;**AEM Sites**&#x200B;输出预设。

   您可以查看&#x200B;**常规**、**内容**、**主题列表**&#x200B;和&#x200B;**交叉映射引用**&#x200B;选项卡。 如果您使用Experience Manager Guides (UUID)版本，将显示&#x200B;**交叉映射引用**&#x200B;选项卡。

   在以下情况中，您将无法查看交叉图链接：
   - 对于4.6版本之前创建的预设。 “交叉引用”选项卡已禁用，并且会显示工具提示“参考映射”操控板。
   - 对于从映射仪表板创建的预设。 请参阅显示映射仪表板工具提示。
   - 对于OOTB预设，请参阅显示映射功能板工具提示。
   - 对于全局预设，请创建此全局预设的本地副本以设置交叉映射引用。
如果要从Web编辑器中使用AEM Sites预设，请创建新预设或复制现有预设。

1. 打开&#x200B;**交叉映射引用**&#x200B;选项卡。

   您会看到一个主题及其引用列表。 您可以为对具有`scope="peer"`的其他DITA映射中可用主题的交叉映射引用列表指定发布上下文。

   要使用Web编辑器中的跨映射引用面板，`<xrefs>`必须具有唯一ID。 如果`<xrefs>`的唯一ID不存在，则在编辑/保存旧内容时将自动生成ID。

   >[!NOTE]
   >
   >**交叉映射引用**&#x200B;选项卡仅显示使用`scope="peer"`链接的主题。 对于具有`scope="local"`的链接，无需指定发布上下文。

   默认情况下，所有链接的主题都会选择其最新的输出预设和映射。 默认情况下，所有链接主题的发布上下文均设置为`<Most recently generated>`映射。

   ![交叉映射引用](images/aem-sites-cross-map-references.png)

1. 如果要使用映射中每个依赖文件的最近发布的输出，请选择&#x200B;**为所有依赖主题使用最近生成的**发布上下文。
在发布包含链接主题的映射之前，您应该发布选定作为父映射的映射。 如果未发布包含链接主题的映射，则在AEM Sites输出中，链接将显示为普通文本而非超链接。
您应为链接的主题选择相同类型的AEM Sites预设。 例如，如果当前AEM Sites预设使用旧版组件映射，则为链接的主题选择类似的AEM Sites预设。
1. 在“父映射”下拉列表中，选择要为其输出链接当前映射输出的映射文件。
选择映射文件会在“父映射UUID”列中显示映射的UUID。 与所选映射关联的输出预设列在父映射的预设列表中。 例如，映射A中的主题1包含对主题2的引用。 主题2可以出现在单个或多个映射中。 您可以选择父映射和特定预设，也可以为每个链接选择最近发布的输出。

1. 如果同一主题在文件中被引用多次，则可以为每个实例添加不同的发布上下文。 这提供了更大的灵活性和对其内容的控制。 例如，主题3同时存在于映射B和映射C中。主题1包含两个对主题3的引用。 您可以选择映射B作为第一个链接的父映射，选择映射C作为第二个链接的父映射。

1. 在父映射的预设下拉列表中，选择要与当前映射的输出链接的输出预设。
   >[!NOTE]
   >
   > 下拉列表中将显示当前映射的其他AEM Sites预设。 如果未选择预设，则会出现警告图标，并且输出生成会失败。
1. 为所有源主题选择所需的映射及其输出预设，然后选择&#x200B;**生成**。







**父主题：** [了解输出预设](generate-output-understand-presets.md)
