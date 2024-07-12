---
title: 图标
description: 图标
role: User, Admin
exl-id: 5ba41c77-7329-49fc-bce5-02682261ea8e
source-git-commit: e40ebf4122decc431d0abb2cdf1794ea704e5496
workflow-type: tm+mt
source-wordcount: '49'
ht-degree: 6%

---

# 图标

要显示图标，我们使用组件“图标”。
JUI中的文本区域组件表示html `<icon/>`。

[Adobe频谱图标](https://spectrum.adobe.com/page/icons/)中可用的图标与我们的应用程序兼容。

```js title="icon.js"
const iconJSON =  {
    "component": "icon", //tells the component name
    "icon": "info", // name of the icon to be used
    "size": "S", // size of the icon
    "title": "Information" // tooltip corresponding to the icon.
},
```

图标也可以添加到按钮中。

呈现的图标将如下所示：

![图标](./imgs/info_icon.png "图标")
