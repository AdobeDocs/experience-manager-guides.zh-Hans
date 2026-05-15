---
title: 发行说明 |修复了Adobe Experience Manager Guides 2024.4.0版本中的问题
description: 了解Adobe Experience Manager Guides as a Cloud Service 2024.04.0版本中的错误修复。
exl-id: 35351d71-7739-4ad3-a063-67adf64906bf
TQID: https://experienceleague.adobe.com/cHKuFCElWbjxik0EHgoTrtlq2t3I62LQ5zUArzBoMqk
product_v2: id: fae5e35a-80c9-4b94-9352-1a060a6aab1did: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2: id: a3bd6397-2eb2-4908-a61c-226e26855dcaid: ab01a588-7dea-43f2-a699-0b3f128465d6
subfeature_v2: id: ad602516-aca3-4247-9ae8-f393d958efa9id: d6596f3f-92a7-43ec-b444-237db6adad05id: f89f75b0-cf2e-4e96-aec8-fe8c39cbd0efid: fd6cc9e1-e5e5-494e-b7b1-a32f2d6cd7c9
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2: id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dc
source-git-commit: 8ed5c9cb07c56b84b36ef56a55af8738989a6d3f
workflow-type: tm+mt
source-wordcount: 577
ht-degree: 8%

---

# 修复了2024.04.0版本中的问题

本文介绍Adobe Experience Manager Guides as a Cloud Service 2024.04.0版本中修复的各个方面的错误。

有关新功能和增强功能的更多信息，请查看 [2024.04.0 版本中的新增功能](whats-new-2024-04-0.md)。

了解2024.04.0版本](upgrade-instructions-2024-04-0.md)的[升级说明。

## 创作

- **复制**&#x200B;函数无法复制Adobe Experience Manager as a Cloud Service中的空文件夹。 (15353)
- Web编辑器无法上传.pptx文件。 (14837)
- 在Web编辑器中查找文本时，按Enter键光标将返回到搜索文本的第一次出现。 (14820)
- 自动保存会导致多个问题，它会重新定位光标，并需要手动单击文档。 (14253)
- 打开通过全局&#x200B;**查找和替换**&#x200B;找到的文件后，搜索结果被禁用。 (12142)
- 在源视图中，`</conbody>`偶尔会插入不正确的位置。 (11305)
- 在XML编辑器中，工具提示功能无法更新Source字段。 (15847)
- **共享UUID链接**&#x200B;功能不适用于Adobe Experience Manager中的图像。 (15598)
- `<reltable>`和`<fig>`标记中出现重叠文本问题。 (15238)
- **属性**&#x200B;面板中出现闪烁问题。 (15237)
- 删除内容中的字符或单词时，光标在块元素之间跳转。 (15224)
- **属性**&#x200B;面板未显示在Web编辑器的Source视图中。 (14387)
- 在Web编辑器的标记末尾编辑时，会添加不需要的不间断空格。 (11786)
- 在更正DITA文件中的拼写错误时，内容将被删除。 (11610)


## 发布

- 启用&#x200B;**删除孤立站点**&#x200B;选项后，AEM站点输出生成失败。 (15896)
- 将文件添加到映射集合时，编辑功能不起作用。 (15813)
- 在JSON输出中，来自DITA映射或主题的元数据无法传播到JSON输出文件。 (15713)
- 重命名预设时，本机PDF发布失败。 (15662)
- 发布的AEM站点输出中的&#x200B;**sourcePath**&#x200B;属性不正确。 (15502)
- 语言变量选择和自定义在本地PDF输出预设中无法正常工作。 (15399)
- 使用具有大型样式表或布局的模板时，本机PDF生成失败。 (15344)
- 如果`<conref>`与绝对路径一起使用，则已发布输出中的内容无法正确呈现。
- 由于`fmdita rewriter`和`ResourceResolver`之间的冲突，AEM Sites URL缩短无法正常工作。 (14793)
- **processing-role=&quot;resource-only&quot;**、**search=&quot;no&quot;**&#x200B;和&#x200B;**chunk=&quot;to-content&quot;**&#x200B;属性在AEM Sites输出中分别不显示。 (14442)
- 如果在任何文件夹配置文件的文件夹路径中设置了包含2k个映射的文件夹，则应用于输出预设的更改将失败。(14852)

## 管理

- 未关闭的&#x200B;**资源解析器**&#x200B;导致会话计数增加，并且在2023年10月发布的Experience Manager Guides as a Cloud Service中出现PathNotFoundException错误。 (15604)
- 功能标志&#x200B;**fmdita.useapproval**&#x200B;未按预期工作。 (15310)
- 使用Java API创建基线不适用于2023年6月发行的Experience Manager Guides as a Cloud Service。 (14787)
- 上传资产超过500 MB时，`/bin/fmdita/import` API无限期地停留在待处理请求中。 (14743)

## 审阅

- 删除审阅节点会中断在Adobe Experience Manager Guides中打开和查看注释的功能。 (15366)
- 在Web编辑器中，审阅面板加载缓慢。 (14680)

## 翻译

- **接受翻译**&#x200B;无法完成临时文件的翻译。 (14665)
