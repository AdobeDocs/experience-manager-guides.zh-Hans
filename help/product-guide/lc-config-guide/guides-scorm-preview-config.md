---
title: 为SCORM预览配置内容安全策略
description: 了解如何使用Cloud Manager中的环境变量为SCORM预览配置内容安全策略
feature: Authoring
role: User
source-git-commit: 730fe6021aa20aa2b57801807da0f471f84a7718
workflow-type: tm+mt
source-wordcount: '538'
ht-degree: 3%

---


# 为SCORM预览配置内容安全策略(CSP)

Experience Manager Guides SCORM预览通过专用环境变量进行管理，该变量控制应用于预览体验的内容安全策略(CSP)。 启用该设置后，管理员可以通过添加其他受信任源来扩展该设置。 这些源可能包括SCORM包在Experience Manager Guides中正确加载和渲染预览所需的脚本、样式、字体、图像、媒体、框架等。

本文介绍了如何在Cloud Manager中添加和配置环境变量，细分了JSON值中每个字段的作用，并展示了如何在需求发生更改时稍后更新该值。

## 配置字段

变量`GUIDES_SCORM_PREVIEW_CONFIG`接受JSON对象作为其值。 每个值可控制在SCORM预览期间应用的CSP的特定方面：

| 字段 | 类型 | 描述 |
|---|---|---|
| `CSP_ENABLED` | 布尔值 | 为SCORM预览打开(`true`)或关闭(`false`) CSP实施。 |
| `ALLOW_UNSAFE_EVAL` | 布尔值 | 当设置为`true`时，允许使用`eval()`和类似的不安全JavaScript评估方法。 |
| `ADDITIONAL_SCRIPT_SRC` | 数组 | 允许向JavaScript提供服务的其他受信任来源。 |
| `ADDITIONAL_STYLE_SRC` | 数组 | 允许为样式表提供其他受信任源。 |
| `ADDITIONAL_FONT_SRC` | 数组 | 允许提供字体的其他可信来源。 |
| `ADDITIONAL_FRAME_SRC` | 数组 | 允许在`<iframe>`元素中加载其他受信任源。 |
| `ADDITIONAL_IMG_SRC` | 数组 | 允许提供图像的更多可信来源。 |
| `ADDITIONAL_MEDIA_SRC` | 数组 | 允许提供音频/视频内容的其他受信任源。 |
| `ADDITIONAL_WORKER_SRC` | 数组 | 允许为Web工作人员提供服务的其他受信任来源。 |
| `ADDITIONAL_CONNECT_SRC` | 数组 | 允许预览连接到的其他受信任源（例如XHR/fetch调用）。 |
| `ADDITIONAL_MANIFEST_SRC` | 数组 | 允许提供Web应用程序清单的其他可信来源。 |
| `ADDITIONAL_OBJECT_SRC` | 数组 | 允许通过`<object>`、`<embed>`或`<applet>`加载其他受信任源。 |


## 配置字段的默认值

```json
{
  "CSP_ENABLED": true,
  "ALLOW_UNSAFE_EVAL": false,
  "ADDITIONAL_STYLE_SRC": ["https://fonts.googleapis.com"],
  "ADDITIONAL_FONT_SRC": ["https://fonts.gstatic.com"],
  "ADDITIONAL_FRAME_SRC": ["https://www.youtube-nocookie.com", "https://www.youtube.com"],
  "ADDITIONAL_SCRIPT_SRC": [],
  "ADDITIONAL_WORKER_SRC": [],
  "ADDITIONAL_IMG_SRC": [],
  "ADDITIONAL_MEDIA_SRC": [],
  "ADDITIONAL_CONNECT_SRC": [],
  "ADDITIONAL_MANIFEST_SRC": [],
  "ADDITIONAL_OBJECT_SRC": []
}
```

根据需要，您不必填充每个值；如果不需要为任何源类型允许其他源，请将其保留为空数组。

>[!NOTE]
>
> 如果要禁用SCORM预览的CSP强制执行，请在JSON值中设置`"CSP_ENABLED": false`。

## 在Cloud Manager中添加变量

1. 登录Cloud Manager并选择要应用配置的环境。
2. 导航到环境的&#x200B;**配置**&#x200B;选项卡。
3. 选择&#x200B;**添加/更新**&#x200B;以添加环境变量。

   ![向Cloud Manager添加新变量](assets/add-new-variable.png){width="650"}

4. 在&#x200B;**名称**&#x200B;字段中输入变量(`GUIDES_SCORM_PREVIEW_CONFIG`)的名称。

   ![在名称字段中添加变量的名称](assets/variable-name.png){width="650"}

5. 在&#x200B;**值**&#x200B;字段中输入完整的JSON配置，包括课程需要的源允许列表。
6. 选择应用的&#x200B;**服务**&#x200B;以选择变量是应应用于&#x200B;**作者**、**发布**，还是同时应用于两者。 对于Experience Manager Guides创作，请选择&#x200B;**创作**。
7. 在&#x200B;**类型**&#x200B;字段中选择&#x200B;**变量**。
8. 选择&#x200B;**添加**。
9. 选择&#x200B;**保存**。

   ![保存变量以应用到环境](assets/save.png){width="650"}

保存后，Cloud Manager会将配置应用到选定的环境。 这通常需要10-12分钟才能传播，因此请留出时间让更新完成。 完成后，新配置将激活，以便在该环境中进行SCORM预览。

## 更新变量值

如果要求发生更改，您可以随时从Cloud Manager中的同一配置选项卡重新访问`GUIDES_SCORM_PREVIEW_CONFIG`变量。 找到现有变量并选择其&#x200B;**添加/更新**&#x200B;选项以打开它进行编辑，然后根据需要修订值。