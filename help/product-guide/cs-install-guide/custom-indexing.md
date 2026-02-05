---
title: 自定义索引部署
description: 了解如何自定义索引内容
feature: Web Editor Configuration
role: Admin
level: Experienced
source-git-commit: 9a4f0391c464d69ea65ecfdaac6ecdcb17d1a3da
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 3%

---

# 部署用于查找和替换(Source视图)功能的自定义索引

## 概述

本指南提供了在Adobe Experience Manager (AEM) as a Cloud Service上部署`guidesAssetLucene‑1‑custom‑1`自定义索引的分步说明。 虽然创作视图中的标准查找和替换功能在没有此索引的情况下工作，但需要专门自定义索引才能在Source视图中启用查找和替换。 “查找和替换”(Source视图)不仅允许您搜索可见的创作内容，而且允许您搜索底层XML结构；包括元素、标记和属性值。

## 先决条件

在继续索引部署之前，请确保您已：

- 已安装AEM Guides的&#x200B;**AEM as a Cloud Service环境**
- **访问项目的代码库** （Git存储库）
- 具有部署权限的&#x200B;**Cloud Manager访问权限**

## 索引定义

要启用查找和替换(Source视图)功能，您需要将名为&#x200B;**`guidesAssetLucene-1-custom-1`**&#x200B;的自定义索引部署到AEM Cloud Service环境。

### 索引名称

```
guidesAssetLucene-1-custom-1
```

### 索引定义(.content.xml)

在项目中创建以下索引定义：

`ui.apps/src/main/content/jcr_root/_oak_index/guidesAssetLucene-1-custom-1/.content.xml`

```xml
<?xml version="1.0" encoding="UTF-8"?>
<jcr:root xmlns:jcr="http://www.jcp.org/jcr/1.0" xmlns:dam="http://www.day.com/dam/1.0"
          xmlns:nt="http://www.jcp.org/jcr/nt/1.0" xmlns:oak="http://jackrabbit.apache.org/oak/ns/1.0"
          xmlns:rep="internal"
          jcr:mixinTypes="[rep:AccessControllable]"
          jcr:primaryType="oak:QueryIndexDefinition"
          async="[async,nrt]"
          compatVersion="{Long}2"
          evaluatePathRestrictions="{Boolean}true"
          includedPaths="[/content/dam]"
          selectionPolicy="tag"
          tags="[ditaSearch]"
          type="lucene">

    <aggregates jcr:primaryType="nt:unstructured">
        <dam:Asset jcr:primaryType="nt:unstructured">
            <include0
                    jcr:primaryType="nt:unstructured"
                    path="jcr:content/renditions/original/jcr:content"
                    relativeNode="{Boolean}true"/>
        </dam:Asset>
    </aggregates>

    <analyzers jcr:primaryType="nt:unstructured">
        <default jcr:primaryType="nt:unstructured">
            <tokenizer
                    jcr:primaryType="nt:unstructured"
                    name="Whitespace"/>
        </default>
    </analyzers>

    <indexRules jcr:primaryType="nt:unstructured">
        <dam:Asset
                jcr:primaryType="nt:unstructured"
                indexNodeName="{Boolean}true">
            <properties jcr:primaryType="nt:unstructured">
                <cqTags
                        jcr:primaryType="nt:unstructured"
                        name="jcr:content/metadata/cq:tags"
                        nodeScopeIndex="{Boolean}true"
                        propertyIndex="{Boolean}true"
                        useInSpellcheck="{Boolean}true"
                        useInSuggest="{Boolean}true"/>
                <jcrLastModified
                        jcr:primaryType="nt:unstructured"
                        name="jcr:content/jcr:lastModified"
                        ordered="{Boolean}true"
                        propertyIndex="{Boolean}true"
                        type="Date"/>
                <jcrCreated
                        jcr:primaryType="nt:unstructured"
                        name="jcr:created"
                        ordered="{Boolean}true"
                        propertyIndex="{Boolean}true"
                        type="Date"/>
                <guidesParentMaps
                        jcr:primaryType="nt:unstructured"
                        name="jcr:content/guidesParentMaps"
                        propertyIndex="{Boolean}true"/>
                <guidesDirectParentMaps
                        jcr:primaryType="nt:unstructured"
                        name="jcr:content/guidesDirectParentMaps"
                        propertyIndex="{Boolean}true"/>
                <ditaClass
                        jcr:primaryType="nt:unstructured"
                        name="jcr:content/metadata/dita_class"
                        propertyIndex="{Boolean}true"/>
                <nodeNameLowerCase
                        jcr:primaryType="nt:unstructured"
                        function="fn:lower-case(fn:name())"
                        ordered="{Boolean}true"
                        propertyIndex="{Boolean}true"/>
                <cqDriveLock
                        jcr:primaryType="nt:unstructured"
                        name="jcr:content/cq:driveLock"
                        propertyIndex="{Boolean}true"
                        ordered="{Boolean}true"/>
                <docState
                        jcr:primaryType="nt:unstructured"
                        name="jcr:content/metadata/docstate"
                        propertyIndex="{Boolean}true"
                        ordered="{Boolean}true"/>
                <jcrPath
                        jcr:primaryType="nt:unstructured"
                        function="fn:path()"
                        ordered="{Boolean}true"/>
                <dcTitleLowerCase
                        jcr:primaryType="nt:unstructured"
                        function="fn:lower-case(jcr:first(jcr:content/metadata/@dc:title))"
                        propertyIndex="{Boolean}true"
                        ordered="{Boolean}true"/>
                <dcTitle
                        jcr:primaryType="nt:unstructured"
                        name="jcr:content/metadata/dc:title"
                        propertyIndex="{Boolean}true"/>
            </properties>
        </dam:Asset>
    </indexRules>

    <tika jcr:primaryType="nt:unstructured">
        <mimeTypes jcr:primaryType="nt:unstructured">
            <application jcr:primaryType="nt:unstructured">
                <xml
                        jcr:primaryType="nt:unstructured"
                        mappedType="application/dita+xml"/>
            </application>
            <text jcr:primaryType="nt:unstructured">
                <markdown
                        jcr:primaryType="nt:unstructured"
                        mappedType="text/markdown+source"/>
            </text>
        </mimeTypes>
    </tika>
</jcr:root>
```

## 部署步骤

有关将自定义索引部署到AEM as a Cloud Service的详细说明，请查看[Content Search and Indexing - AEM as a Cloud Service](https://experienceleague.adobe.com/zh-hans/docs/experience-manager-cloud-service/content/operations/indexing)。

### 此索引的重要点

按照部署指南执行操作时，请为“查找和替换”索引使用以下详细信息：

- **索引名称**： `guidesAssetLucene-1-custom-1`
- **索引类型**：完全自定义索引（不是OOTB索引的自定义）
- **位置**： `ui.apps/src/main/content/jcr_root/_oak_index/guidesAssetLucene-1-custom-1/.content.xml`
- **需要包属性**：
   - `noIntermediateSaves=true`
   - `allowIndexDefinitions=true`

## 重新索引

当您通过AEM as a Cloud Service的CI/CD管道部署索引时，Cloud Manager会&#x200B;**自动**&#x200B;处理重新索引问题。

索引通常自动处理。 但是，如果在正确部署和索引过程完成后旧数据仍然不可搜索，则应当执行一次手动索引重新索引。

### 期待完成的任务

- 索引作业将在部署后自动启动。
- 您可以在Cloud Manager内部版本页面上监控进度。
- 索引期间环境保持完全可操作。

## 验证

部署和索引完成后，请验证索引是否正常工作。

### 验证索引部署

在您的开发环境中(如果CRXDE Lite可用)：

1. 导航到 `/oak:index/guidesAssetLucene-1-custom-1`。
2. 使用预期配置验证节点是否存在。

### 测试查找和替换功能

主要验证是测试该功能：

1. 打开AEM Guides。
2. 导航到&#x200B;**工具** > **指南** > **在存储库中查找和替换**。
3. 在DITA或Markdown文件中配置文本搜索。
4. 验证是否正确返回了搜索结果。
5. 在测试文件中测试替换功能。

## 其他资源

- [AEM as a Cloud Service索引文档](https://experienceleague.adobe.com/zh-hans/docs/experience-manager-cloud-service/content/operations/indexing)
- [Apache Jackrabbit Oak Indexing指南](https://jackrabbit.apache.org/oak/docs/query/indexing.html)
- [AEM Guides文档](https://experienceleague.adobe.com/en/docs/experience-manager-guides)
- [Cloud Manager 文档](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-manager)
