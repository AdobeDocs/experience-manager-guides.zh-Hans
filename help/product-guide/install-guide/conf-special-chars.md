---
title: 配置允许的特殊字符
description: 了解如何配置允许的特殊字符
exl-id: 3dd7752e-0836-480a-b1e1-6fa2099d404f
feature: Web Editor Configuration
role: Admin
level: Experienced
TQID: https://experienceleague.adobe.com/vKiBbH1skwiRRU-VETpOk3YCCAm-Lr-Cbh335E-Q7Z8
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
source-wordcount: 211
ht-degree: 0%

---

# 配置允许的特殊字符 {#id20CIL600035}

利用Web编辑器，可插入一些现成的特殊字符。 但是，您可以自定义作者可以插入其文档中的特殊字符列表。 如果自定义特殊字符列表，则它会覆盖默认的特殊字符集。 只有您在配置中添加的特殊字符才可供作者使用。

执行以下步骤以覆盖默认的特殊字符列表：

1. 登录AEM并打开CRXDE Lite模式。

1. 在以下位置创建`symbols.json`文件：

   ```json
   /apps/fmdita/xmleditor/
   ```

1. 在`symbols.json`文件中添加特殊字符定义，如下所示：

   ```json
   {"symbols": [{"label": "Arrows",
      "items": [
      {   "name": "←",   "title": "Left Arrow"   } 
      ,   
      {   "name": "↑",   "title": "Up Arrow"      } 
      ]   
      }   ]   }
   ```


`symbols.json`文件的结构说明如下：

- `"label": "Arrows"`：这会指定特殊字符的类别。 在该代码片段中，定义了名为`"Arrows"`的类别。
- `"items"`：这将定义类别中特殊字符的集合。
- `"name": "←", "title": "Left Arrow"`：这是特殊字符的定义。 它以`"name"`标签开始，该标签不能更改。 名称后跟特殊字符。 `"title"`是作为特殊字符的工具提示显示的特殊字符的名称或标题。

  您可以在一个类别中定义多个特殊字符定义。


**父主题：**&#x200B;[&#x200B;自定义Web编辑器](conf-web-editor.md)
