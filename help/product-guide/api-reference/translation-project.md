---
title: 创建翻译项目
description: 了解如何创建API翻译项目
feature: Post-Processing Event Handler
role: Developer
level: Experienced
source-git-commit: 41dd3dee5f9d64fb5c58b5b302cc9759e48e3631
workflow-type: tm+mt
source-wordcount: '199'
ht-degree: 17%

---

# 创建翻译项目

一种POST方法，通过接受所需的项目详细信息来帮助您创建翻译项目。

## 请求 URL

`http://<aem-guides-server>:<port-number>/bin/guides/v1/translation/project/create`

## 请求类型

POST

## 请求参数

| 名称 | 类型 | 描述 |
|----|----|-----------|
| `type` | 字符串 | newTranslationProject， xliffTranslationProject， newMultiLingualTranslationProject， addToExistingProject， newScopingTranslationProject |
| `versionDetails`、`versionSelector` | 字符串 | 基线、latestVersion、versionAsOfDate |
| `language` | 字符串 | 逗号分隔语言“de”、“fr” |
| `map.id` | 字符串 | 要翻译的源映射的GUID |
| `map.path` | 字符串 | 要翻译的源映射的路径 |
| `referenceType` | 字符串 | 间接、直接 |
| `fileType` | 字符串 | 映射、主题、其他 |
| `documentState` | 字符串 | 可以是映射配置文件上由用户分配的列表之一 |
| `translationStatus` | 字符串 | 不同步、正在同步、最新、已过期、进行中、缺少副本、无、不适用 |

>[!NOTE]
>
>创建翻译项目时，您可以使用`map.id`或`map.path`。

## 请求示例

```JSON
{
  "title": "Test Project 1 on Dec 5",
  "type": "newTranslationProject",
  "translationDetails": {
    "map": {
      "id": "GUID-06527014-062d-46dc-8fea-48b4b4497c51-en",
      "path": "/content/dam/ajay-test/lang/en/m2.ditamap"
    },
    "languages": ["de"],
    "versionDetails": {
      "versionSelector": "latestVersion"
    }
  },
  "filterDetails": [
    { "name": "referenceType", "values": [] },
    { "name": "fileType", "values": [] },
    { "name": "documentState", "values": [] },
    { "name": "translationStatus", "values": [] }
   ]
```

## 响应值

```JSON
{
  "executionId": "5c13c571-3407-46d5-8f45-50ea9e05a212",
  "path": "/content/projects/test_project_1_ondec5"
}
```

**响应代码**

- 200项成功
- 400输入无效
- 401未经授权的访问
- 500内部服务器错误

## 示例请求

### 添加到现有项目

```json
{
  "title": "Add to existing Project",
  "type": "addToExistingProject",
  "path": "/content/projects/test_project_1_existing",
  "translationDetails": {
    "map": {
      "id": "GUID-06527014-062d-46dc-8fea-48b4b4497c51-en"
    },
    "languages": ["de"],
    "versionDetails": {
      "versionSelector": "versionAsOfDate",
      "version": "2025-12-05T10:30:00+01:30"
    }
  },
  "filterDetails": [
    { "name": "referenceType", "values": [] },
    { "name": "fileType", "values": [] },
    { "name": "documentState", "values": [] },
    { "name": "translationStatus", "values": [] }
  ]
}
```

### 添加到具有基线的现有项目

```json
{
  "title": "Add to existin project Project with baseline",
  "type": "addToExistingProject",
  "path": "/content/projects/existing_project_path",
  "translationDetails": {
    "map": {
      "id": "GUID-06527014-062d-46dc-8fea-48b4b4497c51-en"
    },
    "languages": ["de"],
    "versionDetails": {
      "versionSelector": "baseline",
      "version": "test1"
    }
  },
  "filterDetails": [
    { "name": "referenceType", "values": ["Direct"] },
    { "name": "fileType", "values": [] },
    { "name": "documentState", "values": [] },
    { "name": "translationStatus", "values": [] }
  ]
}
```

## 翻译项目创建状态

跟踪新创建翻译项目的翻译状态的GET API。

## 请求 URL

`http://<aem-guides-server>:<port-number>/bin/guides/v1/translation/project/creationstatus`

## 请求类型

GET

## 请求参数

| 名称 | 类型 | 描述 |
|----|----|-----------|
| `path` | 字符串 | 项目路径 |
| `languageStatusMap` | 字符串 | 对于每个请求的语言，返回完成状态：进行中、已完成、失败、已跳过 |


## 请求示例

```json
{
  "path": "/content/projects/test_project_1_ondec5",
  "languageStatusMap": {
    "de": "Completed"
  }
}
```



