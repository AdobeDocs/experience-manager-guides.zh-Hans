---
title: 为AEM站点输出配置有效文件名
description: 了解如何为AEM站点输出配置有效文件名
feature: Filename Configuration
role: Admin
level: Experienced
source-git-commit: 6f3f05419f4f5cdd45ab580cdee6fa869f20f01d
workflow-type: tm+mt
source-wordcount: '217'
ht-degree: 0%

---

# 为AEM站点输出配置有效文件名 {#id214GK0X0KXA}

与DITA主题允许的有效文件名字符列表类似，您还可以为AEM站点输出配置有效文件名字符列表。 URL中不允许使用的一些已知字符是： ``'<>`@$``。 这些字符配置为在生成AEM站点输出文件名时找到时自动转换为下划线“`_`”。

以下选项卡提供了有关如何根据AEM设置为Experience Manager Guides站点输出配置有效文件名的说明：Cloud Service或内部部署。

>[!BEGINTABS]

>[!TAB Cloud Service]

使用[配置覆盖](download-install-config-override.md#)中提供的说明创建配置文件。 在配置文件中，提供以下\(property\)详细信息以在AEM站点输出中设置有效字符：

| PID | 属性键 | 属性值 |
|---|------------|--------------|
| `com.adobe.fmdita.common.SanitizeNodeNameImpl` | `aemsite.DisallowedFileNameChars` | 在AEM站点输出文件名中添加要替换为下划线的字符。<br> **默认值**： ``'<\>\`@$`` |

>[!TAB 内部部署]

允许您在AEM站点输出中设置有效字符的配置存在于`com.adobe.fmdita.common.SanitizeNodeNameImpl`包中。 **将“不允许发布到AEM Sites的字符集”设置为**，以便在AEM站点输出文件名中包含要用下划线替换的字符。

>[!ENDTABS]
