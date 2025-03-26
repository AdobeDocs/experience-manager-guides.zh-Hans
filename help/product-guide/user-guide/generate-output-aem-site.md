---
title: 增量输出生成
description: 了解AEM Sites的增量输出生成如何在AEM Guides中工作。
exl-id: 019d9fbf-2f23-4669-8022-d693be75c1c3
feature: Publishing
role: User
source-git-commit: ac83f613d87547fc7f6a18070545e40ad4963616
workflow-type: tm+mt
source-wordcount: '579'
ht-degree: 0%

---


# 增量输出生成

>[!NOTE]
>
> 增量输出生成仅适用于AEM Sites输出。 此外，您只能从DITA映射或子映射重新生成DITA \(.dita/.xml\)主题。 如果选择DITA映射、子映射、主题组或具有`@processing-role="resource-only"`的主题，则重新生成选项不可用。

在许多情况下，您只会更新DITA映射中的几个主题，并只实时推送这些更新的主题。 为了处理此类情况，Experience Manager Guides允许您创建增量输出。 如果更新了几个主题，则无需重新生成整个DITA映射。 您只能选择已更新的主题并再生它们。

如果您的映射是分块的，并且您更新了该映射中的单个主题，则需要为更新的主题或内容重新生成整个映射以便反映在输出中。 在主题级别不会获得输出重新生成选项，该选项仅在\(chunked\)映射级别可用。 这适用于父映射和所有子映射。

执行以下步骤以重新生成特定主题或一组主题的输出：

>[!IMPORTANT]
>
> 重新生成AEM Sites输出时，将使用文件的当前版本而不是附加的基线创建输出。

## 从映射控制台生成增量输出

执行以下步骤，使用映射控制台为AEM Sites生成增量输出：

1. [在映射控制台](./open-files-map-console.md)中打开DITA映射文件。
1. 选择要为其生成增量输出的AEM Sites预设。
1. 在&#x200B;**主题**&#x200B;选项卡中，选择要发布的主题。

   ![aem sites主题列表](images/aem-presets-topic-list.png) {align="left"}

   >[!NOTE]
   >
   > 在&#x200B;**内容**&#x200B;选项卡中选择基线时，主题列表将显示附加基线中的主题及其版本。<br><br>
   > 仅当映射的结构未发生更改时，才应使用主题列表中的增量发布。 如果地图结构/目录发生变化，则整个地图应发布一次以更新目录。
1. 选择&#x200B;**保存**&#x200B;以保存更改。
1. 选择&#x200B;**生成输出**&#x200B;以生成输出。


## 从地图仪表板生成增量输出

执行以下步骤，使用“映射”功能板为AEM Sites生成增量输出：

1. 在Assets UI中，导航到并选择DITA映射文件。

   此时将显示DITA映射控制台，其中包含可用于生成输出的输出预设列表。

1. 选择&#x200B;**主题**&#x200B;选项卡。

   将显示DITA映射中可用的主题列表。

1. 选择要重新生成的主题。

   >[!NOTE]
   >
   > 如果您向DITA映射中添加了新主题，您将无法从此处生成这些新主题。 必须首先使用DITA映射发布函数发布新添加的主题。

   ![](images/regenerate-topics.png){align="left"}

1. 选择&#x200B;**重新生成**。

   此时会显示&#x200B;**重新生成选定主题**&#x200B;页面。

1. 选择要用于再生所选主题的输出预设。

1. 选择&#x200B;**重新生成**&#x200B;以启动输出生成过程。


>[!IMPORTANT]
>
> 如果重命名主题标题并重新生成主题，则更新的主题标题不会反映在DITA映射目录中。 要更新目录中的主题标题，必须生成整个DITA映射。

您可以在&#x200B;**输出**&#x200B;选项卡中查看输出生成请求的当前状态。 有关详细信息，请查看[查看输出生成任务](#view-the-status-of-the-output-generation-task)的状态。



**父主题：** [了解输出预设](generate-output-understand-presets.md)
