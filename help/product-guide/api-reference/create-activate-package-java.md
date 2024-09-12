---
title: 用于创建和激活包的基于Java的API
description: 了解用于创建和激活包的基于Java的API
exl-id: b801c2b3-445f-4aa7-a4f2-029563d7cb3a
feature: Java-Based API Packages
role: Developer
level: Experienced
source-git-commit: ed0b0e6124a8656e711a8e64b290b805569fbd48
workflow-type: tm+mt
source-wordcount: '591'
ht-degree: 1%

---

# 用于创建和激活包的基于Java的API {#id175UB30E05Z}

>[!NOTE]
>
> 您可以使用Experience Manager Guides中提供的基于Java的API来创建自定义插件和扩展现成工作流。 本文将于2024年11月存档。
> 有关使用基于Java的API的最新和详细文档，请查看[![javadoc](https://javadoc.io/badge2/com.adobe.aem/aem-guides-sdk-api/javadoc.svg)](https://javadoc.io/doc/com.adobe.aem/aem-guides-sdk-api)。


以下基于Java的API允许您创建和激活CRX包。 此API以捆绑包形式提供。 您必须在代码中包含此捆绑包才能使用此API。

捆绑包详细信息：

- 组ID： **com.adobe.fmdita**

- 项目ID： **api**

- 版本： **3.3**

- 包： **com.adobe.fmdita.api.crxactivate**

- 类详细信息：

  ```JAVA
  public class CRXActivator
  ```

  **`CRXActivator`**&#x200B;类包含用于在发布实例上创建CRX包并复制该包的方法。


## 创建和激活包

`activate`方法会在创作实例上创建CRX包，并在发布实例上复制该包（如果需要）。 假定已在创作实例上设置了AEM复制参数。 此方法会根据JSON字符串中作为输入参数提供的规则列表来创建CRX包。
>[!NOTE]
>
> 在创建或激活过程中遇到的错误将写入`outputstream`。

### 具有两个参数的示例

**语法**：


```JAVA
public static void activate
(
  String json, 
  OutputStream outputstream, 
  Session session
) 
throws GuidesApiException
```

### 带有第三个可选参数的示例

```JAVA
public static void activate
(
  String json, 
  OutputStream outputstream,
  String activationTarget, 
  Session session
) 
throws GuidesApiException
```

**参数**：

| 名称 | 类型 | 描述 |
|----|----|-----------|
| `json` | 字符串 | 确定要构建的CRX包的JSON字符串。 使用以下格式创建JSON字符串： <br>- `activate`：属于布尔型\(`true`/`false`\)。 确定是否在创作实例中创建的CRX包复制到发布实例。 <br> - `rules`：属于JSON数组的类型。 一系列JSON规则，将按顺序处理这些规则以构建CRX包。 <br> - `rootPath`：属于字符串类型。 执行节点/属性查询的基本路径。 如果不存在节点/属性查询，则根路径以及根路径下存在的所有节点都将包含在CRX包中。 <br> - `nodeQueries`：属于正则表达式数组的类型。 一个正则表达式数组，用于包含根路径下的特定文件。 <br> - `propertyQueries`：属于JSON数组的类型。 JSON对象数组，每个JSON对象由要在根路径上执行的XPath查询以及执行查询后每个JCR节点中存在的属性名称组成。 每个JCR节点中的属性值应该是一个路径或路径数组。 此属性中存在的路径已添加到CRX包。 |
| `outputstream` | java.io.OutputStream | 此标头用于编写各个阶段的结果，例如查询执行、文件包含、CRX包创建或激活。 在创建或激活过程中遇到的任何错误都会写入`outputstream`。 这对调试很有用。 |
| `session` | 字符串 | 具有激活权限的有效JCR会话。 |
| `activationTarget` | 字符串 | （*可选*） `preview`或`publish`用于Cloud Service，而`publish`用于内部部署软件<br> — 对于Cloud Service，如果参数包含无效值，则包激活失败。 <br> — 对于On-Premise Software，如果参数包含无效值，将记录错误，并使用默认值`publish`完成发布。 |

**异常**：

引发`java.io.IOException`和`java.io.IllegalArgumentException`


如果未定义可选参数`activationTarget`，则它会使用Cloud Service和内部部署软件的默认发布代理来激活。


**示例**：
以下示例显示如何构建JSON查询：

```JSON
{
  "activate": true,
  "rules": [
    {
      "rootPath": "/content/dam/nested",
      "nodeQueries": [
        ".*\\.jpg",
        ".*\\.png",
        ".*\\.gif"        
      ]
    },
    {
      "rootPath": "/content/output/sites/hierarchy_ditamap"
    },
    {
      "rootPath": "/content/output/sites/hierarchy_ditamap",
      "propertyQueries": [
        {
          "query": "//*[@fileReference]",
          "property": "fileReference"
        }
      ]
    }
  ]
}
```

示例JSON查询包含以下规则：

- 该包中仅包含/content/dam/nested路径下的.png、.jpg和.gif图像。
- /content/output/sites/hierarchy\_ditamap下的所有节点都包含在包中。
- /content/output/sites/hierarchy\_ditamap下的节点的`fileReference`属性中存在的路径包含在包中。
