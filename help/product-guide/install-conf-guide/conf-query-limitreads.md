---
title: 配置查询的LimitReads数
description: 了解如何为查询配置LimitReads的数量
feature: Web Editor Configuration
role: Admin
level: Experienced
exl-id: 53748636-f3d1-4b3b-a772-2730b78741cb
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: fae5e35a-80c9-4b94-9352-1a060a6aab1d
    internal-label: Experience Manager Guides
feature_v2:
  - id: cb8c6a2a-3c38-4e40-867c-756f8c36bb0e
    internal-label: Configuration
subfeature_v2:
  - id: b0521e56-a0b2-40b6-bf47-ebc98751f9ba
    internal-label: Web Editor configuration
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 81a0e7f0736ba4970673dd87a888a4c60d3c1b4e
workflow-type: tm+mt
source-wordcount: '100'
ht-degree: 2%
---
# 为内部部署查询配置LimitReads的数量

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

**父主题：**[&#x200B;自定义编辑器](customize-overview.md)
