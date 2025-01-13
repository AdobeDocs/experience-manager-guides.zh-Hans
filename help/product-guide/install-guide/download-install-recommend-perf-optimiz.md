---
title: Recommendations优化性能
description: 了解Recommendations以实现性能优化
exl-id: b2a836a0-de82-4d89-aae3-43276997da74
feature: Performance Optimization
role: Admin
level: Experienced
source-git-commit: b28b7d96cce69f677b0bcf891b94d7ac84eb1eb0
workflow-type: tm+mt
source-wordcount: '907'
ht-degree: 0%

---

# Recommendations优化性能 {#id213BD0JG0XA}

## 配置数据存储\（必需\）

**有什么变化？**
在配置`org.apache.jackrabbit.oak.plugins.blob.datastore.FileDataStore.`下将`minRecordLength`属性设置为值`100`有关文件日期存储和S3数据存储的更多信息，请参阅[在AEM 6](https://helpx.adobe.com/experience-manager/6-5/sites/deploying/using/data-store-config.html)中配置节点存储和数据存储。

>[!NOTE]
>
> 对于S3数据存储，维护数据存储中的内容的成本也取决于请求数量。 因此，在S3中进行此设置时，还应考虑每个请求的设置成本和缓存大小。

**何时配置？**
在初始设置之后，但在迁移任何内容之前。 您必须在现有系统上执行这项更改，以确保将所有新内容存储在数据存储中，而不是区段存储中。

**此更改的结果**
DITA文件保存在数据存储中，而不是区段存储中。 这会将区段存储大小保持在建议的限制下，从而提高系统的响应性。

## 更新Lucene索引\（必需\）

**有什么变化？**
从oak：index/lucene中排除/var/dxml。

>[!NOTE]
>
> AEM Guides从不使用Lucene索引搜索/var/dxml节点中的内容。

**何时配置？**
如果您在迁移内容之前在新系统上进行了此更改，则只需更新oak：index/lucene。 否则，在内容已迁移的现有系统上，在oak：index/lucene中进行更改后，重新构建Lucene \(*)的索引，可能需要几个小时才能完成*\)。

**此更改的结果**
此更改会阻止/var/dxml节点建立索引并存储在区段存储中。

## Java内存优化\（必需\）

**有什么变化？**
应根据基础架构和磁盘大小仔细调整JVM启动参数。 建议您咨询Adobe支持，以获得有关访问理想配置的帮助。 但是，您可以自行尝试以下配置：

 — 将JVM栈大小设置为最小总可用内存的1/4。 使用参数`-Xmx<size>`设置栈内存大小。 将 — `Xms`的值设置为等于`-Xmx`。

 — 启用`-XX:+HeapDumpOnOutOfMemoryError`并设置`-XX:HeapDumpPath=</path/to/folder``>`的路径。

 — 启用Java GC日志为：

`* -XX:+PrintGCDateStamps`

`* -verbose:gc`

`* -XX:+PrintGCDetails`

`* -XX:+PrintTenuringDistribution`

`* -Xloggc:</path/to/gc.log>`

 — 通常，对于Java 11，使用G1GC \(`-XX:+UseG1GC`\)；对于Java 8，使用CMS \(-`XX:+UseConcMarkSweepGC`\)。

 — 使用`-XX:NewRatio`控制年轻一代内存大小的大小。 默认值为2，这意味着内存的1/3用于年轻一代。 由于有许多对象被快速创建和销毁，使用值1会将内存的1/2分配给年轻一代。

 — 使用`-XX:MaxTenuringThreshold`控制要提升到旧层代的对象数。 使用值15 \(default\)可延迟将对象提升到旧层代的时间。

**何时配置？**
如果是在现有系统上进行此更改，则需要重新启动系统。 如果是全新安装，则在系统启动之前应在启动脚本\(.bat或.sh\)文件中进行此更改。

**此更改的结果**
这导致最佳栈大小和GC的规范执行。

## 创作实例上的客户端库缩小\（可选\）

**有什么变化？**
应将客户端库设置为在创作实例中缩小。 这可以确保在用户从不同位置浏览系统时下载的字节数减少。 要进行此更改，请从Felix控制台的**HTML库管理器**&#x200B;中设置配置。

**何时配置？**
这可以在运行时通过Felix控制台或通过代码部署完成。

**此更改的结果**
由于为加载客户端库而传输的字节数减少，这项更改会缩短页面在创作实例上的加载时间。

## 配置并发发布线程\（必需，具体取决于用例\）

**有什么变化？**
如果您使用DITA-OT发布输出并且还定义了多个并发发布线程，则需要此更改。

默认情况下，AEM Guides将发布线程数设置为CPU+1数量。 但是，建议将此值设置为CPU总数的一半\(1/2\)或三分之一\(1/3\)。 为此，请根据建议在配置`com.adobe.fmdita.publish.manager.PublishThreadManagerImpl`下设置&#x200B;**生成池大小**&#x200B;属性。

**何时配置？**
这可以在运行时通过Felix控制台或通过代码部署完成。

**此更改的结果**
此更改可确保在执行中的创作实例上，所有资源不被分配给发布操作。 这还可以使系统资源可供作者使用，从而提供更好的用户体验。

## 为AEM Site输出生成配置节点的批处理大小\（必需，具体取决于用例\）

**有什么变化？**
如果要生成AEM Sites输出，则必须进行此更改。

根据您的系统配置，将`com.adobe.fmdita.config.ConfigManager`下的&#x200B;**限制栈**&#x200B;中的AEM站点页数设置为一个数字。 此属性定义在生成网站页面时要提交的节点的批量大小。 例如，在具有较大数量的CPU和栈大小的系统上，您可以将默认值从`500`增加到更大的数量。 您需要使用更改后的值测试运行，以得到此属性的最佳值。

**何时配置？**
这可以在运行时通过Felix控制台或通过代码部署完成。

**此更改的结果**
**Limit AEM Site Pages in Heap**&#x200B;属性的数量增加会优化AEM Site输出生成过程。


**父主题：**[&#x200B;下载并安装](download-install.md)
