---
title: 使用工具配置数据源连接器
description: 了解如何使用工具配置数据源连接器。
exl-id: d7cd412b-89ea-43a5-97b3-09944863bbee
feature: Web Editor Configuration
role: Admin
level: Experienced
source-git-commit: 6e23f52fc9124d0f07f8108da1b5fe574f553469
workflow-type: tm+mt
source-wordcount: '883'
ht-degree: 0%

---

# 从用户界面配置数据源连接器

Experience Manager Guides附带了&#x200B;**数据源**&#x200B;工具，可帮助您为数据源配置现成的连接器。 您可以设置JIRA、SQL(MySQL、PostgreSQL、Microsoft SQL Server、SQLite、MariaDB、H2DB)、AdobeCommerce、Elasticsearch和通用REST客户端连接器。


除了这些现成的连接器外，Experience Manager Guides还为Salsify、Akeneo和Microsoft Azure DevOps Boards (ADO)数据源提供连接器。 您可以从[Maven中央存储库](https://central.sonatype.com/search?q=com.adobe.aem.addon.guides)下载并安装这些开源连接器。 然后，用户可以配置这些连接器。
了解如何[安装开源连接器](#install-open-source-connector)。



您还可以使用文件连接器连接到JSON数据文件。 从您的计算机中上传JSON文件或从Adobe Experience Manager资源中浏览该文件。 然后，使用生成器创建内容片段或主题。

要配置连接器，请执行以下步骤：

1. 选择顶部的&#x200B;**Adobe Experience Manager**&#x200B;链接，然后选择“工具”。
1. 从工具列表中选择&#x200B;**指南**。
1. 选择&#x200B;**数据源**&#x200B;磁贴。 显示&#x200B;**数据源**&#x200B;页。 您可以查看连接的数据源。

   您可以在&#x200B;**列表视图**&#x200B;或&#x200B;**平铺视图**&#x200B;之间切换，以列表或平铺方式查看各种连接的数据源。

   <img src="./assets/data-sources-create-window.png" alt= "数据源页面上列出的数据源" width="800">

   *查看或创建数据源连接器。*

1. 单击&#x200B;**创建**。
1. 选择要为其创建连接器的数据库。 例如，Elasticsearch连接器。

   >[!NOTE]
   >
   >列出所有可用的现成数据库。

1. 单击&#x200B;**下一步**。
1. 根据数据库输入配置和连接详细信息。

   >[!TIP]
   >
   >* 将鼠标悬停在 <img src="./assets/info-details.svg" alt= "信息图标" width="25">在字段附近查看有关它的更多详细信息。
   >* 带*的字段为必填字段。 例如，您可以为Elasticsearch连接器输入以下详细信息。

   * **名称**：输入数据源的名称。
   * **身份验证类型**：从下拉列表中选择身份验证类型。 例如，基本的用户名 — 密码身份验证
   * **用户名**：输入您的用户名。
   * **密码**：输入您的用户名和密码。
   * **URL**：添加API URL。


1. 选择&#x200B;**Exclude factory templates**&#x200B;选项可排除工厂模板不用于生成主题和代码片段。 它们不会显示在&#x200B;**添加内容片段生成器**&#x200B;或&#x200B;**添加主题生成器**&#x200B;对话框的&#x200B;**数据映射模板**&#x200B;下拉列表下。
1. 选择&#x200B;**测试连接**。 只有在添加所需的详细信息后，才能查看已启用的&#x200B;**测试连接**&#x200B;按钮。 如果连接详细信息正确，请查看成功消息。 否则，您可能会看到一条错误消息。
1. 选择顶部的&#x200B;**保存**&#x200B;以保存连接器。     查看在您填写所有详细信息后启用的&#x200B;**保存**&#x200B;按钮，并且连接成功。


   如果连接器保存成功，则可以在页面上查看连接的数据源。

**连接到多个资源**

您可以根据某些Connectors的不同URL添加或使用多个资源，这些连接器包括Generic REST Client、Salsify、Akeneo和Microsoft Azure DevOps Boards (ADO)。 然后，与他们联系，使用生成器创建内容片段或主题。

执行以下步骤可创建资源：

1. 在![URL资源部分](assets/Add_icon.svg)中选择&#x200B;**添加图标**&#x200B;为每个URL添加资源。
1. 在&#x200B;**添加资源**&#x200B;对话框中配置所有详细信息。
1. 单击&#x200B;**添加**。
1. 您可以编辑![编辑图标](assets/edit_pencil_icon.svg)或从URL资源列表中删除![删除](assets/Delete_icon.svg)该资源。
1. 您还可以使用可用于数据源(如Salsify、Akeneo和Microsoft ADO)的默认资源。 将您不想为数据源配置的资源的选项切换为OFF。

这有助于从单个内容片段或主题中特定数据源的任何资源快速获取数据。



## 安装开源连接器{#install-open-source-connector}

要将[Maven中央存储库](https://central.sonatype.com/search?q=com.adobe.aem.addon.guides)上存在的依赖项发布到云服务，您需要包含并嵌入开源连接器的依赖项。

1. 在Cloud Manager Git项目代码的`all/pom.xml`中添加依赖项。 例如，您可以为Microsoft Azure DevOps Boards数据源连接器添加以下依赖项。


   ```
   <dependency>
       <groupId>com.adobe.aem.addon.guides</groupId>
       <artifactId>konnect-azure-devops</artifactId>
       <version>1.0.0</version>
       <type>jar</type>
   </dependency> 
   ```

1. 嵌入添加的依赖项。

   ```
   <embedded>
       <groupId>com.adobe.aem.addon.guides</groupId>
       <artifactId>konnect-azure-devops</artifactId>
       <type>jar</type>
       <target>/apps/aemdoxonaemcsstageprogram-vendor-packages/content/install</target>
   </embedded> 
   ```

1. 运行管道以应用云服务中的更改。
连接器安装在您的环境中。


## 可用于连接器的功能

* 在&#x200B;**列表视图**&#x200B;或&#x200B;**平铺视图**&#x200B;之间切换，以列表或平铺方式查看各种连接的数据源。
* 选中单个连接器的复选框。 单击&#x200B;**全选**&#x200B;以选择所有连接器。 选择所有连接器后，您可以单击&#x200B;**取消全选**。

<img src="./assets/data-sources-features.png" alt= "数据源页面上的数据源功能" width="800">

*编辑、重新连接、复制或删除数据源连接器。*

您可以对&#x200B;**数据源**&#x200B;页面上的连接器使用以下功能：

* **编辑**：编辑所选连接器的配置详细信息。

* **重新连接**：重新连接到断开连接的连接器。

* **重复**：使用当前连接器作为基本连接器创建新的重复连接器。 缺省情况下，会创建带有后缀（如connectorname_1）的重复连接器。 例如，sample-elastic-search_1。
如果存在同名的连接器，则会查看错误。

* **删除**：删除所选的连接器。


配置数据源后，连接器将列在Web编辑器的&#x200B;**数据源面板**&#x200B;下。 然后，您可以连接到数据源并将内容片段插入到您的主题中。 有关详细信息，请查看[插入数据源中的内容片段](../user-guide/web-editor-content-snippet.md)。
