---
title: 验证AEM Guides安装
description: 了解如何验证AEM Guides安装
exl-id: 8e0afe18-5675-4c7e-b216-6de1a752bd01
feature: Installation
role: Admin
level: Experienced
hidefromtoc: true
source-git-commit: 3aadc59f5034828cf319992b7acb32d5a88eaf93
workflow-type: tm+mt
source-wordcount: '165'
ht-degree: 0%

---

# 验证AEM Guides安装 {#id213BD030FBE}

安装AEM Guides后，您需要验证安装是否成功。 执行以下步骤来验证安装过程：

1. 登录AEM实例，然后导航到AEM Web控制台包页面。 用于访问捆绑包的默认URL为：

   ```http
   http://<server name>:<port>/system/console/bundles
   ```

   此时将显示捆绑包列表。

1. 通过在过滤文本框中输入fmdita来过滤捆绑列表，然后按&#x200B;**Enter**。

   将筛选捆绑包列表，以显示AEM Guides安装的捆绑包。 如果安装成功，则所有已安装的捆绑包都将具有&#x200B;**活动**&#x200B;的&#x200B;**状态**。

   如果任何捆绑包的状态不是&#x200B;**活动**，请查看AEM日志以解决安装问题。


>[!IMPORTANT]
>
> 您可以考虑使用许多性能优化建议来提高系统性能。 有关详细信息，请参阅[性能优化建议](download-install-recommend-perf-optimiz.md#)。

**父主题：**[&#x200B;下载并安装](download-install.md)
