---
title: 配置查询的LimitReads数
description: 了解如何为查询配置LimitReads的数量
feature: Web Editor Configuration
role: Admin
level: Experienced
source-git-commit: 6f3f05419f4f5cdd45ab580cdee6fa869f20f01d
workflow-type: tm+mt
source-wordcount: '101'
ht-degree: 1%

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

**父主题：**[&#x200B;自定义Web编辑器](customize-overview.md)
