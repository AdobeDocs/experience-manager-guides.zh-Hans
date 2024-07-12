---
title: 默认包含@navtitle属性
description: 了解如何默认包含@navtitle属性
exl-id: 3def20dc-dd24-4526-ae36-45708249d34a
feature: Web Editor Configuration
role: Admin
level: Experienced
source-git-commit: 0513ecac38840a4cc649758bd1180edff1f8aed1
workflow-type: tm+mt
source-wordcount: '222'
ht-degree: 1%

---

# 默认包含@navtitle属性 {#id2115BC0J0XA}

可以在映射中添加不同类型的引用文件，例如主题、引用、任务、\(sub\)映射等。 这些文件中的大多数都支持`@navtitle`属性。 但是，并没有多少作者能够一致地使用它。 如果要强制在映射的所有引用文件中使用`@navtitle`属性，则可以使用简单的配置执行此操作。

启用后，您在映射中添加的每个引用文件都将自动将`@navtitle`属性添加到其属性中。 `@navtitle`还将获取引用内容的`title`元素的值。

要在引用文件的属性中默认包含`@navtitle`属性，请执行以下步骤：

1. 下载ui\_config.json文件。

   您可以在全局级别或文件夹级别配置文件中进行此更改。 根据要进行此更改的位置，您需要下载相应的ui\_config.json文件。 有关下载ui\_config.json文件的详细信息，请参阅[配置和自定义XML Web编辑器](conf-folder-level.md#id2065G300O5Z)。

1. 搜索`ditaAttributes`定义。

   `ditaAttributes`的默认定义为：

   ```json
   "ditaAttributes": {
   "attributes": [],
   "constraint": false,
   "required": {}
   },
   ```

1. 将`required`参数更改为：

   ```json
   "required": {"navtitle": true}
   ```

1. 保存文件。

1. 将文件上传到相应的配置文件\（全局或文件夹\）。


使用此配置，添加到映射的每个引用文件默认情况下将包含`@navtitle`属性。
