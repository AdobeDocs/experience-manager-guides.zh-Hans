---
title: 安装和设置
description: 安装和使用AEM Guides扩展包
role: User, Admin
exl-id: 0304c8d0-35a8-4712-a9af-36557e3b247f
source-git-commit: b4d6c1c8c2d413bb4137e58391554abf2fb68b8c
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 0%

---

# 安装和使用AEM Guides扩展包

通过扩展，您可以自定义您的AEM Guides应用程序，以更好地满足您的需求。 AEM Guides v4.3及更高版本（内部部署）和2310（云）都支持此扩展框架。

## 要求

此包需要[Git Bash](https://github.com/git-guides/install-git)和npm

## 安装

引导AEM Guides Framework安装的最简单方法是通过cli

```bash
npx @adobe/create-guides-extension
```

## 添加自定义设置代码

1. 为要在`src/`目录中扩展的每个组件添加代码文件。 已经为您添加了一些样例文件。
2. 现在，在位于`src/`目录中的`index.ts`文件中：
   - 导入`.ts`文件，其中包含要在内部版本中添加的自定义项。
   - 将导入添加到`window.extension`
   - 注册自定义组件的`id`并对应的`tcx extensions`导入
   - 请参阅示例`/src/index.ts`

## 构建自定义代码

- 在根目录中运行`npm run build`。 您将在目录`dist/`中获取3个文件：
   - `build.css`
   - `guides-extension.js`
   - `guides-extension.umd.cjs`

![生成输出](./../imgs/build_output.png)

## 将自定义项添加到AEM

- 转到`CRXDE` `crx/de/index.jsp#/`
- 在`apps`文件夹下，创建类型为`cq:ClientLibraryFolder`的新节点

![文件夹结构](./../imgs/crxde_folder_structure.png)

- 在节点的`properties`中，选择`Multi`添加以下属性
名称： `categories`
类型： `String []`
值： `apps.fmdita.review_overrides`，`apps.fmdita.xml_editor.page_overrides`

>[!NOTE]
>
> 对于倒数第二个UI，值为： `apps.fmdita.penultimate.xml_editor.page_overrides`和`apps.fmdita.review_overrides`


![文件夹属性](./../imgs/crxde_folder_properties.png)

- 要添加内置js，请在上面创建的节点中创建一个新文件，例如`tcx1.js`。 此处，添加来自`dist/guides-extension.umd.cjs`或`dist/guides-extension.js`的代码。 现在，创建一个新文件`js.txt`，在此处，我们添加js文件的名称，在本例中为：

```t
#base=.
tcx1.js
```

- 要添加内置css，请在上面创建的节点中创建一个新文件，例如`tcx1.css`。 此处，添加来自`dist/build.css`的代码。 现在，创建一个新文件`css.txt`，在此处，我们将添加css文件的名称，在本例中为：

```t
#base=.
tcx1.css
```

- 执行`shift + refresh`以加载包含自定义设置的应用程序！

## 疑难解答

检查上述所有步骤是否正确执行。
将代码添加到tcx.js后，请确保进行硬刷新（shift +刷新）。
现在打开AEM，右键单击并单击`Inspect`
转到“源”并搜索您的`[node_name].js`（例如： extensions.js）文件。 执行控制/Cmd + D以搜索文件。 如果存在包含从`dist/guides-extension.umd.cjs`或`dist/guides-extension.js`粘贴的JS代码的`.js`文件，则已完成设置
