---
title: 迁移非DITA内容
description: 了解如何迁移非DITA内容
exl-id: cf437fb8-ed33-47af-aa7e-ffd8acd232da
feature: Migration
role: Admin
level: Experienced
source-git-commit: cddbd7a19d4dfaa3f6549ed1bd511eeeb02acbb2
workflow-type: tm+mt
source-wordcount: '2940'
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

1. 使用包管理器下载/libs/fmdita/config/w2d\_io.xml文件。

1. 自定义下载的w2d\_io.xml文件。

1. 在Cloud Manager Git存储库中的以下位置添加文件：

   /apps/fmdita/config/w2d\_io.xml

   `w2d_io.xml`文件包含以下可配置参数：

   - 在`inputDir`元素中，指定可用源Word文档的输入文件夹的位置。 例如，如果您的Word文档存储在位于`projects`文件夹中名为`wordtodita`的文件夹中，则将位置指定为： `/content/dam/projects/wordtodita/`

   - 在`outputDir`元素中，指定输出文件夹的位置或保留默认输出位置以保存转换的DITA文档。 如果DAM上不存在指定的输出文件夹，则转换工作流将创建该输出文件夹。

   - 对于`createRev`元素，指定是否创建转换的DITA主题的新版本\(`true`\)\(`false`\)。

   - 在`s2tMap`元素中，指定映射文件的位置，该文件包含Word文档样式到DITA元素的映射。 默认映射存储在位于以下位置的文件中：

     ```
     /libs/fmdita/word2dita/word-builtin-styles-style2tagmap.xml
     ```

     >[!NOTE]
     >
     > 有关`word-builtin-styles-style2tagmap.xml`文件的结构以及如何对其进行自定义的更多信息，请参阅&#x200B;*DITA For Publishers用户指南*&#x200B;中的[样式到标记映射](http://www.dita4publishers.org/docs/repo/org.dita4publishers.word2dita/word2dita/style-to-tag-map-overview.html)。

   - 在props2Propagate元素中，指定应传递到DITA映射的属性。 要将默认元数据（如dc：title、dc：subject、dam：keywords、dam：category）从文档元数据传递到已转换的DITA资源，需要此属性。

1. 运行Cloud Manager管道以部署更新的配置。

1. 在`w2d_io.xml`文件中配置所需参数后，登录AEM并打开Assets UI。

1. 导航到输入文件夹位置\(`wordtodita`\)。

1. 将源Word文档上传到此文件夹中。 有关在DAM上上传内容的信息，请参阅[上传现有DITA内容](migrate-content-upload-existing-dita-content.md#)。


使用`config` `/config`块，您可以定义一个或多个转换配置块。 将执行转换工作流，并且以DITA主题形式的最终输出保存在`outputDir`元素中指定的位置。

**现有用户的自定义更新**

如果您是AEM Guidesas a Cloud Service的现有用户，并且正在从2021年8月版本升级到2022年1月或更高版本，请更新给定属性，因为只有少数文件已移动。

>[!NOTE]
>
> 此更新仅适用于已在使用Microsoft Word到DITA转换工作流的情况。

- 文件路径： /apps/fmdita/config/w2d\_io.xml
- 将`<s2tMap>`的值从/apps/dxml/word2dita/word-builtin-styles-style2tagmap.xml更改为/libs/fmdita/word2dita/word-builtin-styles-style2tagmap.xml
- 在Cloud Manager Git存储库中进行必要的更改，因为对于Cloud Service， /apps中的所有文件都将通过Cloud Manager Git进行覆盖。

## 迁移Adobe InDesign文档 {#id195AD0B0K5Z}

AEM Guides允许您转换InDesign文档。 与FrameMaker类似，InDesign还允许您创建非结构化和结构化文档。 非结构化文档使用段落和字符样式来格式化内容。 结构化文档使用元素及其相应的属性。

转换过程需要将段落和字符样式格式映射到相关的DITA元素。 同样，对于结构化文档，映射文件将包含具有DITA元素和属性的InDesign元素和属性的一对一映射。

转换过程涉及后端中的以下操作：

- *InDesign标记语言* \(IDML\)文件已解压缩到工作目录。
- 读取designmap.xml文件以定位各个InDesign剧本。
- 所有故事都合并到一个XML实例中，“空”故事将被丢弃。
- 所有嵌入式图形都将导出。
- 将标准结构（如表和图形）预转换为DITA格式。
- 根据映射文件映射到最终输出的样式或结构。
- 创建和验证单个DITA主题和DITA映射文件。
- 删除临时文件。

概括地说，转换过程要求您[准备InDesign文件以进行转换](appendix.md#id195DBF0045Z) [appendix.md\#id195DBF0045Z](appendix.md#id195DBF0045Z)和[准备映射文件以InDesign到DITA迁移](appendix.md#id194AF0003HT) [appendix.md\#id194AF0003HT](appendix.md#id194AF0003HT)，然后您需要按照给定的过程运行转换过程。

执行以下步骤，将现有InDesign文档转换为DITA主题类型文档：

1. 登录AEM并打开CRXDE Lite模式。

1. 导航到以下位置提供的默认配置文件：

   `/libs/fmdita/config/idml2dita_io.xml`
1. 若要根据您的要求创建自定义配置，请在`apps`节点内创建`config`文件夹的覆盖节点。

1. 将以下文件或文件夹从`libs`文件夹复制到apps文件夹：

   - `/fmdita/config/idml2dita_io.xml`
   - `/fmdita/idml2dita/config`
   - `/fmdita/idml2dita/xsl`

1. 导航到`apps`节点中可用的配置文件：

   `/apps/fmdita/config/idml2dita_io.xml`

1. 在`idml2dita_io.xml`文件中添加`idml12dita`文件夹中存在的配置的映射。
1. 在`idml2dita_io.xml`文件中添加以下属性：

   ```
   <entry          key="idml2DitaConfig">/apps/fmdita/idml2dita/config</entry>
   
   <entry key="idml2DitaXsl">/apps/fmdita/idml2dita/xsl</entry>
   ```

1. 在`apps`节点内创建`config`文件夹的覆盖节点。


   在`idml2dita_io.xml`文件中配置以下参数：

   - 在`inputDir`元素中，指定源InDesign文档可用的输入文件夹的位置。 例如，如果您的InDesign文档存储在位于`projects`文件夹中名为`indesigntodita`的文件夹中，则将位置指定为： `/content/dam/idmlfiles/indesigntodita/`

   - 在`outputDir`元素中，指定输出文件夹的位置或保留默认输出位置以保存转换的DITA文档。 如果DAM上不存在指定的输出文件夹，则转换工作流将创建该输出文件夹。

   - 在`mapStyle`元素中，指定映射文件的位置，该文件包含用于InDesign文档样式到DITA元素的映射。 默认映射存储在位于以下位置的文件中：

     ```
     /stmap.adobeidml.xml
     ```

     >[!NOTE]
     >
     > 有关`stmap.adobeidml.xml`文件的结构以及如何对其进行自定义的更多信息，请参阅附录中的[appendix.md\#id194AF0003HT](appendix.md#id194AF0003HT)部分。

1. 保存 `idml2dita_io.xml` 文件。

1. 在`idml2dita_io.xml`文件中配置所需参数后，登录AEM并打开Assets UI。

1. 导航到输入文件夹位置\(`indesigntodita`\)。

1. 将源InDesign文档上载到此文件夹。 有关在DAM上上传内容的信息，请参阅[上传现有DITA内容](migrate-content-upload-existing-dita-content.md#)。


## 迁移XHTML文档 {#id1949B04L0Y4}

AEM Guides允许您将现有XHTML文档转换为DITA主题类型文档。 您需要指定输入和输出文件夹位置以及其他参数，文档将转换为DITA格式。 可以使用两种方法来转换结构化HTML文档：

- 将所有文档上载到输入文件夹，或
- 创建包含所有文档以及媒体文件的ZIP文件，并将其上载到输入文件夹中。 这种方法通常用于一组相互链接的HTML文件，这些文件有一个目录\(index.html\)。 index.html文件包含指向集合中所有HTML文件的链接。

无论您是单独上传所有文件，还是以ZIP格式捆绑上传所有文件，转换过程都会在HTML文件和生成的DITA文件之间创建一对一映射。 这基本上意味着为输入文件夹中的每个.html文件创建了一个.dita文件。

在ZIP文件中上传文档时必须考虑以下几点：

- 所有引用的主题都应放在ZIP文件中。

- 所有被引用的介质文件应使用相对链接在主题文件中被引用。

- 创建一个index.html文件，并添加指向要在目录中添加的主题的链接。 此index.html文件用于创建DITA映射文件。 在index.html文件中，还可以创建嵌套主题列表，如以下代码示例中所示：

  ```
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

  从这些DITA文件生成HTML或AEM Site输出时，`outputclass`属性可用于对生成的HTML或AEM Site应用样式类，以匹配源HTML内容。


除了创建ZIP文件的注意事项外，您的XHTML文档还必须结构良好。 例如，您的文档应该有一个&#x200B;*标题*，后面应该有&#x200B;*标题1*、*标题2*，依此类推。 每个标题中都应包含一些内容。 如果您的文档结构不正确，迁移过程可能无法按预期进行。

要将现有XHTML文档转换为DITA主题，请执行以下步骤：

1. 使用包管理器下载/libs/fmdita/config/h2d\_io.xml文件。

1. 自定义下载的h2d\_io.xml文件。

1. 在Cloud Manager Git存储库中的以下位置添加文件：

   /apps/fmdita/config/h2d\_io.xml

   `h2d_io.xml`文件包含以下可配置参数：

   - 在`inputDir`元素中，指定可用源XHTML文档的输入文件夹的位置。 例如，如果您的XHTML文档存储在`projects`文件夹中名为`xhtmltodita`的文件夹中，则将位置指定为： `/content/dam/projects/xhtmltodita/`

   - 在`outputDir`元素中，指定输出文件夹的位置或保留默认输出位置。 如果DAM上不存在指定的输出文件夹，则转换工作流将创建该输出文件夹。

   - 对于`createRev`元素，指定是否创建转换的DITA主题的新版本\(`true`\)\(`false`\)。

1. 运行Cloud Manager管道以部署更新的配置。

1. 在`w2d_io.xml`文件中配置所需参数后，登录AEM并打开Assets UI。

1. *\（可选\）*&#x200B;您还可以将相关链接部分添加到转换后的文档。 要启用此功能，请执行以下步骤：

   >[!NOTE]
   >
   > 默认情况下，转换后的文档中不会创建相关链接部分。

   1. 使用包管理器下载/libs/fmdita/html2dita/h2d.xsl文件。

   2. 搜索以下参数：

      `<xsl:param name="generate-related-links" select="false()"/>`

   3. 将上述参数的值设置为`true()`。

   4. 在Cloud Manager Git存储库中的以下位置提交更新的文件：

      /libs/fmdita/html2dita/

   5. 运行Cloud Manager管道以部署更新的配置。

1. 导航到输入文件夹位置\(`xhtmltodita`\)。

1. 将源XHTML文档上传到此文件夹中。 有关在DAM上上传内容的信息，请参阅[上传现有DITA内容](migrate-content-upload-existing-dita-content.md#)。


使用`<config> </config>`块，您可以定义一个或多个转换配置块。 将执行转换工作流，并且以DITA主题形式的最终输出保存在`outputDir`元素中指定的位置。

## 迁移非结构化FrameMaker文档 {#id1949B050VUI}

AEM Guides允许您将现有的非结构化FrameMaker\（`.fm`和`.book`\）文档转换为DITA文档。 第一步是使用FrameMaker创建样式映射，并将这些设置保存在.sts文件中。 接下来，如果您使用的是自定义DITA，则可以将自定义元素与`ditaElems.xml`文件中的源FrameMaker格式进行映射。 例如，如果您创建了一个名为`impnote`的自定义元素来处理所有重要注释，则可以在`ditaElems.xml`文件中定义此自定义元素。 定义此自定义元素后，在转换包含`impnote`元素的FrameMaker文档时，AEM Guides不会引发错误。

此外，如果要使用自定义或有效的DITA元素指定一些其他属性，可以在style2attrMap.xml文件中定义这些属性。 例如，您可以指定要通过`impnote`元素传递的值为`important`的`type`属性。 可以在style2attrMap.xml文件中指定此附加信息。

除了指定

要将现有的非结构化FrameMaker文档转换为DITA格式，请执行以下步骤：

1. 在FrameMaker中创建样式映射，并将这些设置保存在.sts文件中。

1. 使用包管理器下载/libs/fmdita/config/ditaElems.xml文件。

1. 如果您有自定义DITA元素，请在位于以下位置的`ditaElems.xml`文件中定义这些元素：

   `/libs/fmdita/config/ditaElems.xml`

1. 在Cloud Manager的Git存储库中的以下位置创建ditaElems.xml文件的副本：

   `/apps/fmdita/config/ditaElems.xml`

1. 导航到`apps`节点中可用的配置文件：

   `/apps/fmdita/config/ditaElems.xml`

   `ditaElems.xml`文件包含单个可配置参数：

   - 在`elem`参数中，指定要在转换的DITA文档中使用的自定义元素的名称。 此元素将像在生成的DITA文档中一样传递。

1. 如果要指定其他属性，请在位于以下位置的`style2attrMap.xml`文件中定义这些属性：

   `/libs/fmdita/config/style2attrMap.xml`

1. 在`apps`节点内创建`config`文件夹的覆盖节点。

1. 导航到`apps`节点中可用的配置文件：

   `/apps/fmdita/config/style2attrMap.xml`

   `style2attrMap.xml`文件包含以下可配置参数：

   - 在`fmStyle`参数中，指定要映射的FrameMaker文档中使用的源格式。

   - 在`ditaAttr`元素中，指定要使用源格式映射的DITA属性。

   - 在`ditaVal`元素中，指定映射属性的值。 如果您没有任何值，则可以将此条目留空。

1. 保存 `style2attrMap.xml` 文件。

1. 在`style2attrMap.xml`文件中配置所需参数后，登录AEM并打开Assets UI。

1. 导航到要转换的FrameMaker文档并单击该文档。

   此时将显示DITA映射控制台，其中显示了可用于生成输出的输出预设列表。

1. 选择DITA输出格式并配置所需的参数。

   >[!NOTE]
   >
   > 必须使用您在FrameMaker中创建的相同设置文件\(.sts\)。 另外，指定设置名称和目标路径。

1. 单击&#x200B;**生成**&#x200B;图标以启动输出生成进程。


使用`<attrMap> </attrMap>`块，您可以定义一个或多个转换配置块。 根据内容的不同，可以将.dita文件和.ditamap文件作为转换后的文件。

## 迁移任何其他结构化文档 {#id1949B0590YK}

AEM Guides允许您将现有结构化文档转换为有效的DITA文档。 您需要指定输入和输出文件夹位置、转换文件的位置、保存最终输出的扩展名以及是否需要文档的新版本。

要将现有结构化文档转换为DITA格式，请执行以下步骤：

1. 使用包管理器下载/libs/fmdita/config/XSLConfig.xml文件。

1. 在Cloud Manager Git存储库中的以下位置创建XSLConfig.xml文件的副本：

   `/apps/fmdita/config/XSLConfig.xml`

   `XSLConfig.xml`文件包含以下可配置参数：

   - 在`inputDir`元素中，指定输入文件夹中可用源结构化文档的位置。 例如，如果您的结构化文档存储在`projects`文件夹中名为`xsltodita`的文件夹中，则将位置指定为： `/content/dam/projects/xsltodita/`

   - 在`outputDir`元素中，指定输出文件夹的位置或保留默认输出位置。 如果DAM上不存在指定的输出文件夹，则转换工作流将创建该输出文件夹。

   - 在`xslFolder`元素中，指定存储XSL转换文件的文件夹的位置。

   - 在``xslPath``元素中，指定用于启动转换过程的主.XSL文件的位置。

   - 在``outputExt``元素中，指定从转换流创建的最终输出文件的文件扩展名。

   - 对于`createRev`元素，指定是否创建转换的DITA主题的新版本\(`true`\)\(`false`\)。

1. 保存 `XSLConfig.xml` 文件。

1. 在`XSLConfig.xml`文件中配置所需参数后，登录AEM并打开Assets UI。

1. 导航到输入文件夹位置\(`xsltodita`\)。

1. 将源结构化文档上传到此文件夹中。 有关在DAM上上传内容的信息，请参阅[上传现有DITA内容](migrate-content-upload-existing-dita-content.md#)。


使用`<config> </config>`块，您可以定义一个或多个转换配置块。 将执行转换工作流，并且以DITA主题形式的最终输出保存在`outputDir`元素中指定的位置。

**父主题：**&#x200B;[&#x200B;迁移现有内容](migrate-content.md)
