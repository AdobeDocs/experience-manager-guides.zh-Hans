---
title: PDF
description: 在AEM Guides中为FrameMakerPDF生成并配置文档输出。
exl-id: df3d3cd8-2aa1-4d82-8756-c3f5555cb904
feature: Publishing FrameMaker Documents
role: User
source-git-commit: 462647f953895f1976af5383124129c3ee869fe9
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 3%

---

# PDF {#id205BB0T20RH}

以下选项可用于PDF输出：

>[!NOTE]
>
> 要打开PDF的输出预设，请单击FrameMaker\（`.fm`或`.book`\）文件，单击“输出预设”，然后单击“PDF输出”选项。

| PDF选项 | 描述 |
|-----------|-----------|
| 输出类型 | 要生成的输出类型。 要生成PDF输出，请选择PDF选项。 |
| 设置名称 | 为您正在创建的PDF输出设置提供一个描述性名称。 例如，您可以指定&#x200B;*内部客户输出*&#x200B;或&#x200B;*最终用户输出*。 |
| **作业设置** |
| 选项 | 选择要用于生成PDF输出的PDF预设。 |
| 生成带标记的PDF | 选择此选项可生成包含有关PDF内容和结构的信息的标记文档。 此信息供屏幕阅读器使用。 |
| 为书籍中的每个文件生成PDF | 如果要为帐簿文件生成输出，请选择此选项，为帐簿中的每个文件生成单独的PDF。 |
| 生成PDF以供仅查看 | 选择此选项可在启用注释功能的情况下生成PDF。 |
| 为所有元素和段落创建命名目标 | 选择此选项可根据元素和段落创建命名目标。 |
| **显示设置** |
| 在页面上打开文档 | 指定打开PDF时应显示的页码。 |
| 初始缩放级别 | 选择文档缩放级别。 |
| 注册标记 | 要打印具有裁切标记和注册标记的文档，请从“注册标记”下拉列表中选择一个选项。 |
| 页面宽度和页面高度 | 指定页面的宽度和高度。 |
| 页面范围 | 选择您要发布帐簿中的所有页面还是某个范围的页面。 如果选择“范围”，则必须指定“自”和“至”页面范围。 |
| 将CYMK转换为RGB | 选择此选项可将CYMK颜色转换为所生成PDF中的RGB。 |
| 生成PDF书签 | 创建包含书签的易访问PDF。 |
| 目标路径 | AEM存储库中存储PDF输出的路径。 |
| 运行Post生成工作流 | 选择此选项后，将显示一个新的Post生成工作流下拉列表，其中包含在AEM中配置的所有工作流。 必须选择要在输出生成工作流完成后执行的工作流。 |

**父主题：**[&#x200B;生成FrameMaker文档的输出](fm-output-generatation.md)
