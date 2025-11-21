---
title: 配置输出生成设置
description: 了解如何配置输出生成设置
exl-id: b5cf4f6c-dc56-428e-a514-6c9f879ac03d
feature: Output Generation
role: Admin
level: Experienced
source-git-commit: 6e23f52fc9124d0f07f8108da1b5fe574f553469
workflow-type: tm+mt
source-wordcount: '5615'
ht-degree: 0%

---

# 配置输出生成设置 {#id181AI0B0E30}

AEM Guides提供了许多配置选项，供您自定义输出生成过程。 本主题介绍有助于您设置输出生成过程的所有配置和自定义设置。

## 在DITA映射操控板上配置基线选项卡 {#id223MD0D0YRM}

要在DITA map操控板上隐藏“基线”选项卡，请执行以下步骤：

1. 使用[配置覆盖](download-install-additional-config-override.md#)中提供的说明创建配置文件。
1. 在配置文件中，提供以下\(property\)详细信息以在映射功能板上配置基线选项卡。

| PID | 属性键 | 属性值 |
|---|------------|--------------|
| `com.adobe.fmdita.config.ConfigManager` | `hide.tabs.baseline` | 布尔值\(`true/false`\)。**默认值**： `true` |

>[!NOTE]
>
> 默认情况下，此配置处于启用状态，并且基线选项卡在映射功能板上不可用。

## 在现有AEM站点中配置混合发布 {#id1691I0V0MGR}

如果您有一个包含DITA内容的AEM站点，则可以配置AEM站点输出以将DITA内容发布到站点内的预定义位置。 例如，在以下AEM站点页面屏幕截图中，`ditacontent`节点为存储DITA内容而保留：

![](assets/publish-in-aem-site.png)

页面中的其余节点直接从AEM站点编辑器创作。 将发布设置配置为将DITA内容发布到预定义的位置，可确保AEM Guides发布过程不会修改任何现有的非DITA内容。

您需要在现有站点上执行以下配置，以允许将DITA内容发布到预定义节点：

- 配置网站的模板属性

- 在站点中添加节点以发布DITA内容


执行以下步骤可配置现有站点的模板属性：

1. 使用包管理器下载/libs/fmdita/config/templates/default文件。

   >[!NOTE]
   >
   > 请勿在`libs`节点中使用默认配置文件中的任何自定义设置。 您必须在`libs`节点中创建`apps`节点的叠加，并仅更新`apps`节点中的所需文件。

1. 添加以下属性：

   | 属性名称 | 类型 | 价值 |
   |-------------|----|-----|
   | `topicContentNode` | 字符串 | 指定要发布DITA内容的节点名称。 例如，AEM Guides发布DITA内容的默认节点为： <br> `jcr:content/contentnode` |
   | `topicHeadNode` | 字符串 | 指定要存储DITA内容的元数据信息的节点名称。 例如，AEM Guides存储元数据信息的默认节点为： <br> `jcr:content/headnode` |


下次使用网站的模板配置发布任何DITA内容时，该内容将发布到`topicContentNode`和`topicHeadNode`属性中指定的节点。

## 自定义AEM站点输出 {#id166TG0B30WR}

AEM Guides支持以下列格式创建输出：

- AEM站点
- PDF
- HTML5
- ePub
- 通过DITA-OT自定义输出

对于AEM Site输出，您可以为不同的输出任务分配不同的设计模板。 这些设计模板可以不同布局呈现DITA内容。 例如，您可以为内部和外部受众指定不同的设计模板。

您还可以将自定义DITA Open Toolkit \(DITA-OT\)插件与AEM Guides结合使用。 您可以上传这些自定义DITA-OT插件，以通过特定方式生成PDF输出。

>[!TIP]
>
> 有关创建AEM站点输出的最佳实践，请参阅“最佳实践指南”中的&#x200B;*AEM站点发布*&#x200B;部分。


### 自定义用于生成输出的设计模板 {#customize_xml-add-on}

AEM Guides使用一组预定义的设计模板来生成AEM站点输出。 您可以自定义AEM Guides设计模板，以生成符合您公司品牌策略的输出。 设计模板是各种样式\(CSS\)、脚本\（服务器和客户端\）、资源\（图像、徽标和其他资源\）以及将所有这些资源绑定在一起的JCR节点的集合。 设计模板可以非常简单，只需具有几个JCR节点的单个服务器端脚本，也可以是样式、资源和JCR节点的复杂组合。 设计模板由AEM Guides发布子系统在生成AEM站点输出时使用，它们控制所生成输出的结构、外观和风格。

设计模板资源在服务器上的放置位置没有限制，但通常会根据其功能进行逻辑组织。 例如，默认模板的所有其JavaScript和CSS文件都存储在`/etc/designs/fmdita/clientlibs/siteoutput/default`文件夹下。 无论这些文件位于何处，它们都会通过一组JCR节点链接在一起。 这些JCR节点和文件共同构成了整个设计模板。

AEM Guides附带的默认设计模板允许您自定义登录、主题和搜索页面组件。 您可以复制缺省设计和相应的参照模板，并指定不同的元件来生成所需的输出。

执行以下步骤，指定用于AEM站点输出生成的您自己的设计模板：

1. 使用包管理器从以下位置下载默认设计模板：

   /libs/fmdita/config/templates

1. 在Cloud Manager Git存储库中的以下位置创建已下载文件的副本：

   /apps/fmdita/config/templates

1. 还必须下载并复制从默认模板节点引用的模板。 引用的模板将放置在：

   /libs/fmdita/templates/default/cqtemplates

   下表描述了AEM Guides设计模板的属性。

   | 属性 | 描述 |
   |--------|-----------|
   | `landingPageTemplate`，`searchPageTemplate`，`topicPageTemplate`，`shadowPageTemplate` | 为这些对应页面指定`cq:Template`节点\（登陆、搜索和主题\）。 默认情况下，这些页面的`cq:Template`节点可以在`/libs/fmdita/templates/default/cqtemplates`节点中找到。 此节点定义登录、搜索和主题页面的结构和属性。<br> `shadowPageTemplate`用于优化分块内容。 您需要将此属性的值设置为： `fmdita/templates/default/cqtemplates/shadowpage` <br> **注意：**&#x200B;您必须为`topicPageTemplate`指定一个值。 `landingPageTemplate`和`searchPageTemplate`是可选属性。 如果您不希望生成搜索和登陆页面，请不要指定这些属性。 |
   | `title` | 设计模板的描述性名称。 |
   | `topicContentNode` | 将在主题页面中包含DITA内容的节点的位置。 路径相对于主题页面。 |
   | `topicHeadNode` | 包含派生自DITA内容的头值\（或metadata\）的节点位置。 路径相对于主题页面。 |
   | `tocNode` | 将包含目录的节点的位置。 路径相对于登陆页面或目标路径。 |
   | `basePathProp` | 用于存储已发布站点的根目录的路径的属性名称。 |
   | `indexPathProp` | 用于存储已发布站点的登陆/索引页面路径的属性名称。 |
   | `pdfPathProp` | 用于存储主题PDF路径的属性名称(如果启用了主题PDF生成)。 |
   | `pdfTypeProp` | 用于存储PDF生成类型的属性名称。 目前，此属性始终包含“主题”。 |
   | `searchPathProp` | 用于存储搜索页面路径的属性名称（如果模板包含搜索页面）。 |
   | `siteTitleProp` | 用于存储正在发布的站点标题的属性名称。 此标题通常与正在发布的地图的标题相同。 |
   | `sourcePathProp` | 用于存储当前页面的源DITA主题的路径的属性名称。 |
   | `tocPathProp` | 用于存储已发布站点的目录根目录的路径的属性名称。 |


>[!NOTE]
>
> 创建自定义设计模板节点后，必须更新AEM站点输出预设中的设计选项才能使用自定义设计模板节点。

有关详细信息，请参阅[创建您的第一个Adobe Experience Manager网站](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html?lang=zh-Hans)和[在AEM上开发您自己的网站的基础知识](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/full-stack/develop-wknd-tutorial.html?lang=zh-Hans)。

### 使用文档标题生成AEM站点输出

在生成AEM Site输出时，生成URL的方式对内容的可发现性起着重要作用。 如果您使用的是基于UUID的文件名，则根据文件的UUID生成URL不利于搜索。 作为管理员或发布者，您可以控制如何为AEM站点输出生成URL。 AEM Guides为您提供了一个配置，通过该配置，您可以选择使用文件的标题而不是基于UUID的文件名来生成AEM站点输出的URL。 默认情况下，对于基于UUID的文件系统，此选项处于打开状态。 这意味着在为基于UUID的文件系统生成AEM Site输出时，使用文件的标题来生成URL，而不是文件的UUID。

>[!NOTE]
>
> 您可以进一步配置规则，以仅允许在AEM站点输出的URL中设置一组字符。 有关更多详细信息，请参阅[配置用于创建主题和发布AEM站点输出的文件名清理规则](#id2164D0KD0XA)。

使用[配置覆盖](download-install-additional-config-override.md#)中提供的说明创建配置文件。 在配置文件中，提供以下\(property\)详细信息以在AEM站点输出中配置URL生成：

| PID | 属性键 | 属性值 |
|---|------------|--------------|
| `com.adobe.fmdita.config.ConfigManager` | `aemsite.pagetitle` | 布尔值\(true/false\)。 如果要使用页面标题生成输出，则将此属性设置为true。 默认情况下，它设置为使用文件名。<br> **默认值**： false |

### 配置AEM站点输出的URL以使用文档标题

您可以在AEM站点输出的URL中使用文档标题。 如果文件名不存在或包含所有特殊字符，则可以配置系统以在AEM Site输出的URL中使用分隔符替换特殊字符。 您还可以将其配置为使用第一个子主题名称替换它们。


要配置页面名称，请执行以下步骤：

1. 使用[配置覆盖](download-install-additional-config-override.md#)中提供的说明创建配置文件。
1. 在配置文件中，提供以下（属性）详细信息以配置主题的页面名称。

| PID | 属性键 | 属性值 |
|---|------------|--------------|
| `com.adobe.fmdita.common.SanitizeNodeName` | `nodename.systemDefinedPageName` | 布尔值(`true/false`)。 **默认值**： `false` |

例如，如果&#x200B;*中的*@navtitle`<topichead>`包含所有特殊字符，并且您将`aemsite.pagetitle`属性设置为true，则默认情况下，它使用分隔符。 如果将`nodename.systemDefinedPageName`属性设置为true，它将显示第一个子主题的名称。


### 配置用于创建主题和以AEM Sites和其他格式发布输出的文件名清理规则 {#id2164D0KD0XA}

作为管理员，您可以定义文件名中允许的有效特殊字符列表，这些字符最终形成AEM Site输出的URL。 在早期版本中，允许用户定义包含`@`、`$`、`>`等特殊字符的文件名。 这些特殊字符会在生成AEM网站页面时生成经过编码的URL。

从3.8版本开始，添加了配置以定义允许文件名中使用的特殊字符列表。 默认情况下，有效的文件名配置包含“`a-z A-Z 0-9 - _`”。 这意味着，在创建文件时，文件的标题中可以包含任何特殊字符，但在内部，该文件名中将替换为连字符\(`-`\)。 例如，文件的标题可以是Introduction 1或Introduction@1 ，针对这两种情况生成的相应文件名是Introduction-1。

定义有效字符列表时，请记住，这些字符“`*/:[\]|#%{}?&<>"/+`”和`a space`将始终替换为连字符\(`-`\)。

>[!NOTE]
>
> 如果未配置有效的特殊字符列表，文件创建过程可能会给您一些意外的结果。

使用[配置覆盖](download-install-additional-config-override.md#)中提供的说明创建配置文件。 在配置文件中，提供以下\(property\)详细信息以在文件名和AEM站点输出中配置有效的特殊字符：

| PID | 属性键 | 属性值 |
|---|------------|--------------|
| `com.adobe.fmdita.common.SanitizeNodeNameImpl` | `aemsite.DisallowedFileNameChars` | 确保将该属性设置为``'<>`@$``。 您可以向此列表添加更多特殊字符。 |

>[!NOTE]
> 
> 上述配置适用于所有输出格式。 这意味着在生成PDF、HTML或自定义输出时，最终输出将遵循配置的文件名清理规则。

您还可以配置其他属性，如文件名中的使用小写、用于处理无效字符的分隔符以及文件名中允许的最大字符数。 要配置这些属性，请在配置文件中添加以下键值对：

| 属性键 | 属性值 |
|------------|--------------|
| `nodename.uselower` | 布尔值\(true/false\)。<br> **默认值**： true |
| `nodename.separator` | 任意字符。<br> **默认值**： \_ *\（下划线\）* |
| `nodename.maxlength` | 整数值。<br> **默认值**： 50 |

### 配置AEM站点节点结构的扁平化

在生成AEM Site输出时，将在内部创建主题中每个元素的节点。 对于包含数千个主题的DITA映射，此节点结构可能会变得太深。 对于较大的站点，这种类型的深度嵌套节点结构可能存在性能问题。 以下快照显示AEM站点输出的深度嵌套节点结构：

![](assets/deep-nested-aem-site-node-structure.png)

在上述快照中，请注意为每个`p`元素及其后续子元素创建一个节点，并为主题中使用的其他每个元素创建一个类似结构。

AEM Guides允许您配置如何在内部创建AEM站点输出的节点结构。 可以在指定的元素处拼合节点结构，这意味着您可以定义一个元素，该元素将被视为主元素，其中的所有子元素将与主元素合并。 例如，如果您决定拼合`p`元素，则出现在`p`元素中的任何元素都将与主`p`元素合并。 将不会为`p`元素中的任何子元素创建单独的注释。 以下快照显示扁平化在`p`元素处的节点结构：

![](assets/flattened-aem-site-node-structure.png)

要扁平化AEM Site节点结构，请执行以下步骤：

1. 确定要扁平化节点结构的元素：

1. 覆盖`libs`节点中的`apps`节点，并打开elementmapping.xml文件。

1. 在要扁平化节点结构的元素的定义中添加`<flatten>true</flatten>`属性。 例如，如果要拼合`p`元素的节点结构，则在`p`元素的定义中添加flatten属性，如下所示：

   ```XML
   <ditaelement>
         <name>p</name>
         <class>- topic/p</class>
         <componentpath>fmdita/components/dita/wrapper</componentpath>
         <type>COMPOSITE</type>
         <target>para</target>
         <flatten>true</flatten>
         <wrapelement>div</wrapelement>
      </ditaelement>
   ```

   >[!NOTE]
   >
   > 默认情况下，已在`p`元素上配置了flatten节点属性。

1. 使用[配置覆盖](download-install-additional-config-override.md#)中提供的说明创建配置文件。
1. 在配置文件中，提供以下\(property\)详细信息：

   | PID | 属性键 | 属性值 |
   |---|------------|--------------|
   | `com.adobe.dxml.flattening.FlatteningConfigurationService` | `flattening.enabled` | 布尔值\(true/false\)。<br> **默认值**： `false` |


现在，当您生成AEM站点输出时，`p`元素中的节点将被扁平化并存储在`p`元素本身中。 您可以在CRXDE中找到`p`元素的新拼合属性。

![](assets/flatten-aem-site-note-props-crxde.png)

**在AEM网站输出的内容中搜索字符串**

默认情况下，您只能在AEM站点输出的标题中搜索字符串。 您可以将系统配置为在AEM站点输出的标题以及内容或正文中搜索字符串。

>[!NOTE]
>
> 有时，您的搜索可能适用于内容中的某些元素，但您可以将其配置为适用于整个内容。

![](assets/flatten-aem-site-note-props-crxde-search.png)

要启用搜索，您应该配置AEM站点节点结构的拼合。

注意:

您最多可以搜索1MB的拼合内容。 例如，在上一个屏幕截图中，您可以搜索&lt;p\>标记下的内容是否小于= 1Mb。

>[!NOTE]
>
> 仅当`<flatten>`属性设置为true时，搜索才对元素起作用。 默认情况下，AEM Guides将&lt;p\> &lt;ul\> &lt;lI\>等常用文本元素的`<flatten>`属性设置为true。 但是，如果您已经创建了一些自定义元素，则应在elementmapping.xml文件中将`<flatten>`属性设置为true。

**阻止拼合AEM站点节点结构**

与在AEM站点输出中指定要拼合的节点类似，您还可以指定要从此配置中排除的元素。 例如，如果要拼合`body`元素上的节点，但不希望`table`中的任何`body`元素拼合，则可以在`table`元素的定义中添加exclude属性。

要从拼合中排除`table`元素，请将以下属性添加到`table`元素的定义中：

`<preventancestorflattening>true|false</preventancestorflattening>`

### 在AEM站点输出中为已删除的页面配置版本控制

生成针对“现有输出页面”设置选择了&#x200B;**删除和**&#x200B;创建&#x200B;**&#x200B;**&#x200B;选项的AEM站点输出时，将为要删除的页面创建一个版本。 您可以将系统配置为在删除之前停止创建版本。

执行以下步骤可停止为要删除的页面创建版本：

1. 使用[配置覆盖](download-install-additional-config-override.md#)中提供的说明创建配置文件。
1. 在配置文件中，提供以下\(property\)详细信息以配置&#x200B;**不要为已删除的页面创建版本**&#x200B;选项：

   | PID | 属性键 | 属性值 |
   |---|------------|--------------|
   | `com.adobe.fmdita.confi g.ConfigManager` | `no.version.creation.on.deletion` | 布尔值\(true/false\)。<br> **默认值**： `true` |

   >[!NOTE]
   >
   > 选中此选项后，用户可直接删除任何页面，而无需为其创建任何版本。 如果未选中该选项，则在删除页面之前将创建一个版本。

### 使用Experience Manager Guides设置自定义重写器 {#custom-rewriter}

Experience Manager Guides有一个自定义sling [**重写器**](https://sling.apache.org/documentation/bundles/output-rewriting-pipelines-org-apache-sling-rewriter.html)模块，用于处理在交叉映射情况下生成的链接（两个不同映射的主题之间的链接）。 此重写器配置安装在以下路径中： <br> `/apps/fmdita/config/rewriter/fmdita-crossmap-link-patcher`。

如果您的代码库中有另一个自定义sling重写器，请使用大于50的`'order'`值，因为Experience Manager Guides sling重写器使用`'order'` 50。  要覆盖此值，您需要一个值>50 。 有关详细信息，请查看[输出重写管道](https://sling.apache.org/documentation/bundles/output-rewriting-pipelines-org-apache-sling-rewriter.html)。


## 通过DITA-OT发布输出时使用元数据 {#id191LF0U0TY4}

AEM Guides提供了一种在使用DITA-OT发布输出时传递自定义元数据的方式。 作为管理员和发布者，您需要执行以下任务以在已发布输出中配置和使用自定义元数据：

- 作为管理员，在系统中添加所需的元数据，以便该元数据在DITA映射的“属性”页面上可用。

- 作为管理员，将自定义元数据添加到元数据列表中，以便该元数据显示在DITA映射控制台中。

- 作为发布者，使用DITA映射配置和添加自定义元数据并生成所需的输出。


要在系统中添加所需的元数据，请执行以下步骤：

1. 以管理员身份登录Adobe Experience Manager。

1. 单击顶部的Adobe Experience Manager链接，然后选择&#x200B;**工具**。

1. 从工具列表中选择&#x200B;**Assets**。

1. 单击&#x200B;**元数据架构**&#x200B;磁贴。

   此时会显示元数据架构Forms页面。

1. 从列表中选择&#x200B;**default**&#x200B;表单。

   >[!NOTE]
   >
   > 在DITA映射的“属性”页面上显示的属性取自此表单。

1. 单击&#x200B;**编辑**。

1. 添加要在发布的输出中使用的自定义元数据。 例如，我们将使用以下步骤添加受众元数据：

   1. 从&#x200B;**构建表单**&#x200B;组件列表中，将&#x200B;**单行文本**&#x200B;组件拖放到表单上。

   2. 选择新字段以打开该字段的&#x200B;**设置**。

   3. 在&#x200B;**字段标签**&#x200B;中，输入元数据名称 — Audience。

   4. 在&#x200B;**映射到属性**&#x200B;设置中，指定。/jcr:content/metadata/&lt;元数据的名称\>。 例如，我们将其设置为。/jcr:content/metadata/audience。

   使用这些步骤，添加所有必需的元数据参数。

1. 单击&#x200B;**保存**。


现在，所有DITA映射的“属性”页面中都会显示新参数。

![](assets/properties-page-custom-metadata.PNG)

接下来，您需要使自定义元数据在DITA映射控制台中可用。 执行以下步骤，使自定义元数据在DITA映射短划线板上可用：

1. 使用包管理器访问metadataList文件，该文件可在Cloud Manager Git存储库中的以下位置找到：

   /libs/fmdita/config/metadataList

   >[!NOTE]
   >
   > metadataList文件包含属性列表，这些属性显示在映射仪表板中DITA映射的&#x200B;**属性**&#x200B;下拉列表中。 默认情况下，此文件列出了四个属性 — dostate、dc:language、dc:description和dc:title。

1. 添加您在元数据架构Forms页面中添加的自定义元数据。 例如，将受众参数添加到默认列表的末尾。


现在，自定义元数据将显示在DITA映射控制台的&#x200B;**属性**&#x200B;下拉列表中。

最后，作为发布者，您需要在发布的输出中包含自定义元数据。 要在生成输出时处理自定义元数据，请执行以下步骤：

1. 在Assets UI中，导航到要发布的DITA映射。

1. 选择DITA映射文件并打开其属性页。

1. 在属性页面上，指定自定义元数据的值。 在本例中，我们为受众参数指定了External值。

   ![](assets/properties-page-custom-metadata-value.png)

1. 单击&#x200B;**保存并关闭**。

1. 单击DITA映射文件以打开DITA映射控制台。

1. 在&#x200B;**输出预设**&#x200B;选项卡中，选择要用于生成输出的输出预设。

1. 单击&#x200B;**编辑**。

1. 从&#x200B;**属性**&#x200B;下拉列表中，选择要传递给发布进程的属性。

   ![](assets/props-in-publish-output.PNG)


选定的属性/元数据将传递到发布流程，并在最终输出中可用。

### 验证传递到DITA-OT以供处理的元数据

为了验证传递到DITA-OT的元数据值，可以使用使用云就绪jar的本地环境。 由于我们无法在云上访问本地文件系统，因此验证元数据文件的唯一方法是通过cloud ready jar。

- 文件名： metadata.xml
- 文件位置：crx-quickstart/profiles/ditamaps/&lt;ditamap-1234\>

  要访问metadata.xml，请执行以下操作：

   - 登录到运行AEM实例的服务器位置。
   - 迁移到crx-quickstart/profiles/ditamaps/&lt;new-created-directory-name\>/metadata.xml。
- 示例文件格式：

  **metadata.xml**

  ```XML
  <?xml version="1.0" encoding="UTF-8" standalone="no"?>
  <root>
     <Path id="/absolutePath/sampleMap.ditamap">
        <metadata>
           <meta isArray="false" key="dc:description">This is a file</meta>
           <meta isArray="false" key="dc:title">Myfile</meta>
           <meta isArray="true" key="multivalueText">One;Two;Three</meta>
        </metadata>
     </Path>
     <Path id="/absolutePath/sampleTopic.dita">
        <metadata>
           <meta isArray="false" key="dc:description">description for the accountability</meta>
           <meta isArray="false" key="dc:title">accountability title</meta>
           <meta isArray="true" key="multivalueText">value1</meta>
        </metadata>
     </Path>
  </root>
  ```


- isArray：一个布尔属性，定义元数据是否为多值\(Array\)。 值以分号分隔。
- 路径ID：存储在临时目录下的文件的绝对路径。

>[!NOTE]
>
> 如果文件不存在特定的元数据，则带键的&lt;meta\>标记将不会作为该文件的属性显示在metadata.xml文件中。

## 配置DITA-OT命令行参数字段以接受根映射元数据

要使用DITA-OT命令行参数字段传递根映射元数据，请执行以下步骤：

1. 使用[配置覆盖](download-install-additional-config-override.md#)中提供的说明创建配置文件。
1. 在配置文件中，提供以下\(property\)详细信息以配置预设中的DITA-OT命令行参数字段：

| PID | 属性键 | 属性值 |
|---|------------|--------------|
| `com.adobe.fmdita.config.ConfigManager` | `pass.metadata.args.cmd.line` | 布尔值\(`true/false`\)。**默认值**： `true` |

- 将属性值设置为&#x200B;**true**&#x200B;可启用DITA-OT命令行功能，从而允许您通过DITA-OT命令行传递元数据。
- 将属性值设置为&#x200B;**false**&#x200B;将禁用DITA-OT命令行功能。 然后，您可以使用预设中的属性字段传递元数据。



## 使用AEM组件自定义DITA元素映射 {#id1679J600HEL}

AEM Guides中的DITA元素映射到其对应的AEM组件。 AEM Guides在发布和审阅等工作流中使用此映射，将DITA元素转换为相应的AEM组件。 该映射在`elementmapping.xml`文件中定义，可使用包管理器访问该文件。

>[!NOTE]
>
> 请勿在``libs``节点中使用默认配置文件中的任何自定义设置。 您必须在``libs``节点中创建``apps``节点的叠加，并仅更新``apps``节点中的所需文件。

您可以使用预定义的DITA元素映射，也可以将DITA元素映射到自定义AEM组件。 要使用自定义AEM组件，您需要了解`elementmapping.xml`文件的结构。

### elementmapping.xml结构

`elementmapping.xml`结构的高级概述说明如下：

1. 首先基于元素名称搜索每个DITA元素以查找相应的组件映射。 例如：

   ```XML
   <ditaelement>     
      <name>**substeps**</name>  
      <class>- topic/ol task/substeps</class>  
      <componentpath>dita/components/ditaolist</componentpath>  
      <type>COMPOSITE</type>  
      <target>para</target>
   </ditaelement>
   ```

   在上述示例中，所有`substeps` DITA元素都使用`dita/components/ditaolist`组件渲染。

1. 如果DITA元素没有找到基于名称的匹配项，则会根据`class`进行匹配。 例如：

   ```XML
   <ditaelement>  
      <name>topic</name>  
      <class>**- topic/topic**</class>  
      <componentpath>fmdita/components/dita/topic</componentpath>  
      <type>COMPOSITE</type>  
      <target>para</target>  
      <attributemap> 
         <attribute from="id" to="id" />  
      </attributemap>
   </ditaelement>
   ```

   在上述示例中，如果没有为`task`元素定义映射，则`task`元素将映射到上述组件，因为`task`继承自`topic`组件。

1. 当元素具有相应的组件映射时，其子元素的进一步处理由`type`决定。 例如：

   ```XML
   <ditaelement>  
      <name>title</name>  
      <class>- topic/title</class>  
      <componentpath>foundation/components/title</componentpath>  
      <type>**STANDALONE**</type>  
      <target>para</target>  
      <textprop>jcr:title</textprop>
   </ditaelement>
   ```

   `type`采用以下值：

   - 组合：子元素&#x200B;*的元素到组件*&#x200B;的映射也继续。

   - 独立：当前元素的子元素是&#x200B;*未进一步映射*。

   在上述示例中，如果`<title>`元素具有任何子元素，则这些子元素将不会映射到任何其他组件。 `<title>`元素的组件负责呈现`<title>`元素中的所有子元素。

1. 如果有多个组件映射到单个DITA元素，则会选择该元素的最佳匹配项。 要选择最佳匹配元件，需要考虑DITA元素的域和结构专业化。

   如果存在具有域专门化的DITA元素并且为域专门化映射了组件，则该组件被赋予高优先级。

   同样，如果存在具有结构专门化的DITA元素并且为结构专门化映射了某个组件，则该组件将获得高优先级。

1. 您可以在元素映射中使用`<attributemap>`将属性值映射到相应的节点属性。
1. `textprop`可用于将DITA元素的文本内容序列化为节点属性。 此外，可以在元素标记中多次使用它来序列化已发布层次结构中多个位置的文本内容。 您还可以自定义目标属性的位置和名称。 例如：

   ```XML
   <ditaelement>
      <name>title</name>
      <componentpath>foundation/components/title</componentpath>
      <type>STANDALONE</type>
      <target>para</target>
       <textprop>**jcr:title**</textprop>
   </ditaelement>
   ```

   上述元素映射指定`<title>`元素的文本内容将保存为输出节点上名为`jcr:title`的属性的值。

1. `xmlprop`可用于将给定元素的整个XML序列化为节点属性。 然后，组件可以读取此节点属性并进行自定义渲染。 例如：

   ```XML
   <ditaelement>
       <name>svg-container</name>
      <class>+ topic/foreign svg-d/svg-container</class>
       <componentpath>fmdita/components/dita/svg</componentpath>
       <type>STANDALONE</type>
       <target>para</target>
      <xmlprop>**data**</xmlprop>
   </ditaelement>
   ```

   上述元素映射指定将元素`<svg-container>`的整个XML标记另存为输出节点上名为`data`的属性的值。

1. 在输出生成过程中有一个特殊的属性映射来处理路径解析。 例如：

   ```XML
   <attributemap>
      <attribute from="href" to="fileReference" ispath="true" rel="source" />
      <attribute from="height" to="height" />
       <attribute from="width" to="width" />
   </attributemap>
   ```

   对于上述`attributemap`，DITA元素中的`href`属性将映射到名为`fileReference`的节点属性。 现在，由于`ispath`设置为`true`，输出生成过程解析此路径，然后在`fileReference`节点属性中设置它。

   此解析如何根据属性映射中`rel`属性的值确定。

   - 如果`rel=source`，则相对于当前正在处理的DITA源文件解析`href`的值。 `href`的值已解析并置于`fileReference`属性的值中。

   - 如果`rel=target`，则相对于根发布位置解析`href`的值。 `href`的值已解析并置于`fileReference`属性的值中。

   如果不希望对路径属性进行任何预处理或解析，则无需指定`ispath`属性。 该值会按原样复制，组件可以执行所需的分辨率。


### DITA元素架构

以下是`elementmapping.xml`文件中的DITA元素架构示例：

```XML
<ditaelement>        
    <name>element_name</name>    
    <class>element_class</class>    
    <componentpath>fmdita/components/dita/component_name</componentpath>    
    <type>COMPOSITE|STANDALONE</type>     
    <attributeprop>propname_a</attributeprop>      
    <textprop>propname_t</textprop>    
    <xmlprop>propname_x</xmlprop>     
    <xpath>xpath expression string</xpath>     
    <target>head|para</target>     
    <wrapelement>div</wrapelement>     
    <wrapclass>class_name</wrapclass>     
    <attributemap>         
        <attribute from="attrname"         to="propname"         ispath="true|false"         rel="source|target" />    
    </attributemap>    
    <skip>true|false</skip> 
</ditaelement>
```

下表介绍了DITA元素架构中的元素：

| 元素 | 描述 |
|-------|-----------|
| `<ditaelement>` | 每个映射元素的顶级节点。 |
| `<class>` | 要为其编写组件的目标DITA元素的类属性。<br>例如，DITA主题的类属性为： <br> `- topic/topic` |
| `<componentpath>` | 映射的AEM组件的CRXDE路径。 |
| `<type>` | 可能的值： <br> -   **复合**：处理子元素以及<br> -   **STANDALONE**：跳过子元素的处理 |
| `<attributeprop>` | 用于将序列化DITA属性和值作为属性映射到AEM节点。 例如，如果您有`<note type="Caution">`元素，并且为此元素映射的组件有`<attributeprop>attr_t</ attributeprop>`，则节点的属性和值将序列化为相应AEM节点\(`attr_t`\)的`attr_t->type="caution"`属性。 |
| `<textprop>propname_t</textprop>` | 将`getTextContent()`输出保存到`propname_t.` <br>定义的属性 **注意：**&#x200B;这是一个优化的属性。 |
| `<xmlprop>propname_x </xmlprop>` | 将此节点的序列化XML保存到&#x200B;`propname_x.<br> `**定义的属性。注意：**&#x200B;这是一个优化属性。 |
| `<xpath>` | 如果在元素映射中提供了XPath元素，则还应与元素名称和类一起满足XPath条件以使用组件映射。 |
| `<target>` | 将DITA元素放置在crx存储库中的指定位置。<br>可能的值： <br> - **head**：在标题节点<br> - **text**：在段落节点下 |
| `<wrapelement>` | 要将内容包装在其中的HTML元素。 |
| `<wrapclass>` | 属性`wrapclass.`的元素值 |
| `<attributemap>` | 包含一个或多个`<attribute>`节点的容器节点。 |
| `<attribute from="attrname" to="propname" ispath="true\|false" rel="source\|target" />` | 将DITA属性映射到AEM属性： <br> -   **`from`**： DITA属性名称<br> -   **`to`**： AEM组件属性名称<br> -   **`ispath`**：如果属性是路径值\（例如： *image*\） <br> -   **`rel`**：如果路径是源或目标<br> **注意：**&#x200B;如果`attrname`以`%`开头，则将`attrname minus '%'`映射到prop“`propname`”。 |

**其他备注**

- 如果计划覆盖默认元素映射，建议不要在默认`elementmapping.xml`文件中进行更改。 您应该创建一个新的映射XML文件，并将该文件放置在其他位置，最好是放置在您创建的自定义apps文件夹中。

- 在`elementmapping.xml`文件中，有许多映射条目引用fmdita/components/dita/wrapper组件。 包装器是一个通用组件，它使用站点节点上的属性来生成相关的HTML，从而呈现相对简单的DITA结构。 它使用`wrapelement`属性生成封闭标记并将子渲染委派给相应的组件。 当您只需要容器组件时，此选项非常有用。 您可以将Wrapper组件与`div`和`p`属性结合使用，而不是创建用于呈现特定容器标记（如`wrapelement`或`wrapclass`）的新组件，以实现相同的效果。

- 建议不要在字符串JCR属性中保存大量文本。 输出生成中的优化属性类型计算可确保大型文本内容不会另存为字符串类型。 相反，当需要保存大于特定阈值的内容时，属性的类型会更改为二进制。 默认情况下，此阈值配置为512字节，但可以通过更改&#x200B;*另存为二进制阈值*&#x200B;设置在Configuration Manager \(**com.adobe.fmdita.config.ConfigManager**\)中更改。

- 如果您计划覆盖某些\（而非全部\）元素映射，则无需复制整个`elementmapping.xml`文件。 您需要创建一个新的XML映射文件，并仅定义要覆盖的元素。

- 在自定义位置中创建XML文件后，更新`Override Element Mapping`包中的`com.adobe.fmdita.config.ConfigManager`设置。


## 自定义DITA映射控制台 {#id188HC08M0CZ}

AEM Guides使您可以灵活地扩展DITA映射控制台的功能。 例如，如果您有一组与AEM Guides中可用的报表不同的报表，则可以将这些报表添加到映射控制台。 要自定义映射控制台，您需要创建一个AEM客户端库\（或ClientLib\），该库将包含用于执行所需功能的代码。

>[!NOTE]
>
> 不建议直接修改页面组件，因为新版本的产品将覆盖此设置。

AEM Guides提供了用于自定义映射控制台的`apps.fmdita.dashboard-extn`类别。 每当加载映射控制台时，都会执行并加载在`apps.fmdita.dashboard-extn`类别下创建的功能。

>[!NOTE]
>
> 有关创建AEM客户端库的更多信息，请参阅[使用客户端库](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/full-stack/clientlibs.html?lang=zh-Hans)。

## 在输出生成期间处理图像演绎版 {#id177BF0G0VY4}

AEM提供了一组默认的工作流和媒体句柄来处理资源。 在AEM中，有预定义的工作流用于处理最常见的MIME类型的资源。 通常，AEM会为您上传的每个图像以二进制格式创建相同的多个演绎版。 这些演绎版可以具有不同的尺寸、不同的分辨率、添加的水印或某些其他改变的特征。 有关AEM如何处理资源的更多信息，请参阅AEM文档中的[使用媒体处理程序和工作流处理Assets](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/asset-microservices-overview.html?lang=zh-Hans)。

AEM Guides允许您配置在为文档生成输出时使用的图像演绎版。 例如，您可以从默认图像演绎版中选择或创建图像演绎版，然后使用相同的图像演绎版发布文档。 用于发布文档的图像演绎版映射存储在`/libs/fmdita/config/ **renditionmap.xml**`文件中。 `renditionmap.xml`文件的片段如下所示：

>[!NOTE]
>
> 建议您在`renditionmap.xml`文件夹为所有自定义项创建`apps`文件的副本。

```XML
<renditionmap>
   <mapelement>
      <mimetype>image/png</mimetype>
      <rendition output="AEMSITE">cq5dam.web.1280.1280.jpeg</rendition>
      <rendition output="PDF">original</rendition>
      <rendition output="HTML5">cq5dam.web.1280.1280.jpeg</rendition>
      <rendition output="EPUB">cq5dam.web.1280.1280.jpeg</rendition>
      <rendition output="CUSTOM">cq5dam.web.1280.1280.jpeg</rendition>
   </mapelement>
...
</renditionmap>
```

`mimetype`元素指定文件格式的MIME类型。 `rendition output`元素指定输出格式的类型和应用于发布指定输出的格式副本\（例如，`cq5dam.web.1280.1280.jpeg`\）的名称。 您可以指定用于所有受支持的输出格式(AEMSITE、PDF、HTML5、EPUB和CUSTOM)的图像演绎版。

如果指定的呈现版本不存在，则AEM Guides发布过程将首先查找给定图像的Web呈现版本。 如果找不到Web演绎版，则使用图像的原始演绎版。

>[!NOTE]
>
> 这些图像演绎版仅控制输出生成。 当您打开文档进行预览或审阅时，会使用图像的Web演绎版。

## 为输出历史记录配置自动清除时段 {#id19AAI070V8Q}

生成输出时，将创建输出以及输出日志。 对于大型DITA映射，这些日志可能会占用存储库中的大量空间。 默认情况下，日志存储在存储库中的以下位置：

`/var/dxml/metadata/outputHistory`

在一段时间内，所有日志文件的集合大小可能会达到GB。 AEM Guides允许您配置一个时间段，以将这些日志文件保留在存储库中。 在指定的时间段后，日志以及输出生成历史记录将从存储库中删除。

>[!NOTE]
>
> 输出生成历史记录是输出选项卡中生成的输出列表中的日志条目。

配置历史记录清除功能会影响存储库中所有DITA映射的输出生成。 在DITA映射的输出选项卡中，在指定的天数之后以及在设置中指定的时间清除历史记录。

>[!NOTE]
>
> 删除日志文件和输出生成历史记录不会对生成的输出产生任何影响。

使用[配置覆盖](download-install-additional-config-override.md#)中提供的说明创建配置文件。 在配置文件中，提供以下\(property\)详细信息以设置清除输出历史记录和日志的日期和时间：

| PID | 属性键 | 属性值 |
|---|------------|--------------|
| `com.adobe.fmdita.config.ConfigManager\|output.history.purgeperiod` | 指定清除输出历史记录以及输出日志的天数。 如果要禁用此功能，则将此属性设置为0。每天在指定的时间，对此属性中指定的天数之前生成的输出执行清除过程。 | **默认值**： 5 |
| `output.history.purgetime` | 指定清除流程的启动时间。 | **默认值**： 0:00 \（或12:00午夜\） |

## 更改最近生成的输出列表限制 {#id1679JH0H0O2}

您可以更改DITA映射的输出选项卡中显示的已生成输出的最大数量。

使用[配置覆盖](download-install-additional-config-override.md#)中提供的说明创建配置文件。 在配置文件中，提供以下\（属性\）详细信息以更改要在列表中显示的输出数量：

| PID | 属性键 | 属性值 |
|---|------------|--------------|
| `com.adobe.fmdita.config.ConfigManager` | `output.historylimit` | 整数值。<br> **默认值**： 25 |

>[!TIP]
>
> 有关使用输出历史记录的最佳实践，请参阅最佳实践指南中的&#x200B;*输出历史记录*&#x200B;部分。

