---
title: 扩展存储库简介
description: AEM Guides扩展包目录结构
role: User, Admin
exl-id: 99a00b3e-a5c9-41d8-a73d-8690d587277e
TQID: https://experienceleague.adobe.com/REfq-LVYahMiO0avNtO7aOsXeJvkC9Eqo0stpiX1Qgc
product_v2:
  - id: fae5e35a-80c9-4b94-9352-1a060a6aab1d
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
source-git-commit: 8ed5c9cb07c56b84b36ef56a55af8738989a6d3f
workflow-type: tm+mt
source-wordcount: 110
ht-degree: 0%

---

# AEM Guides扩展包目录结构

```text
├── src
│   ├── **/*{js,ts}
│   ├── index.ts
├── dist
│   ├── guides-extension.js
│   ├── guides-extension.umd.cjs
│   ├── build.css
├── node_modules
├── package.json
├── package-lock.json 
└── .gitignore
└── buildCSS.mjs // for creating tailwind classes
└── vite.config.js // config for specifying TS and javascript build options
└── taliwind.config.js // config for tailwind we can add custom config for a design system here
├── jsons // jsons for the aem app
│   ├── context_menus // jsons for the context menus
│   ├── review_app // jsons for the review app
│   ├── xmleditor // jsons for xmleditor
```

## /src

```text
├── src
│   ├── **/*{js,ts}
│   ├── index.ts
```

源目录将包含扩展的typescript或javascript文件。 index.ts文件是扩展名的入口点。 您可以在此处导入所有组件，并将它们导出为单个对象。 扩展将使用此对象来呈现组件。

### /dist

这是最终生成目录。 该文档包含最终JS和CSS，需要将其复制到AEM

```test
├── dist
│   ├── gudies-extension.js // you can either choose es module (this one) or .cjs(other one) file
│   ├── gudies-extension.umd.cjs
│   ├── build.css // this is your tailwind css output
```

## /jsons

此目录包含各种视图的JSON。 您可以使用这些JSON标识目标和自定义视图。

```text
├── jsons // jsons for the aem app
│   ├── context_menus // jsons for the context menus
│   ├── review_app // jsons for the review app
│   ├── xmleditor // jsons for xmleditor
```
