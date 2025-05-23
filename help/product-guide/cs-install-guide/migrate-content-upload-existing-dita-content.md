---
title: 上载现有DITA内容
description: 了解如何上传现有DITA内容
exl-id: 2b385eef-00a7-4c25-9e78-367a0c9e44ba
feature: Migration
role: Admin
level: Experienced
source-git-commit: 0513ecac38840a4cc649758bd1180edff1f8aed1
workflow-type: tm+mt
source-wordcount: '499'
ht-degree: 0%

---

# 上载现有DITA内容 {#id176FF000JUI}

您很可能有一个包含要与AEM Guides一起使用的现有DITA内容的存储库。 对于此类现有内容，您可以使用[将数字资源添加到Adobe Experience Manager as a Cloud Service Assets](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/manage/add-assets.html?lang=zh-Hans)中介绍的任何受支持方法。

## 配置UUID文件名模式

导入内容时，文件名不必基于UUID。 在使用基于UUID的文件名的系统中，必须使用UUID而不是原始文件名引用所有文件。 如果导入的文件没有基于UUID的文件名，则可以将系统配置为向其文件属性添加UUID。 然后，使用此UUID来引用此类文件，其中UUID不用于命名文件。

使用[配置覆盖](download-install-additional-config-override.md#)中提供的说明创建配置文件。 在配置文件中，提供以下\(property\)详细信息以配置UUID文件名模式：

| PID | 属性键 | 属性值 |
|---|------------|--------------|
| `com.adobe.fmdita.config.ConfigManager` | `uuid.regex` | 指定UUID文件名模式的正则表达式的字符串。 <br>如果文件不遵循指定的模式，则会将UUID添加到文件的属性，并且所有对该文件的引用都将使用分配给该文件的UUID进行更新。<br> **默认值**： `"^GUID-(?<id>.*)"` |

## 使用curl命令

您还可以使用curl命令在DAM中创建文件夹、上传文件以及向上传的内容添加元数据。

**创建文件夹**

运行以下命令以在AEM存储库中创建文件夹：

```
curl --user <username>:<password> --data jcr:primaryType=sling:Folder "<server folder path>"
```

指定以下参数以创建文件夹：

- `<username>:<passowrd>`：指定用于访问AEM存储库的用户名和密码。 此用户必须具有文件夹创建权限。

- `jcr:primaryType=sling:Folder`：将此参数&#x200B;*指定为*&#x200B;以创建文件夹类型资源。

- `<server folder path>`：完整的文件夹路径，包括您要在AEM存储库中创建的新文件夹的名称。 例如，如果您将路径指定为`http://192.168.1.1:4502/content/dam/projects/AEM-Guides`，则在DAM的`projects`文件夹中创建文件夹`AEM-Guides`。


**上载文件**

运行以下命令在AEM资料档案库中上传文件：

```
curl --user <username>:<password> -T "<local file path>" "<server folder path>"
```

指定以下参数以上传文件：

- `<username>:<passowrd>`：指定用于访问AEM存储库的用户名和密码。 此用户必须具有对`server folder path`的写入权限。

- ``local file path``：本地系统上要上载的完整文件路径。

- `<server folder path>`：要上载文件的AEM服务器上的完整文件夹路径。


**添加元数据**

运行以下命令在文件中添加元数据：

```
curl --user <username>:<password> -F<attribute name>=<value> <metadata node path>
```

指定以下参数以添加元数据信息：

- `<username>:<passowrd>`：指定用于访问AEM存储库的用户名和密码。 此用户必须具有对``metadata node path``的写入权限。

- ``-F<attribute name>=<value>``： `<attribute name>`是元数据属性的名称，如`audience`，`<value>`可以是`internal`。 您可以指定多个以空格分隔的属性名称 — 值对。

- `<metadata node path>`：完整的文件夹路径，包括文件名及其元数据节点。 例如，如果将路径指定为`http://192.168.1.1:4502/content/dam/projects/AEM-Guides/intro.xml/jcr:content/metadata`，则指定的元数据信息在`intro.xml`文件中设置。


**父主题：**&#x200B;[&#x200B;迁移现有内容](migrate-content.md)
