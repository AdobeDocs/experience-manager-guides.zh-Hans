---
title: 向DITAPDF的第一页添加企业品牌
description: 通过整合封面页和章节页来实现公司品牌化，确保在内容顶部明确显示企业身份。
feature: Native PDF Output
author: Pulkit Nagpal(punagpal)
role: User, Admin
source-git-commit: a9f8622dc5a2647bcff32c8895700d5c5933be4a
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 0%

---

# 向DITAPDF的第一页添加企业品牌

## 本文将涵盖：

通过将FrontCover页面与章节页面无缝地合并，实现企业品牌化，确保企业身份突出显示在内容顶部。

- [设置您的内容](#set-up-your-content)
- [在PDF模板中进行必要的更改](#create-necessary-changes-in-pdf-template)

**之前：**

![在修复品牌之前：屏幕快照显示预品牌PDF布局](../assets/publishing/branding-image1.png)
<br>
<br>

**之后：**

![修复品牌后：屏幕快照显示贴有品牌的PDF布局](../assets/publishing/branding-image2.png)

## 设置您的内容

要以PDF格式发布内容，必须创建Ditamap或Bookmap。

示例书图结构：

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

示例Ditamap结构：

```
<map title="My map Title">

  <topicref href="topic1.dita" >
  </topicref>
  <topicref href="topic2.dita">
  </topicref>
  
</map>
```

如果Bookmap包含`<frontmatter>`，将自动生成PDF的FrontCover。


## 在PDF模板中进行必要的更改

在本节中，我们将设置模板。 （您可以使用或复制高科技模板以开始操作。）

### 设置模板：

- 转到您的本机PDF模板。
- 转到FrontCover页面布局并进行编辑。
- 在此，在`data-region="content"`中添加您的品牌推广图像。
- 如果需要，可在章节模板中添加其他必要的更改。
- 现在，根据您的内容执行以下步骤。


#### 如果您使用Ditamap来生成PDF：

发布DITAMAP时，本机PDF提供自动生成FrontCover页面的功能。 可以在本机PDF模板中配置启用或禁用FrontCover页生成的选项。

要合并，请执行以下操作：
- 转到本机PDF模板设置 — >页面布局顺序
- 现在，将FrontCover与下一页（即章节和主题）合并。
  ![将FrontCover与章节合并：屏幕快照显示本机PDF模板设置](../assets/publishing/branding-image3.png)
- 保存模板，为预设选择此模板并发布！


#### 如果您使用Bookmap生成PDF

对于书签图，页面布局顺序由书签图的结构而不是模板的顺序控制。

为了在Bookmap中实现这一点，我们将利用NativePDF的JavaScript功能。

- 在模板的资源文件夹中的JavaScript下添加

```
window.addEventListener('DOMContentLoaded', function () {
    window.pdfLayout.onAfterPagination(function () {
        var frontMatterWrappers = document.querySelectorAll('.rh-front-matter-wrapper');

        frontMatterWrappers.forEach(function(wrapper) {
            var contentDiv = wrapper.querySelector('div[data-region="content"]');
            var chapterBody = document.querySelector('.chapter-body');

            if (contentDiv && chapterBody) {
                chapterBody.insertBefore(contentDiv, chapterBody.firstChild);
            }

            wrapper.remove();
        });
    });
});
```

- 在章节模板中包含此JavaScript 。
  ![在章节模板中包含JavaScript：在页面布局PDF模板中显示条目的屏幕快照](../assets/publishing/branding-image4.png)

- 从预设选项启用JavaScript
  ![启用JavaScript预设设置：屏幕快照显示用于启用JavaScript的预设设置](../assets/publishing/branding-image5.png)

- Publish！

## 附件：

- [下载示例PDF模板包以查看应用的更改。](../assets/publishing/NativePDF_DemoTemplate.zip)
- [下载示例PDF预设包以查看应用的更改。](../assets/publishing/Preset_Package.zip)


## 其他资源：

- [如何在PDF中包含DITA Bookmap的目录](./how-to-include-bookmap-toc-in-pdf-publishing.md)
- [本地PDF专家讲座视频](../../expert-sessions/native-pdf-publishing-eamples-part1-june2023.md)

