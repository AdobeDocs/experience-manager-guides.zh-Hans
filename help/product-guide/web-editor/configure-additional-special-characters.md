---
title: 在编辑器工具栏中配置其他特殊字符
description: 了解如何在AEM Guides的编辑器中配置其他特殊字符。
feature: Web Editor
role: User
exl-id: 0fbc05a5-a6b0-4f6b-bbc4-8fca03581d90
TQID: 'https://experienceleague.adobe.com/7InE1R4lpkq7cQ6xptqVIyjG4b-2i9klObtxf2y7Cw8'
product_v2:
  - id: fae5e35a-80c9-4b94-9352-1a060a6aab1d
    internal-label: Experience Manager Guides
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
feature_v2:
  - id: cb8c6a2a-3c38-4e40-867c-756f8c36bb0e
    internal-label: Configuration
  - id: ab01a588-7dea-43f2-a699-0b3f128465d6
    internal-label: Authoring
subfeature_v2:
  - id: f89f75b0-cf2e-4e96-aec8-fe8c39cbd0ef
    internal-label: Web Editor
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
source-git-commit: 81a0e7f0736ba4970673dd87a888a4c60d3c1b4e
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 0%
---
# 如何在内部部署的编辑器工具栏中配置其他特殊字符

Web编辑器工具栏中有一个快捷方式选项，让作者可以插入特殊字符。
如下面的屏幕截图所示：

![特殊字符](assets/special-chars.png)


可在此处配置这些字符列表。 如果需要向其中添加更多字符，请执行以下步骤：

+ 登录AEM并打开CRXDE Lite模式。

+ 在以下位置创建symbols.json文件：“/apps/fmdita/xmleditor/”（您可以从 — “/libs/fmdita/clientlibs/clientlibs/xmleditor/symbols.json”位置复制默认值）

+ 在symbols.json文件中添加特殊字符定义，如下所示：

```
{
      "label": "Logical Symbols",
      "items": [
        {
          "name": "≥",
          "title": "Greater-Than or Equal To"
        },
        {
          "name": "≤",
          "title": "Smaller-Than or Equal To"
        }
      ]
}
```

symbols.json文件的结构说明如下：

+ &quot;label&quot;： &quot;Logical Symbols&quot;：它指定特殊字符的类别。 在该代码片段中，定义了名为“逻辑符号”的类别。

+ “项目”：这定义类别中特殊字符的集合。

+ &quot;name&quot;： &quot;≥&quot;， &quot;title&quot;： &quot;Greater-Than or Equal To&quot;：这是特殊字符的定义。 它以“name”标签开头，该标签不得更改。 名称后跟特殊字符。 “标题”是特殊字符的名称或标题，作为该特殊字符的工具提示显示。

您可以在一个类别中定义多个特殊字符定义。

这将在特殊字符对话框中添加另一个类别：

![特殊符号类别](assets/special-char-category.png)

![插入特殊字符](assets/insert-special-char.png)

>[!MORELIKETHIS]
>
>+ [安装和配置指南](https://helpx.adobe.com/content/dam/help/en/xml-documentation-solution/3-6/XML-Documentation-for-Adobe-Experience-Manager_Installation-Configuration-Guide_EN.pdf)
