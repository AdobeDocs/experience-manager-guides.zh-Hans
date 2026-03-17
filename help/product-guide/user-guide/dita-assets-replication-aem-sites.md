---
title: 管理DITA源资产的复制
description: 了解如何复制DITA源资产
feature: Publishing
role: User
source-git-commit: 52921a33d30817434424772ff32b1b31d4878497
workflow-type: tm+mt
source-wordcount: '155'
ht-degree: 0%

---

# 管理DITA源资产的复制

在某些发布环境中使用&#x200B;**快速发布**&#x200B;或&#x200B;**管理发布**&#x200B;发布从DITA内容生成的输出时，AEM还会尝试发布关联的DITA源资源，例如DITA映射，在某些情况下，还会发布DITA主题。 出现这种情况是因为AEM将DITA资产视为所生成Sites页面的依赖项。

![](images/quick-publish-site-instance.png){width="350" align="left"}

为了防止将DITA内容意外复制到发布环境并避免性能问题，管理员必须通过Configuration Manager明确管理DITA资产复制。 此配置使管理员能够控制受支持的DITA资产类型(包括DITA映射、DITA主题、XML文件和Markdown (.md)文件)的复制。

要配置DITA Assets复制功能，请查看[为Cloud Service配置DITA Assets复制](../cs-install-guide/configure-dita-assets-replication.md)或[为内部部署配置DITA Assets复制](../install-guide/configure-dita-asset-replication.md)，具体取决于您使用的设置

