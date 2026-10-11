---
title: 原生PDF |为本机PDF发布配置JVM标记
description: 为本机PDF发布配置JVM标记
feature: Output Generation
role: Admin
level: Experienced
exl-id: a2a9f44c-cb17-4423-a66e-499bce921398
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: fae5e35a-80c9-4b94-9352-1a060a6aab1d
    internal-label: Experience Manager Guides
feature_v2:
  - id: a3bd6397-2eb2-4908-a61c-226e26855dca
    internal-label: Publishing
subfeature_v2:
  - id: fd6cc9e1-e5e5-494e-b7b1-a32f2d6cd7c9
    internal-label: Output generation
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 81a0e7f0736ba4970673dd87a888a4c60d3c1b4e
workflow-type: tm+mt
source-wordcount: '128'
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
