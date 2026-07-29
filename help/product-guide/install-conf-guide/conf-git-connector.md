---
title: 在AEM Guides中配置Git连接器
description: 了解如何在Experience Manager Guides中配置Git。
feature: Web Editor Configuration
role: Admin
level: Experienced
source-git-commit: eb30be6342a50ba52e8afd8b4a31148b3ad9c340
workflow-type: tm+mt
source-wordcount: '551'
ht-degree: 0%

---

# 从用户界面创建和配置Git连接器

>[!NOTE]
>
> 默认情况下，此功能处于禁用状态。 要启用您的环境，请联系您的客户成功团队。

使用Experience Manager Guides中的“数据源”工具从用户界面创建和配置Git连接器。 成功配置连接器后，您可以使用它将Git存储库中的内容导入Experience Manager Guides。

>[!NOTE]
>
> 在开始之前，请确保将Git连接器部署到您的Cloud Manager项目。 有关详细信息，请查看[将Git连接器添加到您的Cloud Manager项目。](#add-git-connector-to-your-cloud-manager-project)


1. 选择顶部的&#x200B;**Adobe Experience Manager**&#x200B;链接，然后选择&#x200B;**工具**。
1. 从工具列表中选择&#x200B;**指南**。
1. 选择&#x200B;**数据源**&#x200B;磁贴。 显示&#x200B;**数据源**&#x200B;页。
1. 选择&#x200B;**创建**。
1. 从数据源连接器列表中，选择&#x200B;**GitHub**。

   ![](assets/github-connector-tile.png){width="600"}

1. 选择&#x200B;**下一步**。
1. 输入配置和连接详细信息。

   ![](assets/conf-git-connector.png){width="600"}

   >[!TIP]
   >
   >* 将鼠标悬停在 <img src="./assets/info-details.svg" alt= "信息图标" width="25">在字段附近查看有关它的更多详细信息。
   >* 带*的字段为必填字段。 例如，您可以为Elasticsearch连接器输入以下详细信息。

   &#x200B;- **名称**：输入数据源的名称。
   &#x200B;- **Target AEM根路径**：输入从Git导入的内容应存储在AEM存储库中的路径。
   &#x200B;- **文件类型筛选器（包含）**：指定导入期间要包含的文件类型。
   &#x200B;- **排除的路径（正则表达式）**：指定要从导入中排除的路径模式。
   &#x200B;- **身份验证类型**：从下拉列表中选择身份验证类型。 当前，**个人访问令牌(PAT)**&#x200B;是唯一受支持的身份验证方法。 在连接器设置期间输入PAT以验证和访问Git存储库。

     了解如何[生成GitHub个人访问令牌](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens#creating-a-personal-access-token-classic)。

     在GitHub上生成PAT期间选择范围时，请确保启用以下范围：
     &#x200B;- **repo**：选中顶级复选框。 自动选择所有子范围，授予对存储库内容、提交状态和部署的访问权限。
     &#x200B;- **管理员:org**：仅选择&#x200B;**读取:org**。 这是解决组织和团队成员资格问题所必需的。
   * **存储库URL**：输入应从中导入内容的Git存储库URL。
   * **分支**：输入用于内容导入的分支。

1. 测试连接。 只有在输入所需的详细信息后，才会启用&#x200B;**测试连接**&#x200B;按钮。 如果连接详细信息正确，则会显示一条成功消息。 否则，将显示一条错误消息。

   ![](assets/git-connector-test-connection.png){width="600"}

1. 选择顶部的&#x200B;**保存**&#x200B;以保存连接器。

   只有在输入所有必需详细信息并且连接成功后，才会启用“保存”按钮。 如果连接器保存成功，您可以在&#x200B;**数据源**&#x200B;页面上查看配置的Github连接器。

   ![](assets/git-connector-connected.png){width="600"}

## 将Git连接器添加到您的Cloud Manager项目

在可以从&#x200B;**数据源**&#x200B;页面配置Git连接器之前，必须将它作为依赖项嵌入到AEM项目中。 执行以下步骤可添加依赖关系：

1. 在您的AEM项目的`all/pom.xml`中，将Git Connector作为依赖项添加到`<dependencies>`下：

   ```xml
   <dependency>
       <groupId>com.adobe.aem.addon.guides</groupId>
       <artifactId>konnect-github</artifactId>
       <version>1.0.0</version>
   </dependency>
   ```

1. 在同一`pom.xml`中，将依赖关系添加到`filevault-package-maven-plugin`配置的`<embeddeds>`部分：

   ```xml
   <embedded>
       <groupId>com.adobe.aem.addon.guides</groupId>
       <artifactId>konnect-github</artifactId>
       <type>jar</type>
       <target>/apps/YOUR-vendor-packages/content/install</target>
   </embedded>
   ```

   将`YOUR-vendor-packages`替换为您项目的供应商包名称。

1. 提交更改并将其推送到Cloud Manager Git存储库，然后运行管道以部署这些更改。

管道完成后，Git连接器即安装在您的环境中，并可从&#x200B;**数据源**&#x200B;页面进行配置。





