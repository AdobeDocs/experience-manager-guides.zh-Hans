---
title: 配置SCORM预览过滤器
description: 了解如何配置SCORM预览过滤器
feature: Configuration
role: Admin
level: Experienced
source-git-commit: f5b7ae41fe63b31a3b45b38fc73976987a2a5ebe
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 3%

---

# 配置SCORM预览

本文介绍如何配置Experience Manager Guides SCORM预览以管理哪些外部域允许在SCORM预览输出中提供样式表、图像、字体、媒体和嵌入的内容。 以下步骤说明如何根据您使用的设置为SCORM预览配置各种过滤器：

>[!BEGINTABS]

>[!TAB Cloud Service]

1. 使用[配置覆盖](../install-conf-guide/download-install-config-override.md)中提供的说明创建配置文件。

1. 在配置文件中，提供以下属性详细信息：

   | PID | 属性键 | 默认值 |
   |---|---|---|
   | `com.adobe.fmdita.publishworkflow.ScormPreviewResponseFilter` | `additional.style.src` | `https://fonts.googleapis.com` |
   | `com.adobe.fmdita.publishworkflow.ScormPreviewResponseFilter` | `additional.img.src` | - |
   | `com.adobe.fmdita.publishworkflow.ScormPreviewResponseFilter` | `additional.font.src` | `https://fonts.gstatic.com` |
   | `com.adobe.fmdita.publishworkflow.ScormPreviewResponseFilter` | `additional.media.src` | - |
   | `com.adobe.fmdita.publishworkflow.ScormPreviewResponseFilter` | `additional.frame.src` | `https://www.youtube-nocookie.com`, `https://www.youtube.com` |


1. 保存配置文件并将其部署到Cloud Service环境。

保存后，SCORM预览将开始应用更新的域。 域中未添加到此配置的外部资源在预览中将不可用。

>[!NOTE]
>
> 这仅适用于预览环境；可下载的SCORM包会继续按预期交付所有创作内容。


>[!TAB 内部部署]

1. 打开Adobe Experience Manager Web控制台配置页面。

   用于访问配置页面的默认URL为：

   ```http
   http://<server name>:<port>/system/console/configMgr
   ```

1. 搜索并选择&#x200B;**Guides SCORM预览过滤器(com.adobe.fmdita.publishworkflow.ScormPreviewResponseFilter)**&#x200B;包。

   ![](assets/scorm-preview-filters.png){width="600"}


1. 在捆绑包配置中，根据需要为每个资源类型添加允许的域URL：

   | 字段 | 描述 |
   |---|---|
   | **其他style-src主机** | 授权加载外部CSS样式表的域（默认为`https://fonts.googleapis.com`）。 |
   | **其他image-src主机** | 授权从中加载外部图像的域。 |
   | **其他font-src主机** | 授权加载外部字体文件（OTF、WOFF等）的域（默认为`https://fonts.gstatic.com`）。 |
   | **其他media-src主机** | 授权加载外部媒体文件的域。 |
   | **其他frame-src主机** | 授权嵌入iframe内容的域（默认情况下，`https://www.youtube.com`允许YouTube视频嵌入）。 |

1. 选择&#x200B;**保存**。

保存后，SCORM预览将开始应用更新的域。 域中未添加到此配置的外部资源在预览中将不可用。

>[!NOTE]
>
> 这仅适用于预览环境；可下载的SCORM包会继续按预期交付所有创作内容。

>[!ENDTABS]