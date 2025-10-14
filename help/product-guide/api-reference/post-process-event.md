---
title: 后处理事件处理程序
description: 了解后处理事件处理程序
exl-id: 3b105ff5-02d4-40e3-a713-206a7fcf18b2
feature: Post-Processing Event Handler
role: Developer
level: Experienced
source-git-commit: 8e57d4048f4aa13d7f77f25082d4e7aa329ee355
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 5%

---

# 后处理事件处理程序 {#id175UB30E05Z}

## UUID和Cloud Service

Adobe Experience Manager Guides公开用于执行任何后处理操作的`com/adobe/guides/postprocess/complete`事件。 只要对DITA文件执行操作，就会触发此事件。 对DITA文件执行的以下操作会触发此事件：

- 上传
- 创建
- 修改

>[!NOTE]
>
> 后处理事件是通过启用`fire.processing.events`标志而触发的，该标志是`fmdita config manager`中的配置参数。 如果设置为true，它会触发事件(com/adobe/guides/postprocess/complete)以跟踪后处理完成。 默认情况下，设置为false（禁用）。

您需要创建一个Adobe Experience Manager事件处理程序，以读取此事件中可用的属性并进行进一步处理。

活动详情说明如下：

**事件名称**：

```
com/adobe/guides/postprocess/complete 
```

**参数**：

| 名称 | 类型 | 描述 |
|----|----|-----------|
| `path` | 字符串 | 触发此事件的文件的路径。 通常，这是已对其执行操作的文件。 |
| `eventType` | 字符串 | 事件的类型，即CREATE或MODIFY。 |
| `status` | 字符串 | 所执行操作的返回状态。 可能的选项为： - <br>- SUCCESS：后处理操作已成功完成。 <br> — 失败：后处理操作因某些错误而失败。 |
| `errorMsg` | 字符串 | 后处理操作失败时的错误消息。 |
| `uuid` | 字符串 | 触发此事件的文件的UUID。 通常，这是已对其执行操作的文件。 |

**示例事件侦听器**


```
@Component(service = EventHandler.class,
        immediate = true,
        property = {
                EventConstants.EVENT_TOPIC + "=" + "com/adobe/guides/postprocess/complete",
        })
public class PostProcessCompleteEventHandler implements EventHandler {

    protected final Logger log = LoggerFactory.getLogger(this.getClass());

    @Override
    public void handleEvent(final Event event) {
        Set<String> propertyNames = new HashSet<>(Arrays.asList(event.getPropertyNames()));
        Map<String, String> properties = new HashMap<>();
        properties.put("path", (String) event.getProperty("path"));
        properties.put("eventType", (String) event.getProperty("eventType"));
        properties.put("status", (String) event.getProperty("status"));
        if(propertyNames.contains("errorMsg")) {
            properties.put("errorMsg", (String) event.getProperty("errorMsg"));
        }
        if (propertyNames.contains("uuid")) {
            properties.put("uuid", (String) event.getProperty("uuid"));
        }
        String eventTopic = event.getTopic();
        log.debug("eventTopic {}", eventTopic);
        for(Map.Entry entry:properties.entrySet()) {
            log.debug(entry.getKey() + " : " + entry.getValue());
        }
    }
}
```

## 非UUID


Adobe Experience Manager Guides会公开用于执行任何后处理操作的com/adobe/fmdita/postprocess/complete事件。 只要对DITA文件执行操作，就会触发此事件。 对DITA文件执行的以下操作会触发此事件：

>[!NOTE]
>
> 此事件不会为AEM 6.1中的删除操作触发。

- 上传
- 创建
- 修改
- 删除

您需要创建一个Adobe Experience Manager事件处理程序，以读取此事件中可用的属性并进行进一步处理。

活动详情说明如下：

**事件名称**：

```
com/adobe/fmdita/postprocess/complete 
```

**参数**：

| 名称 | 类型 | 描述 |
|----|----|-----------|
| `path` | 字符串 | 触发此事件的文件的路径。 通常，这是已对其执行操作的文件。 |
| `status` | 字符串 | 所执行操作的返回状态。 可能的选项为： - <br>- SUCCESS：后处理操作已成功完成。 <br> — 已完成，但出现错误：后处理操作已完成，但有一些错误。 <br> — 失败：后处理操作因某些错误而失败。 |
| `message` | 字符串 | 如果状态为COMPLETED WITH ERRORS或FAILED ，则此参数包含有关错误或失败原因的详细信息。 |
| `operation` | 字符串 | 对文件执行的后处理操作。 可能的选项为：<br> — 添加<br> — 更新<br> — 删除 |
