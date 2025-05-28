---
title: 在Experience Manager Guides中配置Adobe Workfront
description: 了解如何在Experience Manager Guides中配置Workfront
feature: Authoring
role: Admin
level: Experienced
exl-id: 1f72642c-e694-47cd-9182-f4f4aaf69655
source-git-commit: d5068ac73748ec7bc047450a947924b40977748f
workflow-type: tm+mt
source-wordcount: '480'
ht-degree: 3%

---

# 配置Adobe Workfront

Adobe Workfront是一个基于云的工作管理解决方案，可帮助团队和组织高效地规划、跟踪和管理其工作。 Experience Manager Guides与Adobe Workfront之间的集成让您能够在Experience Manager Guides核心CCMS功能之上访问强大的项目管理功能，从而允许您高效地计划、分配和跟踪任务。

详细了解Experience Manager Guides中的[Adobe Workfront集成](../user-guide/workfront-integration.md)。

## 先决条件

在开始之前，请确保：

1. 您具有Adobe Workfront的标准访问权限以及Experience Manager Guides的管理员访问权限。
2. 您[在Adobe Workfront中创建新的Experience Manager Guides所需的自定义表单](https://experienceleague.adobe.com/zh-hans/docs/workfront/using/administration-and-setup/customize/custom-forms/design-a-form/design-a-form)，具体使用以下字段：

   | 字段类型 | 标签 | 名称 | 选项（启用显示值） |
   |------------|------|------|-------------------------------|
   | 单选下拉菜单 | 任务类型 | task-type | 创作（值=作者）、发布（值=发布）、翻译（值=翻译）、审阅（值=审阅） |
   | 单选下拉菜单 | 任务状态 | 任务状态 | 创作（值= AUTHOR）、审阅（值= REVIEW） |
   | 带格式的文本 | 作者列表 | author-list | - |
   | 带格式的文本 | 查看者列表 | reviewer-list | - |
   | 单行文本 | 审核URL | review-url | - |
   | 单行文本 | 任务URL | task-url | - |
   | 单行文本 | 电子邮件主题 | email-subject | - |

>[!NOTE]
>
> * 在上表中，选项代表&#x200B;**任务类型**&#x200B;字段下的可用选项。 对于每个选项，您需要提供&#x200B;**任务名称**&#x200B;和&#x200B;**任务值**。 每种任务类型的名称和值必须与上表中所述完全相同。 例如，对于任务类型“作者”，请提供&#x200B;**创作**&#x200B;作为名称，提供&#x200B;**AUTHOR**&#x200B;作为其相应的值。
> * 使用本地服务时，请始终确保在&#x200B;**Day CQ Link Externalizer**&#x200B;配置中将`localhost`替换为正确的服务器地址，以正确接收电子邮件通知中已解析的任务链接。

## 开始使用

执行以下步骤以在Experience Manager Guides中配置Adobe Workfront。

1. 打开&#x200B;**工具面板**&#x200B;并选择&#x200B;**指南**。
2. 选择&#x200B;**配置Workfront**。

   显示&#x200B;**Workfront配置**&#x200B;页面。

   ![](assets/configure-workfront-page.png)

3. 在&#x200B;**Workfront配置**&#x200B;页面上，输入组织的Workfront域的完整URL、客户端ID和客户端密钥。

   要访问在Adobe Workfront设置中配置的&#x200B;**客户端ID**&#x200B;和&#x200B;**客户端密钥**&#x200B;密钥，请导航到`Setup >> Systems>> oAuth2 Applications`。

   有关配置Adobe Workfront域的更多详细信息，请在[为Workfront集成创建OAuth2应用程序](https://experienceleague.adobe.com/zh-hans/docs/workfront/using/administration-and-setup/configure-integrations/create-oauth-application#create-an-oauth2-application-using-user-credentials-authorization-code-flow)中查看“授权代码流”部分。

4. 选择&#x200B;**登录并验证**。

   系统会将您重定向至Adobe Workfront登录页面。
5. 使用您的Adobe Workfront电子邮件地址登录，然后选择&#x200B;**允许访问**&#x200B;以允许Oauth2应用程序访问您各自的Adobe Workfront帐户。

   您会被自动重定向到Experience Manager Guides上的Workfront配置页面。

6. 在自定义表单下拉列表中，选择您为Experience Manager Guides创建的Adobe Workfront自定义表单。 查看[先决条件](#prerequisites)。
7. 选择&#x200B;**保存并关闭**&#x200B;以应用并保存Workfront配置更改。

配置完毕后，[使用用户在Experience Manager Guides中的相同电子邮件地址将其添加到Adobe Workfront](https://experienceleague.adobe.com/zh-hans/docs/workfront/using/administration-and-setup/add-users/create-manage-users/add-users)。
