---
title: 以审阅者身份完成审阅任务
description: 了解如何在AEM Guides中将任务标记为已完成审阅者。
feature: Reviewing
role: User
exl-id: 99b64fb5-c509-41cf-b091-ba78b90db481
source-git-commit: e38cd858201ea657ce276eb4b358b0d4eff502b2
workflow-type: tm+mt
source-wordcount: '534'
ht-degree: 0%

---

# 以审阅者身份完成审阅任务

>[!IMPORTANT]
>
> 默认情况下，在2508版的Experience Manager Guides as a Cloud Service中启用了本文中描述的新功能。 在迁移之前创建的审阅不会受到影响，并将继续使用之前的工作流。 如果您希望在不进行这些更新的情况下继续使用现有功能，请联系您的客户成功团队以禁用新功能。

作为审阅人，您可以在审阅完所有内容并想要通知作者后，将审阅任务标记为完成。 您还可以在此阶段留下任何最终注释。

执行以下步骤以完成审阅任务：

1. 打开分配给您的审阅任务。
2. 从顶部选择&#x200B;**标记为完成**，如下所示：

   ![](images/review-task-mark-as-done.png){width="350" align="left"}

   显示&#x200B;**完成任务**&#x200B;对话框。
3. 在&#x200B;**完成任务**&#x200B;对话框中，为作者添加最终注释并选择&#x200B;**完成**。

   >[!NOTE]
   >
   > 任务级注释用作摘要或最终注释，与主题审阅期间添加的文本级注释不同。 在此对话框中，您可以概述诸如请求作者处理特定评论并重新发送任务以供审阅之类的后续操作，或者指示审阅已完成。

   例如，作为查看者，您可以添加注释作为作者的跟进操作：

   ![](images/complete-task-dialog-followup.png){width="350" align="left"}

   或者，添加注释以指示任务已完成，如下所示：

   ![](images/complete-task-dialog.png){width="350" align="left"}


您已成功将任务标记为“已完成”，其状态现在设置为&#x200B;**已完成**。 将任务标记为完成后，不允许执行进一步的操作。 通知将发送给审阅任务的作者或发起人，以立即引起他们的注意。 有关如何触发审阅通知的更多详细信息，请查看[了解审阅通知](./review-understanding-review-notifications.md)。

![](images/task-completed-status.png){width="350" align="left"}

根据反馈，如果任务的作者或发起者决定[关闭审核任务](./review-close-review-task.md)，则审核UI上的任务状态将更改为&#x200B;**已关闭**。

![](images/review-status-closed-review-ui.png){width="350" align="left"}

## 查看任务级注释

所有任务级注释都显示在&#x200B;**任务注释**&#x200B;对话框中，该对话框在只读模式下可用。 当您使用最终注释完成审阅任务时，您的输入将记录在此对话框中，以供将来参考。

要从“审阅”UI访问任务级评论，请导航到左侧面板并选择&#x200B;**任务评论**&#x200B;图标。

![](images/task-comments-icon.png){width="350" align="left"}

**任务备注**&#x200B;对话框显示在右侧。

![](images/task-comments-reviewer.png){width="350" align="left"}

对话框中的注释按时间顺序显示，最近的注释显示在最前，最旧的注释显示在最后。 此顺序可帮助您跟踪一段时间内正在进行的对话。

参与审阅任务的所有用户（包括审阅任务的作者或发起者以及其他审阅者）都可以访问&#x200B;**任务注释**&#x200B;对话框。 因此，来自其他审阅人（如果涉及）的注释也可能出现在任务注释对话框中。 这有助于确保在整个审核过程中进行清晰且可跟踪的通信。

在审阅任务级反馈后，作者可以请求重新审阅或关闭审阅任务。 在这两种情况下，审阅过程中捕获的所有注释在&#x200B;**任务注释**&#x200B;对话框中仍可用，以供参考。
