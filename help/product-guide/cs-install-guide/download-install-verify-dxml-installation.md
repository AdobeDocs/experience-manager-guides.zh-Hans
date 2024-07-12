---
title: 验证AEM Guides安装
description: 了解如何验证AEM Guides安装
exl-id: 4e566c57-a522-4605-bc70-47155f20b429
feature: Installation
role: Admin
level: Experienced
source-git-commit: 0513ecac38840a4cc649758bd1180edff1f8aed1
workflow-type: tm+mt
source-wordcount: '128'
ht-degree: 0%

---

# 验证AEM Guides安装 {#id213BD030FBE}

安装AEM Guides后，您需要验证安装是否成功。 执行以下步骤来验证安装：

1. 访问Cloud Service的Developer Console。

   有关访问Developer Console的详细信息，请参阅AEM文档中的[Developer Console访问](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/developer-console.html)。

1. 访问AEM中的OSGi包列表。

   有关访问包的详细信息，请参阅AEM文档中的[包](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/developer-console.html?lang=en#bundles)。

1. 在捆绑列表中搜索fmdita并检查其状态。

   对于已成功部署的包，状态应显示&#x200B;*活动*。 如果有任何捆绑包不处于“活动”状态，请检查AEM日志以解决安装问题。


**父主题：**[&#x200B;下载并安装](download-install.md)
