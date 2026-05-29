---
title: 为AEM站点输出配置有效文件名
description: 了解如何为AEM站点输出配置有效文件名
exl-id: 1e69d6f8-7baf-4189-bbbd-34cd0fec6634
feature: Filename Configuration
role: Admin
level: Experienced
TQID: https://experienceleague.adobe.com/vGe4--XJ9VL5q74J7hVFCmD0vrBRnUkBAdZDCFcUxeU
product_v2: id: fae5e35a-80c9-4b94-9352-1a060a6aab1did: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2: id: a3bd6397-2eb2-4908-a61c-226e26855dcaid: cb8c6a2a-3c38-4e40-867c-756f8c36bb0e
subfeature_v2: id: ccd46b93-df7f-4458-ba4c-90a3562d9ab0
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
source-git-commit: 179e9016b12edb14c09ce9352a318e06a4fc628a
workflow-type: tm+mt
source-wordcount: 139
ht-degree: 0%

---

# 为AEM站点输出配置有效文件名 {#id214GK0X0KXA}

与DITA主题允许的有效文件名字符列表类似，您还可以为AEM站点输出配置有效文件名字符列表。 URL中不允许使用的一些已知字符是： `<>``@$`。 这些字符配置为在生成AEM站点输出文件名时发现时自动转换为下划线“_”。 允许您在AEM站点输出中设置有效字符的配置存在于`com.adobe.fmdita.common.SanitizeNodeNameImpl`包中。 **将“不允许发布到AEM Sites的字符集”设置为**，以便在AEM站点输出文件名中包含要用下划线替换的字符。

**父主题：**[&#x200B;配置文件名](conf-file-names.md)
