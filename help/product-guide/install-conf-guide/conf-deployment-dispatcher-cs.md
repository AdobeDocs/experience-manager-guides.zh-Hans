---
title: 部署和Dispatcher配置
description: 了解Experience Manager Guides as a Cloud Service中的部署和Dispatcher配置
feature: Introduction, Installation
role: Admin
level: Experienced
source-git-commit: 834959a6a0e22cd5d2b2c5d0e57ceb6d45c0c666
workflow-type: tm+mt
source-wordcount: '308'
ht-degree: 3%

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

Dispatcher 是 Adobe Experience Manager 的缓存和/或负载平衡工具。有关更多详细信息，请参阅[云中的Dispatcher](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/content-delivery/disp-overview.html?lang=zh-Hans)。

1. 要将Dispatcher配置从AMS迁移到Cloud Service，请参阅[将Dispatcher配置从AMS迁移到AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/content-delivery/ams-aem.html?lang=zh-Hans)。
1. 有关如何配置Dispatcher的详细信息，请参阅[配置Dispatcher](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html?lang=zh-Hans)。

>[!NOTE]
>
> AEM as a Cloud Service不支持dispatcher for author实例。
