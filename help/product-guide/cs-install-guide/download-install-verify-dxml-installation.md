---
title: 验证AEM Guides安装
description: 了解如何验证AEM Guides安装
exl-id: 4e566c57-a522-4605-bc70-47155f20b429
feature: Installation
role: Admin
level: Experienced
TQID: 'https://experienceleague.adobe.com/WDiYcOCdCuaJCrGYCupOS0TEk5TV-1q6Zi5z-S7KWLA'
product_v2:
  - id: fae5e35a-80c9-4b94-9352-1a060a6aab1d
    internal-label: Experience Manager Guides
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
feature_v2:
  - id: e88e74c7-6080-446a-8eb0-496f1ac5f7e6
    internal-label: Administration
subfeature_v2:
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
source-wordcount: '162'
ht-degree: 0%
---
# 验证AEM Guides安装 {#id213BD030FBE}

安装AEM Guides后，您需要验证安装是否成功。 执行以下步骤来验证安装：

1. 访问Cloud Service的Developer Console。

   有关访问Developer Console的详细信息，请参阅AEM文档中的[Developer Console访问](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/developer-console.html)。

1. 访问AEM中的OSGi包列表。

   有关访问捆绑包的详细信息，请参阅AEM文档中的[捆绑包](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/developer-console.html?lang=en#bundles)。

1. 在捆绑列表中搜索fmdita并检查其状态。

   对于已成功部署的包，状态应显示&#x200B;*活动*。 如果有任何捆绑包不处于“活动”状态，请查看AEM日志以解决安装问题。


**父主题：**&#x200B;[&#x200B;下载并安装](download-install.md)
