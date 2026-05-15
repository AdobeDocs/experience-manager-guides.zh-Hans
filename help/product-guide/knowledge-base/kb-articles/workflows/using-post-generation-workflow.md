---
title: 后期生成工作流
description: 后处理工作流概述及示例
exl-id: e19fdc0b-0ec6-46ce-81ed-e9490d12c029
feature: Workflow Configuration
role: User, Admin
TQID: https://experienceleague.adobe.com/GmpUvIwR5aDOIQ4RNUXoeOeQB3MrueRuxpvYBwYev4I
product_v2:
  - id: fae5e35a-80c9-4b94-9352-1a060a6aab1d
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: a3bd6397-2eb2-4908-a61c-226e26855dca
  - id: cb8c6a2a-3c38-4e40-867c-756f8c36bb0e
subfeature_v2:
  - id: b455a250-64c4-4598-b015-7b6b6dc528b1
  - id: fd6cc9e1-e5e5-494e-b7b1-a32f2d6cd7c9
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2:
  - id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dc
source-git-commit: 8ed5c9cb07c56b84b36ef56a55af8738989a6d3f
workflow-type: tm+mt
source-wordcount: 327
ht-degree: 0%

---

# AEM Guides发布 — 帖子生成工作流程

AEM Guides可让您灵活地指定输出后生成工作流程。 您可以对使用AEM Guides生成的输出执行一些后处理任务。
例如，您可能想要在PDF输出中设置某些属性，或者在生成输出后向一组用户发送电子邮件。


## 利用后生成工作流涉及哪些步骤

### 创建工作流进程

创建基于Java或ECMA的工作流进程，以对生成的输出执行操作。 例如，将某些元数据从源复制到生成的内容或处理生成的输出的元数据。
- 我们将以使用ECMA脚本创建此类流程为例（您可以引用附加的包）
- 有关基于Java的工作流进程，请参阅[安装和配置指南](https://helpx.adobe.com/content/dam/help/en/xml-documentation-solution/4-2/Adobe-Experience-Manager-Guides_UUID_Installation-Configuration-Guide_EN.pdf#page=119)的“*自定义输出后生成工作流*”部分


### 创建工作流模型

使用您在上一步中创建的自定义工作流流程，创建一个工作流模型并将该流程步骤添加到其中。
- 您还需要添加强制的流程步骤&quot;*完成帖子生成*&quot;作为工作流的最后一个步骤。

请参阅下面显示的工作流模型示例：

![生成后工作流模型](../assets/workflows/pgwf-workflow-model.png)


### 在地图上使用此后期生成工作流

后生成工作流是一个属性，可在AEM Guides发布机制内的任何输出预设上配置该属性。 示例：

在输出预设上生成![后工作流](../assets/workflows/pgwf-preset-settings.png)


假定已创建选定的模型。


### 测试

现在，您可以使用此预设运行发布并验证流程步骤输出


## 样本

供您参考，您可以使用下面的包并通过包管理器安装它，以测试示例的后生成工作流（*，如上面的屏幕截图中所述*）

[基于ECMA的后生成工作流模型示例](../assets/workflows/sample-pgwf-ecma-test-wfmetadata.zip)
