---
title: 配置基本输出位置以发布内部部署服务的输出
description: 配置基本输出位置以发布内部部署服务的输出
feature: Output Generation
role: Admin
level: Experienced
source-git-commit: ab6f1f09de2ef758d7f05ba0a49194ac9f387dea
workflow-type: tm+mt
source-wordcount: '108'
ht-degree: 1%

---

# 配置基本输出位置以发布内部部署服务的输出

执行以下步骤来配置基本输出位置：

1. 打开Adobe Experience Manager Web控制台配置页面。

   用于访问配置页面的默认URL为：

   ```http
   http://<server name>:<port>/system/console/configMgr
   ```

1. 搜索并选择&#x200B;*com.adobe.fmdita.config.ConfigManager*&#x200B;包。

1. 更新属性&#x200B;**基本输出位置**&#x200B;以指定AEM存储库中发布后保存PDF的默认路径。 此外，如果输入的路径无效，它将自动还原为默认路径： /content/dam/fmdita-outputs。

1. 单击&#x200B;**保存**。


