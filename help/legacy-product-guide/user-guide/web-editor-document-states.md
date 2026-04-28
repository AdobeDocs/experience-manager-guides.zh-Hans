---
title: 文档状态
description: Learn the types of document states in AEM Guides. Know how to change or view the document state and use the document state in DDLC.
feature: Authoring, Features of Web Editor, Document State
role: User
hide: true
exl-id: f8367f84-dd46-4140-8748-c3bda0cf933a
source-git-commit: a70b3ce942b3e69445ad1d7ba6c8f7542e0ff176
workflow-type: tm+mt
source-wordcount: '945'
ht-degree: 0%

---

# 文档状态 {#id1821HC00URO}

To manage the readiness of the documents, AEM Guides provides document state property to indicate the current state of the document. Document states help you quickly find out whether a document is new, in review, or review completed state.

## Types of document states

A document can have any of the document states defined in the Document State profile. For example, a document may have any one of the following Document States:

- Draft - Indicates that the document is created and saved with new changes.
- In-Review - Indicates that a review workflow has been initiated for the document.
- Reviewed - Indicates that the document has been reviewed by the intended users.

These states are set manually or automatically according to the Document States profile settings. For example, if the Document State profile is configured with start state as Draft, and In-Review state is defined for documents under review. Then, when you create a document, the document state is set to *Draft*. If you initiate a review task, then the state of the document is changed to In-Review.

You can also manually change the document state for a single or multiple documents. However, if you choose to change the document state for multiple documents, then the allowed state is determined by the common states that are allowed for the selected documents. For example, let&#39;s say you have defined the document states as Draft, In-Review, Reviewed, and Ready to Publish, in the same order. On document one.dita the state is set to *Draft* and on document two.dita, the state is set to Reviewed. When you select both—one.dita and two.dita, then the allowed document state will be *Ready to Publish*. As two.dita is in *Reviewed* state, the next possible state for two.dita is only *Ready to Publish*, which is shown when both documents are selected.

>[!NOTE]
>
> A document can exist in only one state at a time.

## Change document state

To change the state of a document, perform the following steps:

1. 在Assets UI中，选择要更改其文档状态的一个或多个文档。
1. 在主工具栏中，单击&#x200B;**属性**。
1. 从&#x200B;**文档状态**&#x200B;下拉列表中选择新状态。 您只能选择在文档状态配置文件的“状态转换”部分中允许的那些文档状态。

   >[!NOTE]
   >
   >管理员可以查看所有文档状态，并将文档更改为任何可能的状态。

1. 单击&#x200B;**保存并关闭**。

## 查看文档状态

Assets UI的卡片视图显示当前状态以及相应DITA主题或DITA映射的创建日期和大小。

![](images/document_state.png){width="800" align="left"}

## 在DDLC中使用文档状态

在DDLC中，文档状态在文档生命周期管理中起着重要的作用。 如果您的组织严格遵循DDLC，则根据文档状态来控制文档编辑的机制将是一项基本功能。 例如，您可以允许编辑处于&#x200B;*草稿*&#x200B;或&#x200B;*审核中*&#x200B;状态的文档。 但是，一旦文件经过审查并已准备好发布，就应该有办法防止进一步修改文件。

AEM Guides提供文档审批工作流程，帮助您控制文档开发流程的生命周期。 文档准备发布或达到次末级状态后，您可以将其标记为已批准。 文档获得批准后，AEM Guides会创建该文档的新版本并将其设置为只读。 然后，您可以移动文档以进行发布或创建基线以进行进一步处理。

要从标记为已批准的文档开始新版本，作者必须开始新版本。 启动新版本会再次将文档状态更改为&#x200B;*草稿*。 通过将文档状态更改为&#x200B;*草稿*，文档将再次变为可编辑，您可以继续下一个版本的工作。

要使用文档审批功能，请执行以下步骤：

>[!NOTE]
>
> 审批工作流功能必须由管理员启用。 有关更多详细信息，请参阅安装和配置Adobe Experience Manager Guides as a Cloud Service中的&#x200B;*启用审批工作流程*&#x200B;部分。

1. 在Web编辑器中，打开要标记为批准的文档。

1. 单击&#x200B;**标记为已批准**![](images/mark_approve_icon.svg)&#x200B;图标。

1. 如果文档处于标记为已批准状态，则将显示以下对话框：

   ![](images/mark-approved-correct-state.png){width="300" align="left"}

   如果文档无法标记为已批准，则会显示以下消息：

   ![](images/mark-approved-incorrect-state.png){width="300" align="left"}

1. 如果您的文档已准备好标记为已批准，请从下拉列表中选择一个标签，然后单击&#x200B;**批准**。

   >[!NOTE]
   >
   > 如果管理员尚未配置预定义的标签列表，则会显示一个用于输入标签的自由格式文本字段。

1. 成功将文档标记为已批准后，将以只读模式显示文档的&#x200B;**预览**。

   ![](images/approved-doc-read-only.png){width="650" align="left"}

   >[!NOTE]
   >
   > 在预览模式下，将从工具栏中删除所有编辑选项。 此外，文档的“作者”和“Source”视图也已从顶部导航中删除。


文档一旦标记为已批准，就不再可用于编辑。 如果要将该文档用于下一个版本，则需要将其恢复到&#x200B;*草稿*&#x200B;状态。 要将已批准文档的文档状态更改回&#x200B;*草稿*&#x200B;模式，请执行以下步骤：

1. 在批准的文档中，单击&#x200B;**开始新版本**&#x200B;图标![](images/approved-restart-draft-mode-icon.svg)。

   出现“Start New Release（开始新版本）”消息。

1. 单击&#x200B;**确认**。

   文档的状态将更改为“草稿”，并在Web编辑器中以编辑模式打开文档。


**父主题：**&#x200B;[&#x200B;使用Web编辑器](web-editor.md)
