---
title: AI-powered Smart Suggestions to author content
description: Learn how to view and utilize AI-powered smart suggestions in the Web Editor.
hide: true
exl-id: 30c85d46-61ba-486c-979c-1a2ed95f5a32
source-git-commit: a70b3ce942b3e69445ad1d7ba6c8f7542e0ff176
workflow-type: tm+mt
source-wordcount: '687'
ht-degree: 0%

---

# 用于创作内容的AI支持的智能建议

Experience Manager Guides provides the smart suggestions that help you create consistent and accurate content.

While you author content, the **Suggest reusable content** feature in the AI Assistant tool can search using AI and show the existing content that is semantically similar to your content. You can then choose the best matching content you want to include in your current topic as a reference.

This helps you reuse existing content from your documentation repository and create consistent content. For example, you are making a document containing information about **Adobe Firefly**, including a paragraph about **Adobe**. In that case, you can quickly view and add the content reference from another topic, like **Adobe Photoshop**, which includes the same paragraph.
>[!NOTE]
>
> In the [global or folder-level profiles](/help/product-guide/cs-install-guide/conf-folder-level.md#conf-ai-smart-suggestions), your administrator needs to define the files or folders to index for smart suggestions, the minimum number of characters you need to enter to view the suggestions, and the maximum number of suggestions you can view in the list.

Perform the following steps to view the smart suggestions for adding appropriate content references to your topic:


1. Select the content in your topic to view the related suggestions. Ensure that the content&#39;s character length exceeds what your administrator has set in the folder profile for the content suggestions to appear.
1. From the AI Assistant panel, select **Suggest reusable content** ![ai suggest reusable content icon &#x200B;](./images/ai-suggest-reusable-content-icon.svg).

1. Select a tag to view the authoring suggestions for the current tag .  The suggestions to view and add content references from the indexed files are displayed based on the content in the current tag. You can also select multiple tags.


1. Select all tags to view the suggestions based on the content present in the complete document.  The **Suggest reusable content** ![ai suggest reusable content icon &#x200B;](./images/ai-suggest-reusable-content-icon.svg) icon is displayed next to the content where a suitable match is found.



   >[!NOTE]
   >
   > You can only view the suggestions for the current viewport (the content visible on the screen). To view suggestions for any other content in the document, scroll up or down to display it in the viewport, and then select **Suggest reusable content** ![ai suggest reusable content icon &#x200B;](./images/ai-suggest-reusable-content-icon.svg).


1. You can view the smart suggestions in the suggestions panel.  Experience Manager Guides provides suggestions content that is contextually similar or has the same meaning. For example, you can search for the topic that contains the exact version number, like &quot;release version 2023.03.12&quot;. You can also search for &quot;Adobe is headquartered in San Jose, California,&quot; and find similar content like &quot;San Jose has the quarters of many software companies like Adobe.&quot;
1. 选择&#x200B;**内容信息** ![内容信息](images/smart-suggestions-content-info-icon.svg)以查看详细信息。

   ![内容信息面板](images/smart-suggestions-content-information.png){width="300" align="left"}

   *查看有关内容引用的详细信息。*

   1. 包含内容引用的主题的标题显示为超链接。
   1. 包含内容引用的文件的路径。
   1. 引用了内容的引用类型。
   1. 引用主题的DITA文件的名称显示为超链接。
1. 选择&#x200B;**预览** ![预览图标](./images/expand-icon.svg)以将当前内容与建议的内容进行比较。 这有助于您比较差异，并确定您是要为建议的内容添加内容引用并使它保持一致，还是要保留当前内容。

   ![建议可重用内容预览](images/ai-assistant-suggest-reusable-content.png)

   *预览当前内容与建议内容之间的比较。*

1. 单击&#x200B;**接受**&#x200B;在&#x200B;**建议可重用内容**&#x200B;预览中添加建议的内容引用。
1. 您还可以在建议面板中选择&#x200B;**接受**&#x200B;或&#x200B;**消除**&#x200B;以获取相应的建议。


此智能功能非常方便，最大程度地减少了手动内容搜索的工作量，让您能够将更多精力集中在生成新内容上。 它还有助于更好地进行团队协作，并帮助保持由不同作者创建的内容的一致性。

>[!NOTE]
>
>智能建议不会保留当前会话之外的数据。 对于响应，智能建议仅依赖于基于内部数据库中驻留的内容创建的索引。 不使用外部AI工具，确保您的数据保留在系统中。
