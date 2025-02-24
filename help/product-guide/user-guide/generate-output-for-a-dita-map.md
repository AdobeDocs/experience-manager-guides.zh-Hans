---
title: 生成输出
description: 从AEM Guides中的映射控制台和映射仪表板生成DITA映射的输出。
exl-id: d6cbd44c-e74c-4192-bcc4-fb7752c59508
feature: Publishing
role: User
source-git-commit: f6ff978305d9a1587366acbe96d274408bf457f4
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%

---

# 生成输出

有两种方法可为DITA映射生成输出：

- [从映射控制台生成DITA映射的输出](#generate-output-for-a-dita-map-from-the-map-console)
- [从映射仪表板生成DITA映射的输出](#generate-output-for-a-dita-map-from-the-map-dashboard)

## 从映射控制台生成DITA映射的输出

执行以下步骤以使用Map控制台生成DITA映射的输出：

1. [在映射控制台](./open-files-map-console.md)中打开映射文件。
2. 显示DITA映射控制台，其中包含&#x200B;**输出预设**&#x200B;的列表可用于生成输出。

3. 打开要用于生成输出的预设，然后选择&#x200B;**生成输出**&#x200B;以启动生成过程。

   <img src="images/generate-output-pdf.png" alt="“元数据”选项卡" width="600">

   或者，将鼠标悬停在预设上，然后从预设上下文菜单中选择&#x200B;**生成**。


   <img src="images/generate-preset-map-console.png" alt="“元数据”选项卡" width="600">

输出生成完成后，选择&#x200B;**查看输出**&#x200B;以查看输出。

屏幕右下角显示&#x200B;**成功**&#x200B;对话框。

如果输出不成功，则会显示以下错误消息。

<img src="images/error-log.png" alt="错误日志" width="250">

要查看错误日志，请选择&#x200B;**消除**，将鼠标悬停在所选的预设选项卡上，然后从预设上下文菜单中选择&#x200B;**查看日志**。

## 从映射仪表板生成DITA映射的输出

执行以下步骤以使用“映射”仪表板生成DITA映射的输出：

1. 在Assets UI中，导航到要发布的DITA映射文件并将其选定。

   此时将显示DITA映射控制台，其中包含可用于生成输出的输出预设列表。

1. 选择一个或多个要用于生成输出的输出预设。

   ![](images/generate-multiple-outputs-uuid.png){width="800" align="left"}

1. 选择&#x200B;**生成**&#x200B;图标以启动输出生成进程。


您可以在&#x200B;**输出**&#x200B;选项卡中查看输出生成请求的当前状态。 有关详细信息，请查看[查看输出生成任务](./generate-output-manage-process.md#view-the-status-of-the-output-generation-task)的状态。

>[!IMPORTANT]
>
> 如果预设的输出生成过程处于队列中或正在进行中，则无法为同一预设启动另一个输出生成任务。

您还可以从“映射”控制台为一个或多个主题或整个DITA映射生成AEM Sites输出。 有关详细信息，请查看[生成知识库输出](web-editor-article-publishing.md#id218CK0U019I)。




**父主题：**[&#x200B;输出生成](generate-output.md)
