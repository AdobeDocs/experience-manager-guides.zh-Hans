---
title: 为内部部署配置新基线
description: 了解如何启用或禁用On-premise的新基线
feature: Configuration
role: Admin
level: Experienced
source-git-commit: 8d231bdbf00adb354bc31616e880495b00a3959c
workflow-type: tm+mt
source-wordcount: '125'
ht-degree: 1%

---

# 为内部部署配置新基线

>[!IMPORTANT]
>
> 通过代码部署系统配置，而不是在运行时环境中手动应用它们。

以下步骤说明了如何在On-Premise环境中启用“新建基线”。

1. 打开Adobe Experience Manager Web控制台配置页面。

   用于访问配置页面的默认URL为：

   ```http
   http://<server name>:<port>/system/console/configMgr
   ```

1. 搜索并选择&#x200B;**com.adobe.fmdita.config.ConfigManager**&#x200B;包。

1. 启用设置&#x200B;**启用更快的基线(v2)**。 您还可以使用确切的设置名称`enable.baseline.v2`进行搜索。

1. 选择&#x200B;**保存**。

>[!NOTE]
>
>启用此功能后，必须将现有基线迁移到新基线。 有关分步说明和演练视频，请在Experience Manager Guides[&#128279;](../user-guide/web-editor-baseline-v2.md)中查看新基线(Beta)。

