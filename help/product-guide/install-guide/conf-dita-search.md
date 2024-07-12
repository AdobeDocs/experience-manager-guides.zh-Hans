---
title: 配置AEM Assets UI搜索
description: 了解如何配置AEM Assets UI搜索
exl-id: b920ba7f-e8fc-4af6-aa8a-b8516b1cffc0
feature: Search Configuration
role: Admin
level: Experienced
source-git-commit: 0513ecac38840a4cc649758bd1180edff1f8aed1
workflow-type: tm+mt
source-wordcount: '1695'
ht-degree: 1%

---

# 配置AEM Assets UI搜索 {#id192SC800MY4}

默认情况下，AEM不识别DITA内容，因此，它不提供任何机制来搜索其存储库中的DITA内容。 AEM Guides允许您在AEM存储库中添加DITA内容搜索功能。

默认情况下，AEM不识别DITA内容，因此，它不提供任何机制来搜索其存储库中的DITA内容。 此外，OOTB不具备根据内容的UUID搜索内容的功能。 AEM Guides允许您在AEM存储库中添加DITA内容搜索和基于UUID的搜索功能。

配置DITA内容搜索涉及以下任务：

1. [在Assets UI中添加DITA元素搜索组件](#id192SF0F50HS)
1. [在Assets UI中添加基于UUID的搜索组件](#id2034F04K05Z)
1. [向用户提供权限](#id192SF0G0RUI)
1. [在搜索中添加自定义元素或属性](#id192SF0G10YK)
1. [从现有内容提取元数据](#id192SF0GA0HT)

除了添加搜索功能外，您还可以配置不应包含在搜索中的文件夹。 有关详细信息，请参阅[从搜索结果中排除临时文件](#id197AHI0035Z)。

## 在Assets UI中添加DITA元素搜索组件 {#id192SF0F50HS}

执行以下操作以在AEM Assets UI中添加DITA内容搜索组件：

1. 以管理员身份登录Adobe Experience Manager。

1. 单击顶部的&#x200B;**Adobe Experience Manager**&#x200B;链接，然后选择&#x200B;**工具**。

1. 从工具列表中选择&#x200B;**常规**，然后单击&#x200B;**搜索Forms**&#x200B;拼贴。

1. 在&#x200B;**搜索Forms**&#x200B;列表中，选择&#x200B;**Assets管理员搜索边栏**。

1. 单击&#x200B;**编辑**。
1. 在&#x200B;**选择谓词**&#x200B;选项卡中，滚动到列表的末尾。

1. 将&#x200B;**DITA元素谓词**&#x200B;拖放到搜索表单中的所需位置。

   ![](assets/drag-search-predicate.png){width="650" align="left"}

1. 单击&#x200B;**完成**&#x200B;以保存更改。

   当您访问Assets UI中的过滤器选项时，您将获得DITA元素搜索过滤选项。

   ![](assets/search-filter-asset-console.png){width="350" align="left"}


## 在Assets UI中添加基于UUID的搜索组件 {#id2034F04K05Z}

执行以下操作可在AEM Assets UI中添加基于UUID的搜索组件：

1. 以管理员身份登录Adobe Experience Manager。

1. 单击顶部的&#x200B;**Adobe Experience Manager**&#x200B;链接，然后选择&#x200B;**工具**。

1. 从工具列表中选择&#x200B;**常规**，然后单击&#x200B;**搜索Forms**&#x200B;拼贴。

1. 在&#x200B;**搜索Forms**&#x200B;列表中，选择&#x200B;**Assets管理员搜索边栏**。

1. 单击&#x200B;**编辑**。
1. 在&#x200B;**选择谓词**&#x200B;选项卡中，选择&#x200B;**属性谓词**，并将其拖放到搜索表单中的所需位置。

1. 在&#x200B;**设置**&#x200B;选项卡中，为新添加的&#x200B;**属性谓词**&#x200B;组件提供以下详细信息：

   - **字段标签**： UUID
   - **属性名称**： jcr：content/fmUuid
1. 单击&#x200B;**完成**&#x200B;以保存更改。

   当您访问Assets UI中的过滤器选项时，您将获得基于UIS的搜索过滤选项。


## 向用户提供权限 {#id192SF0G0RUI}

作者和发布者需要获得明确权限，才能从Assets UI访问搜索功能。 如果不授予这些权限，则您的用户将无法根据其元素/属性值或UUID搜索DITA内容。

执行以下步骤以提供对DITA搜索功能的访问：

1. 访问用户和群组权限页面。 访问页面的默认URL为：

   `http://<server name>:<port>/useradmin.html`

1. 搜索要向其授予访问权限的用户组或个人用户。 例如，要授予作者组中所有用户的访问权限，请在&#x200B;**筛选查询**&#x200B;字段中输入作者，然后按&#x200B;**Enter**。

   ![](assets/authors-group-permission.png){width="350" align="left"}

1. 选择&#x200B;**作者**&#x200B;组。

1. 在右窗格中，选择&#x200B;**权限**&#x200B;选项卡。

1. 导航到以下文件夹位置：

   /conf/global/settings/dam/search

1. 授予对搜索文件夹的&#x200B;**读取**&#x200B;权限。

   ![](assets/read-permission-authors.png){width="650" align="left"}

1. 单击&#x200B;**保存**。


选定的用户或用户组现在可以访问Assets UI中的搜索DITA内容功能。

## 在搜索中添加自定义元素或属性 {#id192SF0G10YK}

要使DITA搜索正常工作，需要对DITA内容进行一些预处理。 此预处理步骤从单个DITA映射和主题中提取选择性内容，以便可以编制索引以加快搜索。 在内部，此过程称为&#x200B;*序列化*。 DITA文件的序列化在内容上传期间发生，也可以按需执行。 它使用配置文件来确定每个DITA文件中应索引多少内容。 序列化文件的默认位置为：

/libs/fmdita/config/serializationconfig.xml

默认搜索配置允许您搜索DITA `prolog`元素中的所有元素和属性。 如果要基于其他元素或属性进行搜索，则需要配置搜索序列化文件。

>[!NOTE]
>
> 如果要使用`prolog`元素中的默认搜索配置，则可以跳过此过程。

此文件包含两个主要部分 — 属性集和规则集。 下面给出了规则集部分的代码片段：

```XML
<ruleset filetypes="xml dita"><!-- Element rules --><rule xpath="//[contains(@class, 'topic/topic')]/[contains(@class, 'topic/prolog')]//*[not(*)]" text="yes" attributeset="all-attrs" /><!-- Attribute rules --><rule xpath="//[contains(@class, 'topic/topic')]/[contains(@class, 'topic/prolog')]///@[local-name() != 'class']" /></ruleset>
```

在规则集部分，您可以指定：

- 用于提取元素的规则

- 用于提取属性的规则


规则包含以下内容：

xpath
：   这是从DITA文件中检索元素或属性的XPath查询。 元素规则的默认配置将检索所有`prolog`元素。 而且，属性规则的默认配置将检索`prolog`元素的所有属性。 您可以指定XPath查询来序列化要搜索的元素或属性。

XPath查询包含文档类型的类名。 `topic/topic`类用于主题类型DITA文档。 如果要为其他DITA文档创建规则，则必须使用以下类名：

| 文档类型 | 类名称 |
|-------------|----------|
| 主题 |  — 主题/主题 |
| 任务 |  — 主题/主题任务/任务 |
| 概念 |  — 主题/主题概念/概念 |
| 引用 |  — 主题/主题引用/引用 |
| 地图 |  — 地图/地图 |

文本
：   如果要搜索指定元素中的文本，请指定yes值。 如果指定no作为值，则只序列化元素中的属性。 需要在“属性集”部分指定您要搜索的属性。

属性集
：   指定要与此规则关联的属性集的ID。 全属性值是一个特殊的大小写，表示此规则的所有属性都必须序列化。

属性集包含要在DITA内容中搜索的属性列表。 属性集包含以下内容：

id
：   属性集的唯一标识符。 此ID在规则集的属性集参数中指定。

属性
：   要搜索的属性列表。 对于每个属性，您需要在`attribute`元素中创建单个条目。

执行以下步骤以在搜索序列化文件中添加自定义DITA元素或属性：

1. 登录AEM并打开CRXDE Lite模式。

1. 导航到位于以下位置的序列化配置文件：

   /libs/fmdita/config/serializationconfig.xml

1. 在`apps`节点内创建`config`文件夹的覆盖节点。

1. 导航到`apps`节点中可用的配置文件：

   `/apps/fmdita/config/serializationconfig.xml`

1. 添加所需的元素或属性规则集。

1. 保存文件。

1. 打开Adobe Experience Manager Web控制台配置页面。 用于访问配置页面的默认URL为：

   http://&lt;服务器名称\>：&lt;端口\>/system/console/configMgr

1. 搜索并单击&#x200B;*com.adobe.fmdita.config.ConfigManager*&#x200B;包。

1. 单击&#x200B;**保存**。


存储并激活新的序列化信息以进行搜索。 但是，必须从现有DITA内容中提取元数据才能用于搜索。

## 从现有内容提取元数据 {#id192SF0GA0HT}

在默认搜索序列化文件中做出任何更改后，必须在&#x200B;*com.adobe.fmdita.config.ConfigManager*&#x200B;包中启用“DITA元数据提取”选项，然后运行工作流以提取元数据。 这将从现有DITA文件中提取所需的元数据，然后可使用该元数据进行搜索。

如果您在更新序列化文件后创建新文件或编辑任何文件，则会自动从此类文件中提取元数据。 只有AEM资料档案库中已存在的文件才需要提取元数据的过程。

从现有DITA文件提取元数据涉及两个任务：

1. 在configMgr中启用元数据提取选项
1. 运行元数据提取工作流

执行以下步骤以在configMgr中启用元数据提取选项：

1. 打开Adobe Experience Manager Web控制台配置页面。 用于访问配置页面的默认URL为：

   http://&lt;服务器名称\>：&lt;端口\>/system/console/configMgr

1. 搜索并单击&#x200B;*com.adobe.fmdita.config.ConfigManager*&#x200B;包。

1. 选择&#x200B;**启用DITA元数据提取**&#x200B;选项。

1. 单击&#x200B;**保存**。


执行以下步骤以运行元数据提取工作流：

1. 以管理员身份登录Adobe Experience Manager。

1. 单击顶部的&#x200B;**Adobe Experience Manager**&#x200B;链接，然后选择&#x200B;**工具**。

1. 从工具列表中选择&#x200B;**Guides**，然后单击&#x200B;**DITA元数据提取**&#x200B;磁贴。

1. 如果要从单个文件及其依赖项中提取元数据，请单击&#x200B;**选择文件**&#x200B;链接并浏览文件。

1. 如果要从文件夹中的多个文件中提取元数据，请单击&#x200B;**选择文件夹\(s\)**&#x200B;链接，浏览并选择所需的文件夹。 单击&#x200B;**添加**&#x200B;按钮将该文件夹添加到序列化任务列表。

   >[!NOTE]
   >
   > 您可以选择多个文件夹并将其添加到序列化任务。

1. 单击&#x200B;**开始**。

1. 在“确认元数据提取”对话框中，单击&#x200B;**确定**。


## 从搜索结果中排除临时文件 {#id197AHI0035Z}

默认情况下，将对整个AEM存储库执行搜索。 可能有一些位置您希望从搜索中排除。 例如，在启动内容翻译工作流时，未批准的文件将保留在临时文件夹位置。 执行搜索时，搜索结果中还会返回来自此临时位置的文件。

要阻止AEM Guides搜索临时翻译文件夹位置，您需要在排除列表中添加临时文件夹位置。

执行以下步骤以从搜索中排除临时翻译文件夹：

>[!NOTE]
>
> 您可以使用此过程将任何其他文件夹位置添加到排除列表中。

1. 登录AEM并打开CRXDE Lite模式。

1. 导航到位于以下位置的damAssetLucene节点：

   /oak:index/damAssetLucene

1. 在damAssetLucene节点中添加以下属性：

   | 属性名称 | 类型 | 价值 |
   |-------------|----|-----|
   | excludedPaths | String\[\] | 将以下值添加到此属性： <br>/content/dam/projects/translation\_output |

1. 导航到位于以下位置的lucene节点：

   /oak：index/lucene

1. 在lucene节点中添加以下属性：

   | 属性名称 | 类型 | 价值 |
   |-------------|----|-----|
   | excludedPaths | String\[\] | 将以下值添加到此属性： <br><ul><li>/var/dxml</li><li>/content/dam/projects/translation\_output</li></ul> |
