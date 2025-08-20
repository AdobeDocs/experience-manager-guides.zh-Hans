---
title: 原生PDF | PDF输出生成
description: 了解如何使用本机PDF发布、创建和生成PDF输出预设、在生成本机PDF输出后下载临时文件以及在Adobe Experience Manager Guides中使用语言变量。
exl-id: ec3d59b7-1dda-4fd1-848e-21d8a36ff5e4
feature: Publishing, Native PDF Output
role: User
source-git-commit: e722ba35e27599566140709e060f3b391d50b4db
workflow-type: tm+mt
source-wordcount: '3232'
ht-degree: 0%

---

# 原生PDF输出预设

在创作内容时，必须确保内容针对查看、编辑和打印进行了优化。 通过使用诸如W3C CSS3之类的用于内容样式设置的标准和诸如Size、边距、方向、分页符、页眉、页脚和页码等页面定义属性的CSS分页媒体标准，您可以为PDF文档设置视图和布局，以确保一致性和可用性。 原生PDF发布功能使用这些标准生成PDF。

在本机PDF发布中，您可以使用预定义模板来确保内容布局和结构的一致性，应用样式表来更改输出的外观，优化PDF，设置打印机标记，允许屏幕阅读器支持，设置PDF符合性，嵌入字体等等。

使用本机PDF发布功能生成PDF的过程包括两个方面：

* 使用模板将样式应用于内容、设置页面布局和各种设置以微调PDF。 作者可以选择使用/修改提供的示例模板，也可以创建自定义模板并设置发布者和开发人员使用的高级配置选项。

* 创建或配置PDF输出预设以控制PDF设置。 创建PDF输出预设后，即可生成PDF。

## 创建输出预设

执行以下步骤，从“地图”控制台中创建PDF预设：

1. [在映射控制台](../user-guide/open-files-map-console.md)中打开DITA映射文件。

   您还可以从&#x200B;**概述部分**&#x200B;中的[最近使用的文件](../user-guide/intro-home-page.md#overview)构件访问映射文件。 选定的映射文件将在映射控制台中打开。
1. 在&#x200B;**输出预设**&#x200B;选项卡中，选择+图标以创建输出预设。
1. 从&#x200B;**新建输出预设**&#x200B;对话框的“类型”下拉列表中选择&#x200B;**PDF**。
1. 在&#x200B;**名称**&#x200B;字段中，提供此预设的名称。
1. 在&#x200B;**使用**&#x200B;生成PDF字段中，选择&#x200B;**Native-PDF**。
1. 选择&#x200B;**添加到当前文件夹配置文件**&#x200B;选项可在当前文件夹配置文件中创建输出预设。 ![文件夹配置文件图标](./assets/global-preset-icon.svg)表示文件夹配置文件级别的预设。

   了解有关[管理全局和文件夹配置文件输出预设](../user-guide/web-editor-manage-output-presets.md)的更多信息。

1. 选择&#x200B;**添加**。

   将创建PDF的预设。

## 本机PDF预设配置

创建预设后，配置本机PDF预设设置。 DITA-OT的预设配置选项在&#x200B;**常规**、**元数据**、**布局**、**安全性**、**打印**&#x200B;和&#x200B;**高级**&#x200B;选项卡下组织。

<img src="assets/preset-panel-new.png" alt="预设面板" width="800">

**常规**

用于指定基本输出设置，如指定输出路径、PDF文件名等。

| 设置 | 描述 |
| --- | --- |
| **输出路径** | AEM存储库中存储PDF输出的路径。 确保输出路径不在项目文件夹内。 输出路径是通过管理员配置的变量`${base_output_path}`设置的。 要配置输出路径，请查看[为云服务配置基本输出位置](../native-pdf/configure-base-location-cs.md)或[根据您使用的服务为本地服务配置基本输出位置](../native-pdf/configure-base-output-location.md)。 <br>您还可以使用以下现成的变量来定义输出路径。 您可以使用单个变量或变量组合来定义此选项。<br> `${map_filename}`：使用DITA映射文件名称创建目标路径。<br> `${map_title}`：使用DITA映射标题创建目标路径。 <br>`${preset_name}`：使用输出预设名称创建目标路径。<br> `${language_code}`：使用映射文件所在的语言代码创建目标路径。<br> `${map_parentpath}`：使用映射文件的完整路径创建目标路径。  <br>`${path_after_langfolder}`：使用语言文件夹之后的映射文件路径创建目标路径。 |
| **PDF文件** | 指定文件名以保存PDF。 默认情况下，PDF文件名会添加DITA映射名称以及预设名称。 例如，ditamap是“TestMap”，预设的名称为“preset1”，则pdf的默认名称将为“TestMap_preset1.pdf”。 <br>您还可以使用以下现成的变量来定义PDF文件。 您可以使用单个变量或变量组合来定义此选项。<br>`${map_filename}`<br>`${map_title}`<br>`${preset_name}` <br> `${language_code}`。 |
| **使用**&#x200B;应用条件 | 对于条件化内容，请从以下选项中选择以根据这些条件生成PDF输出： <br><ul> <li> **未应用**&#x200B;如果不想对映射和源内容应用任何条件，请选择此选项。<br><li> **DITAVAL文件**&#x200B;选择DITAVAL文件以生成条件内容。 您可以使用浏览对话框或手动输入文件路径来选择多个DITAVAL文件。 要删除选定的文件，请单击其名称旁边的交叉图标。 如果选择了无效文件，则会显示一条错误消息，说明&#x200B;**选择了无效的DITAVAL文件**。<br> <br>每个DITAVAL文件都可以包含一系列属性，如筛选条件和标记样式。 标记允许您使用开始和结束标记直观地标记内容，这些标记可以包括图像或文本格式，如粗体或斜体。 如果出现重叠条件或样式冲突，可以使用“样式”冲突设置定义背景颜色。 有关更多详细信息，请查看[使用DITAVAL编辑器](../user-guide/ditaval-editor.md)。<br><li> **条件预设**&#x200B;从下拉列表中选择条件预设，以在发布输出时应用条件。 如果为DITA映射文件添加了条件，则此选项可见。 条件设置在DITA映射控制台的条件预设选项卡中可用。 要了解有关条件预设的更多信息，请查看[使用条件预设](https://help.adobe.com/en_US/xml-documentation-for-adobe-experience-manager/index.html#t=DXML-master-map%2Fgenerate-output-use-condition-presets.html)。<br> </ul> |
| **使用基线** | 如果已为所选DITA映射创建了基线，请选择此选项以指定要发布的版本。 查看[使用基线](https://help.adobe.com/en_US/xml-documentation-for-adobe-experience-manager/index.html#t=DXML-master-map%2Fgenerate-output-use-baseline-for-publishing.html)以了解更多详细信息。 |
| **创建具有已发布版本间更改条的PDF** | 使用以下选项创建一个使用更改条显示两个版本之间内容差异的PDF：   <br><ul><li> **以前版本的基线**&#x200B;选择要与当前版本或其他基线进行比较的基线版本。 PDF中将显示一个更改栏，以指示修改的内容。 更改条是一条垂直线，用于直观地标识新内容或修订的内容。 更改栏显示在已插入、更改或删除的内容左侧。<br> **注意**：如果您选择&#x200B;**使用基线**&#x200B;并选择要发布的基线，将在两个选定的基线版本之间进行比较。 例如，如果您在&#x200B;**使用基线**&#x200B;下选择基线版本1.3，在&#x200B;**以前版本的基线**&#x200B;下选择基线版本1.1，则将在基线版本1.1和基线版本1.3之间进行比较。<br><li> **显示添加的文本**&#x200B;选择以绿色显示插入的文本并加下划线。 默认情况下，该选项处于选中状态。<br> <li> **显示已删除的文本**&#x200B;选择以红色显示已删除的文本并标记删除线。 默认情况下，该选项处于选中状态。 <br>**注意**&#x200B;您还可以使用样式表自定义更改栏、插入的内容或删除内容的样式。<br></ul> |
| **帖子生成工作流** | 选择以显示一个下拉列表，其中包含在AEM中配置的所有工作流。 您可以选择在PDF生成工作流完成后要执行的工作流。 |

**元数据**

元数据是内容的描述或定义。 元数据有助于内容管理，也有助于在Internet上搜索文件。

使用“元数据”选项卡可设置元数据字段，例如作者的姓名、文档标题、关键字、版权信息以及PDF输出的其他数据字段。 您还可以为PDF输出添加自定义元数据。

此元数据映射到输出PDF **文档属性**&#x200B;的&#x200B;**描述**&#x200B;选项卡中的元数据。



<img src="assets/pdf-metadata.png" alt="“元数据”选项卡" width="600">

从输出预设中，选择&#x200B;**PDF** > **Native-PDF** > **元数据**&#x200B;以添加和自定义元数据选项。
* **使用添加在topicmeta中的元数据**

  默认情况下，该选项处于选中状态。 您可以使用在DITA映射的topicmeta元素中添加的元数据来填充PDF输出的元数据字段。

* **提供XMP文件**

  您还可以通过导入[XMP](https://www.adobe.com/products/xmp.html)（可扩展元数据平台）文件直接填充元数据字段。 您可以从此处下载示例XMP文件。

[下载](assets/SampleXMP.xmp)

  或者，您可以使用Adobe Acrobat生成XMP文件。
   1. 在Acrobat中选择&#x200B;**文件** > **属性**。
   1. 在&#x200B;**描述**&#x200B;下，选择&#x200B;**其他元数据**。
   1. 从左侧面板中选择&#x200B;**高级**。
   1. 选择&#x200B;**保存**。

  XMP文件将保存在设备上。

* **提供元数据名称和值**

   1. 从下拉列表中选择以添加名称，或直接在名称字段中键入以添加自定义元数据。
   1. 输入元数据的值并选择“+”图标。
元数据将添加到PDF的元数据列表中。

您还可以使用变量来定义元数据值。  可以将为DITA映射或书图文件定义的元数据用作变量。 可以在DITA映射或书签映射文件的`/jcr:content/metadata`节点下找到元数据。
使用变量时，将从元数据属性中选取变量的值。

要使用变量，您需要以`${<variable>}`格式定义它。

例如，在/`jcr:content/metadata`节点中定义的元数据属性之一是
`dc:title`。 您可以指定`${dc:title}`，并在最终输出中使用标题值。

您可以使用单个变量或变量组合来定义元数据。 例如，`${dc:title} ${dc:docstate}`。您还可以使用变量和字符串的组合。  例如 `View ${dc:title} in ${dc:language}`。

使用语言变量定义元数据属性的本地化值。 根据您选择的语言，将在PDF输出中自动选取本地化的值。 例如，您可以将“Author”作为元数据值打印在英语中，将“Autorin”作为元数据值打印在德语中。

格式： `${lng:<variable name>}`。 例如，`${lng:author-label}`其中`author-label`是语言变量。

将鼠标悬停在 <img src="./assets/info-details.svg" alt= "信息图标" width="25">接近查看其更多详细信息的选项。


**布局**

用于设置页面布局并指定PDF输出的页面查看选项（如“页面显示”）和设置缩放级别。

| 设置 | 描述 |
| --- | --- |
| **PDF模板** | PDF模板提供了一种清晰的结构，可用于定义页面布局、内容样式和将各种设置应用于PDF输出。 从PDF模板下拉选项中进行选择，以选择您的首选模板。 <br>您还可以选择&#x200B;**浏览模板** <img src="./assets/browse-templates-icon.svg"  alt= "浏览模板图标" width="25">以选择模板。 在&#x200B;**选择PDF模板**&#x200B;对话框中，您还可以预览缩略图并查看所选模板的标题和描述。 |
| **页面显示** | 使用“页面显示”进行页面查看，以显示PDF在打开时的显示方式。 从“页面显示”下拉选项中进行选择，以选择首选视图。<br><ul><li> **默认值**&#x200B;根据用户计算机上PDF查看器的默认设置显示。 <br> <li> **单页视图**&#x200B;一次显示一个页面。   <br> <li> **单页滚动**&#x200B;在连续的垂直列中显示单个页面。 <br> <li> **两个页面视图**&#x200B;一次并排显示两个页面跨页。.<br> <li> **两页滚动**&#x200B;显示两页跨页并排连续滚动。 </ul> |
| **缩放** | 选择可调整页面视图的大小，以显示PDF在打开时的显示方式。 <br><ul><li> **默认值**&#x200B;根据用户计算机上PDF查看器的默认设置显示    <br> <li> **100%**&#x200B;使页面以实际大小显示。     <br> <li> **适合页面**&#x200B;使页面宽度和高度适合文档窗格。   .<br> <li> **调整页面宽度**&#x200B;使页面宽度填充文档窗格的宽度。 <br> <li> **适合页面高度**&#x200B;使页面高度填充文档窗格的高度。 </ul> |

**安全性**

通过添加对打开和读取文件的限制来保护您的PDF。 使用以下选项以避免未经授权的访问。

| 设置 | 描述 |
| --- | --- |
| **设置密码以打开文档** | 选择可添加安全密码以查看您的PDF文件。 在&#x200B;**用户密码**&#x200B;字段中指定密码。 用户只能通过输入此字段中提供的密码来打开PDF。 |
| **设置文档限制** | 选择以限制用户与您的PDF的交互方式。 在&#x200B;**所有者密码**&#x200B;字段中指定密码以使以下限制设置生效。 <br><ul><li> **正在打印**&#x200B;选择此项可允许用户打印PDF。<br> <li> **草稿质量打印**&#x200B;选择此项可允许用户以较低的分辨率打印PDF。 <br> <li> **内容复制**&#x200B;选择此项可允许用户从PDF复制内容。   <br> <li> **批注**&#x200B;选择此项可允许用户在PDF中添加注释或评论。<br> <li> **内容修改**&#x200B;选择此项可允许用户更改PDF中的内容。<br> <li> **为辅助功能复制内容**&#x200B;选择此项可允许屏幕阅读器在PDF中阅读和导航内容。<br>  **文档程序集**&#x200B;选择此项可允许用户在PDF中插入页面。<br> **注意**：用户需要输入所有者密码才能更改Adobe Acrobat中“文件”>“属性”的任何限制。 |

**打印**

>[!NOTE]
>
> 从Experience Manager Guides 5.0/2025.02.0版本开始，“打印”部分现在是&#x200B;**本机PDF输出预设**&#x200B;的一部分。 对于已保存打印设置的现有模板，打印数据将保持不变，但将不再出现在UI中或在输出期间应用。 要继续使用这些设置，必须在本机PDF输出预设中重新配置它们。

配置打印生产设置以分配打印机标记，选择颜色模型，并指定与打印PDF输出相关的属性。

* **打印机标记**：在准备文档以进行打印生产时，打印机标记将添加到页面边界以帮助在打印期间正确对齐、修剪和颜色选择。 通过选择打印机标记，扩展页面边界以容纳在打印期间被修剪的标记。 您可以选择在PDF输出中显示以下打印机标记：
   * **裁切标记**：选择选项以在裁切区域的每个角落处放置标记，以指示打印后需要裁切纸张的位置。
   * **出血标记**：选择此项可在出血框的每一角放置标记，以指示扩展图像的修剪区域。
   * **对齐标记**：选择此项可将标记置于裁切区域之外，以对齐彩色文档中的不同分色。
   * **颜色条**：选择此项可在修剪区域外添加一条颜色条，以保持颜色一致性并在打印时调整油墨密度。

  使用&#x200B;**行宽**、**行色**&#x200B;和&#x200B;**出血框宽**&#x200B;选项设置所选打印机标记的尺寸。

* **媒体盒大小**：这是总页大小，包括打印机标记所占用的扩展区域。 使用下拉选项为PDF输出选择页面大小或创建自己的自定义大小。

* **色彩空间**：您可以选择使用RGB或CMYK色彩空间打印PDF文档。 选择RGB以数字方式显示生成的PDF以及用于物理打印的CMYK。 文档中定义的颜色将转换为所选颜色空间。

* **ICC配置文件**：在这里，您可以通过指定ICC配置文件来管理跨设备的颜色准确性。 这确保在打印输出中呈现一致的颜色。

要配置此设置，请指定服务器上的ICC配置文件路径，并提供ICC配置文件名称以便于识别。 或者，如果ICC配置文件在线存储，则可以提供其URL而不是文件路径。

>[!NOTE]
>
> 如果使用CMYK色彩空间，则创建PDF/A时需要ICC色彩配置文件。

<!--For more information on applying these print settings, see *Printing preferences*.-->

**高级**

使用以下选项指定合并PDF、使用压缩、选择合规性标准等内容的高级设置。

| 设置 | 描述 |
| --- | --- |
| **创建可访问（已标记）的PDF** | 选择此选项可生成带有标记的PDF。 标记的PDF使屏幕阅读器更轻松地阅读和导航内容、超链接、书签等。 例如，如果表被标记，屏幕阅读器将知道它正在读取表，而不仅仅是行和文本。 |
| **合并目录中包含的PDF** | 选择此选项可以将现有PDF作为资源文件添加到DITA映射中，从而将它们合并到输出中。 PDF将插入地图中显示的位置，页面将相应增加。 |
| **嵌入使用的字体** | 在使用可能未安装在最终用户计算机上的字体时，请选择此选项。 选中此选项后，会将使用的字体嵌入到PDF中，从而确保用户能够按预期查看PDF，即使计算机上未安装这些字体也是如此。<br> **注意**：字体只有包含允许嵌入的字体供应商设置的字体才能嵌入。 在嵌入字体之前，请确保您具有所需的设置或许可证。 |
| **使用自动断字** | 启用自动连字符后，行末的词语会在文法正确的位置用连字符断开。 |
| **启用JavaScript** | 如果您拥有要在生成PDF之前动态转换内容的JavaScript代码，请启用此选项。 |
| **嵌入多媒体文件** | 选择此选项可在PDF中包含任何音频、视频和交互式内容。 |
| **使用完全压缩优化PDF大小** | 如果要压缩/减小大型PDF的大小，请选择此选项。 请记住，压缩PDF可能会降低文件质量。 |
| **使用图像压缩优化PDF大小** | 如果要在PDF中压缩/减小使用的图像大小，请选择此选项。 请记住，压缩图像可能会降低图像质量。 |
| **使用自定义分辨率（每英寸像素）** | 它是以像素/英寸为单位的页面显示分辨率。 在选中此选项时显示的字段中输入首选值。 默认值为每英寸96像素。 设置较高的值以在一英寸内容纳更多内容，如果设置较低的值，则反之亦然。 |
| **显示水印** | 选择此选项可在输出中叠加水印。 您可以在文本框中输入新的文本字符串，其字符大小写符合您的要求。 <br><br>使用静态文本或语言变量发布水印的本地化版本。  根据您选择的语言，将在PDF输出中自动选取本地化的值。 例如，您可以将“Publisher”作为水印以英语打印，将“Auteure”作为水印以法语打印。  <br>格式： `${lng:<variable name>}`。 例如，`$ {lng:publisher-label}`其中`publisher-label`是语言变量。 <br>悬停在 <img src="./assets/info-details.svg" alt= "信息图标" width="25">接近查看其更多详细信息的选项。 |
| **启用MathML公式** | 选择此选项以呈现内容中存在的MathML公式。 否则将默认忽略公式。 |
| **创建交互式PDF表单** | 如果要包含交互式和可自定义的PDF表单字段，以便在生成的PDF输出中提供增强的用户输入，请选择此选项。 |
| **包含跟踪更改** | 如果要在生成的PDF中包含跟踪的更改以便于查看和比较，请选择此选项。 |
| **保留临时文件** | 如果要保留在生成本机HTML输出时创建的临时PDF文件，请选择此选项。 生成输出后，您可以稍后下载临时文件。 下载的文件还将包括`system_config.xml`文件，该文件为您提供了有关作者URL、本地URL和发布URL的信息。 这些URL是在AEM外部化设置中配置的，并反映在`system_config.xml`文件中。 |
| **PDF合规性** | 这是您打算保存PDF以确保其合规性的标准。 从下拉列表中选择，以从可用的PDF标准列表中进行选择。 有关支持的标准的更多详细信息，请查看[关于PDF标准](https://helpx.adobe.com/cn/acrobat/using/pdf-conversion-settings.html#about_pdf_x_pdf_e_and_pdf_a_standards)。 |
| **文件属性** | 选择要传递到本机PDF发布的元数据。 该下拉列表会同时列出自定义属性和默认属性。 例如，`dc:description`、`dc:language`、`dc:title`和`docstate`是默认属性，而您可以将`author`作为自定义属性。 所选的元数据属性将传递到使用本机PDF生成的PDF文件。 <br>这些属性是从位于`metadataList`的`/libs/fmdita/config/metadataList`文件中选取的。 <br>此文件可以覆盖在： `/apps/fmdita/config/metadataList`。 |



<!--------------


### Additional notes for PDF output

**Download temporary files after generating the Native PDF output**

If you select the **Download temporary files** option in the Advanced settings, you can also download the interim HTML files created while generating the Native PDF output. Once you've generated the output, you can download the temporary files using the **Download temporary files** ![download temporary files](assets/native-pdf-download-temporary-files-icon.svg)icon on the top bar. This feature helps you view your interim HTML styles and layouts and helps you correct or change your CSS styles according to your requirements.


>[!NOTE]
>
> The **Download temporary files**  ![download temporary files](assets/native-pdf-download-temporary-files-icon.svg) icon appears only if you have generated the last PDF output using the preset wherein you have selected the option in the **Advanced** tab. 


**Use language variables**

AEM Guides also provides the support for language variables. Select **Language Variables** <img src="assets/language-variables.svg" width="25">  in the left panel to define a localized version of the out-of-the-box labels like Note, Caution, and Warning or static text in the PDF output. For more details, view [Support for language variables](../native-pdf/native-pdf-language-variables.md).


**Support for Markdown documents**

Experience Manager Guides also provides support for your Markdown documents.  Markdown files are easy to author and also provide a variety of formatting options. Learn how to [author Markdown documents from the Editor](../user-guide/web-editor-markdown-topic.md). 

You can add the Markdown topics to your DITA map and generate the PDF output using the Native PDF output presets.  Learn how to configure or [create a PDF output preset](#create-a-pdf-output-preset-create-output-preset). 

--------------->