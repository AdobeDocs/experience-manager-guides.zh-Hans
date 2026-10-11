---
title: 用于转化工作流的基于Java的API
description: 了解用于转化工作流的基于Java的API
exl-id: 807d9ffa-23e3-476c-992d-c1f495233892
feature: Java-Based API Conversion Workflow
role: Developer
level: Experienced
TQID: 'https://experienceleague.adobe.com/gAntb7T-OGlwRNInxAsV8orxL3H9qL19Dsjwf5FZ14I'
product_v2:
  - id: fae5e35a-80c9-4b94-9352-1a060a6aab1d
    internal-label: Experience Manager Guides
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
feature_v2:
  - id: a01bfd36-4ab8-4bf8-9dc0-5b45b890552e
    internal-label: APIs
  - id: c6d09140-3c91-45d3-b7ed-b681af752f43
    internal-label: APIs
subfeature_v2:
  - id: c2674c69-1bed-41fa-ba40-ab1a5382af59
    internal-label: Java Based API Conversion Workflow
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 81a0e7f0736ba4970673dd87a888a4c60d3c1b4e
workflow-type: tm+mt
source-wordcount: '326'
ht-degree: 3%
---
# 用于转化工作流的基于Java的API {#id175UB30E05Z}

>[!NOTE]
>
> 您可以使用Experience Manager Guides中提供的基于Java的API来创建自定义插件和扩展现成工作流。 本文将于2024年11月存档。
> 有关使用基于Java的API的最新和详细文档，请查看[![javadoc](https://javadoc.io/badge2/com.adobe.aem/aem-guides-sdk-api/javadoc.svg)](https://javadoc.io/doc/com.adobe.aem/aem-guides-sdk-api)。




以下基于Java的API允许您将HTML和Word文档转换为DITA格式。 这些API以捆绑包形式提供。 您必须在代码中包含此捆绑包才能使用这些API。

**包详细信息**：

- 组ID： **com.adobe.fmdita**

- 项目ID： **api**

- 版本： **3.2**

- 包： **com.adobe.fmdita.api.conversion**

- 类详细信息：

  ```JAVA
  public class ConversionUtils extends Object
  ```

  **ConversionUtils**&#x200B;类包含将HTML和Word文档转换为DITA格式的方法。


## 转换HTML文档

`convertHtmlToDita`方法将HTML文档转换为DITA格式。

**语法**：

```JAVA
public static void convertHtmlToDita(Session session, 
                  String inputFile, 
                  String destPath, 
                  boolean createRev) 
                  throws RepositoryException, WorkflowException
```

**参数**：

| 名称 | 类型 | 描述 |
|----|----|-----------|
| `session` | javax.jcr.Session | 有效的JCR会话。 |
| `inputFile` | 字符串 | AEM存储库中源HTML文件的绝对路径。 |
| `destPath` | 字符串 | 将保存转换的DITA文件的目标位置的绝对路径。 |
| `createRev` | 布尔值 | 指定是否在指定的目标创建了\(`true`\)文件修订版\(`false`\)。 仅当目标位置包含转换文件的现有版本时，才考虑使用此选项。 |

**异常**：
引发`RepositoryException`。

## 转换Word文档

``convertWordToDita``方法将Word文档转换为DITA格式。

**语法**：

```JAVA
public static void convertWordToDita(Session session, 
                  String inputFile,
                  String destPath, 
                  String style2tagMap, 
                  boolean createRev) 
                  throws RepositoryException, WorkflowException
```

**参数**：

| 名称 | 类型 | 描述 |
|----|----|-----------|
| `session` | javax.jcr.Session | 有效的JCR会话。 |
| `inputFile` | 字符串 | AEM存储库中源Word文件的绝对路径。 |
| `destPath` | 字符串 | 将保存转换的DITA文件的目标位置的绝对路径。 |
| `style2tagMap` | 字符串 | 用于转换的样式映射文件的绝对路径。 |
| `createRev` | 布尔值 | 指定是否在指定的目标创建了\(`true`\)文件修订版\(`false`\)。 仅当目标位置包含转换文件的现有版本时，才考虑使用此选项。 |

**异常**：
引发`RepositoryException`。
