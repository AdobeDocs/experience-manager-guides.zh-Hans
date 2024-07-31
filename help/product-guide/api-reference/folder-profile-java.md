---
title: 用于处理文件夹配置文件的基于Java的API
description: 了解用于处理文件夹配置文件的基于Java的API
exl-id: 388ae654-c4f9-4bb7-ba98-370b8919e3a6
feature: Java-Based API Folder Profiles
role: Developer
level: Experienced
source-git-commit: 83966cc9187b13dd3b5956821e0aa038b41db28e
workflow-type: tm+mt
source-wordcount: '245'
ht-degree: 2%

---

# 用于处理文件夹配置文件的基于Java的API {#id175UB30E05Z}

以下基于Java的API允许您向文件夹级别的配置文件添加条件属性。 此API以捆绑包形式提供。 您必须在代码中包含此捆绑包才能使用此API。

捆绑包详细信息：

- 组ID： **com.adobe.fmdita**

- 项目ID： **api**

- 版本： **3.2**

- 包： **com.adobe.fmdita.api.profiles**

- 类详细信息：

  ```JAVA
  public class FolderProfileUtils extends Object
  ```

  **`FolderProfileUtils`**&#x200B;类包含用于在文件夹配置文件中添加条件属性的方法。


## 将条件属性添加到文件夹配置文件

``addAttributeProfiles``方法将条件属性添加到文件夹级别的配置文件。

**语法**：

```JAVA
public static boolean addAttributeProfiles
(List
<String> attributeNames, 
List
    <String> values, 
List
        <String> labels,
String profileName, 
Session session) throws GuidesApiException
```

**参数**：

| 名称 | 类型 | 描述 |
|----|----|-----------|
| ``attributeNames`` | 字符串 | 属性名称的列表。 |
| ``values`` | 字符串 | 给定属性的值列表。 |
| `labels` | 字符串 | `attribute`- `value`对的标签列表。 [1](#fntarg_1) |
| `profileName` | 字符串 | 必须应用这些属性、值和标签的文件夹级别配置文件的名称。 **重要提示：**&#x200B;配置文件中定义的所有现有属性 — 值 — 标签都被覆盖。 |
| `session` | javax.jcr.Session | 有效的JCR会话。 |

**返回**：
`true`表示成功。 如果失败，则抛出异常。

**异常**：
在以下情况下抛出``java.lang.Exception``：

- 如果API无法获取`resourceResolverFactory`对象。 在这种情况下，应重新启动捆绑包。
- 如果传递到API的参数无效。
- 如果API是通过未经授权的用户会话调用的，例如不是给定文件夹配置文件的管理员的用户。

[1](#fnsrc_1)数组列表中同一索引处的`attributeNames`、`values`和`labels`必须对应于同一条目。
