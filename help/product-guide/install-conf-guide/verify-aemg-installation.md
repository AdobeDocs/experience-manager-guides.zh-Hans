---
title: 验证AEM Guides安装
description: 了解如何验证AEM Guides安装
feature: Installation
role: Admin
level: Experienced
source-git-commit: 6f3f05419f4f5cdd45ab580cdee6fa869f20f01d
workflow-type: tm+mt
source-wordcount: '274'
ht-degree: 0%

---

# 验证AEM Guides安装 {#id213BD030FBE}

安装AEM Guides后，您需要验证安装是否成功。

以下选项卡提供了根据Experience Manager Guides设置验证AEM Guides安装情况的说明：Cloud Service或内部部署。

>[!BEGINTABS]

>[!TAB Cloud Service]

执行以下步骤来验证安装：

1. 访问Cloud Service的Developer Console。

   有关访问Developer Console的详细信息，请参阅AEM文档中的[Developer Console访问](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/developer-console.html?lang=zh-Hans)。

1. 访问AEM中的OSGi包列表。

   有关访问捆绑包的详细信息，请参阅AEM文档中的[捆绑包](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/developer-console.html?lang=zh-Hans#bundles)。

1. 在捆绑列表中搜索fmdita并检查其状态。

   对于已成功部署的包，状态应显示&#x200B;*活动*。 如果有任何捆绑包不处于“活动”状态，请查看AEM日志以解决安装问题。

>[!TAB 内部部署]

执行以下步骤来验证安装：

1. 登录AEM实例，然后导航到AEM Web控制台包页面。 用于访问捆绑包的默认URL为：

   ```http
   http://<server name>:<port>/system/console/bundles
   ```

   此时将显示捆绑包列表。

1. 通过在过滤文本框中输入fmdita来过滤捆绑列表，然后按&#x200B;**Enter**。

   将筛选捆绑包列表，以显示AEM Guides安装的捆绑包。 如果安装成功，则所有已安装的捆绑包都将具有&#x200B;**活动**&#x200B;的&#x200B;**状态**。

   如果任何捆绑包的状态不是&#x200B;**活动**，请查看AEM日志以解决安装问题。


>[!IMPORTANT]
>
> 您可以考虑使用许多性能优化建议来提高系统性能。 有关详细信息，请参阅[性能优化建议](perf-optimization-on-prem.md#)。

>[!ENDTABS]


