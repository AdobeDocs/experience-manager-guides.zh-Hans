---
title: 在AEMaaCS上发布基准的指南
description: 了解AEM Cloud上发布的系统限制。
feature: Publishing
role: User, Admin
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: fae5e35a-80c9-4b94-9352-1a060a6aab1d
    internal-label: Experience Manager Guides
feature_v2:
  - id: f59890ff-de81-47d5-9ef8-7ab2dd10c6c3
    internal-label: Authoring and publishing content
subfeature_v2:
  - id: f901afa4-5613-4581-add5-219fa5f03fb5
    internal-label: Publishing
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
source-git-commit: 81a0e7f0736ba4970673dd87a888a4c60d3c1b4e
workflow-type: tm+mt
source-wordcount: '289'
ht-degree: 20%
---
# AEMaaCS上的AEM Guides发布基准

此基准评估了新发布API在各种输出预设以及在AEM Guides as a Cloud Service中增加地图大小时的性能。 目标是了解可扩展性行为并发现性能瓶颈。

发布服务使用具有自动缩放功能的基于[微服务的体系结构](https://experienceleague.adobe.com/en/docs/experience-manager-guides/using/knowledge-base/kb-articles/publishing/publish-microservice-architecture-and-performance)，允许通过额外的pod处理更大的工作负载。

## 执行环境

- **AEM版本**：2026.4.25322.20260407T085152Z
- **Guides附加组件版本**： 2026.5.0
- **初始pod计数**： 2 pod
- **自动缩放行为**：随着负载增加，在4个节点中可扩展到4个Pod
- **vCPU**： 10
- 每个pod **RAM**： 8 GB
- **并发用户**： 1个用户

>[!NOTE]
>
> 本练习重点介绍随着地图大小增加，发布的行为方式，重点介绍较大地图对吞吐量、延迟和负载下总体发布完成情况的影响。


## 输出世代号

**本机AEM站点**

| 地图大小 | 执行时间（秒） | 微服务 |
| ------- | ------------------ | ------------ |
| 10 | 62.378 | 是 |
| 100 | 64.27 | 是 |
| 1000 | 93.091 | 是 |
| 5000 | 496.319 | 是 |
| 10000 | 922.602 | 是 |

**本机PDF**

| 地图大小 | 执行时间（秒） | 微服务 |
| ------- | ------------------ | ------------ |
| 10 | 62.302 | 是 |
| 100 | 62.431 | 是 |
| 1000 | 108.666 | 是 |
| 5000 | 201.379 | 是 |
| 10000 | 1170.689 | 是 |

**PDF**

| 地图大小 | 执行时间（秒） | 微服务 |
| ------- | ------------------ | ------------ |
| 10 | 30.926 | 是 |
| 100 | 30.987 | 是 |
| 1000 | 77.007 | 是 |
| 5000 | 247.505 | 是 |
| 10000 | 686.61 | 是 |

**HTML5**

| 地图大小 | 执行时间（秒） | 微服务 |
| ------- | ------------------ | ------------ |
| 10 | 30.844 | 是 |
| 100 | 30.834 | 是 |
| 1000 | 77.384 | 是 |
| 5000 | 170.237 | 是 |
| 10000 | 419.166 | 是 |


## 主要意见

- AEM站点的生成时间取决于所使用的模板。 如果使用复杂模板，执行时间可能会增加。
- 自定义发布执行时间基于示例自定义输出。 自定义发布时间完全取决于客户自己的转换逻辑。