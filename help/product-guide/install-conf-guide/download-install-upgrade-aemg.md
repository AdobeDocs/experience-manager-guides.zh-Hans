---
title: 升级适用于Cloud Service的AEM Guides
description: 了解如何升级AEM Guides
feature: Installation
role: Admin
level: Experienced
source-git-commit: b416334318a83e882c32318bc4769d24268cdd1c
workflow-type: tm+mt
source-wordcount: '103'
ht-degree: 2%

---

# 升级适用于Cloud Service的AEM Guides {#id213BD050YPH}

要升级AEM Guides，请执行以下步骤：

1. 访问Cloud Manager的Git存储库。

1. 更新`dox/dox.installer/pom.xml`文件。

1. 将`dox.version`变量的值更新为Adobe提供的版本详细信息。

1. 提交更改并运行Cloud Manager管道以部署升级的包。


>[!NOTE]
>
> 有关使用CI/CD管道的更多详细信息，请参阅[在Adobe Cloud Manager中使用CI/CD管道](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/cloud-manager/use-the-cicd-pipeline-in-cloud-manager-for-aem.html?lang=zh-Hans)。

## 清除浏览器缓存

完成升级过程后，所有用户必须先清除浏览器缓存，然后才能使用AEM Guides的升级版本。
