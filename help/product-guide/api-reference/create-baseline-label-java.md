---
title: 用于基线和标签的基于Java的API
description: 了解用于基线和标签的基于Java的API
exl-id: 0e2ba1bb-f5bf-44da-848a-a55385460c83
feature: Java-Based API Baseline
role: Developer
level: Experienced
source-git-commit: 8c80a4da8e61909aab0f2db81ef97149774b36c4
workflow-type: tm+mt
source-wordcount: '931'
ht-degree: 2%

---

# 用于基线和标签的基于Java的API {#id175UB30E05Z}

>[!NOTE]
>
> 您可以使用Experience Manager Guides中提供的基于Java的API来创建自定义插件和扩展现成工作流。 本文将于2024年11月存档。
> 有关使用基于Java的API的最新和详细文档，请查看[![javadoc](https://javadoc.io/badge2/com.adobe.aem/aem-guides-sdk-api/javadoc.svg)](https://javadoc.io/doc/com.adobe.aem/aem-guides-sdk-api)。


以下基于Java的API允许您创建基线并向基线中的文件添加标签。 这些API以捆绑包形式提供。 您必须在代码中包含此捆绑包才能使用这些API。

捆绑包详细信息：

- 组ID： **com.adobe.fmdita**

- 项目ID： **api**

- 版本： **3.5**

- 包： **com.adobe.fmdita.api.baselines**

- 类详细信息：

  ```JAVA
  public class BaselineUtils extends Object
  ```

  **BaselineUtils**&#x200B;类包含用于创建基线以及将标签应用于基线中的文件的方法。


## 创建基线

创建基线方法有两个版本 — 一个用于XML Documentation解决方案版本3.5，另一个用于3.5之前的版本\（包括版本3.4、3.3和3.2\）。 3.5版API允许使用映射文件中的标签、直接引用和间接引用创建基线。

API的另一个版本使用日期和时间创建基线。 保留此API是为了与使用XML Documentation解决方案3.4、3.3或3.2的系统保持向后兼容性。

**语法\（对于版本3.5\）**：

```JAVA
public static String createBaseline(Session session, 
String sourcePath, 
String baselineTitle, 
String label, 
LinkedHashMap directContext, 
LinkedHashMap indirectContext) 
throws GuidesApiException
```

**参数**：

| 名称 | 类型 | 描述 |
|----|----|-----------|
| `session` | javax.jcr.Session | 有效的JCR会话。 用户会话需要同时具有DITA映射的读取和写入权限以及基线中包含的所有引用文件的读取权限。 |
| `sourcePath` | 字符串 | AEM存储库中DITA映射文件的绝对路径。 |
| `baselineTitle` | 字符串 | 基线的唯一标题。 |
| `label` | 字符串 | 选择应用了给定标签的主题的版本。 |
| `directContext` | LinkedHashMap&lt;字符串，对象\> | 对于选择直接引用主题\(content\)的配置，将按照映射中提到的顺序解析版本。 <br>如果在映射的所有键上迭代后未找到版本，则基线创建过程将失败。 <br>如果HashMap为空\（发送空映射，默认映射不为null\），则默认情况下会填充为： <br>`directContext.put("label", label);` <br> `directContext.put("latest", true);` <br>如果您希望基线创建仅选择给定标签的版本，并且如果不存在此类版本，则失败，请放置`label`键和您要创建基线的标签。 |
| `indirectContext` | LinkedHashMap&lt;字符串，对象\> | 对于选择间接引用主题\（引用内容\）的配置，将按照映射中提到的顺序解析版本。 <br>如果在映射的所有键上迭代后未找到版本，则基线创建过程将失败。 <br>如果哈希映射为空\（发送空映射，默认为null映射\），则默认填充为： <br>`indirectContext.put("label", label);` <br>`indirectContext.put "pickAutomatically", null);` <br>如果您希望它成为最新版本而不是自动选取版本，请替换： <br>`indirectContext.put("pickAutomatically", null);` <br> _具有：_ <br>`indirectContext.put("latest", true)` |

**返回**：
基线的名称，即JCR存储库中基线的节点名称。 新创建的基线的标题将显示在DITA映射的“基线”页上，供用户使用。

**异常**：
如果具有相同标题的基线已存在，则抛出``ItemExistExceptiom``。

**语法\（适用于版本3.4、3.3和3.2\）**

```JAVA
public static String createBaseline
(Session session, 
String sourcePath, 
String baselineTitle, 
Date versionDate) throws GuidesApiException
```

**参数**：

| 名称 | 类型 | 描述 |
|----|----|-----------|
| `session` | javax.jcr.Session | 有效的JCR会话。 用户会话需要同时具有DITA映射的读取和写入权限以及基线中包含的所有引用文件的读取权限。 |
| ``sourcePath`` | 字符串 | AEM存储库中DITA映射文件的绝对路径。 |
| `baselineTitle` | 字符串 | 基线的唯一标题。 |
| `versionDate` | 日期 | 基线是使用此日期的主题\（直接从DITA映射中引用）的版本创建的。 以`d-MM-yyyy H:mm`格式指定日期。 |

**返回**：
基线的名称，即JCR存储库中基线的节点名称。 新创建的基线的标题将显示在DITA映射的“基线”页上，供用户使用。

**异常**：
抛出``RepositoryException.``

## 应用标签

``applyLabel``方法将一个或多个标签应用于基线中的文件。

**语法**：

```JAVA
public static void applyLabel(Session session,
                  String sourcePath,
                  String baselineName,
                  String label)
                  throws RepositoryException, WorkflowException, Exception
```

**参数**：

| 名称 | 类型 | 描述 |
|----|----|-----------|
| `session` | javax.jcr.Session | 有效的JCR会话。 |
| `sourcePath` | 字符串 | AEM存储库中DITA映射文件的绝对路径。 |
| ``baselineName`` | 字符串 | 必须应用标签的基线节点的名称。 要获取基线节点的名称，您可以使用[\#id185NFF0085Z](#id185NFF0085Z)方法或在CRXDE中检查DITA映射的基线节点。<br> **注意：**&#x200B;标签应用于从基线中的映射文件直接引用的文件版本。 |
| `label` | 字符串 | 应用于基线中文件的标签。 确保标签中不包含下列字符： &amp;amp；sol； &amp;amp；逗号； &amp;amp；冒号； &amp;amp；逗号； &amp;amp；lbrack； &amp;amp；逗号； &amp;amp；vert； &amp;amp；逗号； &amp;amp； &amp;amp；ast； <br>如果要设置多个标签，请用逗号分隔标签；例如Label1， Label2。 |

**异常**：
抛出`RepositoryException`。

## 删除标签

``deleteLabel``方法从基线中的文件删除一个或多个标签。

**语法**：

```JAVA
public static Map
<String, String> deleteLabel(Session session, 
String sourcePath, 
String baselineName, 
String label) throws GuidesApiException
```

**参数**：

| 名称 | 类型 | 描述 |
|----|----|-----------|
| `session` | javax.jcr.Session | 有效的JCR会话。 |
| `sourcePath` | 字符串 | AEM存储库中DITA映射文件的绝对路径。 |
| `baselineName` | 字符串 | 必须从中删除标签的基线名称。<br> **注意：**&#x200B;标签已从直接从基线中的映射文件引用的文件版本中删除。 |
| `label` | 字符串 | 要从基线中的文件删除的标签。 <br>如果要删除多个标签，请用逗号分隔标签；例如Label1、Label2。 |

**返回**：
对于基线中的所有文件，映射具有*key：value*&#x200B;对`path:deletedlabels`。

**异常**：
抛出``RepositoryException`, `VersionException`, `Exception``。
