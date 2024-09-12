---
title: 使用工具配置数据源连接器
description: 了解如何使用工具配置数据源连接器。
exl-id: 2a0ac0a0-b2a9-453e-851b-fb04c8903526
feature: Web Editor Configuration
role: Admin
level: Experienced
source-git-commit: 1eb4fcb33d6f905df3f543232e7040d1da42560b
workflow-type: tm+mt
source-wordcount: '539'
ht-degree: 0%

---

# 从用户界面配置数据源连接器

Experience Manager Guides附带了&#x200B;**数据源**&#x200B;工具，可帮助您为数据源配置现成的连接器。 您可以为JIRA、SQL(MySQL、PostgreSQL、Microsoft SQL Server、SQLite、MariaDB、H2DB)、AdobeCommerce和Elasticsearch数据库设置连接器。

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
   >* 将鼠标悬停在 <img src="./assets/info-details.svg" alt= "信息图标" width="25">在字段附近查看有关它的更多详细信息。
   > * 带*的字段为必填字段。 例如，您可以为Elasticsearch连接器输入以下详细信息。

   * **名称**：输入数据源的名称。
   * 身份验证类型：从下拉列表中选择身份验证类型。 例如，基本的用户名 — 密码身份验证
   * **用户名**：输入您的用户名。
   * **密码**：输入您的用户名和密码。
   * **URL**：添加API URL。

1. 选择&#x200B;**测试连接**。 只有在添加所需的详细信息后，才能查看已启用的&#x200B;**测试连接**&#x200B;按钮。 如果连接详细信息正确，请查看成功消息。 否则，您可能会看到一条错误消息。



1. 选择顶部的&#x200B;**保存**&#x200B;以保存连接器。     查看在您填写所有详细信息后启用的&#x200B;**保存**&#x200B;按钮，并且连接成功。


   如果连接器保存成功，则可以在页面上查看连接的数据源。

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


配置数据源后，连接器将列在Web编辑器的&#x200B;**数据源面板**&#x200B;下。 然后，您可以连接到数据源并将内容片段插入到您的主题中。 有关更多详细信息，请查看[使用数据源中的数据](../user-guide/web-editor-content-snippet.md)。

>[!NOTE]
>
>您还可以创建自定义连接器并将它们用于不同的数据源。 了解如何[配置自定义连接器](../knowledge-base/kb-articles/data-source/conf-custom-data-source-connector.md)。