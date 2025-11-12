---
title: 下载并安装适用于Cloud Services的AEM Sites模板
description: 了解如何下载并安装适用于Cloud Service的AEM Sites模板
feature: Installation
role: Admin
level: Experienced
exl-id: 67f7ff26-fbc7-426c-aa7d-9bf4debf05d8
source-git-commit: 4c564a0ffaa8f287bcaf012634d49dbf1e0682b4
workflow-type: tm+mt
source-wordcount: '671'
ht-degree: 1%

---

# 下载并安装AEM Sites模板(Cloud Service)

本指南提供了分步说明，用于设置和配置最新的AEM Guides模板，以在云环境中生成AEM Sites页面。 按照以下步骤安装所需的包，创建和配置预设，以及生成AEM Sites。

## 先决条件

在继续设置之前，请确保满足以下先决条件：

- **Adobe Experience Manager (AEM) Cloud**：正在运行的&#x200B;**AEM as a Cloud Service**&#x200B;实例，具有&#x200B;**AEM Guides 2502或更高版本**。

- **所需权限**：您必须具有以下权限：

   - 访问&#x200B;**Cloud Manager**&#x200B;以部署包。
   - 访问与您的环境关联的&#x200B;**Git存储库**。
   - 在AEM Guides中创建和修改预设的权限。

- **下载包**：从软件分发门户下载以下包：

   - 组件包：guides-components.all-1.x.0.zip
   - 站点模板：aemg-docs-1.x.0.zip

## 通过云部署安装包

安装&#x200B;**组件包(guides-components.all-1.x.x.zip)**&#x200B;并执行以下步骤

1. **克隆Git存储库：**
   1. 导航到Cloud Manager左侧面板中的&#x200B;**存储库**。
   2. 选择&#x200B;**访问存储库信息**&#x200B;并复制git clone命令。

      ![选择访问存储库信息](/help/product-guide/knowledge-base/kb-articles/assets/publishing/access-repo.png){width="350" align="left"}

   3. 使用提供的用户名和密码将存储库克隆到本地系统（如果需要，生成密码）。
2. **将包添加到Maven捆绑包：**
   1. 在本地克隆的存储库中，创建一个新的Maven捆绑包或将其添加到现有捆绑包中。
   2. 确保Maven项目中存在结构`/jcr_root/apps/fmdita/`安装。

      Maven项目中的![结构](/help/product-guide/knowledge-base/kb-articles/assets/publishing/maven-structure.png){width="650" align="left"}


   3. 将下载的guides-components.all-1.x.x.zip文件放在安装文件夹中。

3. **更新筛选器.xml：**

   1. 打开位于父内容目录的META-INF文件夹中的filters.xml文件。
   2. 添加以下筛选器：筛选器根=`/apps/fmdita` mode=`merge`/


      ![添加筛选器](/help/product-guide/knowledge-base/kb-articles/assets/publishing/add-filter-xml.png){width="650" align="left"}


4. **配置pom.xml：**&#x200B;根据您的环境要求更新pom.xml文件。
5. **推送更改并运行管道：**
   1. 将更改推送到主Git存储库。
   2. 导航到Cloud Manager中的&#x200B;**管道**，并为所需的环境运行该管道。
6. **验证安装：**&#x200B;部署完成后，组件包将安装在AEM Cloud环境中。

## 使用已安装的模板创建站点

1. **导入站点模板：**
   1. 转到AEM Sites页面(servername/sites.html/content)。
   2. 从模板中选择&#x200B;**创建** > **站点**。
   3. 使用&#x200B;**导入**&#x200B;选项导入站点模板aemg-docs-1.x.x.zip。
2. **选择模板：**&#x200B;选择&#x200B;**AEMG Docs 1.x.x**，然后选择&#x200B;**下一步**。
3. **输入站点详细信息：**&#x200B;输入&#x200B;**站点标题**&#x200B;和&#x200B;**站点名称**。

   ![创建站点](/help/product-guide/knowledge-base/kb-articles/assets/publishing/create-site.png){width="350" align="left"}

4. 选择&#x200B;**创建**。

## 创建AEM站点预设

1. **创建新预设：**
   1. 在AEM Guides中打开DITA映射并导航到&#x200B;**输出**&#x200B;面板。
   2. 选择&#x200B;**创建预设**。
   3. 选择类型为&#x200B;**AEM Sites**。
   4. 输入预设的名称。
   5. 取消选中&#x200B;**使用旧版组件映射**&#x200B;设置。

      ![创建新的AEM站点预设](/help/product-guide/knowledge-base/kb-articles/assets/publishing/create-new-output-preset.png){width="350" align="left"}

   6. 选择&#x200B;**添加**&#x200B;以创建预设。
2. **配置AEM站点预设：**&#x200B;有两个选项可用于配置现成(OOTB)站点：

   **选项1：使用站点下拉列表**

   1. 选择&#x200B;**站点**&#x200B;作为上面创建的站点（例如，AEMG文档站点）。
   2. 验证&#x200B;**发布路径**&#x200B;和&#x200B;**主题页面**&#x200B;模板是否自动设置为：
      - 发布路径： `/content/AEMG-Docs-Site/en/docs/product`
      - 主题页模板：“主题”页

      ![使用站点下拉菜单配置AEM站点](/help/product-guide/knowledge-base/kb-articles/assets/publishing/use-site-dropdown-cs.png){width="350" align="left"}

   **选项2：使用站点路径**

   1. 手动将&#x200B;**站点路径**&#x200B;设置为`/content/AEMG-Docs-Site/en/docs/product`。
   2. 验证&#x200B;**主题页**&#x200B;模板是否自动设置为主题页。

      ![使用站点路径配置AEM站点](/help/product-guide/knowledge-base/kb-articles/assets/publishing/use-site-path-cs.png){width="650" align="left"}

3. **保存预设：**&#x200B;保存对预设所做的更改。

## 生成AEM Sites

1. **生成站点：**
   1. 配置预设后，为相应的DITA映射生成AEM站点。
   2. 生成的站点将在以下路径中可用： `/content/AEMG-Docs-Site/en/docs/product`。
2. **更改默认生成路径（可选）：**&#x200B;如果要更改网站生成的默认路径，请执行以下步骤：
   1. 导航到&#x200B;**AEM Sites**。
   2. 在OOTB站点结构下创建新产品页面。
   3. 导航到&#x200B;**AEMG文档** > **英语** > **文档**。

      ![创建页面](/help/product-guide/knowledge-base/kb-articles/assets/publishing/create-page-cs.png){width="650" align="left"}

   4. 选择&#x200B;**主页**&#x200B;磁贴，然后选择&#x200B;**下一步**。

      ![选择主磁贴](/help/product-guide/knowledge-base/kb-articles/assets/publishing/home-tile-cs.png){width="650" align="left"}

   5. 输入页面的&#x200B;**标题**&#x200B;和&#x200B;**名称**。
   6. 选择&#x200B;**创建**。

>[!NOTE]
>
> 在部署到生产环境之前，请确保所有配置都已在非生产环境中进行了测试。 <br><br>有关更多详细信息，请参阅官方的[部署到AEM as a Cloud Service文档](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/deploying/overview)。
