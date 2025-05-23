---
title: AEM Guides中的DITA内容重用
description: 这篇简短文章介绍AEM Guides和DITA如何帮助您在使用内容重用性时节省时间和精力
role: User, Admin
author: Pulkit Nagpal(punagpal)
exl-id: 1522ebf5-2aea-4d8f-ade7-367227b31dd9
source-git-commit: f971be4be9e2d32618616727cd9c682941dd3fb2
workflow-type: tm+mt
source-wordcount: '541'
ht-degree: 0%

---

# AEM Guides中的内容重用性

AdobeAEM Guides利用DITA的优势为内容重用提供用户友好的界面。

本文将讨论：

1. [使用主题引用(](#reusability-using-topic-referencestopicref)
2. [使用内容引用(](#reusability-using-content-reference-conref--conkeyref)
3. [通过在AEM Guides中执行拖放操作来重复使用内容的额外提示](#reuse-content-with-a-single-click-in-aem-guides)

## 使用主题引用的可重用性(topicref)



假设您是一家制造公司，拥有安全防范或故障排除技术的通用主题。

这些可在每个机器型号的特定用户手册中参考和修改，从而减少冗余并确保核心安全信息保持一致。

```
<map id="user_manual_model 100" title="ABC Model 100 User Manual ">


<topicref href="Safety_Information.dita" format="dita">
</topicref>
.
.
.
.
.
</map>
```


同样适用于Model 200

```
<map id="user_manual_model 200" title="ABC Model 200 User Manual ">

<topicref href="Safety_Information.dita" format="dita">
</topicref>
.
.
.
.
.
  
</map>
```

## 使用内容引用的可重用性(conref &amp; conkeyref)

内容引用(conref)属性允许您链接到内容的其他部分。 这提高了可重用性，减少了冗余。

例如：

假设您是一家金融企业，有一个通用的KYC主题，其中包含针对个人、公司等的KYC过程。

您希望对“保存帐户”和“Demat帐户”主题重复使用单个KYC片段。

```
<section id="kyc_requirements_saving_account">
  <title>Know Your Customer (KYC) Requirements</title>
  <p>To comply with regulations and ensure customer identification, all individual applicants for savings  accounts must fulfill the KYC requirements as outlined below</p>
  <p conref=kyc_procedures.dita#individual_kyc></p>
</section>
```

此处`conref=kyc_procedures.dita#indvidual_kyc` kyc_procedures.dita是文件标识符，#individual_kyc是片段标识符。

Kyc_procedure.dita仍然是唯一的信息源。 如果法规更改需要更新KYC流程，请使用新路径更新主题路径。 这些更改将自动反映在引用它的所有主题中。

使用AEM Guides，只需单击两次

步骤1：单击插入可重用内容
![工具栏](../../assets/publishing/content-reusability_image1.png)

<br>

步骤2：选择需要重复使用的文件和片段。
![conref](../../assets/publishing/content-reusability_image2.png)

与“conref”类似，您也可以使用“conkeyref”，其中，您可以通过键引用内容，而不是提供内容路径

代码示例：

```
<section conkeyref="kyc_procedure/individual_kyc_procedure" id="individual_kyc_procedure"></section>
```

键定义如下所示：

```
<map id="ABC_manual">
  <title>ABC_Manual</title>
  <topicref href="kyc_procedure_2020.dita" keys="kyc_procedure" processing-role="resource-only" type="concept">
  </topicref>
  <topicref href="savings_account.dita" type="concept">
  </topicref>
</map>
```

Key - &#39;Kyc_procedure&#39;仍然是信息的单一来源。 如果根据法规要求对KYC流程进行了任何更改，则只需使用一个新主题路径更新一个主题路径即可，这些更改将自动反映在引用它的所有主题中。

```
<map id="ABC_manual">
  <title>ABC_Manual</title>
  <topicref href="kyc_procedure_2024.dita" keys="kyc_procedure" processing-role="resource-only" type="concept">
  </topicref>
  <topicref href="savings_account.dita" type="concept">
  </topicref>
</map>
```

在此处，由于最近的法规更改，主题路径已从“kyc_procedure_2020.dita”更改为“kyc_procedure_2024.dita”。

使用AEM Guides，只需单击两次

步骤1：单击插入可重用内容
![工具栏](../../assets/publishing/content-reusability_image1.png)

步骤2：选择根映射（可选）、键以及需要重用的片段。
![conkeyref](../../assets/publishing/content-reusability_image3.png)

此处已自动选择根映射，因为它已在映射视图中打开。


## 在AEM Guides中单击一下即可重用内容

AEM Guides提供了一种“可重复使用的内容”功能，只需单击一下即可添加内容引用。

步骤1：将通用主题添加到可重用内容

![添加可重复使用的内容](../../assets/publishing/content-reusability_image4.png)

步骤2：添加后，拖放要在任何目标主题中重用的片段。

![添加可重复使用的内容gif](../../assets/publishing/content-reusability_image5.gif)



## 常见问题解答

- ### 在“重用内容”对话框中选择了文件/键后，所有内容都未显示

将ID分配给要在其他主题中重用的片段（Dita元素）

- ## 在“重用内容”对话框中未显示键

  请确保已在映射视图中打开了根映射/父映射，该视图具有键定义，或在同一对话框中手动添加根映射路径。


<br>
<br>
<br>


在AEM Guides社区[论坛](https://experienceleaguecommunities.adobe.com/t5/experience-manager-guides/ct-p/aem-xml-documentation)上发布任何查询。
