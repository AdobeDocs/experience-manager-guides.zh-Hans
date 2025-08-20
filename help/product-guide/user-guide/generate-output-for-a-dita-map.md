---
title: 生成输出
description: 从AEM Guides中的映射控制台和映射仪表板生成DITA映射的输出。
exl-id: d6cbd44c-e74c-4192-bcc4-fb7752c59508
feature: Publishing
role: User
source-git-commit: 358d38ca761661eaee7aeac2cc7d46c53105c543
workflow-type: tm+mt
source-wordcount: '511'
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

   ![](images/generate-multiple-outputs-uuid.png){align="left"}

1. 选择&#x200B;**生成**&#x200B;图标以启动输出生成进程。


您可以在&#x200B;**输出**&#x200B;选项卡中查看输出生成请求的当前状态。 有关详细信息，请查看[查看输出生成任务](./generate-output-manage-process.md#view-the-status-of-the-output-generation-task)的状态。

>[!IMPORTANT]
>
> 如果预设的输出生成过程处于队列中或正在进行中，则无法为同一预设启动另一个输出生成任务。

您还可以从“映射”控制台为一个或多个主题或整个DITA映射生成AEM Sites输出。 有关详细信息，请查看[生成知识库输出](web-editor-article-publishing.md#id218CK0U019I)。

## 使用`chunk`属性合并DITA映射中的不同主题

DITA映射可以包含不同的主题类型，例如引用、概念和任务。 利用`chunk=to-content`属性，可合并这些主题以在AEM Sites上生成单页输出。 但是，要正确发布合并的主题，请确保管理员已在DITA配置文件中配置了正确的XML目录。

系统要求在XML目录中具有关键字`composite`的公共ID才能正确识别并应用相应的DTD规则。
默认情况下，此配置包含在标准XML目录中。 但是，如果您使用的是自定义XML目录，请确保管理员已将此公共ID添加到配置中。 如果没有它，合并的主题可能无法正确发布。

有关如何在自定义DTD/XSD中使用公共ID和系统ID的详细信息，请查看[集成DITA专业化](../cs-install-guide/dita-ot-specialization.md#integrate-dita-specialization-id211mb0e00xa)。



**父主题：**&#x200B;[&#x200B;输出生成](generate-output.md)
