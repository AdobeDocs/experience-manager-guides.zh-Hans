---
title: 用于处理DITA映射的基于Java的API
description: 了解用于处理DITA映射的基于Java的API
exl-id: bd91fc90-75f8-487c-99d1-2637e9cf9924
feature: Java-Based API Dita Map
role: Developer
level: Experienced
source-git-commit: 8c80a4da8e61909aab0f2db81ef97149774b36c4
workflow-type: tm+mt
source-wordcount: '1068'
ht-degree: 2%

---

# 用于处理DITA映射的基于Java的API {#id175UB30E05Z}

>[!NOTE]
>
> 您可以使用Experience Manager Guides中提供的基于Java的API来创建自定义插件和扩展现成工作流。 本文将于2024年11月存档。
> 有关使用基于Java的API的最新和详细文档，请查看[![javadoc](https://javadoc.io/badge2/com.adobe.aem/aem-guides-sdk-api/javadoc.svg)](https://javadoc.io/doc/com.adobe.aem/aem-guides-sdk-api)。



以下基于Java的API允许您在AEM Guides中使用DITA映射。 这些API以捆绑包形式提供。 您必须在代码中包含此捆绑包才能使用这些API。

捆绑包详细信息：

- 组ID： **com.adobe.fmdita**

- 项目ID： **api**

- 版本： **3.2**

- 包： **com.adobe.fmdita.api.maps**

- 类详细信息：

  ```JAVA
  public class MapUtilities extends Object
  ```

  MapUtilities类包含用于从DITA映射文件中检索元数据信息的方法。


## 下载具有依赖项的DITA映射

`zipMapWithDependents`方法创建一个.zip文件，其中包含DITA映射及其所有依赖项，例如引用的主题、子映射、图像和DTD。 DITA映射的.zip文件基于给定的基线创建。

它还允许您维护相同的结构\（父文件夹和子文件夹\）或在单个文件夹内为所有从属文件创建平面文件结构。

>[!IMPORTANT]
>
> 如果缺少任何依赖文件，则API将引发异常，并且无法创建.zip文件。

**语法**：

```JAVA
public static void zipMapWithDependents(Session session, 
                     String sourcePath, 
                     String baseline, 
                     OutputStream outputStream,
                     boolean flatFS) 
                     throws RepositoryException, IOException
```

**参数**：

| 名称 | 类型 | 描述 |
|----|----|-----------|
| `session` | javax.jcr.Session | 有效的JCR会话。 |
| `sourcePath` | 字符串 | 需要下载的DITA映射文件的路径\(在AEM存储库中\)。 |
| `outputStream` | java.io.OutputStream | 要将ZIP写入的流。 |
| `baseline` | 字符串 | 用于检索版本化内容的基线的标题。<br> **注意：**&#x200B;该值区分大小写。 |
| flatFS | 布尔值 | \(Optional\)如果设置为true，则在ZIP文件中返回文件的平面结构。 例如，如果DITA映射引用多个文件夹中的内容，则所有引用的文件都将提取到单个文件夹中。 如果存在同名文件，则通过添加数字后缀来重命名这些文件。 所有引用\（在DITA映射和主题中\）都会自动处理，因为它们会根据平面文件夹结构中文件的新位置进行更新。 如果设置为false，则文件夹结构将保持不变。 如果DITA映射从多个位置引用文件，则所有这些位置也会在ZIP文件中创建。 恢复ZIP文件时，会在目标位置创建精确的文件夹结构。 <br>此参数的默认值为false。 |

**返回**：
ZIP的内容将写入`outputStream`。

**异常**：
引发``javax.jcr.RepositoryException``，`java.io.IOException`。

## 下载包含依赖项的DITA映射\（异步\）

或者，您可以在异步模式下下载具有依赖项的DITA映射。 此方法对于较大的DITA映射更为有用。

`zipMapWithDependents`方法创建一个.zip文件，其中包含DITA映射及其所有依赖项，例如引用的主题、子映射、图像和DTD。 DITA映射的.zip文件基于给定的基线创建。

它还允许您维护相同的结构\（父文件夹和子文件夹\）或在单个文件夹内为所有从属文件创建平面文件结构。

>[!NOTE]
>
> 此节点会根据output.history.purgetime配置（如果已定义）在一段时间后自动删除，或默认删除5天。

**语法**：

```JAVA
public static CompletableFuture<Node> zipMapWithDependencies(Session session,
                     String sourcePath, 
                     String baseline, 
                     boolean flatFS) 
```

**参数**：

| 名称 | 类型 | 描述 |
|----|----|-----------|
| `session` | javax.jcr.Session | 有效的JCR会话。 |
| `sourcePath` | 字符串 | 需要下载的DITA映射文件的路径\(在AEM存储库中\)。 |
| `baseline` | 字符串 | 用于检索版本化内容的基线的标题。<br> **注意：**&#x200B;该值区分大小写。 |
| flatFS | 布尔值 | \(Optional\)如果设置为true，则在ZIP文件中返回文件的平面结构。 例如，如果DITA映射引用多个文件夹中的内容，则所有引用的文件都将提取到单个文件夹中。 如果存在同名文件，则通过添加数字后缀来重命名这些文件。 所有引用\（在DITA映射和主题中\）都会自动处理，因为它们会根据平面文件夹结构中文件的新位置进行更新。 如果设置为false，则文件夹结构将保持不变。 如果DITA映射从多个位置引用文件，则所有这些位置也会在ZIP文件中创建。 恢复ZIP文件时，会在目标位置创建精确的文件夹结构。<br>此参数的默认值为false。 |

**返回**：
zip文件的节点封装在`CompletableFuture`类中。 用户可以继续异步处理它，并且可以在需要节点时使用未来的`.get()`方法阻止线程。 返回的值也可能以错误结束，并且可以使用`.exceptionally()`方法处理。

## 获取基线列表

``getBaselineList``方法检索给定DITA映射存在的所有基线的列表。

**语法**：

```JAVA
public static List<HashMap<String,String>> getBaselineList( 
                  javax.jcr.Session session, 
                  String sourcePath)
                  throws javax.jcr.RepositoryException
```

**参数**：

| 名称 | 类型 | 描述 |
|----|----|-----------|
| `session` | javax.jcr.Session | 有效的JCR会话。 |
| `sourcePath` | 字符串 | 要检索其基线信息的DITA映射文件的路径\(在AEM存储库中\)。 |

**返回**：
`HashMap`对象的列表。 每个`HashMap`对象表示一个基线，并包含基线的名称和标题。

**异常**：
抛出``javax.jcr.RepositoryException``。

## 获取条件预设列表

``getConditionalPresetList``方法检索给定DITA映射存在的所有条件预设的列表。

**语法**：

```JAVA
public static List<HashMap<String,String>> getConditionalPresetList (
                  javax.jcr.Session session,
                  String sourcePath)
                  throws javax.jcr.RepositoryException
```

**参数**：

| 名称 | 类型 | 描述 |
|----|----|-----------|
| `session` | javax.jcr.Session | 有效的JCR会话。 |
| `sourcePath` | 字符串 | 要检索其条件预设信息的DITA映射文件的路径\(在AEM存储库中\)。 |

**返回**：
`HashMap`对象的列表。 每个`HashMap`对象都表示一个条件预设，并包含条件预设的名称和标题。

**异常**：
抛出``javax.jcr.RepositoryException``。

## 获取条件预设的DITAVAL文件信息

``getDitavalFromConditionalPreset``方法检索与给定DITA映射的条件预设对应的DITAVAL文件的路径。

**语法**：

```JAVA
public static String getDitavalFromConditionalPreset
    (Session session,
    String sourcePath, 
    String cpName) throws RepositoryException
```

**参数**：

| 名称 | 类型 | 描述 |
|----|----|-----------|
| `session` | javax.jcr.Session | 有效的JCR会话。 |
| `sourcePath` | 字符串 | 要检索DITAVAL文件的DITA映射文件的路径\(在AEM存储库中)。 |
| `cpName` | 字符串 | DITA映射中要检索DITAVAL文件的条件预设的名称。 |

**返回**：
与DITA映射文件中定义的条件预设相对应的DITAVAL文件的路径。

## 获取节点的所有依赖关系

``getAllDependencies``方法返回给定节点的所有依赖项。

**语法**：

```JAVA
public static List
<Node> getAllDependencies 
(Node rootNode) throws GuidesApiException
```

**参数**：

| 名称 | 类型 | 描述 |
|----|----|-----------|
| `rootNode` | javax.jcr.Node | 要检索其所有依赖项的根节点。 |

**返回**：
包含根节点的所有依赖关系的节点列表。
