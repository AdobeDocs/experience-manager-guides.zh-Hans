---
title: 使用curl命令
description: 了解如何在Experience Manager Guides中对上传的内容使用curl命令。
feature: Migration
role: Admin
level: Experienced
source-git-commit: 834959a6a0e22cd5d2b2c5d0e57ceb6d45c0c666
workflow-type: tm+mt
source-wordcount: '289'
ht-degree: 1%

---

# 使用curl命令

您还可以使用curl命令在DAM中创建文件夹、上传文件以及向上传的内容添加元数据。

## 创建文件夹

运行以下命令以在AEM存储库中创建文件夹：

```curl
curl --user <username>:<password> --data jcr:primaryType=sling:Folder "<server folder path>"
```

指定以下参数以创建文件夹：

- `<username>:<passowrd>`：指定用于访问AEM存储库的用户名和密码。 此用户必须具有文件夹创建权限。

- `jcr:primaryType=sling:Folder`：将此参数&#x200B;*指定为*&#x200B;以创建文件夹类型资源。

- `<server folder path>`：完整的文件夹路径，包括您要在AEM存储库中创建的新文件夹的名称。 例如，如果您将路径指定为`http://192.168.1.1:4502/content/dam/projects/AEM-Guides`，则在DAM的`AEM-Guides`文件夹中创建文件夹`projects`。


## 上传文件

运行以下命令以在AEM存储库中上传文件：

```curl
curl --user <username>:<password> -T "<local file path>" "<server folder path>"
```

指定以下参数以上传文件：

- `<username>:<passowrd>`：指定用于访问AEM存储库的用户名和密码。 此用户必须具有对`server folder path`的写入权限。

- ``local file path``：本地系统上要上载的完整文件路径。

- `<server folder path>`：您要将文件上传到的AEM服务器上的完整文件夹路径。


## 添加元数据

运行以下命令在文件中添加元数据：

```curl
curl --user <username>:<password> -F<attribute name>=<value> <metadata node path>
```

指定以下参数以添加元数据信息：

- `<username>:<passowrd>`：指定用于访问AEM存储库的用户名和密码。 此用户必须具有对``metadata node path``的写入权限。

- ``-F<attribute name>=<value>``： `<attribute name>`是元数据属性的名称，如`audience`，`<value>`可以是`internal`。 您可以指定多个以空格分隔的属性名称 — 值对。

- `<metadata node path>`：完整的文件夹路径，包括文件名及其元数据节点。 例如，如果将路径指定为`http://192.168.1.1:4502/content/dam/projects/AEM-Guides/intro.xml/jcr:content/metadata`，则指定的元数据信息在`intro.xml`文件中设置。