---
title: 配置文档状态过滤器
description: 了解如何配置文档状态过滤器
feature: Web Editor Configuration
role: Admin
level: Experienced
source-git-commit: 4942b914ff278ebcf09d00da32d6f9c7cc4d7ff9
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 0%

---

# 配置文档状态过滤器

Adobe Experience Manager Guides提供了根据文件的当前文档状态搜索文件的功能。 您可以使用过滤器搜索从存储库界面中搜索文件来浏览文件。

执行以下步骤来配置文档状态过滤器：

1. 以管理员身份登录Adobe Experience Manager。
1. 选择顶部的Adobe Experience Manager链接，然后选择&#x200B;**工具**。
1. 从工具列表中选择&#x200B;**指南**，然后选择&#x200B;**文件夹配置文件**。
1. 打开&#x200B;**全局配置文件**&#x200B;磁贴。 如果希望这些更改仅应用于该文件夹，而不是全局应用于该文件夹，您还可以选择特定文件夹配置文件拼贴。
1. 导航到&#x200B;**XML编辑器配置**。
1. 选择顶部的&#x200B;**编辑**&#x200B;图标。
1. 选择&#x200B;**下载**&#x200B;图标以在您的本地系统上下载`ui\_config.json`文件。
在下载的`ui\_config.json`文件中，请参阅以下部分：

       “
”       “repositoryFilters”： &lbrack;
       &lbrace;
       “title”：“Document state”，
       &quot;property&quot;： &quot;jcr：content/metadata/docstate&quot;，
       “子项”：&lbrack;
       &lbrace;
       “title”：“Draft”，
       &quot;value&quot;： &quot;Draft&quot;
       &rbrace;，
       &lbrace;
       &quot;title&quot;： &quot;Edit&quot;，
       &quot;value&quot;： &quot;Edit&quot;
       &rbrace;，
       &lbrace;
       &quot;title&quot;：&quot;In-Review&quot;，
       &quot;value&quot;：&quot;In-Review&quot;
       &rbrace;，
       &lbrace;
       &quot;title&quot;：&quot;Approved&quot;，
       &quot;value&quot;：&quot;Approved&quot;
       &rbrace;，
       &lbrace;
       “title”：“已审核”，
       &quot;value&quot;：&quot;Reviewed&quot;
       &rbrace;，
       &lbrace;
       &quot;title&quot;：&quot;Done&quot;，
       &quot;value&quot;： &quot;Done&quot;
       &rbrace;
       &rbrack;
       &rbrace;
       &rbrack;
       “
”   此代码片段表示Experience Manager Guides中可用的默认文档状态过滤器。

1. 您可以根据组织的工作流程来自定义过滤器值。 例如，要添加自定义文档状态&#x200B;**待定**，请在`children`下插入以下条目：

   ```
   {
       "title": "Pending",
       "value": "Pending"
   }
   ```

1. 更新后，保存文件并将其上传。

配置的筛选器显示在主页存储库中的&#x200B;**筛选器**&#x200B;面板中。

**父主题：**&#x200B;[&#x200B;自定义Web编辑器](conf-web-editor.md)
