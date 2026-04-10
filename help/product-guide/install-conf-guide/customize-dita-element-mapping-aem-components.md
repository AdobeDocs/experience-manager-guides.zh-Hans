---
title: 使用AEM组件自定义dita元素映射
description: 了解如何使用AEM组件自定义DITA元素映射
feature: Output Generation
role: Admin
level: Experienced
source-git-commit: 834959a6a0e22cd5d2b2c5d0e57ceb6d45c0c666
workflow-type: tm+mt
source-wordcount: '1268'
ht-degree: 1%

---


# 使用AEM组件自定义DITA元素映射 {#id1679J600HEL}

AEM Guides中的DITA元素映射到其对应的AEM组件。 AEM Guides在发布和审阅等工作流中使用此映射，将DITA元素转换为相应的AEM组件。 映射在`elementmapping.xml`文件中定义，可使用Cloud Service设置的包管理器访问该文件，也可以在CRXDE Lite模式下通过以下URL访问该文件，以进行内部部署设置。`/libs/fmdita/config/elementmapping.xml`

>[!NOTE]
>
> 请勿在``libs``节点中使用默认配置文件中的任何自定义设置。 您必须在``libs``节点中创建``apps``节点的叠加，并仅更新``apps``节点中的所需文件。

您可以使用预定义的DITA元素映射，也可以将DITA元素映射到自定义AEM组件。 要使用自定义AEM组件，您需要了解`elementmapping.xml`文件的结构。

## elementmapping.xml结构

`elementmapping.xml`结构的高级概述说明如下：

1. 首先基于元素名称搜索每个DITA元素以查找相应的组件映射。 例如：

   ```XML
   <ditaelement>     
      <name>**substeps**</name>  
      <class>- topic/ol task/substeps</class>  
      <componentpath>dita/components/ditaolist</componentpath>  
      <type>COMPOSITE</type>  
      <target>para</target>
   </ditaelement>
   ```

   在上述示例中，所有`substeps` DITA元素都使用`dita/components/ditaolist`组件渲染。

1. 如果DITA元素没有找到基于名称的匹配项，则会根据`class`进行匹配。 例如：

   ```XML
   <ditaelement>  
      <name>topic</name>  
      <class>**- topic/topic**</class>  
      <componentpath>fmdita/components/dita/topic</componentpath>  
      <type>COMPOSITE</type>  
      <target>para</target>  
      <attributemap> 
         <attribute from="id" to="id" />  
      </attributemap>
   </ditaelement>
   ```

   在上述示例中，如果没有为`task`元素定义映射，则`task`元素将映射到上述组件，因为`task`继承自`topic`组件。

1. 当元素具有相应的组件映射时，其子元素的进一步处理由`type`决定。 例如：

   ```XML
   <ditaelement>  
      <name>title</name>  
      <class>- topic/title</class>  
      <componentpath>foundation/components/title</componentpath>  
      <type>**STANDALONE**</type>  
      <target>para</target>  
      <textprop>jcr:title</textprop>
   </ditaelement>
   ```

   `type`采用以下值：

   - 组合：子元素&#x200B;*的元素到组件*&#x200B;的映射也继续。

   - 独立：当前元素的子元素是&#x200B;*未进一步映射*。

   在上述示例中，如果`<title>`元素具有任何子元素，则这些子元素将不会映射到任何其他组件。 `<title>`元素的组件负责呈现`<title>`元素中的所有子元素。

1. 如果有多个组件映射到单个DITA元素，则会选择该元素的最佳匹配项。 要选择最佳匹配元件，需要考虑DITA元素的域和结构专业化。

   如果存在具有域专门化的DITA元素并且为域专门化映射了组件，则该组件被赋予高优先级。

   同样，如果存在具有结构专门化的DITA元素并且为结构专门化映射了某个组件，则该组件将获得高优先级。

1. 您可以在元素映射中使用`<attributemap>`将属性值映射到相应的节点属性。
1. `textprop`可用于将DITA元素的文本内容序列化为节点属性。 此外，可以在元素标记中多次使用它来序列化已发布层次结构中多个位置的文本内容。 您还可以自定义目标属性的位置和名称。 例如：

   ```XML
   <ditaelement>
      <name>title</name>
      <componentpath>foundation/components/title</componentpath>
      <type>STANDALONE</type>
      <target>para</target>
       <textprop>**jcr:title**</textprop>
   </ditaelement>
   ```

   上述元素映射指定`<title>`元素的文本内容将保存为输出节点上名为`jcr:title`的属性的值。

1. `xmlprop`可用于将给定元素的整个XML序列化为节点属性。 然后，组件可以读取此节点属性并进行自定义渲染。 例如：

   ```XML
   <ditaelement>
       <name>svg-container</name>
      <class>+ topic/foreign svg-d/svg-container</class>
       <componentpath>fmdita/components/dita/svg</componentpath>
       <type>STANDALONE</type>
       <target>para</target>
      <xmlprop>**data**</xmlprop>
   </ditaelement>
   ```

   上述元素映射指定将元素`<svg-container>`的整个XML标记另存为输出节点上名为`data`的属性的值。

1. 在输出生成过程中有一个特殊的属性映射来处理路径解析。 例如：

   ```XML
   <attributemap>
      <attribute from="href" to="fileReference" ispath="true" rel="source" />
      <attribute from="height" to="height" />
       <attribute from="width" to="width" />
   </attributemap>
   ```

   对于上述`attributemap`，DITA元素中的`href`属性将映射到名为`fileReference`的节点属性。 现在，由于`ispath`设置为`true`，输出生成过程解析此路径，然后在`fileReference`节点属性中设置它。

   此解析如何根据属性映射中`rel`属性的值确定。

   - 如果`rel=source`，则相对于当前正在处理的DITA源文件解析`href`的值。 `href`的值已解析并置于`fileReference`属性的值中。

   - 如果`rel=target`，则相对于根发布位置解析`href`的值。 `href`的值已解析并置于`fileReference`属性的值中。

   如果不希望对路径属性进行任何预处理或解析，则无需指定`ispath`属性。 该值会按原样复制，组件可以执行所需的分辨率。


## DITA元素架构

以下是`elementmapping.xml`文件中的DITA元素架构示例：

```XML
<ditaelement>        
    <name>element_name</name>    
    <class>element_class</class>    
    <componentpath>fmdita/components/dita/component_name</componentpath>    
    <type>COMPOSITE|STANDALONE</type>     
    <attributeprop>propname_a</attributeprop>      
    <textprop>propname_t</textprop>    
    <xmlprop>propname_x</xmlprop>     
    <xpath>xpath expression string</xpath>     
    <target>head|para</target>     
    <wrapelement>div</wrapelement>     
    <wrapclass>class_name</wrapclass>     
    <attributemap>         
        <attribute from="attrname"         to="propname"         ispath="true|false"         rel="source|target" />    
    </attributemap>    
    <skip>true|false</skip> 
</ditaelement>
```

下表介绍了DITA元素架构中的元素：

| 元素 | 描述 |
|-------|-----------|
| `<ditaelement>` | 每个映射元素的顶级节点。 |
| `<class>` | 要为其编写组件的目标DITA元素的类属性。<br>例如，DITA主题的类属性为： <br> `- topic/topic` |
| `<componentpath>` | 映射的AEM组件的CRXDE路径。 |
| `<type>` | 可能的值： <br> -   **复合**：处理子元素以及<br> -   **STANDALONE**：跳过子元素的处理 |
| `<attributeprop>` | 用于将序列化DITA属性和值作为属性映射到AEM节点。 例如，如果您有`<note type="Caution">`元素，并且为此元素映射的组件有`<attributeprop>attr_t</ attributeprop>`，则节点的属性和值将序列化为相应AEM节点\(`attr_t`\)的`attr_t->type="caution"`属性。 |
| `<textprop>propname_t</textprop>` | 将`getTextContent()`输出保存到`propname_t.` <br>定义的属性 **注意：**&#x200B;这是一个优化的属性。 |
| `<xmlprop>propname_x </xmlprop>` | 将此节点的序列化XML保存到&#x200B;`propname_x.<br> `**定义的属性。注意：**&#x200B;这是一个优化属性。 |
| `<xpath>` | 如果在元素映射中提供了XPath元素，则还应与元素名称和类一起满足XPath条件以使用组件映射。 |
| `<target>` | 将DITA元素放置在crx存储库中的指定位置。<br>可能的值： <br> - **head**：在标题节点<br> - **text**：在段落节点下 |
| `<wrapelement>` | 要将内容包装在其中的HTML元素。 |
| `<wrapclass>` | 属性`wrapclass.`的元素值 |
| `<attributemap>` | 包含一个或多个`<attribute>`节点的容器节点。 |
| `<attribute from="attrname" to="propname" ispath="true\|false" rel="source\|target" />` | 将DITA属性映射到AEM属性： <br> -   **`from`**： DITA属性名称<br> -   **`to`**： AEM组件属性名称<br> -   **`ispath`**：如果属性是路径值\（例如： *image*\） <br> -   **`rel`**：如果路径是源或目标<br> **注意：**&#x200B;如果`attrname`以`%`开头，则将`attrname minus '%'`映射到prop“`propname`”。 |

**其他备注**

- 如果计划覆盖默认元素映射，建议不要在默认`elementmapping.xml`文件中进行更改。 您应该创建一个新的映射XML文件，并将该文件放置在其他位置，最好是放置在您创建的自定义apps文件夹中。

- 在`elementmapping.xml`文件中，有许多映射条目引用fmdita/components/dita/wrapper组件。 包装器是一个通用组件，它使用站点节点上的属性来生成相关的HTML，从而呈现相对简单的DITA结构。 它使用`wrapelement`属性生成封闭标记并将子渲染委派给相应的组件。 当您只需要容器组件时，此选项非常有用。 您可以将Wrapper组件与`div`和`p`属性结合使用，而不是创建用于呈现特定容器标记（如`wrapelement`或`wrapclass`）的新组件，以实现相同的效果。

- 建议不要在字符串JCR属性中保存大量文本。 输出生成中的优化属性类型计算可确保大型文本内容不会另存为字符串类型。 相反，当需要保存大于特定阈值的内容时，属性的类型会更改为二进制。 默认情况下，此阈值配置为512字节，但可以通过更改&#x200B;*另存为二进制阈值*&#x200B;设置在Configuration Manager \(**com.adobe.fmdita.config.ConfigManager**\)中更改。

- 如果您计划覆盖某些\（而非全部\）元素映射，则无需复制整个`elementmapping.xml`文件。 您需要创建一个新的XML映射文件，并仅定义要覆盖的元素。

- 在自定义位置中创建XML文件后，更新`Override Element Mapping`包中的`com.adobe.fmdita.config.ConfigManager`设置。


