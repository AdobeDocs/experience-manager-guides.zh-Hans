---
title: 自定义AEM的默认词典
description: 了解如何自定义AEM的默认词典
feature: Web Editor Configuration
role: Admin
level: Experienced
source-git-commit: 6f3f05419f4f5cdd45ab580cdee6fa869f20f01d
workflow-type: tm+mt
source-wordcount: '269'
ht-degree: 2%

---

# 自定义AEM的默认词典 {#id209SD8000WU}

可以将Web编辑器配置为使用AEM的拼写检查器或浏览器的拼写检查器。 如果您选择使用AEM的拼写检查器，则可以灵活地定义自定义单词列表。 这些自定义单词随后将添加到AEM的词典中，并且不会在Web编辑器中标记这些单词\（不正确\）。

以下选项卡提供了创建自定义单词列表的说明，这些列表已根据您的Experience Manager Guides设置添加到AEM的词典中： Cloud Service或内部部署。

>[!BEGINTABS]

>[!TAB Cloud Service]

1. 创建user\_dictionary.txt文件，其中包含要在自定义字典中定义的单词列表。

   >[!NOTE]
   >
   > 必须在新行上定义每个自定义单词。

1. 将文件保存在Cloud Manager Git存储库中的以下位置：

   /apps/fmdita/config

1. 保存文件。

   提交更改并运行Cloud Manager \(CI/CD\)管道以部署配置更改。


作者需要重新启动Web编辑器会话才能在AEM词典中更新自定义词列表。

>[!TAB 内部部署]

1. 登录AEM并打开CRXDE Lite模式。

1. 导航到以下节点：

   /apps/fmdita/config

1. 创建一个名为user\_dictionary.txt的新文件。

1. 打开文件，并添加要在自定义词典中定义的单词列表。

   以下屏幕截图显示了添加到user\_dictionary.txt文件中的自定义单词列表：

   ![](assets/custom-words-list-dictionary.png){width="650" align="left"}

1. 保存并关闭该文件。


作者需要重新启动Web编辑器会话才能在AEM词典中更新自定义词列表。

>[!ENDTABS]

**父主题：**[&#x200B;自定义Web编辑器](customize-overview.md)
