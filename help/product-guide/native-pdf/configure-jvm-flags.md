---
title: 本机PDF |为本机PDF发布配置JVM标记
description: 为本机PDF发布配置JVM标记
feature: Output Generation
role: Admin
level: Experienced
hidefromtoc: true
source-git-commit: 3aadc59f5034828cf319992b7acb32d5a88eaf93
workflow-type: tm+mt
source-wordcount: '127'
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

1. 更新本机pdf **(** native.pdf.java.opts *)的属性* Java命令行选项以传递任何标准JVM标志。



1. 单击&#x200B;**保存**。
