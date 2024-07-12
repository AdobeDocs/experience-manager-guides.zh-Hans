---
title: 在 [!DNL AEM Guides]中设置自定义DITA-OT
description: 了解如何在 [!DNL Adobe Experience Manager Guides]中设置自定义DITA-OT
role: Admin
exl-id: f479c2cf-5b8b-4517-be97-81303468007a
feature: DITA-OT Configuration
source-git-commit: be06612d832785a91a3b2a89b84e0c2438ba30f2
workflow-type: tm+mt
source-wordcount: '143'
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
+ 通过&#x200B;**[!UICONTROL 工具]** > **[!UICONTROL 指南]** > **[!UICONTROL DITA配置文件]**添加DITA配置文件（使用上载自定义DITA-OT的DITA-OT路径，请参见下面的屏幕快照）
  ![DITA配置文件](assets/dita-profile.png)

>[!MORELIKETHIS]
>
>+ [自定义DITA-OT插件示例](https://www.dita-ot.org/dev/topics/pdf-customization.html)
