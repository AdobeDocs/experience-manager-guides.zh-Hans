---
title: 配置DITA Assets复制
description: 了解如何配置Dita Assets复制
feature: Output Generation
role: Admin
level: Experienced
source-git-commit: 453da51a42984b912547570f2e1de70806b41171
workflow-type: tm+mt
source-wordcount: '109'
ht-degree: 3%

---

# 配置DITA assets复制

以下选项卡提供了有关根据Experience Manager Guides设置配置DITA Assets复制功能的说明：Cloud Service或内部部署。

>[!BEGINTABS]

>[!TAB Cloud Service]

1. 使用[配置覆盖](../install-conf-guide/download-install-config-override.md)中提供的说明创建配置文件。

1. 在配置文件中，提供以下（属性）详细信息：

   | PID | 属性键 | 属性值 |
   |---|---|---|
   | `com.adobe.fmdita.config.ConfigManager` | `publish.replicate` | **默认值：** &quot;true&quot; |

>[!TAB 内部部署]

1. 打开Adobe Experience Manager Web控制台配置页面。

   用于访问配置页面的默认URL为：

   ```http
   http://<server name>:<port>/system/console/configMgr
   ```

1. 搜索并选择&#x200B;*com.adobe.fmdita.config.ConfigManager*&#x200B;包。

1. 根据需要配置设置`Replicate DITA assets`。 默认情况下，该设置处于启用状态。


   ![](assets/dita-assets-replication.png){width="350" align="left"}


1. 选择&#x200B;**保存**。

>[!ENDTABS]
