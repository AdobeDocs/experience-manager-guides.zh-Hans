---
title: 将AEM Assets元数据传播到DITA-OT插件生成的输出
description: 在AEM中配置DITA-OT插件和内容以将元数据推送到生成的输出
role: Developer
feature: DITA-OT publishing
source-git-commit: ed35fa94d9c3cec70a4959d7efe69678b066a2e0
workflow-type: tm+mt
source-wordcount: '906'
ht-degree: 0%

---


# 关于本文

在本文中，我们将说明如何对DITA-OT插件实施更改以读取metadata.xml _（可用于临时文件）_，并利用AEM Guides发布工作流传递的属性在DITA-OT插件中并在生成的输出中设置它。

概括地说，以下是您将在本文中学习的步骤：
- 在AEM Guides中对ditamap的输出预设设置元数据
- 在生成输出时，访问DITA-OT临时目录中的此metadata.xml
- 在DITA-OT插件中实施以读取此&#x200B;_metadata.xml_，并使用生成的输出中的可用属性
- 检查生成的输出以查看传播的元数据

## 背景

借助AEM Guides，您可以使用DITA-OT插件发布到您选择的输出格式，并使用配置的插件，以及
您还可以将在AEM DAM中管理的资源的元数据传递给DITA-OT进程，以便在生成的输出中使用它 — 请参阅关于如何设置ditamap/主题以通过输出预设传递元数据的文档](https://experienceleague.adobe.com/en/docs/experience-manager-guides/using/user-guide/output-gen/pass-metadata-dita-ot)[


## 假设

您已使用AEM Guides版本4.4.0/2024.6或更高版本设置AEM
您事先知道DITA-OT的工作方式及其目录结构


## 步骤说明

### 在资源中设置元数据

利用AEM Assets元数据架构，您可以在AEM中为Assets创建自定义属性字段，并且用户可以为资源分配元数据。 以&#x200B;_topic_&#x200B;资源为例，可以设置名为&#x200B;_customprop_&#x200B;的元数据作为示例 — 请参阅下面的屏幕快照：

![在元数据编辑器中为资源设置属性](../../assets/publishing/assets-metadata-properties-ui-customprop.png)


### 配置ditamap输出预设上的元数据以传递到DITA-OT

在映射上配置您选择的输出预设以导出元数据并传递到DITA-OT
假设我们正在使用DITA-OT插件（如_adobe.html_）生成HTML5输出。
请参阅下面的屏幕快照，了解如何为映射配置输出预设以将元数据传递到DITA-OT插件。
1. 打开映射并浏览到此映射的&#x200B;_输出_&#x200B;选项卡，然后打开HTML5预设，然后单击&#x200B;_高级_&#x200B;选项卡，在此上将转换名称设置为&#x200B;_adobe.html_（我们将配置并用于示例的插件，您也可以定义自定义插件）
2. 设置&#x200B;_保留临时文件_，以便能够下载临时文件并检查metadata.xml的形成方式，您可以将其用于开发
3. 选择要通过metadata.xml传递到DITA-OT的元数据属性。 在此示例中，假设我们要传递&#x200B;_dc：title_&#x200B;和&#x200B;_customprop_
4. 保存预设并生成输出
5. 使用预设上显示的按钮下载临时文件

请参阅下面的屏幕截图以了解上述步骤：
![为地图配置输出预设以传递元数据](../../assets/publishing/map-outputpreset-html5-customprop.png)


### 实施DITA-OT插件

#### 访问临时目录中的metadata.xml

在下载的临时文件包中，您会看到一个metadata.xml文件，您可以在其中查看属性和值的结构（请参见下面的屏幕快照）
![metadata.xml结构和结构](../../assets/publishing/publish-tempfiles-metadata-structure.png)

##### 了解metadata.xml

- 此文件包含已发布的所有资源的列表，每个资源具有：
   - 路径元素]的DITA目录[id属性中的文件路径
   - _元数据_&#x200B;元素]下的元数据属性值对[的列表

```
        <Path id="topics\about-this-document.dita">
            <sourceProps>
                ...
            </sourceProps>
            <metadata>
                <meta isArray="false" key="dc:title">About This Document</meta>
                <meta isArray="false" key="customprop">customval</meta>
            </metadata>
        </Path>
```

#### 访问DITA-OT插件中每个资产的元数据

要使DITA-OT插件读取&#x200B;_metadata.xml_&#x200B;及其中可用的属性，我们需要执行以下操作：
- 在&#x200B;_plugins.xml_&#x200B;中定义自定义插件设置，其中定义了插件初始化的参数和集成器，插件文件的样例如下所示：

```
<?xml version="1.0" encoding="UTF-8"?>
<plugin id="com.adobe.html">
    <require plugin="org.dita.html5"/>
    <feature extension="dita.conductor.transtype.check" value="adobe.html"/>
    <feature extension="ant.import" file="integrator.xml"/>
    <feature extension="dita.conductor.html5.param" file="params.xml"/>
    <feature extension="package.version" value="2024.1"/>
</plugin>
```

- 在插件启动时：
   - 设置一个变量以指向metadata.xml文件，即在插件下的&#x200B;_integrator.xml_&#x200B;中设置一个属性以定义元数据文件的路径，并且
   - 定义运行自定义xsl转换规则的文件，即&#x200B;_args.xsl_，在本例中，该文件将指向文件&#x200B;_xsl/adobe-html5.xsl_。
请参阅下面的代码：

```
    <property name="adobe.html.xsl.dir" value="${dita.plugin.com.adobe.html.dir}${file.separator}xsl${file.separator}"/>
    <property name="args.xsl" location="${adobe.html.xsl.dir}adobe-html5.xsl" />
    <dirname property="input.dirname" file="${args.input}"/>
    <makeurl file="${input.dirname}/metadata.xml" property="metadata.url"/>
```

- 将变量&#x200B;_metadata.url_&#x200B;的值传递给自定义XSL以根据需要使用它，即在现有/创建的&#x200B;_param.xml_&#x200B;中将参数传递给插件，请参见下面的params.xml示例文件：

```
    <?xml version="1.0" encoding="UTF-8"?>
    <params xmlns:if="ant:if">
        <param name="metadata.url" expression="${metadata.url}" if:set="metadata.url"/>
    </params>
```

- 在自定义XSL转换文件&#x200B;_xsl/adobe-html5.xsl_&#x200B;中，您可以从元数据文件中读取元数据值，并按照您所需的方式在输出中设置它。 在本例中，我们将向html head > meta标记中添加元数据值。 请参阅下面的代码：

```
<xsl:import href="plugin:org.dita.html5:xsl/dita2html5.xsl"/>
    <xsl:param name="metadata.url"/>
    <xsl:template name="copyright">
        <xsl:if test="doc-available( $metadata.url )">
            <xsl:variable name="docName" select="tokenize( base-uri(), '/' )[ last() ]"/>
            <xsl:variable name="doc" select="doc( $metadata.url )"/>
            <xsl:for-each select="$doc//Path[ ends-with( @id, concat( '\', $docName ) ) ]/metadata/meta">
                <meta name="{ @key }" content="{ . }"/>
            </xsl:for-each>
        </xsl:if>
    </xsl:template>
```

请参阅下面的屏幕截图，突出显示上述步骤
实施dita-ot插件的![步骤](../../assets/publishing/publishing-metadata-dita-ot-plugin-implementation.png)


### 测试插件实施

您可以通过运行以下命令来测试插件，并使用从AEM下载的临时文件（包含映射内容及其metadata.xml）来测试插件

```
./dita --input=docsrc/samples/HTML5/aem_forms_documentation.ditamap --format=adobe.html
```

假设您已将下载的临时文件复制到“DITA-OT/docsrc/samples/HTML5”目录下。
您还可以下载下面资源部分中提供的示例。

执行上述命令时，您可以检查目录“DITA-OT/bin/out”中的输出，其中您可以检查为主题“about-this-document.dita”生成的html文件，该文件的&#x200B;_head_&#x200B;元素中将包含自定义元数据

```
<head>
    <meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
    <meta charset="UTF-8">
    <meta name="copyright" content="(C) Copyright 2024">
    <meta name="DC.format" content="HTML5">
    <meta name="DC.identifier" content="GUID-f193ea85-989d-4d80-99e2-2f5dea3d5310">
    <meta name="DC.language" content="en-US">
    <meta name="dc:title" content="About This Document">
    <meta name="customprop" content="customval">
    <title>About This Document</title>
</head>
```

### 部署

开发DITA-OT插件后，可以使用DITA-OT目录下的&#x200B;_dita —install_&#x200B;命令将此插件集成到DITA-OT中，并将其部署到AEM服务器[有关更多详细信息，请参阅本文](https://experienceleaguecommunities.adobe.com/t5/experience-manager-guides/steps-to-setup-a-custom-dita-ot/td-p/407659)


## 资源

1. 从示例ditamap下载的示例临时文件 — 使用此链接[下载](../../assets/publishing/sample-temp-html5-adobe.html-content.zip)
2. 具有上述说明的实施[的DITA-OT插件使用此链接](../../assets/publishing/sample-custom-plugin-com.adobe.html.zip)下载