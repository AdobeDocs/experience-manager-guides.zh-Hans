---
title: 从翻译中排除主题中的段落
description: 如何从翻译中排除主题中的段落
feature: Translation
role: User
exl-id: 21e41bb4-52f3-4352-92d9-4a60f636de99
TQID: https://experienceleague.adobe.com/IAY5PLpWlHEpMygjmHI-BqS75-VqAU5x1o9mdiu4Aac
product_v2: id: fae5e35a-80c9-4b94-9352-1a060a6aab1did: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2: id: cb8c6a2a-3c38-4e40-867c-756f8c36bb0e
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554
source-git-commit: 8ed5c9cb07c56b84b36ef56a55af8738989a6d3f
workflow-type: tm+mt
source-wordcount: 148
ht-degree: 0%

---

# 如何从翻译中排除主题中的段落

最简单的方法是使用translation=no attribute。

+ 作者可以在他们不想翻译的段落上插入附加属性，如&#x200B;**translation=no**。 需要通知翻译供应商，他们可以在终端进行配置以忽略具有此属性的文本。
+ OOTB机器翻译（带有试用版Microsoft翻译连接器）具有相同的行为。
+ 使用Microsoft翻译进行测试：如果在段落级别定义&#x200B;**translate=no**&#x200B;属性，则不会翻译完整的段落。 此属性可以在任何元素中定义，并且不会翻译该元素中的内容。


以下是一些屏幕截图，进一步解释了这一点：

**Source内容**

![Source内容](assets/source-content.jpg)

**西班牙语翻译的内容**

![西班牙语翻译的内容](assets/trans-content.jpg)
