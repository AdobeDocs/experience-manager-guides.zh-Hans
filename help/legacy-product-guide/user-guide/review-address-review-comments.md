---
title: 地址审核注释
description: 了解如何在AEM Guides中以作者身份处理审核评论。 了解作者如何编辑、筛选、接受或拒绝文档中的评论。
feature: Reviewing
role: User
hide: true
exl-id: a9551eb0-ad30-424d-b1c8-c079125d8118
source-git-commit: a70b3ce942b3e69445ad1d7ba6c8f7542e0ff176
workflow-type: tm+mt
source-wordcount: '1036'
ht-degree: 0%

---

# 地址审核注释 {#id2056B0X0KBI}


作为作者，您可以使用Web编辑器在主题中处理注释。 根据在“审阅”面板中选择的审阅任务载入注释。 有关更多详细信息，请在[左侧面板](../user-guide/web-editor-features.md#id2051EA0M0HS)部分中查看&#x200B;**审阅**&#x200B;面板![](images/active-review-tasklist-icon.svg)功能说明。

以下各节介绍在Web编辑器中编辑注释的方法。

作者可以在Web编辑器的文档中处理注释。 提供了视觉指示器，用于指示已插入\(text\)、删除还是高亮显示注释。 每个注释条目的顶部还会提及注释的类型。

>[!NOTE]
>
> 处理审阅注释\（对于活动审阅文档\）时，请确保不要在启用了完整标记视图的多个选项卡中打开审阅中主题，也不要在“创作”和“Source”视图模式之间切换。

![](images/comments-page-web-editor_cs.png){width="800" align="left"}

在Web编辑器模式中，右侧面板包含审阅和跟踪的更改图标。 “审阅”面板显示审阅者在您的文档中所做的所有注释。 **跟踪的更改**&#x200B;面板显示文档中所有插入和删除的注释的状态。

- **A**：选择审核任务以查看审核注释。 如果您的主题已在多个审阅任务中共享以供审阅，您将看到这些任务在此下拉列表中列出。

  从列表中选择审阅任务时，您可以查看审阅人在该任务中所做的评论。 您可以在任务中单独处理审阅注释，这意味着对注释的任何更新仅对相应任务的审阅者可见。

- **B：**&#x200B;在&#x200B;**注释**&#x200B;面板中选择&#x200B;**审阅详细信息** ![](images/active-review-info-icon.svg)以查看有关审阅任务的更多信息：

   - **名称**：审核任务的名称。
   - **审阅版本**：显示与所选审阅任务关联的版本。 这有助于跟踪您共享以供审阅的版本
   - **状态**：审核任务的当前状态。

  >[!NOTE]
  >
  > 如果审核任务的根映射与创作根映射不同，则会显示有关该任务的信息，以指示创作根映射与审核根映射不匹配。

- **C**：如果在启动审阅后更新了主题，则单击“将主题还原为审阅版本”图标会将工作副本还原为共享以供审阅的版本。 这样，您就可以更轻松地直接将审阅反馈合并到共享以供审阅的版本中。 在合并反馈后，可将更改保存在还原版本中或创建主题的新修订版本。 如果选择创建主题的新修订版本，则会从共享以供审阅的主题版本创建一个新分支。 例如，如果在当前创作版本为`1.3`时共享了某个主题的`1.2`版本以供审阅，则可以使用此图标切换回版本`1.2`以合并审阅注释。 如果您选择在将更改合并到版本`1.2`之后创建新的修订版本，则会为该主题创建一个版本为`1.2.0`的新分支。

  通常，在合并审阅反馈后，您希望合并来自主题最新版本的更改。 为此，请使用[合并](web-editor-features.md#id205DF04E0HS)功能获取在共享主题以供审阅后所做的所有更新。

- **D**：打开并排视图，以显示该主题的注释版本。 如上面的屏幕快照所示，最左边的部分是可在其中进行更改的主题的最新版本。 下一部分是该主题的注释版本。 在主题中的注释之间导航时，侧视图会更改并显示在其中添加注释的主题版本。 评论面板中的每个评论都链接到此部分中的相应文本。 它有助于您识别注释的文本。 注释按文档中注释文本的顺序显示。

  您可以在侧视图顶部看到版本号。 再次单击此图标将隐藏该主题的注释版本。

- E：直接在主题中导入插入和删除的\（或删除线\）注释。 单击“导入”图标后，所有文本插入和删除都将显示在主题的工作副本中。 现在，可以通过两种方式接受或拒绝评论。

  如果要一次合并一个建议的更改\（插入或删除\），只需右键单击内容中的注释并选择“接受更改”或“拒绝更改”。 根据您的选择，可接受或拒绝评论。 如果接受评论，内容会添加到内容中；如果拒绝，则会从内容中删除。 此外，评论的状态在“审阅”面板中更改。

  ![](images/import-comment-accept-web-editor_cs.png){width="800" align="left"}

  也可使用右侧面板中的审阅功能来接受或拒绝注释。 Clicking on any comment highlights the comment in the document.

  ![](images/changes-tab_cs.png){width="800" align="left"}

  >[!IMPORTANT]
  >
  > The import comments feature works only on those documents that have not changed since they were shared for review. If you have made any change after sending the document for review, you will get an alert to **Force Import** comments into your document. However, doing so will result in loss of all updates that you have made in your document. The **Force Import** alert is also shown if the document is created outside and then shared for review. You can go ahead and import the comments.

  As and when you accept or reject a comment, it is removed from the Tracked Changes list. This also serves as an indicator of how many comments need to be addressed in the document.

- **F**: From the More Options menu, Download all attachments available in the review topic.
- **G**: Search for a text within comments.
- **H**: Accept or reject a comment.

- **I**: Apply a filter on the comments. You can filter to see comments on the basis of Review Type \(all, highlighted, deleted, inserted, or sticky note\), Review Status \(all, accepted, rejected, or none\), Reviewers \(all or specific reviewer\(s\)\), or Versions of topic.


**父主题：**[&#x200B;审阅主题或映射](review.md)
