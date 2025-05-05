---
title: 为AEM站点输出配置有效文件名
description: 了解如何为AEM站点输出配置有效文件名
exl-id: 1e69d6f8-7baf-4189-bbbd-34cd0fec6634
feature: Filename Configuration
role: Admin
level: Experienced
source-git-commit: 0513ecac38840a4cc649758bd1180edff1f8aed1
workflow-type: tm+mt
source-wordcount: '141'
ht-degree: 0%

---

# 为AEM站点输出配置有效文件名 {#id214GK0X0KXA}

与DITA主题允许的有效文件名字符列表类似，您还可以为AEM Site输出配置有效文件名字符列表。 URL中不允许使用的一些已知字符是： ```'<>`@$```。 这些字符配置为在生成AEM Site输出文件名时发现时自动转换为下划线“_”。 允许您在AEM站点输出中设置有效字符的配置存在于`com.adobe.fmdita.common.SanitizeNodeNameImpl`包中。 **将“不允许发布到AEM Sites的字符集”设置为**，以便在AEM Site输出文件名中包含要用下划线替换的字符。

**父主题：**&#x200B;[&#x200B;配置文件名](conf-file-names.md)
