---
title: SCORM预设配置
description: 在产品培训和学习中了解各种SCORM预设配置
feature: Authoring
role: User
exl-id: b3000708-6120-4725-bea1-0b8e58048948
TQID: https://experienceleague.adobe.com/9WSwgksrX0fahrniOalbizWFXCqcW0QlGAHn707vm-k
product_v2: id: fae5e35a-80c9-4b94-9352-1a060a6aab1did: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2: id: ab01a588-7dea-43f2-a699-0b3f128465d6id: cb8c6a2a-3c38-4e40-867c-756f8c36bb0e
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554
source-git-commit: f7c0b10f032c2584fb6e951da898faaeb4ca7aaf
workflow-type: tm+mt
source-wordcount: 331
ht-degree: 0%

---

# 配置SCORM输出预设

创建预设后，配置SCORM预设设置。 预设配置选项组织在“常规”、“内容”和“发布”选项卡下。

- **常规：**&#x200B;用于指定基本输出设置，例如支持的版本、输出路径、ZIP文件名、输出模板以及与学习者体验相关的其他选项。

  ![](assets/scorm-general-tab-v3.png){width="650"}

  **学习者的体验**

   - **学习者必须按顺序完成内容**：确保学习者按固定顺序完成测验，且不能跳过或跳到问题之间。
   - **学习者必须尝试每个问题才能继续**：要求学习者在提交测试之前尝试所有问题，以防止提交不完整。
   - **随机排列每次尝试的问题顺序**：以不同的顺序显示每次尝试的测验问题，这有助于降低可预测性。
   - **随机选择每次尝试的答案**：在每次尝试时随机选择每个问题的答案，减少根据位置猜测的机会。
   - **在测验报告中使用问题ID**：在测验报告中包含唯一的问题ID，这样更容易跟踪、分析并将结果映射回特定问题。
   - **后期生成工作流**：选择此选项时，将显示一个新的后期生成工作流下拉列表，其中包含配置的所有工作流。

- **内容：**&#x200B;用于指定可用的条件筛选（使用DITAVAL或使用某些条件预设）和变量集。

  ![](assets/scorm-content-tab.png){width="650"}


- **发布到LMS：**&#x200B;使用此设置将您的内容直接发布到Adobe Learning Manager (ALM)。 从&#x200B;**发布服务器**&#x200B;下拉列表中，选择&#x200B;**Adobe Learning Manager**，然后选择以前在Workspace设置中配置的所需&#x200B;**发布配置文件**。 选定的配置文件用于建立连接，并将生成的内容上传到ALM。

  >[!NOTE]
  >
  > 在将内容发布到ALM之前，必须配置Adobe Learning Manager发布配置文件。 有关详细信息，请查看[发布配置文件](../lc-config-guide/lc-folder-profile.md)。

  ![](assets/scorm-publish-lms.png){width="650"}

配置所有更改后，使用SCORM预设页面工具栏右角的&#x200B;**保存**&#x200B;保存对SCORM预设所做的更改。
