---
title: 发行说明 | Adobe Experience Manager Guides as a Cloud Service，2023年4月版
description: 2023年4月版Adobe Experience Manager Guides as a Cloud Service
exl-id: fa339eab-d3d0-4763-adbf-6411e39aa213
feature: Release Notes
role: Leader
TQID: https://experienceleague.adobe.com/tGOV1IcAL8f2B5ziGWPOMfkkPZGPlxcXSerTtAO3LW0
product_v2: id: fae5e35a-80c9-4b94-9352-1a060a6aab1did: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2: id: a3bd6397-2eb2-4908-a61c-226e26855dcaid: ab01a588-7dea-43f2-a699-0b3f128465d6
subfeature_v2: id: d5ea0417-7932-4688-a3e2-4d3b2e7076a3
role_v2: id: f8a45b24-4be7-4f1b-909b-60d06b483a20
topic_v2: id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dc
source-git-commit: 8ed5c9cb07c56b84b36ef56a55af8738989a6d3f
workflow-type: tm+mt
source-wordcount: 602
ht-degree: 2%

---

# 2023年4月版Adobe Experience Manager Guides as a Cloud Service

此发行说明涵盖了升级说明、兼容性矩阵，以及Adobe Experience Manager Guides版本2023年4月中修复的问题（后称为&#x200B;*AEM Guides as a Cloud Service*）。

有关新增功能和增强功能的更多信息，请参阅[AEM Guides as a Cloud Service 2023年4月版的新增功能](whats-new-2023-4-0.md)。

## 升级到2023年4月版

请通过以下步骤升级您当前的AEM Guides as a Cloud Service设置：

1. 检查云服务的Git代码，并切换到在云服务管道中配置的与您要升级的环境对应的分支。
2. 将云服务Git代码的`/dox/dox.installer/pom.xml`文件中的`<dox.version>`属性更新为2023.4.249。
3. 提交更改并运行云服务管道，以升级到AEM Guides as a Cloud Service的2023年4月版本。

## 为现有内容编制索引的步骤（仅当使用的版本早于9月份的AEM Guides as a Cloud Service时）

执行以下步骤来索引现有内容并在映射级别使用新的查找和替换文本：

* 对服务器运行POST请求（使用正确的身份验证） — `http://<server:port>/bin/guides/map-find/indexing`。
(可选：您可以传递映射的特定路径来对其进行索引，默认情况下，所有映射都将进行索引 示例： `https://<Server:port>/bin/guides/map-find/indexing?paths=<map_path_in_repository>`)

* 该API将返回作业ID。 要检查作业的状态，您可以将带有作业ID的GET请求发送到同一端点 —  `http://<server:port>/bin/guides/map-find/indexing?jobId={jobId}`
（例如：http://&lt;_localhost:8080_/bin/guides/map-find/indexing？jobId=2022/9/15/7/27/7dfa1271-981e-4617-b5a4-c18379f11c42_678）

* 作业完成后，上述GET请求将做出成功响应，并提及是否有任何映射失败。 可以从服务器日志中确认已成功编制索引的映射。

## 兼容性矩阵

本部分列出了AEM Guides as a Cloud Service 2023年4月版本支持的软件应用程序的兼容性矩阵。

### FrameMaker和FrameMaker Publishing Server

| AEM Guides as a Cloud | FMPS | FrameMaker |
| --- | --- | --- |
| 2023.04.0 | 不兼容 | 2022或更高版本 |
| | | |


### 氧气连接器

| AEM Guides as a Cloud | 氧气连接器窗口 | 氧气连接器Mac | 在氧气窗口中编辑 | 在氧气Mac中编辑 |
| --- | --- | --- | --- | --- |
| 2023.04.0 | 2.9-uuid-2 | 2.9-uuid-2 | 2.3 | 2.3 |
|  |  |  |  |  |



## 修复的问题

修复了多个区域中的错误如下：

* 原生PDF |发布包含带有brackets()的输出类的内容会导致发布冻结。 (11596)
* 在移动（拖放）到启用了跟踪更改的现有列表项的位置时，出现问题。 (11570)
* 作为启用了跟踪更改的新列表项移动（拖放）时出现问题。 (11569)
* 在启用跟踪更改时，缩进或减少缩进列表项无法按预期工作。 (11568)
* 在启用了跟踪更改的行中添加内容，然后关闭跟踪更改实际上并不会将其关闭。 (11567)
* 无法拖放列表项，文本将移动以代替列表项。 (11566)
* 已完成审阅未在只读模式下打开。 (11387)
* AEM站点搜索中出现问题（在2-3级节点之外不起作用）。 (11352)
* 在创作以绿色显示的元素（跟踪更改）时，即使禁用跟踪更改，新内容也会显示为跟踪更改。 (7021)

### 有变通方法的已知问题

Adobe已发现AEM Guides as a Cloud Service 2023年4月版存在的以下已知问题。

* 原生PDF |在显式打开输出预设之前，不会填充旧元数据。
