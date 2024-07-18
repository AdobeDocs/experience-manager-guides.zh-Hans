---
title: 用于注册数据源连接器的REST API
description: 了解用于注册数据源连接器的REST API
exl-id: e2811892-c3cf-41f5-94d8-c2b37823a53a
feature: Rest API Data Source
role: Developer
level: Experienced
source-git-commit: b4762314ec5269abe62b622184f1724762a6cfa0
workflow-type: tm+mt
source-wordcount: '81'
ht-degree: 7%

---

# 用于注册数据源连接器的REST API {#id236LG0Y0CXA}

以下REST API允许您注册数据源连接器。

## 注册数据源连接器

注册数据源连接器的GET方法。

**请求URL**：
`http://server:port/bin/guides/v1/konnect/config/register?path=<uploaded file path>`

**参数**：

| 名称 | 类型 | 必需 | 描述 |
|----|----|--------|-----------|
| `path` | 字符串 | 是 | 一个字符串，指向AEM存储库中的路径。 它可以是`/content/dam or /var/dxml`中的路径。 |

**示例**：\
`http://host:4502/bin/guides/v1/konnect/config/register?path=/var/dxml/konnect/jira.json`
