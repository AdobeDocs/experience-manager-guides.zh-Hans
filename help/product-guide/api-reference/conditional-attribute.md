---
title: 用于条件属性的REST API
description: 了解用于条件属性的REST API
exl-id: 1f0e023a-422c-47b9-917f-b0d80090471c
feature: Rest API Conditional Attributes
role: Developer
level: Experienced
TQID: https://experienceleague.adobe.com/qtmJN6jjCm3xeNYAaHTWr7G3SZFSOodcVqBOKctR3B8
product_v2: id: fae5e35a-80c9-4b94-9352-1a060a6aab1did: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2: id: a01bfd36-4ab8-4bf8-9dc0-5b45b890552eid: c6d09140-3c91-45d3-b7ed-b681af752f43
subfeature_v2: id: d27d524e-c4e5-4b77-b86b-3db049db0b25
role_v2: id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 8ed5c9cb07c56b84b36ef56a55af8738989a6d3f
workflow-type: tm+mt
source-wordcount: 154
ht-degree: 5%

---

# 用于条件属性的REST API {#id175UB30E05Z}

以下REST API允许您在文件夹配置文件中添加条件属性。

## 在文件夹级别的配置文件中添加条件属性

一种POST方法，用于将条件属性添加到给定的文件夹级配置文件。

**请求URL**：\
http://*<aem-guides-server\>*： *<端口号\>*/bin/fmdita/folderprofiles

**参数**：

| 名称 | 类型 | 必需 | 描述 |
|----|----|--------|-----------|
| `:operation` | 字符串 | 是 | 要调用的操作的名称。 此参数的值为``ADDATTRIBUTEPROFILES``。<br> **注意：**&#x200B;该值不区分大小写。 |
| `profilename` | 字符串 | 是 | 必须添加条件属性的文件夹级别配置文件的显示名称。 |
| `conditionalprofiles` | JSON阵列 | 是 | 由条件属性名称和值组成的JSON数组。 以下示例代码片段显示了具有两个属性（`platform`和`product`）的JSON数组，这两个属性分配了多个值。 |

```JSON
[  {    name: "platform",    
        values: [       
                {value: "win", label: "Windows"},       
                {value: "mac", label: "Mac OS"}    
                ]},
                {    
                    name: "product",    
                    values: [      
                        {value: "aem_1", label: "AEM 6.1"},     
                        {value: "aem_4,  label: "AEM 6.4"}  
                        ]  
                }]
```

**响应值**：\
返回HTTP 200 \(Successful\)响应。
