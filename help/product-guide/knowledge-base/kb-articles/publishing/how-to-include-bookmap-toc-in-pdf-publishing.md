---
title: 使用NativePDF的TOC（目录）发布
description: 使用NativePDF发布Dita书签的目录和其他书签
feature: Native PDF Output
author: Pulkit Nagpal(punagpal)
role: User, Admin
exl-id: c551f0a8-f973-4c5a-bd34-f52890a91342
TQID: https://experienceleague.adobe.com/GyB4TpCF64rEGNgHVPKq4fUCBQsJjqh4jWA0CJC4A-0
product_v2: id: fae5e35a-80c9-4b94-9352-1a060a6aab1did: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2: id: a3bd6397-2eb2-4908-a61c-226e26855dca
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2: id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dc
source-git-commit: 8ed5c9cb07c56b84b36ef56a55af8738989a6d3f
workflow-type: tm+mt
source-wordcount: 322
ht-degree: 0%

---

# 在PDF发布中生成书签映射的目录

## 设置书图

包括`<toc>`元素：
在书签的`<frontmatter>`元素中，找到`<booklists>`元素。  在`<booklists>`中嵌套`<toc>`元素，如下所示：

```
<frontmatter>
  <booklists>
    <toc/>  <figurelist/>
    <tablelist/>
  </booklists>
</frontmatter>
```

DITA规范还允许将TOC和书签放在`<backmatter>`部分中。


```
<backmatter>
    <booklists>
      <toc/>
      <figurelist/>
      <indexlist/>
    </booklists>
  </backmatter>
```

书签的目录结构、前件图表和表表结构、后件索引表结构。

```
<bookmap>
  <title>My Bookmap Title </title>
  <frontmatter>
    <booklists>
      <toc/>
      <figurelist/>
      <tablelist/>
    </booklists>
  </frontmatter>

  <chapter href="chapter1.ditamap">
  <chapter href="chapter2.ditamap">
  </chapter>

  <backmatter>
    <booklists>
      <indexlist/>
    </booklists>
  </backmatter>
</bookmap>
```

目录和书签列表会根据书签映射中定义的结构自动生成。

设置书图后，使用本机PDF生成PDF输出。 它处理书签图结构和引用，包括目录和书签。

## PDF中的TOC设计和其顺序

原生PDF功能提供了一种便捷的方法，可用于定制目录的布局和设计。

您可以通过目录的分页布局和通过layout.css的样式来控制设计。

PDF中的目录和其他书签列表顺序仅基于书签映射的结构。

![目录](../assets/publishing/toc.png)


## 常见问题解答

### 如何在PDF中包含Ditamap的目录

Ditamap本身并不像书签那样直接具有目录(TOC)。 但是，在定义内容结构时，Ditamap起着关键作用，并间接有助于目录生成过程。

如果您要发布Ditamap，则本机PDF提供自动生成目录和书列表的功能，您可以在本机PDF设置中启用/禁用在ditamap上生成目录。

![启用禁用目录](../assets/publishing/pageorder.png)

## 其他资源：

- [原生PDF设计页面布局文档](https://experienceleague.adobe.com/en/docs/experience-manager-guides/using/install-guide/on-prem-ig/output-gen-config/config-native-pdf-publish/design-page-layout)
- [本机PDF Essentials预先录制的Expert讲座](https://experienceleague.adobe.com/en/docs/experience-manager-guides/using/knowledge-base/expert-session/native-pdf-publishing-essentials-feb23)

<br>
<br>

在AEM Guides社区[论坛](https://experienceleaguecommunities.adobe.com/t5/experience-manager-guides/ct-p/aem-xml-documentation)上发布任何查询。



