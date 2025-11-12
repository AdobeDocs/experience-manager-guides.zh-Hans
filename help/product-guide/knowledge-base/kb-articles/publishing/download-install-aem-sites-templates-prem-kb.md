---
title: 下载并安装适用于内部部署服务的AEM Sites模板
description: 了解如何在Prem Services上下载并安装适用于的AEM Sites模板
feature: Installation
role: Admin
level: Experienced
exl-id: aa843a72-ff0d-4c9a-a87d-48d099087b5e
source-git-commit: 4c564a0ffaa8f287bcaf012634d49dbf1e0682b4
workflow-type: tm+mt
source-wordcount: '440'
ht-degree: 0%

---

# 下载并安装AEM Sites模板（内部部署服务）

本指南提供了设置和配置用于生成AEM Sites的最新AEM Guides模板的分步说明。 按照以下步骤安装所需的包，创建和配置预设，以及生成AEM Sites。

## 先决条件

在继续设置之前，请确保满足以下先决条件：

- **Adobe Experience Manager (AEM)：**&#x200B;已安装&#x200B;**Service Pack** 21、20和19以及&#x200B;**AEM 4.6.0**&#x200B;或更高版本的&#x200B;**AEM Guides 6.5**&#x200B;的运行实例。

- **所需权限**：确保具有以下权限：

   - 访问&#x200B;**软件分发门户**&#x200B;以下载所需的包
   - 访问&#x200B;**CRX包管理器**&#x200B;以在AEM中安装包。
   - 在AEM Guides中创建和修改预设的权限。

- **下载包**：从&#x200B;**软件分发门户**&#x200B;下载以下包：

   - 组件包： on-prem-guides-components.all-1.x.0.zip
   - 站点包：aemg-docs.all-1.x.0.zip

## 使用CRX包管理器安装包

1. **安装组件包：**
   1. 导航到&#x200B;[**CRX包管理器**](http://&lt;your-aem-instance>/crx/packmgr)。
   2. 上传并安装on-prem-guides-components.all-1.x.0.zip包。

2. **安装站点包：**&#x200B;使用CRX包管理器上载并安装aemg-docs.all-1.x.0.zip包。


## 创建和配置AEM站点预设

1. **创建新预设：**
   1. 在AEM Guides中打开DITA映射并导航到&#x200B;**输出**&#x200B;面板。
   2. 选择&#x200B;**创建预设**。
   3. 选择类型为&#x200B;**AEM Sites**。
   4. 输入预设的名称。
   5. 取消选中&#x200B;**使用旧版组件映射**&#x200B;设置。
   6. 选择&#x200B;**添加**&#x200B;以创建预设。

      ![新的输出预设对话框](/help/product-guide/knowledge-base/kb-articles/assets/publishing/new-output-preset.png){width="350" align="left"}


2. **配置AEM站点预设：**&#x200B;有两个选项可用于配置现成(OOTB)站点：

   **选项1：使用站点下拉列表**

   1. 选择&#x200B;**站点**&#x200B;作为&#x200B;**AEMG文档**。
   2. 验证&#x200B;**发布路径**&#x200B;和&#x200B;**主题页模板**&#x200B;是否自动设置为：
      - 发布路径： `aemg-docs/en/docs/product1`
      - 主题页模板：主题页。

      ![使用网站下拉列表](/help/product-guide/knowledge-base/kb-articles/assets/publishing/use-site-dropdown.png){width="350" align="left"}

   **选项2：使用站点路径**

   1. 手动将&#x200B;**站点路径**&#x200B;设置为`/content/aemg-docs/en/docs/product1`。
   2. 验证&#x200B;**主题页模板**&#x200B;是否自动设置为主题页。

      ![使用站点路径](/help/product-guide/knowledge-base/kb-articles/assets/publishing/use-site-path.png){width="350" align="left"}

3. **保存预设：**&#x200B;保存对预设所做的更改。

## 生成AEM Sites

1. **生成站点：**
   1. 配置预设后，您现在可以为相应的DITA映射生成AEM站点。
   2. 生成的站点将在以下路径中可用： `/content/aemg-docs/en/docs/product1`。
2. **更改默认生成路径（可选）：**&#x200B;如果要更改网站生成的默认路径，请执行以下步骤：

   1. 导航到&#x200B;**AEM Sites**。
   2. 在OOTB站点结构下创建新产品页面。
   3. 导航到&#x200B;**AEMG文档** > **英语** > **文档**。

      ![在AEM站点结构](/help/product-guide/knowledge-base/kb-articles/assets/publishing/create-new-page.png){width="350" align="left"}中创建页面

   4. 选择&#x200B;**主页**&#x200B;磁贴，然后选择&#x200B;**下一步**。

      ![选择主页拼贴](/help/product-guide/knowledge-base/kb-articles/assets/publishing/home-page-tile.png){width="350" align="left"}

   5. 输入页面的&#x200B;**标题**&#x200B;和&#x200B;**名称**。
   6. 选择&#x200B;**创建**。
