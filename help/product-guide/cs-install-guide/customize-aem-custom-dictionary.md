---
title: 自定义AEM默认词典
description: 了解如何自定义AEM默认词典
exl-id: ecffcd14-6728-4938-a209-5c4b12af6fbb
feature: Web Editor Configuration
role: Admin
level: Experienced
source-git-commit: 0513ecac38840a4cc649758bd1180edff1f8aed1
workflow-type: tm+mt
source-wordcount: '175'
ht-degree: 1%

---

# 自定义AEM默认词典 {#id209SD8000WU}

可以将Web编辑器配置为使用AEM的拼写检查器或浏览器的拼写检查器。 如果您选择使用AEM的拼写检查器，则可以灵活地定义自定义单词列表。 这些自定义单词随后将添加到AEM词典中，并且不会在Web编辑器中标记\（为不正确\）。

执行以下步骤可创建添加到AEM词典中的自定义单词列表：

1. 创建user\_dictionary.txt文件，其中包含要在自定义字典中定义的单词列表。

   >[!NOTE]
   >
   > 必须在新行上定义每个自定义单词。

1. 将文件保存在Cloud Manager Git存储库中的以下位置：

   /apps/fmdita/config

1. 保存文件。

   提交更改并运行Cloud Manager \(CI/CD\)管道以部署配置更改。


作者需要重新启动Web编辑器会话才能在AEM词典中更新自定义词列表。

**父主题：**&#x200B;[&#x200B;自定义Web编辑器](conf-web-editor.md)
