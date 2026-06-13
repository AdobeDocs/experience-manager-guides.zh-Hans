---
title: 将企业品牌添加到DITA PDF的第一页
description: 通过整合封面页和章节页来实现公司品牌化，确保在内容顶部明确显示企业身份。
feature: Native PDF Output
author: Pulkit Nagpal(punagpal)
role: User, Admin
exl-id: ab452529-3c7f-4057-a0f6-212b9f52a99d
TQID: https://experienceleague.adobe.com/6CGRK2QWFZ6nIXmIAQZy3lX7t4KYP2-HeyqlVW2-7eE
product_v2:
  - id: fae5e35a-80c9-4b94-9352-1a060a6aab1d
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: a3bd6397-2eb2-4908-a61c-226e26855dca
subfeature_v2:
  - id: d6596f3f-92a7-43ec-b444-237db6adad05
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
source-git-commit: 8ed5c9cb07c56b84b36ef56a55af8738989a6d3f
workflow-type: tm+mt
source-wordcount: 422
ht-degree: 0%

---

# 将企业品牌添加到DITA PDF的第一页

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

如果Bookmap包含`<frontmatter>`，则会自动生成PDF的FrontCover。


## 在PDF模板中进行必要的更改

在本节中，我们将设置模板。 （您可以使用或复制高科技模板以开始操作。）

### 设置模板：

- 转到您的本机PDF模板。
- 转到FrontCover页面布局并进行编辑。
- 在此，在`data-region="content"`中添加您的品牌推广图像。
- 如果需要，可在章节模板中添加其他必要的更改。
- 现在，根据您的内容执行以下步骤。


#### 如果您使用Ditamap来生成PDF ：

发布DITAMAP时，本机PDF提供自动生成FrontCover页面的功能。 可以在本机PDF模板中配置启用或禁用FrontCover页面生成的选项。

要合并，请执行以下操作：
- 转到原生PDF模板设置 — >页面布局顺序
- 现在，将FrontCover与下一页（即章节和主题）合并。
  ![将FrontCover与章节合并：屏幕快照显示原生PDF模板设置](../assets/publishing/branding-image3.png)
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
  ![在章节模板中包含JavaScript：屏幕快照显示页面布局PDF模板中的条目](../assets/publishing/branding-image4.png)

- 从预设选项启用JavaScript
  ![启用JavaScript预设设置：屏幕快照显示用于启用JavaScript的预设设置](../assets/publishing/branding-image5.png)

- 发布！

## 附件：

- [下载示例PDF模板包以查看应用的更改。](../assets/publishing/NativePDF_DemoTemplate.zip)
- [下载示例的PDF预设包以查看应用的更改。](../assets/publishing/Preset_Package.zip)


## 其他资源：

- [如何在PDF中包含DITA书签映射的目录](./how-to-include-bookmap-toc-in-pdf-publishing.md)
- [原生PDF专家讲座视频](../../expert-sessions/native-pdf-publishing-eamples-part1-june2023.md)
