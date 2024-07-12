---
title: 用于生成输出的基于Java的API
description: 了解用于生成输出的基于Java的API
exl-id: e19439df-39ec-47fd-9da5-24f51750a7e5
feature: Java-Based API Publishing
role: Developer
level: Experienced
source-git-commit: be06612d832785a91a3b2a89b84e0c2438ba30f2
workflow-type: tm+mt
source-wordcount: '160'
ht-degree: 0%

---

# 用于生成输出的基于Java的API {#id175UB30E05Z}

以下基于Java的API允许您为DITA映射生成输出。 此API以捆绑包形式提供。 您必须在代码中包含此捆绑包才能使用此API。

捆绑包详细信息：

- 组ID： **com.adobe.fmdita**

- 项目ID： **api**

- 版本： **3.4**

- 包： ****com.adobe.fmdita.api.maps****

- 类详细信息：

  ```JAVA
  public class **PublishUtils** extends Object
  ```

  **`PublishUtils`**&#x200B;类包含用于为一个或多个输出预设生成输出的方法。


## 生成输出

``generateOutput``方法使用指定的输出预设为DITA映射文件生成输出。

**语法**：

```JAVA
public static void generateOutput(Session session,
String sourcePath,
String outputName)
throws GuidesApiException
```

**参数**：
名称|类型|描述|
--------文-----------
|`session`|javax.jcr.Session|有效的JCR会话。|
需要为其生成输出的DITA映射文件的|``sourcePath``|字符串|路径\(在AEM存储库中\)。|
|``outputName``|字符串|用于生成输出的输出预设的名称。 可以使用管道分隔符(“\|”\)指定多个输出预设，例如`aemsite\|pdfoutput`。|

**异常**：
抛出``javax.jcr.RepositoryException``、`java.io.IOException`和`java.lang.Exception`。
