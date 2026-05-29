---
title: 配置新编辑器
description: 了解如何启用或禁用“新建编辑器”
feature: Configuration
role: Admin
level: Experienced
source-git-commit: 8d231bdbf00adb354bc31616e880495b00a3959c
workflow-type: tm+mt
source-wordcount: '79'
ht-degree: 2%

---

# 为内部部署配置新编辑器

>[!IMPORTANT]
>
> 通过代码部署系统配置，而不是在运行时环境中手动应用它们。

以下步骤说明了如何在On-Premise环境中启用“新编辑器”。

1. 打开Adobe Experience Manager Web控制台配置页面。

   用于访问配置页面的默认URL为：

   ```http
   http://<server name>:<port>/system/console/configMgr
   ```

1. 搜索并选择&#x200B;**com.adobe.fmdita.config.ConfigManager**&#x200B;包。

1. 启用设置&#x200B;**启用编辑器2.0** (`enable.markup.editor`)。

1. 选择&#x200B;**保存**。

