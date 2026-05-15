---
title: 简介
description: AEM Guides API参考指南简介
exl-id: d8ee9cf7-1d67-4b4a-aa80-64e893a99463
feature: API Introduction
role: Developer
level: Experienced
TQID: https://experienceleague.adobe.com/dNO8nZusaPCor506Q-2drrcJGf68mx-Hxo4uaT-cDtM
product_v2:
  - id: fae5e35a-80c9-4b94-9352-1a060a6aab1d
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: a01bfd36-4ab8-4bf8-9dc0-5b45b890552e
  - id: a3bd6397-2eb2-4908-a61c-226e26855dca
  - id: c6d09140-3c91-45d3-b7ed-b681af752f43
  - id: cb8c6a2a-3c38-4e40-867c-756f8c36bb0e
subfeature_v2:
  - id: b1ef4d86-3917-4b76-a0bc-4a4771f9b3b0
  - id: f3645292-50bd-4f4a-ac6a-29dcecdf8abe
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 8ed5c9cb07c56b84b36ef56a55af8738989a6d3f
workflow-type: tm+mt
source-wordcount: 656
ht-degree: 0%

---

# 简介 {#id1761C0007W7}

Adobe Experience Manager Guides \（以后称为&#x200B;*AEM Guides*\）是一种端到端的企业解决方案，它使Adobe Experience Manager \(AEM\)能够具有用于基于DITA的内容创建和交付的组件内容管理解决方案\(CCMS\)功能。 客户可以使用AEM Guides API以编程方式访问AEM Guides工作流，以将其与其他企业应用程序集成。 Adobe合作伙伴还可以使用这些API来增强AEM Guides的价值主张，方法是扩展其功能或将其与其他应用程序或服务集成。

## AEM GUIDES API

AEM Guides API有两种格式：

- [基于Java的API](#java-based-apis)
- [基于REST的API](#rest-based-apis)

这些API向应用程序开发人员公开AEM Guides的关键功能。 使用这些函数，开发人员可以创建自己的插件来扩展现成的工作流。 这些API可用于管理DITA内容的输出、使用DITA映射、将条件属性添加到文件夹级别配置文件以及将HTML和Words文档转换为DITA格式。


### 基于Java的API

您可以使用Experience Manager Guides中提供的基于Java的API来创建自定义插件和扩展现成工作流。

**从Maven中央存储库为AEM Guides as a Cloud Service配置SDK**

>[!INFO]
>
>查看[![javadoc](./images/javadoc-cs-icon.svg)](https://javadoc.io/doc/com.adobe.aem/aem-dox-sdk-api/latest/index.html)，了解有关使用适用于Experience Manager Guides as a Cloud Service的基于Java的API的最新和详细文档。

要在项目中从Maven存储库配置和使用服务API JAR，请将API SDK作为项目依赖项添加到项目的`pom.xml`文件中，如下所示。

```XML
<dependency>
<groupId>com.adobe.aem</groupId>
<artifactId>aem-dox-sdk-api</artifactId>
<version>${RELEASE}</version>
</dependency>
```

>[!NOTE]
>
> 确保使用与服务器上安装的AEM Guides包相同版本的API JAR。

**配置并使用Maven中央存储库中的API JAR（内部部署）**

>[!INFO]
>
>有关使用基于Java的API进行Experience Manager Guides本地设置的最新和详细文档，请查看[![javadoc](https://javadoc.io/badge2/com.adobe.aem/aem-guides-sdk-api/javadoc.svg)](https://javadoc.io/doc/com.adobe.aem/aem-guides-sdk-api/latest/index.html)。

要为内部部署配置和使用服务API JAR，请将服务API JAR作为项目依赖项添加到项目的`pom.xml`文件中，如下所示：

```XML
<dependency>
<groupId>com.adobe.aem</groupId>
<artifactId>aem-guides-sdk-api</artifactId>
<version>${RELEASE}</version>
</dependency>
```

>[!NOTE]
>
> 确保使用与服务器上安装的AEM Guides包相同版本的API JAR。


**配置并使用AEM Guides公共Maven存储库中的API JAR（内部部署）**

>[!NOTE]
>
> 在5.3.0版本的Experience Manager Guides之后，将弃用公共AEM Guides Maven存储库。 之后，API JAR将仅在Maven中央存储库中可用。

执行以下步骤以使用公共Maven存储库中的服务API JAR：

1. 在`pom.xml`或`settings.xml`文件中配置AEM Guides公共Maven存储库，如下所示：

   ```XML
   <repository>
       <id>fmdita-public</id>
       <name>fmdita-public</name>
       <url>https://repo.aem-guides.com/repository/fmdita-public</url>
    </repository>
   ```

1. 设置存储库后，将服务API JAR作为项目依赖项添加到项目的`pom.xml`文件中。

   ```XML
   <dependency>
       <groupId>com.adobe.fmdita</groupId>
       <artifactId>api</artifactId>
       <version>${RELEASE}</version>
   </dependency>
   ```

   >[!NOTE]
   >
   > 使用与您在服务器上安装的AEM Guides包相同版本的API JAR。

一旦在项目的`pom.xml`文件中将服务API JAR添加为项目依赖项，您便可以在项目中生成和使用AEM Guides Java API。


### 基于REST的API

Experience Manager Guides提供了一组全面的基于REST的API，允许开发人员通过HTTP访问核心功能并与之交互。

这些API非常适合：

- 将Experience Manager Guides与其他企业系统集成
- 自动化发布和审核工作流
- 构建自定义应用程序和扩展

有关API使用情况、参数和示例请求的详细信息，请在Experience Manager Guides文档的&#x200B;**API引用**&#x200B;部分中查看相关主题。

## 其他资源

以下是AEM Guides其他有用资源的列表，这些资源位于[学习与支持](https://helpx.adobe.com/support/xml-documentation-for-experience-manager.html)页面上：

- 用户指南
- 安装和配置指南
- 快速入门指南
- [帮助存档页面](https://helpx.adobe.com/xml-documentation-for-experience-manager/archive.html) \（访问旧版文档\）
