---
title: 使用AI助手智能创作文档'
description: 了解如何使用AI助手在Adobe Experience Manager Guides中智能地搜索和创作文档。
exl-id: c18e8761-333e-40ef-9e16-e71a194a754a
TQID: https://experienceleague.adobe.com/pg9zeEg8m3NeDbN-j945SqPbaMX0GgBmuquAsQcrjOM
product_v2:
  - id: fae5e35a-80c9-4b94-9352-1a060a6aab1d
    internal-label: Experience Manager Guides
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
feature_v2:
  - id: ab01a588-7dea-43f2-a699-0b3f128465d6
    internal-label: Authoring
  - id: ec4263d9-bf7c-44c7-b3f1-3e664861c8f2
    internal-label: Generative AI
subfeature_v2:
  - id: ad602516-aca3-4247-9ae8-f393d958efa9
    internal-label: Editor
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
topic_v2:
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
    internal-label: Security
  - id: f5c2a4bb-71ca-4d7e-8efd-442250e6ba48
    internal-label: Content reuse
source-git-commit: 5ed0a5191e1852dd65e0461f02d520b195f7cc39
workflow-type: tm+mt
source-wordcount: '615'
ht-degree: 0%
---
# AI助手(Beta)

Adobe Experience Manager Guides中的&#x200B;**AI助手**&#x200B;是一款功能强大的AI驱动工具，旨在通过智能帮助、创作和标记功能提高您的工作效率。 在&#x200B;**Standard**&#x200B;模式下，它将两项强大的AI功能（**创作**&#x200B;和&#x200B;**帮助**）整合到Experience Manager Guides界面中，使您能够更快、更高效地创作内容并访问Experience Manager Guides文档中的信息。 在&#x200B;**代理**&#x200B;模式下，AI Assistant改为提供&#x200B;**智能标记**，允许您通过对话提示窗口请求为内容添加标记推荐，并在一个或多个主题中应用这些推荐。

>[!NOTE]
>
> AI助手功能当前适用于Adobe Experience Manager Guides as a Cloud Service。

## AI助手模式

>[!NOTE]
>
>要为环境以代理模式启用AI助手，请联系客户成功团队。

AI助手有两种模式可用：**代理**&#x200B;和&#x200B;**标准**。 管理员可以在&#x200B;**Workspace设置**&#x200B;中&#x200B;**常规**&#x200B;选项卡的&#x200B;**AI助手**&#x200B;部分中选择这两种模式。 在编辑器中，AI助手面板在两个模式中保持相同，但其中可用的功能有所不同：

* **代理**&#x200B;模式使用Adobe CX Enterprise Coworker的&#x200B;**智能标记**&#x200B;技能来分析您的内容并根据您组织的分类推荐相关标记。
* **标准**&#x200B;模式通过AI助手面板中的&#x200B;**帮助**&#x200B;和&#x200B;**创作**&#x200B;选项卡提供现有的AI助手体验。

## 代理模式

### 智能标记

代理模式中的AI助手可通过对话提示窗口更快速、更轻松地标记内容。 使用Adobe CX Enterprise Coworker的代理智能标记技能，AI Assistant会在您请求内容时为其推荐相关标记。 您可以通过查看建议的标记并选择将它们应用于一个或多个主题（包括映射中的多个主题）来保持控制。

有关更多详细信息，请查看[开始使用Agentic AI助手](./ai-assistant-agentic.md)。

![ai助手智能标记](./images/suggested-prompts.png)

## 标准模式

### 创作

当在&#x200B;**标准**&#x200B;模式下配置AI助手时，AI助手中的&#x200B;**创作**&#x200B;功能可使您的创作过程更智能和更快。 它提供了多种功能，例如生成内容重用的智能建议、翻译内容、提高内容质量等，所有这些都基于您选择的内容。 此功能增强了总体创作体验和作者的工作效率。

有关详细信息，请查看[创作](./ai-assistant-right-panel.md)。

![ai助手](./images/ai-assistant-panel.png)

### 帮助

当在&#x200B;**标准**&#x200B;模式下配置AI助手时，**帮助**&#x200B;功能可提供基于聊天的直观体验，帮助您了解Experience Manager Guides、排查问题并查找Adobe Experience Manager Guides文档中的信息。 您可以使用&#x200B;**帮助**&#x200B;功能快速查找与您的查询相关的答案，而不是搜索用户指南和参考文档。 这有助于节省时间，并让您能够专注于内容创建，从而提高工作效率和效率。

有关详细信息，请查看[帮助](./ai-based-smart-help.md)。


![智能帮助面板](images/smart-help-panel.png)

## 在标准模式下开始使用AI助手

当您首次在标准模式下使用&#x200B;**AI Assistant**&#x200B;时，系统会提示您先提交同意，然后再使用Experience Manager Guides Generative AI功能。

执行以下步骤以启动AI助手：

1. 登录Experience Manager Guides。
1. 在主页上，从顶部选择&#x200B;**AI助手**。 确保管理员已在所需模式下启用AI助手功能。

AI助手显示关键功能、用户指南链接和&#x200B;**入门**&#x200B;按钮。

![智能帮助面板](images/get-started-ai.png)

仔细阅读用户准则，然后选择&#x200B;**开始使用**&#x200B;以启动AI助手。

**相关主题**

[AI Assistant安全常见问题解答](./ai-assistant-faq.md)

[Adobe Experience Manager Guides Generative AI披露](./adobe-generative-ai-disclosures.md)

[配置AI助手以进行智能帮助和创作](../cs-install-guide/conf-smart-suggestions.md)
