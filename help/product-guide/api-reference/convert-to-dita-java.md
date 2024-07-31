---
title: 用于转化工作流的基于Java的API
description: 了解用于转化工作流的基于Java的API
exl-id: 807d9ffa-23e3-476c-992d-c1f495233892
feature: Java-Based API Conversion Workflow
role: Developer
level: Experienced
source-git-commit: 83966cc9187b13dd3b5956821e0aa038b41db28e
workflow-type: tm+mt
source-wordcount: '259'
ht-degree: 5%

---

# 用于转化工作流的基于Java的API {#id175UB30E05Z}

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
抛出`RepositoryException`。

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
抛出`RepositoryException`。
