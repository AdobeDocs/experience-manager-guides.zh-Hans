---
title: 自定义工具栏
description: 了解如何自定义工具栏
exl-id: 14a82c7e-5c07-43a8-bd9e-b221d80f6d05
feature: Web Editor Configuration
role: Admin
level: Experienced
source-git-commit: 5778ed2855287d1010728e689abbe6020ad56574
workflow-type: tm+mt
source-wordcount: '951'
ht-degree: 0%

---

# 自定义工具栏 {#id172FB00L0V6}

默认情况下，Web编辑器附带了任何DITA编辑器所需的最常见编辑功能。 编辑器中提供了插入列表\（编号或项目符号\）类型的元素、交叉引用、内容引用、表格、段落和字符格式等功能。 除了这些基本元素之外，您还可以自定义Web编辑器以插入在创作环境中使用的元素。

>[!NOTE]
>
> 从旧UI迁移到新AEM Guides UI(适用于AEM Guides的2502和5.0版本)时，`ui_config`的更新必须转换为更灵活和模块化的UI配置。 此框架有助于在适用的情况下无缝地采用对editor_toolbar和其他目标构件所做的更改。 有关详细信息，请查看[转换UI配置概述](https://experienceleague.adobe.com/zh-hans/docs/experience-manager-guides-learn/videos/advanced-user-guide/conver-ui-config)。

可通过两种方式自定义Web编辑器的工具栏：

- 向工具栏添加新功能

- 从工具栏中删除任何现有功能


## 在工具栏中添加功能

向Web编辑器添加功能涉及两个主要任务 — 在&#x200B;*ui\_config.json*&#x200B;文件中为该功能添加图标，以及在JavaScript中添加后台功能。

**在工具栏中添加图标**

执行以下步骤以将功能添加到Web编辑器的工具栏：

1. 登录AEM并打开CRXDE Lite模式。

1. 导航到以下位置提供的默认配置文件：

   `/libs/fmdita/clientlibs/clientlibs/xmleditor/ui_config.json`

1. 在以下位置创建默认配置文件的副本：

   `/apps/fmdita/xmleditor/ui_config.json`

1. 导航到`apps`节点中的`ui_config.json`文件并将其打开以进行编辑。

1. 在`ui_config.json`文件中，在工具栏部分中添加新功能的定义。 通常，您可以创建新的工具栏按钮组，并向其添加一个或多个工具栏按钮。 或者，您可以在现有工具栏组中添加新的工具栏按钮。 需要以下详细信息才能创建新的工具栏组：

   - **type：**&#x200B;指定`blockGroup`作为`type`值。 此值表示您正在创建包含一个或多个工具栏组的块组。

   - **extraclass：**&#x200B;用空格分隔的一个或多个类的名称。

   - **项：**&#x200B;在工具栏中指定所有组的定义。 每个组可以包含一个或多个工具栏图标。 若要在工具栏组中定义图标，您需要在`items`中再次定义`type`属性，并将其值设置为`buttonGroup`。 在`extraclass`属性中指定一个或多个类名。 在`label`属性中指定功能名称。 `ui_config.json`文件中的以下代码片段显示了主工具栏块的定义，后跟`buttonGroup`定义：

     ```json
     "toolbar": {    
       "type": "blockGroup",    
       "extraclass": 
       "toolbar operations",    
         "items": [      
           {        
             "type": "buttonGroup",        
             "extraclass": "left-controls",        
             "label": "Left Controls",        
             "items": [
     ```

     在`items`集合中，您需要指定一个或多个工具栏图标的定义。
您需要定义以下属性以添加工具栏图标：

   - **类型：**&#x200B;指定`button`作为`type`值。 此值表示您正在添加工具栏按钮。

   - **图标：**&#x200B;指定要在工具栏中使用的Coral图标的名称。

   - **变体：**&#x200B;指定`quiet`作为`variant`值。

   - **标题：**&#x200B;指定图标的工具提示。

   - **单击：**&#x200B;在JavaScript文件中指定为该功能定义的命令名称。 如果命令需要输入参数，则将命令名称指定为：

     ```JavaScript
     "on-click": {"name": "AUTHOR_INSERT_ELEMENT", "args": "simpletable"}
     ```

   - **显示或隐藏：**&#x200B;如果要定义`show`属性，请指定图标的显示模式。 可能的值为 — `@isAuthorMode`、`@isSourceMode`、`@isPreviewMode`、`true` \（在所有模式下显示\）或`false` \（在所有模式下隐藏\）。

   您还可以定义`hide`属性，以代替`show`。 可能的值与`show`属性中的值相同，唯一的区别是指定的模式不显示图标。

1. 创建一个&#x200B;*clientlib*&#x200B;文件夹并将您的JavaScript添加到此文件夹中。

1. 通过将&#x200B;*apps.fmdita.xml\_editor.page\_overrides*&#x200B;的值指定给&#x200B;*clientlib*&#x200B;文件夹来更新其类别属性。

1. 保存&#x200B;*ui\_config.json*&#x200B;文件并重新加载Web编辑器。


**JavaScript代码示例**

本节提供两个JavaScript代码示例，可帮助您开始添加自定义功能。 以下示例显示了当用户单击工具栏中的“显示版本”图标时AEM Guides的版本号。

将以下代码添加到JavaScript文件：

```JavaScript
/**
* This file contains an example to show AEM Guides version 
* number when a user clicks on the Show Version icon in the toolbar. 
* Step 1. Create a clientlib folder and add save a file with your *JavaScript code into this folder. A code sample is shared below.
* Step 2: Update the categories property of the clientlib folder by *assigning it the value of 
* "apps.fmdita.xml_editor.page_overrides".
* Step 3: Add the feature in the ui_config.json file as shown after the *sample code. Save the ui_config.json file and reload the Web Editor
 */

(function (window) {
  "use strict";

  window.addEventListener('DOMContentLoaded', function () {
    fmxml.ready(function () {
      fmxml.eventHandler.subscribe({
        key: 'user.alert',
        next: function next() {
          alert("AEM Guides version x.x");
        }
      });
    });
  });
})(window);
```

在ui\_config.json文件中添加以下功能：

```json
 {
      "type": "button",
      "icon": "alert",
      "title": "About AEM Guides",
      "variant": "quiet",

  "show": "true",
      "on-click": "user.alert"
  } 
```

以下示例说明如何将活动文件的文档状态更改为“正在审阅”。

```JavaScript
/**
* This file contains an example to set the document state of an active *open documen to "In-Review". 
* Step 1. Create a clientlib folder and add save a file with your *JavaScript code into this folder. A code sample is shared below.
* Step 2: Update the categories property of the clientlib folder by *assigning it the value of 
* "apps.fmdita.xml_editor.page_overrides".
* Step 3: Add the feature in the ui_config.json file as shown after the *sample code. Save the ui_config.json file and reload the Web Editor
 */

(function (window) {
  "use strict";

  //Wait for the page has been completely loaded 

  window.addEventListener('DOMContentLoaded', function () {

    //Wait for the xml editor to start
    fmxml.ready(function () {

      //Subscribe to 'user.docstate.to.in-review' event
      fmxml.eventHandler.subscribe({
        key: 'user.docstate.to.in-review',
        next: function next() {
          var docstate = "In-Review"; // New docstate name
          var filePath = fmxml.curEditor.filePath; 
// Get the file path of active open file
          if (filePath) {
            //Call API to change the doc state
            $.ajax({
              type: 'POST',
              url: '/bin/fmdita/states',
              data: {
                paths: filePath,
                operation: "setdocstates",
                docstate: docstate
              }
            }).fail(function (xhr, textStatus, errorThrown) {
              console.error("Cannot update docstate to " + docstate);
            }).success(function (data) {
              console.log('docstate updated to ' + docstate);
            });
          }
        }
      });
    });
  });
})(window);
```

在ui\_config.json文件中添加以下功能：

```json
 {
      "type": "button",
      "icon": "actions",
      "title": "Change document state to In-Review",
      "variant": "quiet",
      "show": "true",
      "on-click": "user.docstate.to.in-review"
    } 
```

## 从工具栏中删除功能

有时，您可能不希望提供Web编辑器中当前可用的所有功能，在这种情况下，您可以从Web编辑器的工具栏中删除不需要的功能。

执行以下步骤，从工具栏中删除任何不需要的功能：

1. 登录AEM并打开CRXDE Lite模式。

1. 导航到以下位置提供的默认配置文件：。

   `/libs/fmdita/clientlibs/clientlibs/xmleditor/ui_config.json`

1. 在以下位置创建默认配置文件的副本：

   `/apps/fmdita/xmleditor/ui_config.json`

1. 导航到`apps`节点中的`ui_config.json`文件并将其打开以进行编辑。
`ui_config.json`文件包含三个部分：

- **工具栏：**   本节包含编辑器工具栏中所有可用功能的定义，如插入/删除编号列表、\(file\)关闭、保存、注释等。

- **快捷键：**   本节包含指定给编辑器中特定功能的键盘快捷键的定义。

- **模板：**   本节包含可在文档中使用的DITA元素的预定义结构。 默认情况下，“模板”部分包含段落、简单表格、表格和正文元素的模板定义。 通过为所需元素添加有效的XML结构，可以为任何元素创建模板定义。 例如，如果要向列表中添加一个包含每个新`li`元素的`p`元素，则可以在模板部分的末尾添加以下代码以实现此目的：

```HTML
"li": "<li><p></p></li>"
```

1. 从工具栏部分中，删除不想向用户公开的功能条目。

1. 保存&#x200B;*ui\_config.json*&#x200B;文件并重新加载Web编辑器。


**父主题：**&#x200B;[&#x200B;自定义Web编辑器](conf-web-editor.md)
