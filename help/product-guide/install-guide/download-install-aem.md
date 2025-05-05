---
title: 安装Adobe Experience Manager
description: 了解如何安装Adobe Experience Manager
exl-id: 4693b102-b75a-4904-b2d5-914e774305f3
feature: Introduction, Installation
role: Admin
level: Experienced
source-git-commit: be06612d832785a91a3b2a89b84e0c2438ba30f2
workflow-type: tm+mt
source-wordcount: '172'
ht-degree: 0%

---

# 安装Adobe Experience Manager {#id213BCI020E8}

AEM Guides是一个安装在Adobe Experience Manager之上的插件。 安装AEM需要了解一些基本的AEM概念和建议的部署方案。 以下链接将帮助您开始安装AEM：

- [基本AEM概念](https://helpx.adobe.com/experience-manager/6-5/sites/deploying/using/deploy.html#BasicConcepts)

- [建议的AEM部署](https://helpx.adobe.com/experience-manager/6-5/sites/deploying/using/recommended-deploys.html)


>[!IMPORTANT]
>
> 如果您将Java 11与AEM 6.5.x一起使用，则可能会遇到问题 — *JDK 11导致`NoClassDefFoundError`*。 参考[JDK 11导致NoClassDefFoundError \| AEM 6.5](https://helpx.adobe.com/experience-manager/kb/jdk-11-causes-noclassdeffounderror---aem-6-5.html)文章来解决此问题。

确定最适合贵组织的部署策略后，请按照AEM文档的&#x200B;*[快速入门](https://helpx.adobe.com/experience-manager/6-5/sites/deploying/using/deploy.html#GettingStarted)*&#x200B;部分中的说明执行安装过程。

如果您计划升级AEM实例，则必须按照给定的顺序操作：

1. 卸载AEM Guides。
1. 升级您的AEM实例。
1. 安装AEM Guides。

>[!IMPORTANT]
>
> 您可以考虑使用许多性能优化建议来提高系统性能。 有关详细信息，请参阅[Recommendations以进行性能优化](download-install-recommend-perf-optimiz.md#)。

**父主题：**&#x200B;[&#x200B;下载并安装](download-install.md)
