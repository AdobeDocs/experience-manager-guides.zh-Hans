---
title: 用于跟踪文件夹或资产的后处理的API
description: 了解用于跟踪文件夹或资产的后处理的API
feature: Post-Processing Event Handler
role: Developer
level: Experienced
exl-id: f902fac1-2717-4696-a835-c4b0bb8add3d
TQID: 'https://experienceleague.adobe.com/Lyv-S5o-Z40bMqqIHhbxKrsmn9CCqHRnqnpiq91EjGU'
product_v2:
  - id: fae5e35a-80c9-4b94-9352-1a060a6aab1d
    internal-label: Experience Manager Guides
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
feature_v2:
  - id: c6d09140-3c91-45d3-b7ed-b681af752f43
    internal-label: APIs
subfeature_v2:
  - id: e0bef973-8c57-4760-9b12-ec950a3c7247
    internal-label: Post processing event handler
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 81a0e7f0736ba4970673dd87a888a4c60d3c1b4e
workflow-type: tm+mt
source-wordcount: '198'
ht-degree: 8%
---
# 用于跟踪文件夹或资产的后处理状态的API

>[!NOTE]
>
> 有关最新的REST API端点定义和相关详细信息，请在`https://<aem-author-url>/libs/fmdita/clientlibs/api-docs/index.html`处查看Swagger文档（将`<aem-author-url>`替换为您的AEM服务器URL）。 由于本文计划于2026年10月存档，因此我们建议您今后使用Swagger文档来了解API的最新信息。

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

获取由上述API运行的异步作业状态的GET方法。

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
