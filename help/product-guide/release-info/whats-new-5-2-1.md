---
title: 发行说明 | Adobe Experience Manager Guides 5.2.0 Service Pack 1版本中的新增功能
description: 了解Adobe Experience Manager Guides 5.2.0 Service Pack 1版本中的新增功能和增强功能
role: Leader
TQID: https://experienceleague.adobe.com/dXXQ1YvVduT11vvF5qyXHLqnuo1xMKkAb5I-EoD2JAA
product_v2:
  - id: fae5e35a-80c9-4b94-9352-1a060a6aab1d
    internal-label: Experience Manager Guides
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
feature_v2:
  - id: a3bd6397-2eb2-4908-a61c-226e26855dca
    internal-label: Publishing
subfeature_v2:
  - id: fd6cc9e1-e5e5-494e-b7b1-a32f2d6cd7c9
    internal-label: Output generation
role_v2:
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
    internal-label: Leader
source-git-commit: 788d0b9a2e2f07d2990bcc4f984f3ba4a4aabf17
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 0%
---
# 5.2.0 Service Pack 1版（2026年9月）的新增功能

本文介绍Adobe Experience Manager Guides版本5.2.0 Service Pack 1中引入的新功能和增强功能。

有关此版本中已修复的问题的列表，请查看[5.2.0 Service Pack 1版本](fixed-issues-5-2-0-sp1.md)中已修复的问题。

了解5.2.0 Service Pack 1版本](../release-info/upgrade-instructions-5-2-0-sp1.md)的[升级说明。


## Experience Manager Guides添加了MCP支持

Experience Manager Guides现在支持模型上下文协议(MCP)。 您可以将Claude、Cursor等AI工具连接到Guides，而无需任何自定义工作。 通过单个MCP端点，在这个版本中，经过身份验证的用户可以将Guides用作Headless系统，并管理主题和映射、创建和导出基线以及生成报表，所有这些操作都是在其现有AEM权限下进行的。 这使文档团队能够使用AI应用程序和代理更高效地工作。

有关详细信息，请查看[使用Adobe Experience Manager Guides MCP服务器](../install-conf-guide/conf-aem-guides-mcp.md)。


## 新编辑器中现在支持外部数据源和引文

新编辑器现在支持两种现有的Experience Manager Guides功能：与外部数据源连接以及在文档中使用引用的功能。

在新编辑器中创建或更新内容时，作者可以继续使用已配置的外部数据源。 由于还支持引用，因此作者可以在其内容中添加和管理引用，而无需切换编辑器。

## 支持AMA引用样式

Experience Manager Guides现在支持美国医学协会(AMA)的引文风格，并扩展了现有的引文框架，以满足医疗保健、监管和生命科学行业客户所要求的文档标准。

在&#x200B;**Workspace设置**&#x200B;中选择AMA作为引用样式时，引用将根据AMA准则自动设置格式，包括数字上标渲染、顺序编号和精确的引用列表排序。 编辑器中的&#x200B;**分析引文**&#x200B;选项仅在选择AMA时可用，允许作者添加和分析引文而不切换上下文。

本机PDF和AEM Sites输出格式支持AMA引文样式。 要配置引文样式，请转到&#x200B;**Workspace设置**，然后从引文样式选项中选择AMA。 有关详细信息，请查看[使用引文](../user-guide/web-editor-apply-citations.md)。


