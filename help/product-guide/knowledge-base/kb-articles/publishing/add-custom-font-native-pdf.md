---
title: 将自定义字体添加到DITA PDF
description: 实现自定义字体集成，以强化本机DITA PDF中所有内容的品牌标识和视觉一致性。
feature: Native PDF Output
author: Pulkit Nagpal(punagpal)
role: User, Admin
exl-id: 151e3b1c-6340-4ff2-84d4-246bc4b68065
TQID: https://experienceleague.adobe.com/xqr9eYA2XTcyXL8X4aS-Wu2-FmU8-aCWDpb-L2BBFqI
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
source-wordcount: 223
ht-degree: 0%

---

# 将自定义字体添加到DITA Native PDF

## 本文涵盖：

添加自定义字体以加强所有内容的品牌标识和视觉一致性。

此过程包括3个步骤：

- [上传自定义字体](#step-1--upload-the-custom-font-to-the-resource-folder-of-your-template)
- [在PDF模板的样式表中进行必要的更改](#step-2--make-necessary-changes-in-pdf-templatess-stylesheet)

- [嵌入使用的字体（可选）](#step-3-optional--embed-used-font-in-pdf)

## 步骤1 ：将自定义字体上传到模板的资源文件夹

![自定义字体上载和导入](../assets/publishing/custom-font1.png)

## 第2步：在PDF模板的样式表中进行必要的更改

![PDF模板样式表](../assets/publishing/custom-font2.png)中的字体

## 步骤3（可选） ：在PDF中嵌入使用的字体

![嵌入到DITA PDF中的自定义字体](../assets/publishing/custom-font3.png)

## 常见问题解答

### 我可以使用Adobe Fonts吗？

> 是，转到fonts.adobe.com并单击“添加到Web项目”。
> 
> 复制导入代码，如`" @import url("https://use.typekit.net/xxxx.css")`；
>
> 将粘贴到内容CSS中，然后在CSS文件中进行所需的更改。

![在DITA PDF中使用Adobe字体](../assets/publishing/custom-font4.png)


### PDF中不显示我的字体

> 双重检查字体名称拼写（最常见的错误）
>
> 如果在打开PDF的系统上无法使用字体，请确保嵌入字体

## 有关任何其他查询，请联系您各自的CSM


## 其他资源：

- [如何在PDF中包含DITA Bookmap的目录](./how-to-include-bookmap-toc-in-pdf-publishing.md)
- [如何在PDF发布中包含目录](./how-to-include-bookmap-toc-in-pdf-publishing.md)
- [关于原生PDF的专家讲座视频](../../expert-sessions/native-pdf-publishing-eamples-part1-june2023.md)
