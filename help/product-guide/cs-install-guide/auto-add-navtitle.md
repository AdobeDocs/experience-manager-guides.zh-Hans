---
title: 默认包含@navtitle属性
description: 了解如何默认包含@navtitle属性
exl-id: 38711c0c-efa8-461a-92e1-ecfcdcdd36d3
feature: Web Editor Configuration
role: Admin
level: Experienced
source-git-commit: a3c7973868549c72e868c05a3fc6ca8bdce9bce3
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 0%

---

# 默认包含@navtitle属性 {#id2115BC0J0XA}

可以在映射中添加不同类型的引用文件，例如主题、引用、任务、\(sub\)映射等。 这些文件中的大多数都支持`@navtitle`属性。 但是，并没有多少作者能够一致地使用它。 如果要强制在映射的所有引用文件中使用`@navtitle`属性，则可以使用简单的配置执行此操作。

启用后，您在映射中添加的每个引用文件都将自动将`@navtitle`属性添加到其属性中。 `@navtitle`还将获取引用内容的`title`元素的值。

要在引用文件的属性中默认包含`@navtitle`属性，请执行以下步骤：

1. 要下载UI配置文件，请以管理员身份登录到Adobe Experience Manager。

1. 单击顶部的Adobe Experience Manager链接，然后选择&#x200B;**工具**。
1. 从工具列表中选择&#x200B;**指南**，然后单击&#x200B;**文件夹配置文件**。
1. 单击&#x200B;**全局配置文件**&#x200B;拼贴。
1. 选择&#x200B;**XML编辑器配置**&#x200B;选项卡，然后单击顶部的&#x200B;**编辑**&#x200B;图标
1. 单击&#x200B;**下载**&#x200B;图标可在本地系统上下载ui\_config.json文件。
1. 您可以在全局级别或文件夹级别配置文件中进行此更改。 根据要进行此更改的位置，您需要下载相应的ui\_config.json文件。 有关下载ui\_config.json文件的详细信息，请参阅[配置和自定义XML Web编辑器](conf-folder-level.md#id2065G300O5Z)。

1. 搜索`ditaAttributes`定义。

   `ditaAttributes`的默认定义为：

   ```
   "ditaAttributes": {
                           "attributes": [],
                           "constraint": false,
                           "required": {}
                           },
   ```

1. 更改`required`参数，如下所示：

   ```
   "required": {"navtitle": true}
   ```

   当设置为`true`时，将启用&#x200B;**刷新导航标题属性**&#x200B;按钮，使其显示在编辑器工具栏中。 当设置为`false`或留空时，按钮在编辑器中保持隐藏状态。
1. 保存文件。

1. 将文件上传到相应的配置文件\（全局或文件夹\）。


使用此配置，添加到映射的每个引用文件默认情况下将包含`@navtitle`属性。



**父主题：**[&#x200B;自定义Web编辑器](conf-web-editor.md)
