---
title: 本机PDF |配置基本输出位置以发布适用于云服务的PDF
description: 配置基本输出位置以发布适用于云服务的PDF
feature: Output Generation
role: Admin
level: Experienced
exl-id: d79085d6-938a-4e80-84a2-03562e6b76e0
hidefromtoc: true
source-git-commit: 564ee1731be2378744ffd2ed54a2fd423901a0b3
workflow-type: tm+mt
source-wordcount: '79'
ht-degree: 2%

---

# 配置用于发布云服务输出的基本输出位置

要配置基本输出位置，请执行以下步骤：

1. 使用[配置覆盖](../cs-install-guide/download-install-additional-config-override.md)中提供的说明创建配置文件。

1. 在配置文件中，提供以下（属性）详细信息以配置基本输出位置：

   | PID | 属性键 | 属性值 |
   |---|---|---|
   | `com.adobe.fmdita.config.ConfigManager` | `base.output.path` | **默认值：** &quot;/content/dam/fmdita-outputs&quot; |
