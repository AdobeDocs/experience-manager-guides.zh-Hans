---
title: 用于跟踪文件夹或资产的后处理的API
description: 了解用于跟踪文件夹或资产的后处理的API
feature: Post-Processing Event Handler
role: Developer
level: Experienced
source-git-commit: 558108650aeeeda440895972e460fa523b804bb2
workflow-type: tm+mt
source-wordcount: '150'
ht-degree: 10%

---

# 用于跟踪文件夹或资产的后处理状态的API

以下是一种POST方法，用于启动异步作业以获取资产的状态。

## 在指南中查找资产状态

**请求URL**

`http://<aem-guides-server>:<port-number>bin/guides/v1/assets/status `

**参数**

| 名称 | 类型 | 必需 | 描述 |
|----|----|--------|-----------|
| `path` | 字符串 | 是 | 需要获取其状态的文件夹或资源路径。 |
| `excludedPaths` | 字符串 | 否 | 要从上述列表中排除的文件夹路径。 |

```JSON
{ 

    "paths": [ 

        "/content/dam/status-fetch1", 

        "/content/dam/status-fetch2" 

    ], 

    "excludedPaths": [ 

        "content/dam/status-fetch1/excluded-folder" 

    ] 

} 
```

**响应值**
要轮询以获取异步作业状态的作业ID。

```JSON
{ 

  "jobId": "akjhdfalkj1132", 

  "status": "WAITING", 

 

} 
```

## Poller API

一种GET方法，可获取由上述API运行的异步作业的状态。

**请求URL**

`http://<aem-guides-server>:<port-number>bin/guides/v1/assets/status`

**参数**

| 名称 | 类型 | 必需 | 描述 |
|----|----|--------|-----------|
| `jobId` | 字符串 | 是 | 由上述API返回的作业ID 。 |

**响应值**

资源及其状态的列表。

```JSON
{ 

  "jobId": " akjhdfalkj1132", 

  "status": "SUCCESS", 

  "assets": [ 

    { 

      "path": "/content/dam/status-fetch1/a.dita", 

      "uuid": "GUID-1293914ansd", 

      "status": "SUCCESS", 

      "exists": true 

    }, 

    { 

      "path": "/content/dam/status-fetch1/b.dita", 

      "uuid": "GUID-1883241", 

      "status": "FAILURE", 

      "exists": true 

    } 

 

  ] 

} 
```

**状态值：** SUCCESS， FAILURE， PROCESSING， PENDING
