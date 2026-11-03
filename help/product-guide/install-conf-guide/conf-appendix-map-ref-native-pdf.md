---
title: 在本机PDF输出中配置映射引用的附录渲染
description: 了解如何将Experience Manager Guides配置为将附录中子映射下添加的主题呈现为本机PDF输出中的附录内容。
feature: Output Generation
role: Admin
level: Experienced
source-git-commit: 63ae0f947d50646bed34cd815db6b9fb585fc015
workflow-type: tm+mt
source-wordcount: '284'
ht-degree: 0%
---

# 在本机PDF输出中配置映射引用的附录渲染

在本机PDF输出中，`<appendix>`元素内的子映射中引用的主题可以呈现为章节而不是附录。 默认情况下，Experience Manager Guides会按元素名称对映射引用进行分类，一旦映射在处理期间被扁平化，该信息将丢失。

使用此设置可改为使用DITA-OT生成的`class`属性对映射引用进行分类。 然后，附录子映射中的主题呈现为附录。

>[!NOTE]
>
>此设置更改对映射引用进行分类的方式。 默认情况下处于禁用状态。 仅当您的内容将主题放置在`<appendix>`内的子映射中，并且您看到它们在本机PDF输出中呈现为章节时，才启用它。

## 何时使用此配置

请考虑以下书籍地图示例：

- `<appendix>`元素直接引用主题。 这些主题在生成的PDF中作为附录呈现。

  ```XML
  <booktitle>
      <mainbooktitle>Product Guide</mainbooktitle>
    </booktitle>
    <frontmatter>
      <booklists>
        <toc/>
        <tablelist/>
      </booklists>
      <preface href="topics/preface.dita">
      </preface>
    </frontmatter>
    <chapter class="foo" href="topics/getting-started.dita">
    </chapter>  
    <appendix href="topics/appendix-reference-tables.dita">
    </appendix>
    <appendix href="topics/appendix-troubleshooting.dita">
    </appendix>
    <backmatter>
      <booklists>
        <indexlist/>
      </booklists>
    </backmatter>
  </bookmap>`
  ```

- 另一个`<appendix>`元素引用了子映射，并且子映射使用`<topicref>`引用主题。

  ```xml
  <booktitle>
      <mainbooktitle>Product Guide</mainbooktitle>
    </booktitle>
    <frontmatter>
      <booklists>
        <toc/>
        <tablelist/>
      </booklists>
      <preface href="topics/preface.dita">
      </preface>
    </frontmatter>
    <chapter class="foo" href="topics/getting-started.dita">
    </chapter>  
    <appendix format="ditamap" href="submap-for-appendix.ditamap" type="map">
    </appendix>
    <backmatter>
      <booklists>
        <indexlist/>
      </booklists>
    </backmatter>
  </bookmap>
  ```

  附录子映射：

  ```xml
  <map id="GUID-cc306264-825c-455e-89db-d27af9197a2f">
    <title>submap-for-appendix</title>
    <topicref href="topics/appendix-reference-tables.dita" type="reference">
    </topicref>
    <topicref href="topics/appendix-troubleshooting.dita" type="topic">
    </topicref>
  </map>
  ```

如果没有此配置，第一个附录中的主题将以附录的形式呈现，但子映射中的主题以章节的形式呈现。 只发布主题；子映射本身用于层次结构，不会显示在输出中。

## 配置设置

以下是配置此设置的说明：

1. 使用[配置覆盖](../install-conf-guide/download-install-config-override.md)中提供的说明创建配置文件。

2. 在配置文件中，提供以下（属性）详细信息：

   | PID | 属性键 | 属性值 |
   | --------------------------------------- | -------------------------------- | ----------------------------- |
   | `com.adobe.fmdita.config.ConfigManager` | `guides.publish.config` | {USE_DITA_OT_GENERATED_CLASS&quot;： false} |

3. 将该值设置为`true`以启用该设置，并使用Cloud Manager部署配置。