---
title: 配置查询的LimitReads数
description: 了解如何为查询配置LimitReads的数量
exl-id: f6010cc3-5fec-4ec7-adf7-5ad3c9bd8879
feature: Web Editor Configuration
role: Admin
level: Experienced
TQID: https://experienceleague.adobe.com/BwhrVPLcY4zw-pzB2wYGXnzBQHV2eFruoQnHWOE4F88
product_v2:
  - id: fae5e35a-80c9-4b94-9352-1a060a6aab1d
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: a3bd6397-2eb2-4908-a61c-226e26855dca
  - id: cb8c6a2a-3c38-4e40-867c-756f8c36bb0e
subfeature_v2:
  - id: b0521e56-a0b2-40b6-bf47-ebc98751f9ba
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
source-git-commit: 8ed5c9cb07c56b84b36ef56a55af8738989a6d3f
workflow-type: tm+mt
source-wordcount: 98
ht-degree: 2%

---

# 配置查询的LimitReads数 {#id231RC0HL0ID}

要增加查询一次可读取的节点数，请执行以下步骤：

1. 打开Adobe Experience Manager Web控制台JMX页面。

   用于访问配置页面的默认URL为：

   ```http
   http://<server name>:<port>/system/console/jmx
   ```

1. 搜索并单击&#x200B;**QueryEngineSettings**。

1. 更改&#x200B;**LimitReads**&#x200B;属性的属性值。

1. 单击&#x200B;**保存**。


当增加此属性值时，它有助于为较大的DITA映射生成报告。

**父主题：**&#x200B;[&#x200B;自定义Web编辑器](conf-web-editor.md)
