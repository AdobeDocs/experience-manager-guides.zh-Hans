---
title: 附录
description: 了解如何准备InDesign文件以进行转换
exl-id: 02da0e61-7a73-4c4c-9bd7-2664d90fa728
feature: InDesign File Conversion
role: Admin
level: Experienced
source-git-commit: 0513ecac38840a4cc649758bd1180edff1f8aed1
workflow-type: tm+mt
source-wordcount: '2851'
ht-degree: 0%

---

# 附录 {#id195AD0L60Y4}

## 准备InDesign文件进行转换 {#id195DBF0045Z}

InDesign为作者提供了一组丰富的功能，用于创建吸引人且复杂的文档。 通常，这意味着文档的各个部分会以可视方式放置在页面上，但不尝试在这些文本框架之间提供任何流向。 未定义文本框架的“*读取顺序*”时，IDML文件将包含可能未遵循任何有意义的顺序的内文。 最终结果将是一个或多个DITA主题，其中包含以随机顺序排列的段落、表格和图形。

虽然可以在DITA编辑器中将DITA内容编辑为合理的顺序，但在创建IDML文件之前修复InDesign文件要容易得多。 可以在不改变源文档外观的情况下完成此操作。 通过正确定义阅读顺序，它还有助于使源文档可访问。

***线程化文本框架***

InDesign将术语&#x200B;*&#39;线程&#39;*&#x200B;用于链接一个帧到另一个帧的过程。 有关线程化文本框架的更多详细信息，请参阅InDesign文档中的&#x200B;*[线程化文本](https://helpx.adobe.com/in/indesign/using/threading-text.html)*&#x200B;主题。

***帧重叠***

有些InDesign文档出于布局原因使用无线程重叠框架。 将此内容合并到主线程中可能非常困难。 最佳选项可能是在DITA环境中编辑结果。

***InDesign故事***

InDesign文档中的每个线程内容流都称为“*story*”。 为获得最佳结果，建议限制文章数量。 但是，在DITA输出中可能不需要文档的某些部分。 例如，页脚很少需要，但如果处理不当，它们可能会出现在主题的中间。

排除文档中不需要的文本的最简单方法是为其指定一个特殊的&#x200B;*段落标记*，该标记仅用于不需要的内容。 例如，不要为页脚重复使用&#x200B;*\[基本段落\]*，而要创建专用的&#x200B;*页脚*&#x200B;标记。 然后，在MapStyle文件中，只需设置要删除的&#x200B;*页脚*&#x200B;段落，如下所示：

```XML
<paraRule style="Footer" local="0" refactor="drop">
   <attributeRules createID="false"/>
</paraRule>
```

***映射到DITA doctypes***

源文档必须具有至少一个可以标记主题开头的段落样式或元素。 文档通常使用&#x200B;*标题1*&#x200B;作为文档中顶级标题的名称。 然后，您可以创建从该样式到特定DITA doctype的映射。 如果您的文档组织良好，并且始终使用&#x200B;*标题1*，那么您将获得良好的结果。

***多个DITA文档类型***

如果需要将某些&#x200B;*标题1*&#x200B;段落转换为其他DITA文档类型，请复制InDesign的段落样式。 根据需要，为这些样式提供一个易于识别的名称，例如&#x200B;*Heading1\_genTask*&#x200B;或&#x200B;*Heading1\_troubleshooting*。 然后，设置mapStyle文件，如下所示：

```XML
<doctypes>
   <doctypeParaRule style="Heading1" local="0" mapToDoctype="concept">
      <attributeRules createID="true"/>
   </doctypeParaRule>
   <doctypeParaRule style="Heading1_genTask" local="0" mapToDoctype=" generalTask">
      <attributeRules createID="true"/>
   </doctypeParaRule>
   <doctypeParaRule style="Heading1_troubleshooting" local="0"mapToDoctype=" troubleshooting">
      <attributeRules createID="true"/>
   </doctypeParaRule>
</doctypes>
```

***结构化InDesign文档***

InDesign与XML的关系很松散。 虽然文档可以包含XML DTD，并且主故事可能对该DTD有效，但也可以创建一些内容是XML但不包含DTD的混合文档。 这些是成功转换为DITA的不希望出现的情况。 如果文档包含XML部件，请尝试将输出保存为XML，并查看结果是否可接受。 如果不包含，则DITA内容也将包含无效内容，或者可能完全失败。

***表格格式***

从InDesign表格式规则转换为DITA中的等效表格式是一个复杂的过程。 这是因为与DITA中使用的Oasis \(CALS\)表模型提供的基本选项相比，源文件中提供了丰富的格式功能。 提供了垂直和水平文本对齐方式，并且提供了类似的结果，尽管两端对齐的文本始终根据文本方向对齐，而InDesign则允许两端对齐和两端对齐的文本。

InDesign对列和行分隔符的处理，再次比Oasis表格模型的基本选项要强大得多。 InDesign提供四种单元格边框 — 边框类型\（实心或图案\）、边框粗细、边框颜色、边框色调、边框间隙颜色和边框间隙色调。 所有这些都必须向下映射到每个单元格右侧和底部的边框\(entry element\)，其中唯一选项为0或1 — 隐藏边框或显示边框。

InDesign的边界裁定可以应用于以下级别：

- 表格样式
- 单元格样式
- 每个单元格上的本地覆盖

InDesign到DITA的转换过程应用以下边界规则：

- 表样式映射到垂直规则的`colspec/@colsep`属性。 水平规则映射到`row/@rowsep`属性。 在这两种情况下，如果未定义边框，则不会创建属性。
- 单元格样式映射到`entry/@colsep`和`entry/@rowsep`属性。 这些值将覆盖任何表样式派生的边框规则。
- 局部覆盖将格式设置直接应用于单元格，并覆盖表格样式和单元格样式。

***交替模式***

InDesign表样式允许列和单元格直排遵循交替模式。 虽然该功能支持转换，但只有当一个模式组映射为显示正线\(1\)，而另一个模式组映射为隐藏正线\(0\)时，转换的结果才明显。

## 准备映射文件以InDesign到DITA迁移 {#id194AF0003HT}

正确的DITA转换需要一个与源文档内容匹配的映射文件。 对于非结构化InDesign文档，这意味着需要映射所有可用的段落样式和字符样式。 对于XML结构化InDesign文档，必须映射其关联DTD中的所有元素。

非结构化和结构化InDesign文档的映射文件是不同的。 这是因为将非结构化源内容转换为DITA的处理要求更加复杂。

下面给出了映射文件的示例：

```XML
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE styleMap SYSTEM "mapStyle.dtd">
<styleMap xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="mapStyle.xsd" >
   <doctypes>
      <mapDoctypeParaRule root="itpx:stories" mapToDoctype="map">
         <attributeRules createID="true">
            <addNew name="outputclass" value="map"/>
         </attributeRules>
      </mapDoctypeParaRule>
      <doctypeParaRule style="Heading 1" local="0" mapToDoctype="concept">
         <attributeRules createID="true"/>
      </doctypeParaRule>
      <doctypeParaRule style="Heading A" local="0" mapToDoctype="topic">
         <attributeRules createID="true"/>
      </doctypeParaRule>
   </doctypes>
   <wrappingRules>
      <wrap elements="li+" context="number" wrapper="ol">
         <attributeRules createID="true"/>
      </wrap>
      <wrap elements="li+" context="bullet" wrapper="ul">
         <attributeRules createID="true"/>
      </wrap>
   </wrappingRules>
   <paragraphStyleRules>
      <paraRule style="Heading 2" local="0"  mapTo="p">
         <attributeRules createID="true"/>
      </paraRule>
      <paraRule style="Heading 3" local="0"  mapTo="p">
         <attributeRules createID="true"/>
      </paraRule>
      <paraRule style="List Paragraph" local="p[-|-|-|-|-|b|-|-]" context="bullet" mapTo="li">
         <attributeRules createID="true"/>
      </paraRule>
      <paraRule style="List Paragraph" local="p[-|-|-|-|-|n|-|-]" context="number" mapTo="li">
         <attributeRules createID="true"/>
      </paraRule>
      <paraRule style="List Paragraph" local="0" context="bullet" mapTo="li">
         <attributeRules createID="true"/>
      </paraRule>
      <paraRule style="Normal" local="0"  mapTo="p">
         <attributeRules createID="true"/>
      </paraRule>
      <paraRule style="Normal" local="p[-|-|-|-|-|b|-|-]" context="bullet" mapTo="li">
         <attributeRules createID="true"/>
      </paraRule>
      <paraRule style="Title" local="0"  mapTo="p">
         <attributeRules createID="true"/>
      </paraRule>
   </paragraphStyleRules>
   <characterStyleRules>
      <charRule style="Bold" local="0" mapTo="b">
         <attributeRules createID="false"/>
      </charRule>
      <charRule style="Code" local="0" mapTo="codeph">
         <attributeRules createID="false"/>
      </charRule>
      <charRule style="[No character style]" local="c[Bold|-|-|-|-|-|-|-]" mapTo="b">
         <attributeRules createID="false"/>
      </charRule>
      <charRule style="[No character style]" local="c[Italic|-|-|-|-|-|-|-]" mapTo="i">
         <attributeRules createID="false"/>
      </charRule>
   </characterStyleRules>
</styleMap>
```

映射文件是一个具有简单结构的XML文件，其中列出了所有源段落样式和字符样式代码。 文件内容说明如下：

**样式映射**

在`styleMap`元素中，您可以指定两个可选属性 — `@map_date`和`@map_version`，以记录映射文件的版本。

**文档类型**

`doctypes`元素列出了支持的DITA映射和主题映射。

**映射文档类型段落规则**

`mapDoctypeParaRule`元素是必需的。 不能编辑此元素的属性，因为源XML的根元素始终映射到DITA映射的根`map`元素。

**文档类型段落规则**

`doctypeParaRule`元素是必需的。 这为转换过程提供了一种识别新主题开始位置的方法。 通常`@style`属性单独使用，并将`@local`属性设置为0。 但是，如果所选样式上始终存在本地格式覆盖，则必须为每个样式添加规则及其本地覆盖。 这很容易识别生成的映射文件中可以找到以下内容或类似内容的地方：

```XML
<paraRule style="Heading 1" local="0" mapTo="p">
   <attributeRules createID="true"/>
</paraRule>
<paraRule style="Heading 1" local="p[Italic|-|-|-|-|-|-|-]" mapTo="p">
   <attributeRules createID="true"/>
</paraRule>
```

在上述示例中，`@style` = &quot;Heading1&quot;包含两个`paraRule`元素。 只需创建一个等效的`doctypeParaRule`元素，并根据需要设置`@mapToDoctype`属性。

`doctypeParaRule`中使用的属性说明如下：

- `@style`：源InDesign文档中样式的名称。
- `@local`：请参阅[\#id194CG0V005Z](#id194CG0V005Z)。
- `@mapToDoctype`：所有有效`doctypes`的枚举列表中的DITA主题类型的名称。

**元素包装规则**

元素封装规则定义根据一组属性值将传入文档中的元素封装或移动到预定义元素中的方式。

***`wrap`元素***

这是一个可选元素。 `wrap`元素列出了将封装或移动的元素。 封装通常用于必须为一系列元素指定公共父元素的情况。 例如，多个`li`元素将封装在`ol`元素中。 此外，`wrap`还可用于移动元素，例如插图和表格的标题。

`wrap`中使用的属性说明如下：

- `@element`：元素名称后的加号显示，所有具有相同名称的相邻元素将封装在`@wrapper`属性中命名的元素中。
- `@wrapper`：包装元素的名称。
- `@context`：提供进一步细化给定元素包装方式的方法。 以下示例显示了一种根据`@context`值\（上下文定义在`paraRule`元素\）映射有序列表`ol`或无序列表`ul`中的一系列`li`元素的方法：

  ```XML
  <wrap elements="li+" context="number" wrapper="ol">
     <attributeRules createID="true"/>
  </wrap>
  <wrap elements="li+" context="bullet" wrapper="ul">
     <attributeRules createID="true"/>
  </wrap>
  ```


以下示例显示如何从`title`和`image`元素创建`fig`元素：

- `@elements`：用逗号分隔的列出元素将封装在`@wrapper`属性中命名的元素中。 由于在图像下方包含图形标题的常见做法，标题将为`image`之后紧接的`title`元素。

  以下换行规则：

  ```XML
  <wrap elements="title, image" context="FigTitle" wrapper="fig">
     <attributeRules createID="true"/>
  </wrap>
  ```

  转换以下中间XML：

  ```XML
  <image href="Links/myImage.png" scale="59">
     <title>IDML2DITA workflow</title>
  ```

  转换为以下有效的DITA图结构：

  ```XML
  <fig id="id397504">
     <title>IDML2DITA workflow</title>
     <image href="Links/myImage.png" scale="59">
  </fig>
  ```

- `@wrapper`：包装元素的名称。
- `@context`：提供进一步细化给定元素包装方式的方法\（上下文在`paraRule`元素上定义\）。

以下示例说明如何将`title`移入`table`：

- `@elements`：位于`table`之前或之后的`title`元素将封装在`@wrapper`属性中命名的元素中。 XPath样式谓词可以将title元素的位置标识为`[before]`或`[after]`。

  示例：以下换行规则：

  ```XML
  <wrap elements="title[before]" context="TableTitle" wrapper="table">
     <attributeRules createID="true"/>
  </wrap>
  ```

  转换以下中间XML：

  ```XML
  <title>IDML2DITA workflow</title>
  <table id="id289742" outputclass="BasicTable">
     <tgroup cols="2">
        <colspec colname="0" colwidth="0.7*">
           <colspec colname="1" colwidth="0.3*">
  ```

  在此有效的DITA图结构中：

  ```XML
  <table id="id289742" outputclass="BasicTable">
     <title>IDML2DITA workflow</title>
     <tgroup cols="2">
        <colspec colname="0" colwidth="0.7*">
           <colspec colname="1" colwidth="0.3*">
  ```

- `@wrapper`：包装元素的名称。

- `@context`：提供进一步细化给定元素包装方式的方法\（上下文在`paraRule`元素上定义\）。


**段落样式规则**

`<paragraphStyleRule>`元素描述如下：

***`paraRule`元素***

`paraRule`元素是必需的。 这会指定所有段落样式的映射规则。 在InDesign文档中，所有文本都包含在段落样式的子结构中，即使没有任何样式的段落也被命名为`[No paragraph style]`。 方括号，表示内置InDesign样式名称。

>[!NOTE]
>
> 方括号表示内置InDesign样式名称。

`paraRule`中使用的属性说明如下：

- `@style`：源InDesign文档中样式的名称。
- `@local`：请参阅[\#id194CG0V005Z](#id194CG0V005Z)。
- `@mapTo`： DITA目标元素的名称。

- `@context`：当有多个包装器选择可用时，此属性用于链接到特定的&#x200B;**wrap**&#x200B;规则。 示例： `li`元素可以封装在`ol`或`ul`元素中。 要标识不同的列表类型，您可以使用特定的样式名或`@local`属性，该属性可显示以下内容：
   - `local="p[-|-|-|-|-|b|-|-]"`其中字段6中的“`b`”表示项目符号列表项。 在这种情况下，将`@context`设置为“`bullet`”。
   - `local="p[-|-|-|-|-|n|-|-]"`其中字段6中的“`n`”表示编号列表项。 在这种情况下，将`@context`设置为“`number`”。

- `@commentOut`：此属性允许在XML注释中封装目标元素，这样信息就不会丢失，但用户可手动处理。 如果无法强制源内容符合DITA结构规则，这将很有用。

- `@refactor`：此可选属性可以选择两个值：

- `unwrap`：删除匹配的元素，同时保留其内容。

- `drop`：已删除匹配的元素及其所有内容。


**字符样式规则**

`charRule`元素描述如下：

>[!NOTE]
>
> 在`local="0"`时，内置字符样式`[No character style]`将没有映射，因为它们在预处理期间被删除。

***`charRule`元素***

这是一个可选元素。

这些是所有字符样式的映射规则。 在InDesign文档中，所有文本都包含在字符样式的子元素中。

`charRule`中使用的属性说明如下：

- `@style`：源InDesign文档中样式的名称。
- `@local`：请参阅[\#id194CG0V005Z](#id194CG0V005Z)。
- `@mapTo`： DITA目标元素的名称。
- `@refactor`：此可选属性可以选择两个值：
   - `unwrap`：删除匹配的元素，同时保留其内容。

   - `drop`：已删除匹配的元素及其所有内容。


**属性规则**

此元素可以是以下元素上下文的子元素：

- `mapDoctypeParaRule`
- `mapDoctypeElemRule`
- `doctypeParaRule`
- `doctypeElemRule`
- `paraRule`
- `charRule`
- `elementRule`

属性规则的用途是管理匹配元素的属性。

根据上下文，`attributeRules`元素可以使用以下属性：

- `@createID`：为匹配的元素生成唯一ID。 允许的值`true`或`false`。 在所有上下文中均可用。
- `@copyAll`：仅从结构化源文件的源XML内容复制所有属性。 允许值为`true`或`false`。 可用于上下文`mapDoctypeParaRule`、`mapDoctypeElemRule`、`doctypeElemRule`和`elementRule`。


`attributeRules`中使用的属性说明如下：

>[!NOTE]
>
> 此元素可以包含多个子元素。

- `addNew`：向匹配的元素添加新属性。 可用于所有上下文。 它具有两个属性：
   - `@name`：必须是合法的XML名称，最好对DITA上下文有效。
   - `@value`：可以是文本或简单的XPath表达式。
- `copyAtt`：将单个属性复制到目标，同时可以选择在此过程中重命名该属性。 此值不会更改。 可用于上下文`mapDoctypeParaRule`、`mapDoctypeElemRule`、`doctypeElemRule`和`elementRule`。 当此元素存在时，`@copyAllAtts`值被假定为`false`。 它具有两个属性：
   - `@name`：必须是源XML元素上存在的属性的名称。
   - `@mapTo`：必须是合法的XML名称，最好对DITA上下文有效。

**本地格式代码**

在任何InDesign文档中，段落样式和字符样式都可以包含数百种不同的格式覆盖。 这些属性中的大多数在转换过程中没有发挥任何有用的作用。 但是，我们已确定了一组核心格式特征，这些特征确实会影响文档的语义，并且需要影响转换过程。

`@local`属性显示为特殊分隔格式，其中提供了8个字段以及前缀，以显示格式覆盖的类型。 下面列出了格式化代码字段：

- para样式本地覆盖的前缀&#x200B;**p**&#x200B;或字符样式本地覆盖的前缀&#x200B;**c**。
- **字体样式**，是系列名和属性，如“***粗体斜体***”。
- **字体大小**（以点为单位）。
- 上标或下标的&#x200B;**字符位置**。
- 下划线为&#x200B;**Under**。
- 删除线&#x200B;**删除**。
- **列表代码**，用于标识列表类型为项目符号或编号 — 并不总是由InDesign使用。
- **项目符号代码**&#x200B;列出了文档中定义的所有项目符号类型。
- **编号代码**&#x200B;列出文档中所有定义的编号样式。

谨慎使用此功能会丢失本地格式，这有助于提高从样式化内容传输到DITA的质量。 此示例可解析为项目符号列表`p[Italic|16|-|-|-|b|-|-]`中表示斜体、16pt文本。

**结构映射**

结构映射文件类似于样式映射文件，其结构非常简单，列出了所有源元素和相关属性类型。 提供了两个属性`@map_date`和`@map_version`来记录要使用的映射文件的版本。

**文档类型**

`doctypes`元素列出了支持的DITA映射和主题映射。

**映射文档类型元素规则**

`mapDoctypeElemRule`元素是必需的。 不能编辑此元素的属性，因为源XML的根元素始终映射到DITA映射的根`map`元素。

**元素包装规则**

**`elementRules`元素**&#x200B;这将列出所有元素。

**`elementRule`元素** `elementRule`元素是必需的。 这些是所有源元素的映射规则。 当InDesign文档不包含非结构化样式元素时，除非启用“***混合模式***”处理，否则结构化内容将忽略这些元素。

`elementRule`中使用的属性说明如下：

- `@elementName`：源InDesign文档中元素的名称。

- `@local`：请参阅[\#id194CG0V005Z](#id194CG0V005Z)。 \（仅适用于混合文档\）。

- `@mapTo`： DITA目标元素的名称。

- `@refactor`：此可选属性可以选择两个值：

   - `unwrap`：删除匹配的元素，同时保留其内容。

   - `drop`：已删除匹配的元素及其所有内容。

- `@context`：当有多个包装选项可用时，此属性用于链接到特定包装规则。 示例： `li`元素可以封装在`ol`或`ul`元素中。

- `@commentOut`：此属性允许在XML注释中封装目标元素，这样信息就不会丢失，但用户可手动处理。 如果无法强制源内容符合DITA结构规则，这将很有用。


## AEM Guides疑难解答

安装和配置AEM Guides后，您可以对这些问题进行故障诊断。

## 验证引用

您可以运行给定的脚本来验证引用。 这些脚本可帮助您识别损坏的引用，然后对其进行修补或修复。

- `/bin/fmdita/validatebtree?operation=validate` — 报告任何损坏的内容引用，但不会修复它们。
- `/bin/fmdita/validatebtree?operation=patch` — 列出中断的内容引用和修补程序或对其进行修复。

**验证脚本**

使用以下步骤，使用产品包中提供的验证脚本检查引用：

1. 运行验证脚本\[`/bin/fmdita/validatebtree?operation=validate`\]以检查是否存在任何新的已损坏引用。
1. 如果验证脚本报告任何错误，可以使用修补程序脚本对其进行修补程序。
1. 记录以下提供的详细信息，并在必要时与客户成功团队分享：
1. &#x200B;
   - 验证脚本打印的日志
- “`/content/fmdita/references`”的包
- 任何其他所需的详细信息，具体取决于所报告的情景

**修补程序脚本**

使用产品包中提供的修补程序脚本，执行以下步骤来修补任何损坏的引用：

1. 运行修补程序脚本`[/bin/fmdita/validatebtree?operation=patch]`以修复损坏的引用。 脚本执行需要几分钟时间，并在执行过程中打印日志。 执行完成后，它会在末尾打印“`Done`”。

   **注意：*&#x200B;建议您复制并保存日志以供参考。

1. 成功执行修补程序脚本后，可以执行以下检查：
1. &#x200B;
   - 检查`/content/fmdita`下是否创建了新节点“`references_backup_<timestamp>"`”
- 检查引用是否已修复

**记录器**

您还可以为此脚本执行创建一个单独的日志程序，如下所示：

- 在类“`adobe.fmdita.common.BTreeReferenceValidator`”上添加记录器
- 将其设置为`DEBUG`

创建的日志文件将记录与脚本执行相关的所有信息，并在浏览器会话超时同时从浏览器触发脚本的情况下很有用。
