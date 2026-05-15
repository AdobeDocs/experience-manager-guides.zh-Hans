---
title: 在 [!DNL AEM Guides]中设置自定义DITA-OT
description: 了解如何在 [!DNL Adobe Experience Manager Guides]中设置自定义DITA-OT
role: Admin
exl-id: f479c2cf-5b8b-4517-be97-81303468007a
feature: DITA-OT Configuration
TQID: https://experienceleague.adobe.com/EaU6rkZL-RBkkYDhKxHNkizIVSqNzEDd-TtFlJAmREw
product_v2:
  - id: fae5e35a-80c9-4b94-9352-1a060a6aab1d
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: a3bd6397-2eb2-4908-a61c-226e26855dca
  - id: cb8c6a2a-3c38-4e40-867c-756f8c36bb0e
subfeature_v2:
  - id: b1ef4d86-3917-4b76-a0bc-4a4771f9b3b0
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2:
  - id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dc
source-git-commit: 8ed5c9cb07c56b84b36ef56a55af8738989a6d3f
workflow-type: tm+mt
source-wordcount: 174
ht-degree: 0%

---

# 在[!DNL AEM Guides]中为AEM设置自定义DITA-OT

_安装和配置指南_&#x200B;的&#x200B;_使用自定义DITA-OT插件_&#x200B;部分介绍了添加自定义DITA-OT的步骤。

从较高层面来看，这些步骤包括：

+ 获取基本DITA-OT
   + 如果要从[!DNL AEM Guides]获取现成DITA-OT的副本，请从路径`/etc/fmdita/dita_resources/DITA-OT.zip`下载
   + 如果要获取其他版本，则可以从[dita-ot repo](https://www.dita-ot.org/download)下载
+ 对DITA-OT进行更改，如[添加新插件](https://www.dita-ot.org/dev/topics/plugins-installing.html)，或自定义现有插件（请参阅下面相关链接部分中的示例）
+ 将`DITA-OT.zip`上传至`/apps/<project-folder>/dita_resources`（建议创建自定义项目文件夹）
+ 通过&#x200B;**[!UICONTROL 工具]** > **[!UICONTROL 指南]** > **[!UICONTROL DITA配置文件]**&#x200B;添加DITA配置文件（使用上载自定义DITA-OT的DITA-OT路径，请参见下面的屏幕快照）
  ![DITA配置文件](assets/dita-profile.png)

>[!MORELIKETHIS]
>
>+ [自定义DITA-OT插件示例](https://www.dita-ot.org/dev/topics/pdf-customization.html)
