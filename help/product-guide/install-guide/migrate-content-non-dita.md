---
title: 迁移非DITA内容
description: 了解如何迁移非DITA内容
exl-id: 4597d1be-5426-4eba-8490-e42d0e565427
feature: Migration
role: Admin
level: Experienced
source-git-commit: d3b156b8617cab8cf0702a483aef0fde7889e6a7
workflow-type: tm+mt
source-wordcount: '2351'
ht-degree: 0%

---

# 迁移非DITA内容 {#id181AH0R02HT}

本节将指导您完成将非DITA文档迁移到DITA格式的迁移过程。 AEM Guides提供了从以下源进行的迁移：

- [Microsoft Word](#id1949B040Z5Z)

- [InDesign文档](#id195AD0B0K5Z)

- [XHTML](#id1949B04L0Y4)

- [非结构化FrameMaker文档](#id1949B050VUI)

- [任何其他结构化文档](#id1949B0590YK)


## 迁移Microsoft Word文档 {#id1949B040Z5Z}

AEM Guides允许您将现有Word文档\(`.docx`\)迁移到DITA主题类型文档。 您需要指定输入和输出文件夹位置以及其他参数，文档将被转换为DITA文档。 根据内容的不同，可以有.dita文件和.ditamap文件。

为了能够成功转换Word文档，您的文档应该结构良好。 例如，您的文档应该有一个标题，后跟标题1、标题2，依此类推。 每个标题中都应包含一些内容。 如果您的文档结构不正确，则该过程可能无法按预期运行。

默认情况下，AEM Guides使用[Word到DITA \(Word2DITA\)转换框架](http://www.dita4publishers.org/docs/repo/org.dita4publishers.word2dita/word2dita/word2dita-intro.html)。 此转换依赖于[样式到标记的映射](http://www.dita4publishers.org/docs/repo/org.dita4publishers.word2dita/word2dita/style-to-tag-map-overview.html)配置文件。 要成功使用Word2DITA转换，您必须考虑以下准则来准备Word文档进行转换：

>[!NOTE]
>
> 如果在默认样式到标记的映射配置文件中进行任何更改，则必须更新并使用确认已更新样式映射的准则。

- 确保您的文档以标题开头；此标题已映射到DITA映射标题。 此外，标题后面必须跟一些常规内容。

- 在标题之后，应该有标题1、标题2，依此类推。 每个标题中都必须有一些内容。 标题将转换为新的概念类型主题。 根据文档中的标题级别，生成的主题的层次结构是，例如，标题1位于标题2之前，标题2位于标题3内容之前。

- 文档必须具有至少一个标题类型内容。

- 确保您没有任何分组的图像。 如果文档中包含已分组的图像，请取消所有此类图像的分组。

- 删除所有页眉和页脚。

- 内联样式（如粗体、斜体和下划线）将转换为`b`、`i`和`u`元素。

- 所有已排序和未排序列表都转换为`ol`和`ul`元素。 这也适用于嵌套列表、表格、注释或脚注中的列表。

- 所有超链接都已转换为`xref`。

- 转换文件的文件名基于标题文本，后跟文件编号。 文件编号是基于标题文本在文档中的位置的连续数字。 例如，如果标题文本是“示例标题”，并且是文档中的第10个标题，则此主题的结果文件名将类似于Sample\_Heading\_10.dita。


执行以下步骤，将现有Word文档转换为DITA主题类型文档：

1. 登录AEM并打开CRXDE Lite模式。

1. 导航到以下位置提供的默认配置文件：

   `/libs/fmdita/config/w2d_io.xml`

1. 在`config`节点内创建`apps`文件夹的覆盖节点。

1. 导航到`apps`节点中可用的配置文件：

   `/apps/fmdita/config/w2d_io.xml`

   `w2d_io.xml`文件包含以下可配置参数：

   - 在`inputDir`元素中，指定可用源Word文档的输入文件夹的位置。 例如，如果您的Word文档存储在位于`wordtodita`文件夹中名为`projects`的文件夹中，则将位置指定为： `/content/dam/projects/wordtodita/`

   - 在`outputDir`元素中，指定输出文件夹的位置或保留默认输出位置以保存转换的DITA文档。 如果DAM上不存在指定的输出文件夹，则转换工作流将创建该输出文件夹。

   - 对于`createRev`元素，指定是否创建转换的DITA主题的新版本\(`true`\)\(`false`\)。

   - 在`s2tMap`元素中，指定映射文件的位置，该文件包含Word文档样式到DITA元素的映射。 默认映射存储在位于以下位置的文件中：

     ```XML
     /libs/fmdita/word2dita/word-builtin-styles-style2tagmap.xml
     ```

     >[!NOTE]
     >
     > 有关`word-builtin-styles-style2tagmap.xml`文件的结构以及如何对其进行自定义的更多信息，请参阅[DITA For Publishers用户指南](http://www.dita4publishers.org/docs/repo/org.dita4publishers.word2dita/word2dita/style-to-tag-map-overview.html)中的&#x200B;*样式到标记映射*。

   - 在props2Propagate元素中，指定应传递到DITA映射的属性。 此属性需要将默认元数据（如dc:title、dc:subject、dam:keywords、dam:category）从文档元数据传递到转换的DITA资产。

1. 保存 `w2d_io.xml` 文件。

1. 在`w2d_io.xml`文件中配置所需的参数后，登录到AEM并打开Assets UI。

1. 导航到输入文件夹位置\(`wordtodita`\)。

1. 将源Word文档上传到此文件夹中。 有关在DAM上上传内容的信息，请参阅[上传现有DITA内容](migrate-content-upload-existing-dita-content.md#)。


使用`config` `/config`块，您可以定义一个或多个转换配置块。 将执行转换工作流，并且以DITA主题形式的最终输出保存在`outputDir`元素中指定的位置。

## 迁移Adobe InDesign文档 {#id195AD0B0K5Z}

AEM Guides允许您转换InDesign文档。 与FrameMaker类似，InDesign还允许您创建非结构化和结构化文档。 非结构化文档使用段落和字符样式来格式化内容。 结构化文档使用元素及其相应的属性。

转换过程需要将段落和字符样式格式映射到相关的DITA元素。 同样，对于结构化文档，映射文件将包含具有DITA元素和属性的InDesign元素和属性的一对一映射。

转换过程涉及后端中的以下操作：

- *InDesign标记语言* \(IDML\)文件已解压缩到工作目录中。
- 读取designmap.xml文件以查找各个InDesign故事。
- 所有故事都合并到一个XML实例中，“空”故事将被丢弃。
- 所有嵌入式图形都将导出。
- 将标准结构（如表和图形）预转换为DITA格式。
- 根据映射文件映射到最终输出的样式或结构。
- 创建和验证单个DITA主题和DITA映射文件。
- 删除临时文件。

概括地说，转换过程要求您[准备InDesign文件进行转换](appendix.md#id195DBF0045Z)和[准备映射文件以进行InDesign到DITA的迁移](appendix.md#id194AF0003HT)，然后您需要按照给定的过程运行转换过程。

执行以下步骤，将现有InDesign文档转换为DITA主题类型文档：

1. 登录AEM并打开CRXDE Lite模式。

1. 导航到以下位置提供的默认配置文件：

   `/libs/fmdita/config/idml2dita_io.xml`

1. 若要根据您的要求创建自定义配置，请在`config`节点内创建`apps`文件夹的覆盖节点。

1. 将以下文件或文件夹从`libs`文件夹复制到apps文件夹：

   - `/fmdita/config/idml2dita_io.xml`
   - `/fmdita/idml2dita/config`
   - `/fmdita/idml2dita/xsl`

1. 导航到`apps`节点中可用的配置文件：

   `/apps/fmdita/config/idml2dita_io.xml`

1. 在`idml12dita`文件中添加`idml2dita_io.xml`文件夹中存在的配置的映射。
1. 在`idml2dita_io.xml`文件中添加以下属性：

   ```
   <entry key="idml2DitaConfig">/apps/fmdita/idml2dita/config</entry>
   
   <entry key="idml2DitaXsl">/apps/fmdita/idml2dita/xsl</entry>
   ```

在`idml2dita_io.xml`文件中配置以下参数：

- 在`inputDir`元素中，指定可在其中使用源InDesign文档的输入文件夹的位置。 例如，如果您的InDesign文档存储在`indesigntodita`文件夹中名为`projects`的文件夹中，则将位置指定为： `/content/dam/idmlfiles/indesigntodita/`

- 在`outputDir`元素中，指定输出文件夹的位置或保留默认输出位置以保存转换的DITA文档。 如果DAM上不存在指定的输出文件夹，则转换工作流将创建该输出文件夹。

- 在`mapStyle`元素中，指定映射文件的位置，该文件包含InDesign文档样式到DITA元素的映射。 默认映射存储在位于以下位置的文件中：

```XML
    /stmap.adobeidml.xml
```

>[!NOTE]
>
> 有关`stmap.adobeidml.xml`文件的结构以及如何对其进行自定义的更多信息，请参阅[附录](appendix.md#id194AF0003HT)中的&#x200B;*准备映射文件以用于InDesign到DITA的迁移*&#x200B;部分。

1. 保存 `idml2dita_io.xml` 文件。

1. 在`idml2dita_io.xml`文件中配置所需的参数后，登录到AEM并打开Assets UI。

1. 导航到输入文件夹位置\(`indesigntodita`\)。

1. 将源InDesign文档上传到此文件夹中。 有关在DAM上上传内容的信息，请参阅[上传现有DITA内容](migrate-content-upload-existing-dita-content.md#)。


## 迁移XHTML文档 {#id1949B04L0Y4}

AEM Guides允许您将现有XHTML文档转换为DITA主题类型文档。 您需要指定输入和输出文件夹位置以及其他参数，文档将转换为DITA格式。 可以使用以下两种方法转换结构化HTML文档：

- 将所有文档上载到输入文件夹，或
- 创建包含所有文档以及媒体文件的ZIP文件，并将其上载到输入文件夹中。 这种方法通常用于一组相互链接的HTML文件，这些文件有一个目录\(index.html\)。 index.html文件包含指向集合中所有HTML文件的链接。

无论您是单独上传所有文件，还是以ZIP格式捆绑上传所有文件，转换过程都会在HTML文件与生成的DITA文件之间创建一对一映射。 这基本上意味着为输入文件夹中的每个.html文件创建了一个.dita文件。

在ZIP文件中上传文档时必须考虑以下几点：

- 所有引用的主题都应放在ZIP文件中。

- 所有被引用的介质文件应使用相对链接在主题文件中被引用。

- 创建一个index.html文件，并添加指向要在目录中添加的主题的链接。 此index.html文件用于创建DITA映射文件。 在index.html文件中，还可以创建嵌套主题列表，如以下代码示例中所示：

  ```XML
  <?xml version="1.0" encoding="UTF-8"?>
  <html
  xmlns="http://www.w3.org/1999/xhtml">
      <head>
          <title>Sample Index File</title>
      </head>
      <body>
          <h1>Sample Index</h1>
          <div class="content">
              <ul class="book">
                  <li class="topicref">
                      <a href="Topic1.html">Topic 1</a>
                      <ul class="book">
                          <li class="topicref">
                              <a href="Topic1-1.html">Topic 1.1</a>
                          </li>
                          <li class="topicref">
                              <a href="Topic1-2.html">Topic 1.2</a>
                          </li>
                      </ul>
                  </li>
                  <li class="topicref">
                      <a href="Topic2.html">Topic 2</a>
                  </li>
              </ul>
          </div>
      </body>
  </html>
  ```

  请注意，每个`ul`标记都必须将`class`属性设置为`book`。 同样，必须将每个`li`标记的`class`设置为`topicref`。

- 如果使用内联样式，则在XHTML文件中将内联样式转换为基于CSS的样式类。 然后，使用样式属性映射将这些基于类的样式转换为转换后的DITA文件中的DITA `outputclass`属性。

  从这些DITA文件生成HTML或AEM站点输出时，`outputclass`属性可用于对生成的HTML或AEM站点应用样式类，以匹配源HTML内容。


除了创建ZIP文件的注意事项外，您的XHTML文档还必须结构良好。 例如，您的文档应该有一个&#x200B;*标题*，后面应该有&#x200B;*标题1*、*标题2*，依此类推。 每个标题中都应包含一些内容。 如果您的文档结构不正确，迁移过程可能无法按预期进行。

要将现有XHTML文档转换为DITA主题，请执行以下步骤：

1. 登录AEM并打开CRXDE Lite模式。

1. 导航到以下位置提供的默认配置文件：

   `/libs/fmdita/config/h2d_io.xml`

1. 在`config`节点内创建`apps`文件夹的覆盖节点。

1. 导航到`apps`节点中可用的配置文件：

   `/apps/fmdita/config/h2d_io.xml`

   `h2d_io.xml`文件包含以下可配置参数：

   - 在`inputDir`元素中，指定可用源XHTML文档的输入文件夹的位置。 例如，如果您的XHTML文档存储在`xhtmltodita`文件夹中名为`projects`的文件夹中，则将位置指定为： `/content/dam/projects/xhtmltodita/`

   - 在`outputDir`元素中，指定输出文件夹的位置或保留默认输出位置。 如果DAM上不存在指定的输出文件夹，则转换工作流将创建该输出文件夹。

   - 对于`createRev`元素，指定是否创建转换的DITA主题的新版本\(`true`\)\(`false`\)。

1. 保存 `h2d_io.xml` 文件。

1. 在`h2d_io.xml`文件中配置所需的参数后，登录到AEM并打开Assets UI。

1. *\（可选\）*&#x200B;您还可以将相关链接部分添加到转换后的文档。 要启用此功能，请执行以下步骤：

   >[!NOTE]
   >
   > 默认情况下，转换后的文档中不会创建相关链接部分。

   1. 导航到位于以下位置的h2d.xsl文件：

      /libs/fmdita/html2dita/

   2. 搜索以下参数：

      `<xsl:param name="generate-related-links" select="false()"/>`

   3. 将上述参数的值设置为`true()`。
   4. 保存并关闭该文件。
1. 导航到输入文件夹位置\(`xhtmltodita`\)。

1. 将源XHTML文档上传到此文件夹中。 有关在DAM上上传内容的信息，请参阅[上传现有DITA内容](migrate-content-upload-existing-dita-content.md#)。


使用`<config> </config>`块，您可以定义一个或多个转换配置块。 将执行转换工作流，并且以DITA主题形式的最终输出保存在`outputDir`元素中指定的位置。

## 迁移非结构化FrameMaker文档 {#id1949B050VUI}

AEM Guides允许您将现有的非结构化FrameMaker \（`.fm`和`.book`\）文档转换为DITA文档。 有关该过程的完整详细信息，请查看[在Adobe FrameMaker中将技术文档从非结构化迁移到DITA](https://migrate-from-unstructured-to-dita-step-by-step-guide.meetus.adobeevents.com/)。

<!-- Deprecated information -
 //The first step is to create style mappings using FrameMaker and save those settings in a .sts file. Next, if you are using custom DITA, then you can map your custom elements with the source FrameMaker formats in the `ditaElems.xml` file. For example, if you have created a custom element named `impnote` to handle all important notes, then you can define this custom element in the `ditaElems.xml` file. Once this custom element is defined, AEM Guides would not raise an error while converting FrameMaker document containing `impnote` element.

Also, If you want to specify some additional attributes with your custom or valid DITA element, you can define those in the style2attrMap.xml file. For example, you can specify the `type` attribute with the value of `important` to be passed on with the `impnote` element. This additional information can be specified in the style2attrMap.xml file.

In addition to specifying

To convert your existing unstructured FrameMaker documents into DITA format, perform the following steps:

1.  Create style mappings in FrameMaker and save those settings in a .sts file.

1.  Log into AEM and open the CRXDE Lite mode.

1.  If you have custom DITA elements, define those in the `ditaElems.xml` file available at the following location:

    `/libs/fmdita/config/ditaElems.xml`

1.  Create an overlay node of the `config` folder within the `apps` node.

1.  Navigate to the configuration file available in the `apps` node:

    `/apps/fmdita/config/ditaElems.xml`

    The `ditaElems.xml` file contains a single configurable parameter:

    -   In the `elem` parameter, specify the name of the custom element that you want to use in your converted DITA documents. This element would be passed on as is in the generated DITA documents.

1.  If you want to specify additional attributes, define those in the `style2attrMap.xml` file available at the following location:

    `/libs/fmdita/config/style2attrMap.xml`

1.  Create an overlay node of the `config` folder within the `apps` node.

1.  Navigate to the configuration file available in the `apps` node:

    `/apps/fmdita/config/style2attrMap.xml`

    The `style2attrMap.xml` file contains the following configurable parameters:

    -   In the `fmStyle` parameter, specify the source format used in the FrameMaker document that you want to map.

    -   In the`ditaAttr` element, specify the DITA attribute that you want to map with the source format.

    -   In the `ditaVal` element, specify the value for the mapped attribute. If you don't have any value, you can leave this entry blank.

1.  Save the `style2attrMap.xml` file.

1. After configuring the required parameters in the `style2attrMap.xml` file, log into AEM and open the Assets UI.

1. Navigate to and click on the FrameMaker document that you want to convert.

    The DITA map console appears showing the list of Output Presets available to generate output.

1. Select DITA output format and configure the required parameters.

    >[!NOTE]
    >
    > You must use the same settings file \(.sts\) that you created in FrameMaker. Also, specify the Settings Name and Destination Path.

1. Click the **Generate** icon to start the output generation process.


Using the `<attrMap> </attrMap>` block, you can define one or multiple blocks of configurations for conversion. Depending on the content, you could have a .dita file and a .ditamap file as the converted files.

-->

## 迁移任何其他结构化文档 {#id1949B0590YK}

AEM Guides允许您将现有结构化文档转换为有效的DITA文档。 您需要指定输入和输出文件夹位置、转换文件的位置、保存最终输出的扩展名以及是否需要文档的新版本。

要将现有结构化文档转换为DITA格式，请执行以下步骤：

1. 登录AEM并打开CRXDE Lite模式。

1. 导航到以下位置提供的默认配置文件：

   `/libs/fmdita/config/XSLConfig.xml`

1. 在`config`节点内创建`apps`文件夹的覆盖节点。

1. 导航到`apps`节点中可用的配置文件：

   `/apps/fmdita/config/XSLConfig.xml`

   `XSLConfig.xml`文件包含以下可配置参数：

   - 在`inputDir`元素中，指定输入文件夹中可用源结构化文档的位置。 例如，如果您的结构化文档存储在`xsltodita`文件夹中名为`projects`的文件夹中，则将位置指定为： `/content/dam/projects/xsltodita/`

   - 在`outputDir`元素中，指定输出文件夹的位置或保留默认输出位置。 如果DAM上不存在指定的输出文件夹，则转换工作流将创建该输出文件夹。

   - 在`xslFolder`元素中，指定存储XSL转换文件的文件夹的位置。

   - 在``xslPath``元素中，指定用于启动转换过程的主.XSL文件的位置。

   - 在``outputExt``元素中，指定从转换流创建的最终输出文件的文件扩展名。

   - 对于`createRev`元素，指定是否创建转换的DITA主题的新版本\(`true`\)\(`false`\)。

1. 保存 `XSLConfig.xml` 文件。

1. 在`XSLConfig.xml`文件中配置所需的参数后，登录到AEM并打开Assets UI。

1. 导航到输入文件夹位置\(`xsltodita`\)。

1. 将源结构化文档上传到此文件夹中。 有关在DAM上上传内容的信息，请参阅[上传现有DITA内容](migrate-content-upload-existing-dita-content.md#)。


使用`<config> </config>`块，您可以定义一个或多个转换配置块。 将执行转换工作流，并且以DITA主题形式的最终输出保存在`outputDir`元素中指定的位置。

**父主题：**&#x200B;[&#x200B;迁移现有内容](migrate-content.md)
