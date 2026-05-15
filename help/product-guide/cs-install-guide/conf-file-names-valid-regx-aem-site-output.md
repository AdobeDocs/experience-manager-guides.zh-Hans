---
title: 为AEM站点输出配置有效文件名
description: 了解如何为AEM站点输出配置有效文件名
exl-id: 05215bec-653b-4563-83c6-a1bb16200469
feature: Filename Configuration
role: Admin
level: Experienced
TQID: https://experienceleague.adobe.com/hhc9Q8A-Eq3e8PAHHDXf1jXf8qVb-p4sU3Cum53ra9M
product_v2:
  - id: fae5e35a-80c9-4b94-9352-1a060a6aab1d
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: cb8c6a2a-3c38-4e40-867c-756f8c36bb0e
subfeature_v2:
  - id: ccd46b93-df7f-4458-ba4c-90a3562d9ab0
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
source-git-commit: 8ed5c9cb07c56b84b36ef56a55af8738989a6d3f
workflow-type: tm+mt
source-wordcount: 145
ht-degree: 1%

---

# 为AEM站点输出配置有效文件名 {#id214GK0X0KXA}

与DITA主题允许的有效文件名字符列表类似，您还可以为AEM站点输出配置有效文件名字符列表。 URL中不允许使用的一些已知字符是： ``'<>`@$``。 这些字符配置为在生成AEM站点输出文件名时找到时自动转换为下划线“`_`”。

使用[配置覆盖](download-install-additional-config-override.md#)中提供的说明创建配置文件。 在配置文件中，提供以下\(property\)详细信息以在AEM站点输出中设置有效字符：

| PID | 属性键 | 属性值 |
|---|------------|--------------|
| `com.adobe.fmdita.common.SanitizeNodeNameImpl` | `aemsite.DisallowedFileNameChars` | 在AEM站点输出文件名中添加要替换为下划线的字符。<br> **默认值**： ``'<\>\`@$`` |

**父主题：**&#x200B;[&#x200B;配置文件名](conf-file-names.md)
