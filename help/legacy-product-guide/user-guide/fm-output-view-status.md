---
title: 查看输出生成任务的状态
description: 查看FrameMaker文档的输出生成队列。 了解如何查看输出生成任务的状态。
feature: Publishing FrameMaker Documents
role: User
hide: true
exl-id: bf5a4365-0183-43d5-a39a-b9eb8a34b27d
TQID: https://experienceleague.adobe.com/FP5RxNtyWcdS-xpw2Atttt3x6DHx73Ljv-Ym91IxY5s
product_v2: id: fae5e35a-80c9-4b94-9352-1a060a6aab1did: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2: id: a3bd6397-2eb2-4908-a61c-226e26855dcaid: d90290ec-3e61-4ebd-8649-bcafe0836803
subfeature_v2: id: bf79f6d3-0ad0-4d82-99e4-42ce98324d60id: fd6cc9e1-e5e5-494e-b7b1-a32f2d6cd7c9
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554
source-git-commit: 2e0c04c623ad0fc59d962c3b7c9f2c82d4ff70e0
workflow-type: tm+mt
source-wordcount: 245
ht-degree: 0%

---

# 查看输出生成任务的状态 {#viewing_output_history}

启动FrameMaker文档的输出生成任务后，AEM Guides会将此任务发送到输出生成队列。 此队列将实时更新，显示队列中每个输出生成任务的状态。

执行以下步骤以查看输出生成队列：

1. 在Assets UI中，导航到要检查输出生成状态的FrameMaker文档并单击该文档。

1. 单击输出。

   ![](images/output-queued-fm.png){width="800"}

1. “输出”页面分为两个部分：

   - **已排队的输出：**

     列出正在等待生成或正在生成过程中的输出。 您还可以找到用于已排队任务的输出生成设置或预设、类型、启动任务的用户、自任务排队以来的时间以及当前状态。

   - **生成的输出**

     列出已完成的输出任务。 同样，这里显示的信息与已排队输出部分类似，只是输出生成时间不同。

     在此列表中，您可能有已成功执行的任务或失败的任务。 对于已成功完成的任务，发布过程会创建一个日志文件\(logs.txt\)，可通过单击“生成位置”列中的链接访问该文件。


**父主题：**[&#x200B;生成FrameMaker文档的输出](fm-output-generatation.md)

