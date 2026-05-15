---
title: 升级AEM Guides
description: 了解如何升级AEM Guides
exl-id: 57ae906f-69e3-4319-89f6-0fa9ddb7a3ff
feature: Installation
role: Admin
level: Experienced
TQID: https://experienceleague.adobe.com/jGMljbRp60Wst7hVLeanMTLHY79Yhqo7yeUCCsLXx3k
product_v2:
  - id: fae5e35a-80c9-4b94-9352-1a060a6aab1d
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: cb8c6a2a-3c38-4e40-867c-756f8c36bb0e
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
source-git-commit: 8ed5c9cb07c56b84b36ef56a55af8738989a6d3f
workflow-type: tm+mt
source-wordcount: 114
ht-degree: 2%

---

# 升级AEM Guides {#id213BD050YPH}

1. 访问Cloud Manager的Git存储库。

1. 更新dox/dox.installer/pom.xml文件。

1. 将dox.version变量的值更新为Adobe提供的版本详细信息。

1. 提交更改并运行Cloud Manager管道以部署升级的包。


>[!NOTE]
>
> 有关使用CI/CD管道的更多详细信息，请参阅[在Adobe Cloud Manager中使用CI/CD管道](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/cloud-manager/use-the-cicd-pipeline-in-cloud-manager-for-aem.html?lang=zh-Hans)。

## 清除浏览器缓存

完成升级过程后，所有用户必须先清除浏览器缓存，然后才能使用AEM Guides的升级版本。

**父主题：**&#x200B;[&#x200B;下载并安装](download-install.md)
