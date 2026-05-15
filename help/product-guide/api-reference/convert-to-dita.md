---
title: 用于转换工作流的REST API
description: 了解用于转换工作流的REST API
exl-id: f091782e-ab54-4db4-9018-9bcbff9da7b2
feature: Rest API Conversion Workflow
role: Developer
level: Experienced
TQID: https://experienceleague.adobe.com/EG-ugDPVpviaEI1SXHOaFLPfChkzqQ8tSkPV-LZ-X3o
product_v2:
  - id: fae5e35a-80c9-4b94-9352-1a060a6aab1d
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: a01bfd36-4ab8-4bf8-9dc0-5b45b890552e
  - id: c6d09140-3c91-45d3-b7ed-b681af752f43
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 8ed5c9cb07c56b84b36ef56a55af8738989a6d3f
workflow-type: tm+mt
source-wordcount: 402
ht-degree: 9%

---

# 用于转换工作流的REST API {#id175UB30E05Z}

以下REST API允许您将Word、HTML和InDesign文档转换为DITA格式。

## 转换Word文档

一种将Word文档转换为DITA格式的GET方法。

**请求URL**：
http://*&lt;aem-guides-server\>*： *&lt;端口号\>*/bin/fmdita/conversion

| 名称 | 类型 | 必需 | 描述 |
|----|----|--------|-----------|
| ``operation`` | 字符串 | 是 | 要调用的操作的名称。 此参数的值为``word2dita``。<br> **注意：**&#x200B;该值不区分大小写。 |
| `inputFile` | 字符串 | 是 | AEM存储库中源Word文件的绝对路径。 |
| `destPath` | 字符串 | 是 | 将保存转换的DITA文件的目标位置的绝对路径。 |
| `createRev` | 布尔值 | 是 | 指定是否在指定的目标创建了\(`true`\)文件修订版\(`false`\)。 仅当目标位置包含转换文件的现有版本时，才考虑使用此选项。 |
| `style2tagMap` | 字符串 | 是 | 用于转换的样式映射文件的绝对路径。 |

**响应值**：
返回HTTP 200 \(Successful\)响应。

## 转换HTML文档

一种将HTML文档转换为DITA格式的GET方法。

**请求URL**：

http://*<aem-guides-server\>*： *<端口号\>*/bin/fmdita/conversion

**参数**：

| 名称 | 类型 | 必需 | 描述 |
|----|----|--------|-----------|
| `operation` | 字符串 | 是 | 要调用的操作的名称。 此参数的值为``html2dita``。<br> **注意：**&#x200B;该值不区分大小写。 |
| `inputFile` | 字符串 | 是 | AEM存储库中源HTML文件的绝对路径。 |
| `destPath` | 字符串 | 是 | 将保存转换的DITA文件的目标位置的绝对路径。 |
| `createRev` | 布尔值 | 是 | 指定是否在指定的目标创建了\(`true`\)文件修订版\(`false`\)。 仅当目标位置包含转换文件的现有版本时，才考虑使用此选项。 |

**响应值**：

返回HTTP 200 \(Successful\)响应。

## 转换InDesign文档

一种将InDesign文档转换为DITA格式的GET方法。

**请求URL**：
http://*&lt;aem-guides-server\>*： *&lt;端口号\>*/bin/fmdita/conversion

**参数**：

| 名称 | 类型 | 必需 | 描述 |
|----|----|--------|-----------|
| ``operation`` | 字符串 | 是 | 要调用的操作的名称。 此参数的值为``idml2dita``。<br> **注意：**&#x200B;该值不区分大小写。 |
| `inputFile` | 字符串 | 是 | AEM存储库中源InDesign文件的绝对路径。 |
| `destPath` | 字符串 | 是 | 将保存转换的DITA文件的目标位置的绝对路径。 |
| `createRev` | 布尔值 | 是 | 指定是否在指定的目标创建了\(`true`\)文件修订版\(`false`\)。 仅当目标位置包含转换文件的现有版本时，才考虑使用此选项。 |

**响应值**：
返回HTTP 200 \(Successful\)响应。
