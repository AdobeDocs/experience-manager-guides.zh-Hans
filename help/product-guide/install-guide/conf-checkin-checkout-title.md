---
title: 配置签入和签出图标的标题
description: 了解如何配置签入和签出图标的标题
exl-id: a8888a17-e819-4fa2-bb6f-cafe1002803a
feature: Web Editor Configuration
role: Admin
level: Experienced
source-git-commit: 0513ecac38840a4cc649758bd1180edff1f8aed1
workflow-type: tm+mt
source-wordcount: '166'
ht-degree: 0%

---

# 配置签入和签出图标的标题

AEM Guides允许您在Web编辑器中配置签入和签出图标的标题。 执行以下步骤来配置检入和检出图标的标题：

1. 以管理员身份登录Adobe Experience Manager以下载用户界面配置文件。
1. 单击顶部的Adobe Experience Manager链接，然后选择&#x200B;**工具**。
1. 从工具列表中选择&#x200B;**指南**，然后单击&#x200B;**文件夹配置文件**。
1. 单击&#x200B;**全局配置文件**&#x200B;拼贴。
1. 选择&#x200B;**XML编辑器配置**&#x200B;选项卡，然后单击顶部的&#x200B;**编辑**&#x200B;图标。
1. 在&#x200B;**XML编辑器UI配置**&#x200B;部分中，单击&#x200B;**下载**&#x200B;图标以在本机系统上下载`ui_config.json`文件。
1. 在`ui_config.json`文件中，更改“顶栏”部分中的标题。 您可以更改以下值：

   ```json
   //Change title to "Check out" instead of "Lock"
           "title": "Check out"
   
   //Change title to "Check in" instead of "@checkOutBy
            "title": "Check in"
   ```

1. 保存文件并将其上传。
