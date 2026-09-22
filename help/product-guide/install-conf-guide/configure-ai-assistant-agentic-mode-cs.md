---
title: 在代理模式下配置AI助手
description: 了解如何在Experience Manager Guides中配置代理AI助手
source-git-commit: 5ed0a5191e1852dd65e0461f02d520b195f7cc39
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 1%
---

# 为Cloud Service以代理模式配置AI助手

作为管理员，您可以在Experience Manager Guides中为组织以代理模式配置AI助手。 配置步骤因在AEM as a Cloud Service环境中是否启用Unified Shell设置以及用户是通过SSO还是非SSO身份验证登录而异。 本文介绍了每个方案的配置过程。

## 先决条件

在代理模式下配置AI助手之前，必须将您的组织载入&#x200B;**CX Enterprise Coworker**。

## 根据您的环境配置AI助手

使用下表确定适用于用户的配置路径，然后执行相应的步骤。

| Unified shell | 登录类型 | 需要配置 |
|---|---|---|
| 已启用 | SSO | 无其他配置。 一切开箱即用 |
| 已启用 | 非SSO | 将IMS配置添加到环境 |
| 已禁用 | SSO | 将IMS配置添加到环境 |
| 已禁用 | 非SSO | 将IMS配置添加到环境 |

### 启用了Unified shell的用户

**SSO登录**

如果启用了Unified Shell，并且您的用户通过SSO登录，则无需其他配置。 将组织载入CX Enterprise Coworker后，代理模式中的AI助手会自动工作。

**非SSO登录**

如果已启用Unified Shell，但您的用户未使用SSO登录，则您必须[将IMS配置添加到下面的环境](#add-ims-configuration-to-the-environment)。

### 已禁用Unified Shell的用户

如果已禁用Unified Shell，则必须为以下两者[将IMS配置添加到环境](#add-ims-configuration-to-the-environment)：

- SSO登录
- 非SSO登录

## 将IMS配置添加到环境

执行以下步骤以将IMS配置添加到环境：

1. 打开Experience Manager，然后选择包含要配置的环境的程序。

2. 切换到&#x200B;**环境**&#x200B;选项卡。

3. 选择要配置的环境名称。 这会将您导航到&#x200B;**环境信息**&#x200B;页面。

4. 切换到&#x200B;**配置**&#x200B;选项卡。

5. 将JSON服务详细信息（在Adobe Developer Console中创建IMS配置时下载）粘贴到与`SERVICE_ACCOUNT_DETAILS`对应的&#x200B;**值**&#x200B;字段中。 确保使用环境所需的相同名称和配置。

>[!NOTE]
>如果您尚未为您的环境创建OAuth/IMS凭据，请先在Adobe Developer Console中创建，然后再完成此步骤。

![ims服务帐户配置](assets/ims-service-account-config.png){width="800"}

## 启用代理模式

为您的环境完成配置后，请联系客户成功团队以启用代理模式。

在为您的环境启用代理模式后，导航到&#x200B;**Workspace设置**，并在&#x200B;**AI助手**&#x200B;部分的&#x200B;**常规**&#x200B;选项卡下启用&#x200B;**代理**&#x200B;切换开关。
