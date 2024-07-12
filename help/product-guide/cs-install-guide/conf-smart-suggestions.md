---
title: 配置用于创作的智能建议
description: 了解如何为创作配置智能建议
exl-id: a595ca1f-0123-40d3-a79c-a066bc6517b4
source-git-commit: d3e0c475ebd50a2664ea45c293d34b3a10772633
workflow-type: tm+mt
source-wordcount: '745'
ht-degree: 1%

---

# 为创作配置AI支持的智能建议

作为管理员，您可以为作者配置智能建议功能。 智能建议服务由基于Adobe IMS身份验证的身份验证来保护。 将您的环境与Adobe基于令牌的安全身份验证工作流集成，并开始使用新的智能建议功能。 以下配置可帮助您将&#x200B;**AI配置**&#x200B;选项卡添加到文件夹配置文件。 添加后，您可以在Web编辑器中使用智能建议功能。

## 在Adobe Developer Console中创建IMS配置

执行以下步骤可在Adobe Developer Console中创建IMS配置：

>[!NOTE]
>
>如果您已经创建了OAuth项目来配置基于微服务的发布，则可以跳过以下步骤来创建项目。

1. 启动[Adobe Developer Console](https://developer.adobe.com/console)。
1. 成功登录到Developer Console后，您将看到&#x200B;**主页**&#x200B;屏幕。 在&#x200B;**主页**&#x200B;屏幕上，您可以轻松地查找信息和快速链接，包括指向项目和下载的顶部导航链接。
1. 要创建新的空项目，请从&#x200B;**快速入门**&#x200B;链接中选择&#x200B;**新建项目**。
   ![快速入门链接](assets/conf-ss-quick-start.png) {width="550" align="left"}
   *创建新项目。*

1. 从&#x200B;**项目**&#x200B;屏幕中选择&#x200B;**添加API**。  出现&#x200B;**添加API**&#x200B;屏幕。 此屏幕显示了可用于开发应用程序的Adobe产品和技术的所有可用API、事件和服务。

1. 选择&#x200B;**I/O管理API**以将其添加到您的项目中。
   ![IO管理API](assets/confi-ss-io-management.png)
   *将I/O管理API添加到您的项目中。*

1. 创建新的&#x200B;**OAuth凭据**&#x200B;并保存它。

   配置API中的![OAuth凭据磁贴](assets/conf-ss-OAuth-credential.png)

   *为你的API配置OAuth凭据。*

1. 在&#x200B;**项目**&#x200B;选项卡中，选择&#x200B;**OAuth服务器到服务器**&#x200B;选项，然后选择新创建的凭据。

1. 选择&#x200B;**OAuth服务器到服务器**&#x200B;链接以查看项目的凭据详细信息。

   ![已连接的凭据](assets/conf-ss-connected-credentials.png) {width="800" align="left"}

   *连接到项目以查看凭据详细信息。*

1. 返回&#x200B;**项目**&#x200B;选项卡，然后在左侧选择&#x200B;**项目概述**。

   <img src="assets/project-overview.png" alt="项目概述" width="500">

   *开始新项目。*

1. 单击顶部的&#x200B;**下载**&#x200B;按钮以下载服务JSON。

   <img src="assets/download-json.png" alt="下载json" width="500">

   *下载JSON服务详细信息。*

您已配置OAuth身份验证详细信息并下载JSON服务详细信息。 根据下一节中的要求，随时准备此文件。

### 将IMS配置添加到环境

执行以下步骤以将IMS配置添加到环境：

1. 打开Experience Manager，然后选择包含要配置的环境的程序。
1. 切换到&#x200B;**环境**&#x200B;选项卡。
1. 选择要配置的环境名称。 这应该会将您导航到&#x200B;**环境信息**&#x200B;页面。
1. 切换到&#x200B;**配置**&#x200B;选项卡。
1. 更新SERVICE_ACCOUNT_DETAILS JSON字段。 确保您使用以下屏幕快照中给出的相同名称和配置。

![ims服务帐户配置](assets/ims-service-account-config.png){width="800" align="left"}


*添加环境配置详细信息。*




将IMS配置添加到环境后，执行以下步骤以使用OSGi将这些资产与AEM Guides链接：

1. 在您的Cloud Manager Git项目代码中，添加以下给定两个文件（对于文件内容，请查看[附录](#appendix)）。

   * `com.adobe.aem.guides.eventing.ImsConfiguratorService.cfg.json`
   * `com.adobe.fmdita.smartsuggest.service.SmartSuggestConfigurationConsumer.cfg.json`
1. 确保`filter.xml`涵盖新添加的文件。
1. 提交并推送您的Git更改。
1. 运行管道以在环境中应用更改。

完成此操作后，您应该能够使用智能建议功能。



## 附录 {#appendix}

**文件**：
`com.adobe.aem.guides.eventing.ImsConfiguratorService.cfg.json`

**内容**：

```
{
 "service.account.details": "$[secret:SERVICE_ACCOUNT_DETAILS]",
}
```

**文件**： `com.adobe.fmdita.smartsuggest.service.SmartSuggestConfigurationConsumer.cfg.json`

**内容**：

```
{
  "smart.suggestion.flag":true,
  "conref.inline.threshold":0.6,
  "conref.block.threshold":0.7,
  "emerald.url":"https://adobeioruntime.net/apis/543112-smartsuggest/emerald/v1",
  "instance.type":"prod"
}
```

## 智能建议配置详细信息

| 键 | 描述 | 允许的值 | 默认值 |
|---|---|---|---|
| smart.suggestion.flag | 控制是否启用智能建议 | true/false | false |
| conref.inline.threshold | 控制为用户当前键入的标记获取的建议精确度/回调度的阈值。 | 从–1.0到1.0的任何值。 | 0.6 |
| conref.block.threshold | 控制在整个文件中为标记获取的建议精确度/回调度的阈值。 | 从–1.0到1.0的任何值。 | 0.7 |
| emerald.url | 翡翠矢量数据库的端点 | [https://adobeioruntime.net/apis/543112-smartsuggest/emerald/v1](https://adobeioruntime.net/apis/543112-smartsuggest/emerald/v1) | [https://adobeioruntime.net/apis/543112-smartsuggest/emerald/v1](https://adobeioruntime.net/apis/543112-smartsuggest/emerald/v1) |
| instance.type | AEM实例的类型。 请确保对于已配置智能建议的每个AEM实例而言，这是唯一的。 用例是在暂存环境中使用“instance.type”=“stage”测试该功能，与此同时，该功能也在“prod”上配置。 | 标识环境的任意唯一键。 仅允许&#x200B;*个字母数字*&#x200B;值。 “dev”/“stage”/“prod”/“test1”/“stage2” | &quot;prod&quot; |

配置完毕后，智能建议图标将显示在Web编辑器的右侧面板中。 编辑主题时，可以查看智能建议列表。 有关更多详细信息，请查看《Experience Manager用户指南》中用于创作的[基于人工智能的智能建议](../user-guide/authoring-ai-based-smart-suggestions.md)部分。
