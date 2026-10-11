---
title: 安装Adobe Experience Manager
description: 了解如何安装Adobe Experience Manager
exl-id: 4693b102-b75a-4904-b2d5-914e774305f3
feature: Introduction, Installation
role: Admin
level: Experienced
TQID: 'https://experienceleague.adobe.com/yoV8cMoMPIDbFi-cTm2LmmOSTpOjx8TrhengJ3WPrBs'
product_v2:
  - id: fae5e35a-80c9-4b94-9352-1a060a6aab1d
    internal-label: Experience Manager Guides
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
feature_v2:
  - id: e88e74c7-6080-446a-8eb0-496f1ac5f7e6
    internal-label: Administration
subfeature_v2:
  - id: c5fd2af0-6cbb-4746-ab0d-40ecb093af12
    internal-label: Introduction
  - id: e557051c-ff02-4ff8-9421-cf452af0edd5
    internal-label: Installation
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
topic_v2:
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
    internal-label: Optimization
source-git-commit: 81a0e7f0736ba4970673dd87a888a4c60d3c1b4e
workflow-type: tm+mt
source-wordcount: '215'
ht-degree: 0%
---
# 安装Adobe Experience Manager {#id213BCI020E8}

AEM Guides是一个安装在Adobe Experience Manager之上的插件。 安装AEM需要了解一些基本的AEM概念和建议的部署方案。 以下链接将帮助您开始安装AEM：

- [AEM的基本概念](https://helpx.adobe.com/experience-manager/6-5/sites/deploying/using/deploy.html#BasicConcepts)

- [建议的AEM部署](https://helpx.adobe.com/experience-manager/6-5/sites/deploying/using/recommended-deploys.html)


>[!IMPORTANT]
>
> 如果您将Java 11与AEM 6.5.x一起使用，则可能会遇到问题 — *JDK 11导致`NoClassDefFoundError`*。 参考[JDK 11会导致NoClassDefFoundError \| AEM 6.5](https://helpx.adobe.com/experience-manager/kb/jdk-11-causes-noclassdeffounderror---aem-6-5.html)文章解决此问题。

确定最适合贵组织的部署策略后，请按照AEM文档的&#x200B;*[快速入门](https://helpx.adobe.com/experience-manager/6-5/sites/deploying/using/deploy.html#GettingStarted)*&#x200B;部分中的说明执行安装过程。

如果您计划升级AEM实例，则必须按照给定的顺序操作：

1. 卸载AEM Guides。
1. 升级您的AEM实例。
1. 安装AEM Guides。

>[!IMPORTANT]
>
> 您可以考虑使用许多性能优化建议来提高系统性能。 有关详细信息，请参阅[性能优化建议](download-install-recommend-perf-optimiz.md#)。

**父主题：**[&#x200B;下载并安装](download-install.md)
