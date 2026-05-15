---
title: 在从AEM Guides生成的AEM Sites页面中启用上下文内容变量(CCVAR)
description: 在从AEM Guides生成的AEM Sites页面中使用上下文内容变量(CCVAR)
feature: Web Editor
role: User, Admin
exl-id: f9adbb3f-6c1c-4d6f-b55d-1fb45acca91a
TQID: https://experienceleague.adobe.com/ehW4uJQaj3XqejwquxVwFo4vFx6q7qCsVIm6MowolZE
product_v2: id: fae5e35a-80c9-4b94-9352-1a060a6aab1did: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2: id: a3bd6397-2eb2-4908-a61c-226e26855dcaid: cb8c6a2a-3c38-4e40-867c-756f8c36bb0e
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
source-git-commit: 8ed5c9cb07c56b84b36ef56a55af8738989a6d3f
workflow-type: tm+mt
source-wordcount: 497
ht-degree: 2%

---

# 在从AEM Guides生成的AEM Sites页面中启用上下文内容变量(CCVAR)

上下文内容变量(CCVAR)是一种ACS Commons功能，它允许作者直接在其创作的文本中使用动态内容变量。 虽然CCVAR在AEM Sites中经常使用，但本文介绍如何通过使用在&#x200B;**AEM Guides** *中创作的内容生成的页面，主要通过使用DITA映射*&#x200B;中定义的关键字来实现类似功能。


## 什么是上下文内容变量(CCVAR)？

CCVAR允许作者将动态变量插入其内容，这些变量在运行时根据上下文解析。 例如，像`((page_properties.pageTitle))`这样的变量可以在内容呈现期间动态提取页面标题。


## 如何在从AEM Guides生成的AEM Sites页面中启用CCVAR？

考虑到AEM Guides被用作所有内容（包括AEM Sites、PDF或HTML5）的源，要在从AEM Guides生成的页面上启用CCVAR，您需要使用关键字来定义CCVAR名称。 要在指南中执行此操作，请使用`<keydef>`元素在DITA映射中定义&#x200B;**关键字**。 这些关键字可以对应于动态值（或CCVAR名称），从而允许您在DITA主题中引用它们。


## 先决条件

在继续操作之前，请确保满足以下先决条件：

1. **已安装AEM ACS Commons**：
   - 确保您的AEM实例上安装了&#x200B;**ACS AEM Commons**。 使用CCVAR时需要具备此权限。

2. **上下文内容变量配置**：
   - 使用[官方文档](https://adobe-consulting-services.github.io/acs-aem-commons/features/contextual-content-variables/index.html)在AEM中完成&#x200B;**上下文内容变量**&#x200B;的设置。 这包括：
      - 正在启用&#x200B;**属性聚合**。
      - 正在配置&#x200B;**HTML重写**（如果使用HTML输出）。
      - 正在配置&#x200B;**JSON重写**（如果使用JSON输出）。



## 在AEM Guides中启用CCVAR的步骤

### &#x200B;1. 在DITA映射中定义关键字

- 在AEM Guides中，使用DITA映射中的`<keydef>`元素定义关键字，以使其与CCVAR相对应。
- 例如：

```xml
  <keydef keys="product">
    <topicmeta>
      <keywords>
        <keyword>((page_properties.pageTitle))</keyword>
      </keywords>
    </topicmeta>
  </keydef>
```

- `keys`属性（在此示例中为`product`）将用于在DITA主题中引用此变量。


## &#x200B;2. 在DITA主题中使用关键字

- 在主题中，无论在何处使用CCVar，都使用关键字。
- 例如：

```xml
  <p>This is the title of the product: <keyword keyref="product"/> </p>
```

- `keyref`属性指向`<keydef>`元素（`product`，本例中为）中定义的`keys`值。
- 在输出生成期间，关键字将被相应的CCVar值替换。


## &#x200B;3. 生成输出

- 生成AEM Sites的输出时，关键词引用将被解析为相应的动态值。
- 例如：
   - 如果`((page_properties.pageTitle))`解析为`My Product`，则将显示输出：

```xml
   This is the title of the product: My Product.
```


## 示例用例

假设您要动态地将页面的语言插入到DITA主题中。 下面介绍了如何实现此目标：

**在DITA映射中定义关键字**：

```xml
   <keydef keys="pageLanguage">
     <topicmeta>
       <keywords>
         <keyword>((inherited_page_properties.jcr:language))</keyword>
       </keywords>
     </topicmeta>
   </keydef>
```

**引用DITA主题中的关键字**：

```xml
   <p>The title of this page is: <keyword keyref="pageLanguage"/>.</p>
```

**生成的输出**：

如果`((inherited_page_properties.jcr:language))`解析为`en`，则将显示输出：

```
     The language of this page is: en.
```


### 资源

有关&#x200B;**上下文内容变量**&#x200B;的更多详细信息，请参阅官方文档：\
[AEM Commons中的上下文内容变量](https://adobe-consulting-services.github.io/acs-aem-commons/features/contextual-content-variables/index.html)
