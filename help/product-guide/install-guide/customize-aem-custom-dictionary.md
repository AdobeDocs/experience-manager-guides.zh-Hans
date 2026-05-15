---
title: 自定义AEM的默认词典
description: 了解如何自定义AEM的默认词典
exl-id: 8bfd3ea7-0be8-4e7a-b389-5face043200b
feature: Web Editor Configuration
role: Admin
level: Experienced
TQID: https://experienceleague.adobe.com/q1L3-BdWTGmgtrqjOipnk-39Tw-50NT6R--khdTXhbI
product_v2:
  - id: fae5e35a-80c9-4b94-9352-1a060a6aab1d
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: cb8c6a2a-3c38-4e40-867c-756f8c36bb0e
subfeature_v2:
  - id: b0521e56-a0b2-40b6-bf47-ebc98751f9ba
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
source-git-commit: 8ed5c9cb07c56b84b36ef56a55af8738989a6d3f
workflow-type: tm+mt
source-wordcount: 172
ht-degree: 2%

---

# 自定义AEM的默认词典 {#id209SD8000WU}

可以将Web编辑器配置为使用AEM的拼写检查器或浏览器的拼写检查器。 如果您选择使用AEM的拼写检查器，则可以灵活地定义自定义单词列表。 这些自定义单词随后将添加到AEM的词典中，并且不会在Web编辑器中标记这些单词\（不正确\）。

执行以下步骤可创建添加到AEM词典中的自定义单词列表：

1. 登录AEM并打开CRXDE Lite模式。

1. 导航到以下节点：

   /apps/fmdita/config

1. 创建一个名为user\_dictionary.txt的新文件。

1. 打开文件，并添加要在自定义词典中定义的单词列表。

   以下屏幕截图显示了添加到user\_dictionary.txt文件中的自定义单词列表：

   ![](assets/custom-words-list-dictionary.png){width="650"}

1. 保存并关闭该文件。


作者需要重新启动Web编辑器会话才能在AEM词典中更新自定义词列表。

**父主题：**&#x200B;[&#x200B;自定义Web编辑器](conf-web-editor.md)
