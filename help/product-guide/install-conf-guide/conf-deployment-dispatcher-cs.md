---
title: 部署和Dispatcher配置
description: 了解Experience Manager Guides as a Cloud Service中的部署和Dispatcher配置
feature: Introduction, Installation
role: Admin
level: Experienced
exl-id: 657a42be-36e7-4657-83d5-e866f8e55f09
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: fae5e35a-80c9-4b94-9352-1a060a6aab1d
    internal-label: Experience Manager Guides
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
source-git-commit: 81a0e7f0736ba4970673dd87a888a4c60d3c1b4e
workflow-type: tm+mt
source-wordcount: '347'
ht-degree: 6%
---
# 部署和Dispatcher配置

本文介绍了如何部署Experience Manager Guides as a Cloud Service和配置Dispatcher。

## 部署Experience Manager Guides as a Cloud Service

您可以首先通过Cloud Manager部署Experience Manager Guides。 要部署该模块，请按照[AEM Guides as a Cloud Service部署](../release-info/deploy-xml-on-aemaacs.md)中所述的说明操作。

>[!NOTE]
>
> 从2024.2.0版本开始，Experience Manager Guides仅作为Experience Manager as a Cloud Service的自动加载项提供。 如果您使用的是2023年12月版或更早版本，则可以从GitHub存储库下载并安装Adobe Experience Manager Guides。 如果您使用Experience Manager Guides的手动部署，请在为项目启用Experience Manager Guides之前，删除cloud manage git代码库中的第`<module>dox.installer</module> from file dox/pom.xml`行。

执行以下步骤以部署Experience Manager Guides模块：

1. 登录到[!UICONTROL Cloud Manager]。

1. 编辑要为其配置[!DNL Experience Manager Guides]的程序。

1. 切换到&#x200B;**[!UICONTROL 解决方案和加载项]**&#x200B;选项卡。

1. 在&#x200B;**[!UICONTROL 解决方案和加载项]**&#x200B;表中，单击&#x200B;**[!UICONTROL Assets]**。

1. 选择&#x200B;**[!UICONTROL 指南]**&#x200B;并选择&#x200B;**[!UICONTROL 保存]**。

您已成功配置项目以自动配置Experience Manager Guides解决方案。

![配置Experience Manager Guides解决方案](assets/addon-configuration.png)

>[!NOTE]
>
>要在集成程序下的任何环境中安装[!DNL Experience Manager Guides]，必须运行与该环境关联的管道。 在CM Git代码库中无需额外配置即可安装[!DNL Experience Manager Guides]。


## 配置调度程序

Dispatcher 是 Adobe Experience Manager 的缓存和/或负载平衡工具。 有关更多详细信息，请参阅[云中的Dispatcher](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/content-delivery/disp-overview.html?lang=zh-Hans)。

1. 要将Dispatcher配置从AMS迁移到Cloud Service，请参阅[将Dispatcher配置从AMS迁移到AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/content-delivery/ams-aem.html?lang=zh-Hans)。
1. 有关如何配置Dispatcher的详细信息，请参阅[配置Dispatcher](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html?lang=zh-Hans)。

>[!NOTE]
>
> AEM as a Cloud Service不支持dispatcher for author实例。
