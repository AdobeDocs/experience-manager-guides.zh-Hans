---
title: 配置允许的特殊字符
description: 了解如何配置允许的特殊字符
feature: Web Editor Configuration
role: Admin
level: Experienced
source-git-commit: 6f3f05419f4f5cdd45ab580cdee6fa869f20f01d
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 0%

---

# 配置允许的特殊字符 {#id20CIL600035}

利用Web编辑器，可插入一些现成的特殊字符。 但是，您可以自定义作者可以插入其文档中的特殊字符列表。 如果自定义特殊字符列表，则它会覆盖默认的特殊字符集。 只有您在配置中添加的特殊字符才可供作者使用。

以下选项卡提供了有关如何根据您的Experience Manager Guides设置覆盖默认特殊字符列表的说明：Cloud Service或内部部署。

>[!BEGINTABS]

>[!TAB Cloud Service]

1. 在Cloud Manager Git存储库中的以下位置创建`symbols.json`文件：

   ```
   /apps/fmdita/xmleditor/
   ```

1. 在`symbols.json`文件中添加特殊字符定义，如下所示：

   ```
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

>[!TAB 内部部署]

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

>[!ENDTABS]

**父主题：**&#x200B;[&#x200B;自定义Web编辑器](customize-overview.md)
