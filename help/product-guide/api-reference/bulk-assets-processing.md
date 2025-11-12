---
title: 用于开始批量处理资产的API
description: 了解开始批量处理资产的API
feature: Post-Processing Event Handler
role: Developer
level: Experienced
source-git-commit: e2eca63a5dd56e358aeea047b37f4b0f88dc720b
workflow-type: tm+mt
source-wordcount: '542'
ht-degree: 8%

---

# 用于开始批量处理资产的API

为指定路径启动批量资产处理的POST方法。 此API支持基于JCR和基于数据库的资产处理。 它会启动一个异步作业，用于处理给定路径及其子路径下的所有资产。 启动后，API会返回唯一的processingID，该ID可用于跟踪作业状态。

**请求URL**

`http://<aem-guides-server>:<port-number>/bin/guides/v1/assets/process`

**请求参数**

| 名称 | 类型 | 必需 | 描述 |
|----|----|--------|-----------|
| `path` | 字符串 | 是 | AEM存储库中要处理的文件夹或资源的绝对路径。 |
| `excludedPaths` | 字符串 | 否 | 要从处理中排除的路径列表 |
| `type` | 字符串 | 是 | 要执行的处理的类型。 例如：ASSET_PROCESSING。 |

**请求示例**

```JSON
{
  "path": "/content/dam/status-fetch1",
  "excludedPaths": [
    "content/dam/status-fetch1/excluded-folder"
  ],
  "type": "ASSET_PROCESSING"
}
```

**响应值**

processingId轮询以获取异步作业的状态。

```JSON
{
  "processingId": "akjhdfalkj1132"
}
```

**响应代码**

- 200项成功
- 400输入无效
- 401未经授权的访问
- 500内部服务器错误

## 检查作业状态

一种GET方法，用于检索先前启动的资源处理作业的当前状态。

**请求URL**

`http://<aem-guides-server>:<port-number>/bin/guides/v1/assets/process/status`

**请求参数**

| 名称 | 类型 | 必需 | 描述 |
|----|----|--------|-----------|
| `processingId` | 字符串 | 是 | 状态被查询的作业的唯一ID。 |

**响应示例**

```JSON
{
  "processingId": "string",
  "path": "string",
  "excludedPaths": ["string"],
  "status": "WAITING",
  "triggeredCount": 0,
  "startedAt": 0,
  "completedAt": 0,
  "hasLogs": true,
  "createdBy": "string",
  "type": "ASSET_PROCESSING",
  "migrationSet": {
    "totalFiles": 0,
    "calculationStatus": "WAITING"
  },
  "eta": {
    "value": 0,
    "unit": "string"
  },
  "comments": "string",
  "restartable": true,
  "resumable": true,
  "cancellable": true
}
```

**响应代码**

- 200项成功
- 400输入无效
- 401未经授权的访问
- 500内部服务器错误

## 查看作业日志

一种GET方法，可检索给定作业ID的日志。 此API可获取资产处理作业的日志。 processingid是必需的。 API提供偏移和限制参数以及跟踪策略。

**请求URL**

`http://<aem-guides-server>:<port-number>/bin/guides/v1/assets/process/logs`

**请求参数**

| 名称 | 类型 | 必需 | 描述 |
|----|----|--------|-----------|
| `processingId` | 字符串 | 是 | 要查看其日志的作业的唯一ID。 |
| `offset` | 整数 | 否 | 应从中读取日志的起点（行号）。 用于分页，跳过前N行。 |
| `limit` | 整数 | 否 | 要提取的最大日志行数。 |
| `tail` | 整数 | 否 | 要从结尾检索的日志行数。 |


**响应示例**

```JSON
{
  "lines": [
    "string"
  ],
  "limit": 0,
  "offset": 0,
  "hasMore": true
}
```

**响应代码**

- 200项成功
- 400输入无效
- 401未经授权的访问
- 500内部服务器错误


## 下载作业日志

一种GET方法，可将给定作业的日志文件下载为ZIP文件。

**请求URL**

`http://<aem-guides-server>:<port-number>/bin/guides/v1/assets/process/logs/download`

**请求参数**

| 名称 | 类型 | 必需 | 描述 |
|----|----|--------|-----------|
| `processingId` | 字符串 | 是 | 需要下载日志文件的作业的唯一ID。 |


**响应示例**

```JSON
{
  "logFilePaths": [
    "string"
  ]
}
 
```

**响应代码**

- 400输入无效
- 401未经授权的访问
- 500内部服务器错误

## 取消作业

取消正在进行的批量资产处理请求的POST API。 如果未找到作业，则API会返回错误。

**请求URL**

`http://<aem-guides-server>:<port-number>/bin/guides/v1/assets/process/cancel`

**请求参数**

| 名称 | 类型 | 必需 | 描述 |
|----|----|--------|-----------|
| `processingId` | 字符串 | 是 | 状态被查询的作业的唯一ID。 |


**响应代码**

- 200项成功
- 400输入无效
- 401未经授权的访问
- 500内部服务器错误


## 继续执行作业

一个POST API，可重新启动之前已取消或失败的批量资产处理请求。 它会从上一个检查点恢复处理。 如果未找到作业或作业当前正在运行，则API会返回错误。

**请求URL**

`http://<aem-guides-server>:<port-number>/bin/guides/v1/assets/process/resume`

**请求参数**

| 名称 | 类型 | 必需 | 描述 |
|----|----|--------|-----------|
| `processingId` | 字符串 | 是 | 状态被查询的作业的唯一ID。 |


**响应代码**

- 200项成功
- 400输入无效
- 401未经授权的访问
- 500内部服务器错误

## 查看作业历史记录

一个GET API，可返回资产后处理的最后“N”次执行。

**请求URL**

`http://<aem-guides-server>:<port-number>/bin/guides/v1/assets/process/history`

**请求参数**

无。 此GET请求无需输入参数即可检索作业历史记录。

**响应示例**

```JSON
{
  "executionHistory": [
    {
      "processingId": "165f1de6-68c4-4dcd-9223-2b7242b62306",
      "path": "/content/dam/22858",
      "status": "SUCCESS",
      "triggeredCount": 6,
      "startedAt": 1761291362776,
      "completedAt": 1761291364026,
      "hasLogs": true,
      "createdBy": "user",
      "type": "ASSET_PROCESSING",
      "migrationSet": {
        "totalFiles": 6,
        "calculationStatus": "SUCCESS"
      },
      "eta": {
        "value": 0,
        "unit": "SECONDS"
      },
      "comments": "",
      "filter": {
        "fileTypes": [],
        "filterProcessedAssets": false
      },
      "cancellable": false,
      "resumable": false,
      "restartable": true
    }
  ]
}
```



