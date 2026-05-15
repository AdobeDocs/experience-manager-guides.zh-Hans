---
title: 原生PDF |为本机PDF发布配置JVM标记
description: 为本机PDF发布配置JVM标记
feature: Output Generation
role: Admin
level: Experienced
exl-id: d5432913-4b5a-48e7-9467-7f6c6e0adbe4
TQID: https://experienceleague.adobe.com/UvDTutOu-rfQ7tNTMZ6f1dNYJ90dwSGCtTJvWWFm638
product_v2: id: fae5e35a-80c9-4b94-9352-1a060a6aab1did: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2: id: a3bd6397-2eb2-4908-a61c-226e26855dcaid: cb8c6a2a-3c38-4e40-867c-756f8c36bb0e
subfeature_v2: id: d6596f3f-92a7-43ec-b444-237db6adad05id: fd6cc9e1-e5e5-494e-b7b1-a32f2d6cd7c9
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
source-git-commit: 8ed5c9cb07c56b84b36ef56a55af8738989a6d3f
workflow-type: tm+mt
source-wordcount: 128
ht-degree: 1%

---

# 为本地本地PDF发布配置JVM标记

本机PDF发布会启动一个单独的JVM进程来生成PDF。 您可能需要调整此JVM的配置以支持不同的场景。 例如，要运行较大的工作负载，应增加派生的JVM进程可用的最大栈大小。

执行以下步骤以配置AEM Guides本机PDF发布JVM标记：

1. 打开Adobe Experience Manager Web控制台配置页面。

   用于访问配置页面的默认URL为：

   ```http
   http://<server name>:<port>/system/console/configMgr
   ```

1. 搜索并选择&#x200B;*com.adobe.fmdita.config.ConfigManager*&#x200B;包。

1. 更新本机pdf **(*native.pdf.java.opts*)的属性** Java命令行选项以传递任何标准JVM标志。



1. 单击&#x200B;**保存**。
