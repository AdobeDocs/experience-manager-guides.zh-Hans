---
title: 用于创建和激活包的REST API
description: 了解用于创建和激活包的REST API
exl-id: 90686f77-a769-44bc-90eb-116cf9d0341e
feature: Rest API Packages
role: Developer
level: Experienced
TQID: https://experienceleague.adobe.com/cJUVS3QdzVhnZjFF7uoHfpOSBefgm5W2jh-kWM1PvmE
product_v2: id: fae5e35a-80c9-4b94-9352-1a060a6aab1did: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2: id: a01bfd36-4ab8-4bf8-9dc0-5b45b890552eid: a3bd6397-2eb2-4908-a61c-226e26855dcaid: c6d09140-3c91-45d3-b7ed-b681af752f43
role_v2: id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 8ed5c9cb07c56b84b36ef56a55af8738989a6d3f
workflow-type: tm+mt
source-wordcount: 181
ht-degree: 0%

---

# 用于创建和激活包的REST API {#id198CF0260Y4}

以下REST API允许您创建和激活CRX包。

## 创建和激活包

创建并激活CRX包的POST方法。

**请求URL**：
http://*&lt;aem-guides-server\>*： *&lt;port-number\>*/bin/fmdita/activate

**参数**：
请求查询包含JSON规则字符串。 POST请求的内容类型必须设置为`application/json; charset=UTF-8`。

**示例**：
以下示例演示了使用curl命令的API调用：

```XML
curl -u <*username*>:<*password*> -H "Content-Type: application/json; charset=UTF-8"  -k -X POST -d "{[JSON rules string](create-activate-package-java.md#example-create-activate-package-id198JH0B905Z)}" http://<*aem-guides-server*>:<*port-number*>/bin/fmdita/activate
```


**可选参数**

`activationTarget`

**有效值**

Cloud Service的`preview`或`publish`，内部部署软件的`publish`

- 对于Cloud Service，如果参数包含无效值，则包激活失败。

- 对于内部部署软件，如果参数包含无效值，将记录错误，并使用默认值`publish`完成发布。

如果未定义可选参数`activationTarget`，则它会使用Cloud Service和On-premise Software的默认发布代理来激活。



以下示例显示使用带有可选参数的curl命令的API调用：


```XML
curl -u <*username*>:<*password*> -H "Content-Type: application/json; charset=UTF-8"  -k -X POST -d "{[JSON rules string](create-activate-package-java.md#example-create-activate-package-id198JH0B905Z)}" http://<*aem-guides-server*>:<*port-number*>/bin/fmdita/activate?activationTarget=`<validActivationTargetValue>`
```
