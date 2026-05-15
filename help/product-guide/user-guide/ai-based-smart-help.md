---
title: 用于搜索内容的AI支持的智能帮助
description: 了解如何查看和利用AI支持的Smart Help。
exl-id: 61a15208-9600-4bb8-adc0-feca1a0ffef3
TQID: https://experienceleague.adobe.com/FQZ-2VrO9yjsX7gwcZHC8mb5OU9b0r0WTTJva17oAJ4
product_v2: id: fae5e35a-80c9-4b94-9352-1a060a6aab1did: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2: id: ab01a588-7dea-43f2-a699-0b3f128465d6
subfeature_v2: id: ad602516-aca3-4247-9ae8-f393d958efa9
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2: id: c1579802-ddd4-4214-8a91-97b2066abe11
source-git-commit: 8ed5c9cb07c56b84b36ef56a55af8738989a6d3f
workflow-type: tm+mt
source-wordcount: 621
ht-degree: 0%

---

# 利用AI助手(Beta)中的智能帮助提高效率

Experience Manager Guides提供了基于GenAI的智能帮助，这是一项对话式搜索功能，可帮助您从[Adobe Experience Manager Guides文档](https://experienceleague.adobe.com/en/docs/experience-manager-guides/using/overview)中查找相关内容。

您可以提出问题并以信息性的方式获得答案。 您的查询答案取决于产品文档中的内容。 此搜索完全是对话式的。 您可以询问有关Experience Manager Guides各种功能的问题，也可以选择咨询故障排除查询。 根据响应，您还可以提出进一步的问题。 响应中还包括指向源文档的链接，您可以参阅这些链接以了解详细信息。

例如，您可能想问诸如&#x200B;*如何发布地图？*&#x200B;之类的问题 您将获得响应和相关文章的链接。 然后，如果您想了解如何使用特定方法发布输出，可以询问有关它的问题。 例如，*如何将映射发布到PDF？*

当您在主页、地图控制台或编辑器中打开&#x200B;**AI助手**&#x200B;时，**帮助**&#x200B;面板将在右侧打开。 对于Editor，还会显示“创作”面板，为您提供智能创作功能。 有关详细信息，请查看[智能创作文档的AI助手](./ai-assistant-right-panel.md)

![智能帮助面板](images/smart-help-panel.png){width="300"}

*查看&#x200B;**帮助**面板。*

执行以下步骤以使用“帮助”面板查找相应的内容并解决您的查询：

1. 选择&#x200B;**AI助手**&#x200B;以打开“帮助”面板。

   >[!NOTE]
   >
   > 在[全局或文件夹级别配置文件](../cs-install-guide/conf-folder-level.md#conf-ai-guides-assistant)中，您的管理员需要定义显示在面板中的默认问题。

1. 键入问题可在Experience Manager Guides文档中查找相关内容。 您可以在面板中选择默认问题，或在文本框中键入您的问题。

1. 选择&#x200B;**发送** ![发送图标](images/send-icon.svg)或按&#x200B;**Enter**&#x200B;查看对您问题的答复。

   根据您的问题，您可以查看内容、适用的图像以及指向文章的链接。

   ![智能帮助面板响应](images/smart-help-panel-response.png){width="300"}


   *选择示例问题并查看内容与图像以作响应。*

1. 选择末尾文章的链接，并查看有关问题答案的详细信息。


1. 选择&#x200B;**清除对话** ![清除对话](images/clear-conversation-icon.svg)以从面板中删除对话历史记录。 然后，您可以开始新的对话并查找相关内容。

您可以使用&#x200B;**帮助**&#x200B;功能快速查找与您的查询相关的答案，而不是搜索用户指南和参考文档。 这有助于节省时间，并让您能够专注于内容创建，从而提高工作效率和效率。

## 可用于AI助手帮助响应的选项

当您在&#x200B;**帮助**&#x200B;面板中收到AI助手响应时，可以与其交互或提供反馈以提高其准确性和可靠性。 您的反馈有助于Experience Manager Guides团队增强AI Assistant响应的准确性和相关性，从而随着时间的推移改善其性能。

以下选项可用于与AI助手&#x200B;**帮助**&#x200B;面板提供的响应进行交互或提供反馈：

![](images/ai-assistant-response-options.png){width="300"}

- **复制**：复制响应以在您的文档中使用。
- **Like**：表示响应有用或准确。 选择“赞”图标以赞响应，并使用&#x200B;**告诉我们更多**&#x200B;选项提供详细反馈。
- **不喜欢**：将响应标记为无帮助或不正确。 选择“不喜欢”图标以喜欢响应，并使用&#x200B;**告诉我们更多**&#x200B;选项提供详细反馈。
- **报告**：如果响应包含错误或不准确的内容，则标记该响应以供查看。 选择标志图标以打开&#x200B;**报告结果**&#x200B;对话框。 从可用选项中进行选择，或提供自定义反馈。