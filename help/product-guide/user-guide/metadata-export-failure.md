---
title: 在Experience Manager Guides中，元数据导出因“字符串太长”异常而失败
description: 了解为什么Assets UI中指南内容的元数据导出可能会失败。
feature: Authoring, Publishing
role: User
product_v2: id: fae5e35a-80c9-4b94-9352-1a060a6aab1did: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2: id: a3bd6397-2eb2-4908-a61c-226e26855dcaid: ab01a588-7dea-43f2-a699-0b3f128465d6
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2: id: c1579802-ddd4-4214-8a91-97b2066abe11
source-git-commit: 1c61df4820e559417410d25c81800637481b040c
workflow-type: tm+mt
source-wordcount: 274
ht-degree: 0%

---

# 为什么文件夹元数据导出失败并出现“字符串太长”异常？

当您从Assets UI [导出文件夹的元数据](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/assets/using/metadata#export-metadata)时，导出作业可能会失败，并出现`String is too long`异常。 当文件夹包含存储非字符串值（如`baselineObj`）的Experience Manager Guides特定属性时，通常会发生这种情况。

**为什么会出现这种情况？**

存储在资产的元数据节点下的某些属性可供Experience Manager Guides内部使用，这些属性包含数据（例如JSON对象），而不是纯字符串值。 在导出文件夹的元数据时，如果要导出的属性&#x200B;**设置为**&#x200B;全部&#x200B;**，导出作业会尝试将每个属性转换为字符串，并且在包含此类数据的属性上失败。**

**如何阻止此行为？**

为避免此故障，默认情况下，**资产元数据导出程序配置**&#x200B;中的元数据导出中排除以下属性：

- `baseline`
- `namedoutputs`
- `conditionpresets`
- `nextgenbaselinestore`

**我仍可以导出这些属性吗？**

是。 如果在导出中需要这些属性中的一个或多个属性，可以编辑&#x200B;**资产元数据导出器配置**&#x200B;并从排除列表中删除它们。

从排除列表中删除属性并不能保证导出成功。 根据基础数据的大小和内容，作业仍可能会失败，并出现相同的异常。 如果在重新启用某个属性后遇到这种情况，请将其添加回排除列表以恢复默认可靠的导出行为。
