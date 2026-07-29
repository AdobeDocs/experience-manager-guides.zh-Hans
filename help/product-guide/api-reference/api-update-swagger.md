---
title: Experience Manager Guides版本中的API更新
description: 了解Experience Manager Guides版本中的各种API更新
source-git-commit: 24637376024107ae575620e5491c0150da6cc956
workflow-type: tm+mt
source-wordcount: '500'
ht-degree: 2%

---


# Experience Manager Guides版本中的API更新

本文在Adobe Experience Manager Guides版本的Swagger文档中提供了新添加的API的详细信息。 您可以导航到&#x200B;**工具** > **指南** > **API Swagger**，通过AEM界面访问Swagger文档。

<table style="border: 1; border-collapse: collapse; table-layout:fixed">
    <tr>
        <td colspan="5"><strong>2026.08.0版</strong></td>
    </tr>
    <tr>
        <td>功能</td>
        <td>子特征</td>
        <td>方法</td>
        <td>API</td>
        <td>描述</td>
    </tr>
    <tr>
        <td rowspan="7"><b>Assets</b></td>
        <td rowspan="7"></td>
        <td>POST</td>
        <td>'/bin/guides/v1/asset/import'</td>
        <td>将一个或多个资产导入目标文件夹；支持多部分上传和冲突解决</td>
    </tr>
    <tr>
        <td>POST</td>
        <td>'/bin/guides/v1/asset/list'</td>
        <td>返回文件夹路径下资产的分页列表</td>
    </tr>
    <tr>
        <td>POST</td>
        <td>'/bin/guides/v1/asset/validatexml'</td>
        <td>验证DITA XML的格式正确、架构有效性和控制台完整性</td>
    </tr>
    <tr>
        <td>POST</td>
        <td>'/bin/guides/v1/asset/version/revert'</td>
        <td>将资源还原到指定版本</td>
    </tr>
    <tr>
        <td>GET</td>
        <td>'/bin/guides/v1/asset/currentversion/detail'</td>
        <td>返回当前版本详细信息（版本名称、已更新状态、标签等）</td>
    </tr>
    <tr>
        <td>POST</td>
        <td>'/bin/guides/v1/assets/status'</td>
        <td>启动异步作业以检查给定路径下资产的指南状态</td>
    </tr>
    <tr>
        <td>GET</td>
        <td>'/bin/guides/v1/assets/status'</td>
        <td>按作业ID检索资源状态作业的状态/结果</td>
    </tr>
    <tr>
        <td rowspan="3"><b>发布</b></td>
        <td rowspan="3"></td>
        <td>POST</td>
        <td>'/bin/guides/v1/output/generate'</td>
        <td>开始执行预设以生成地图的输出</td>
    </tr>
    <tr>
        <td>GET</td>
        <td>'/bin/guides/v1/output/status'</td>
        <td>按映射路径和生成ID返回单个输出生成的状态</td>
    </tr>
    <tr>
        <td>GET</td>
        <td>'/bin/guides/v1/output/status/list'</td>
        <td>返回映射路径的所有已生成预设的状态</td>
    </tr>
    <tr>
        <td rowspan="18"><b>翻译</b></td>
        <td rowspan="6">语言</td>
        <td>GET</td>
        <td>'/bin/guides/v1/translation/language/copies'</td>
        <td>按路径或UUID列出的资产的语言副本</td>
    </tr>
    <tr>
        <td>GET</td>
        <td>'/bin/guides/v1/translation/language/groups'</td>
        <td>文件夹配置文件的语言组</td>
    </tr>
    <tr>
        <td>GET</td>
        <td>'/bin/guides/v1/translation/language/list'</td>
        <td>支持翻译语言（已过滤）</td>
    </tr>
    <tr>
        <td>GET</td>
        <td>'/bin/guides/v1/translation/language/root'</td>
        <td>资源路径可用的根语言</td>
    </tr>
    <tr>
        <td>GET</td>
        <td>'/bin/guides/v1/translation/language/variable'</td>
        <td>按类型和语言代码划分的语言变量</td>
    </tr>
    <tr>
        <td>POST</td>
        <td>'/bin/guides/v1/translation/language/variable'</td>
        <td>创建、更新或删除语言变量</td>
    </tr>
    <tr>
        <td rowspan="7">项目</td>
        <td>POST</td>
        <td>'/bin/guides/v1/translation/project/create'</td>
        <td>为DITA映射创建/更新翻译项目</td>
    </tr>
    <tr>
        <td>POST</td>
        <td>'/bin/guides/v1/translation/project/sync'</td>
        <td>创建/更新翻译项目（同步流程）</td>
    </tr>
    <tr>
        <td>GET</td>
        <td>'/bin/guides/v1/translation/project/creationstatus'</td>
        <td>按路径显示的项目翻译同步状态</td>
    </tr>
    <tr>
        <td>GET</td>
        <td>'/bin/guides/v1/translation/project/existing'</td>
        <td>当前用户的现有翻译项目</td>
    </tr>
    <tr>
        <td>GET</td>
        <td>'/bin/guides/v1/translation/project/inprogress'</td>
        <td>给定资产正在处理的项目</td>
    </tr>
    <tr>
        <td>删除</td>
        <td>'/bin/guides/v1/translation/project/delete'</td>
        <td>资产翻译状态/属性的预删除更新</td>
    </tr>
    <tr>
        <td>删除</td>
        <td>'/bin/guides/v1/translation/project/job/delete'</td>
        <td>作业移除前资源状态的预删除更新</td>
    </tr>
    <tr>
        <td rowspan="5">引用</td>
        <td>POST</td>
        <td>'/bin/guides/v1/translation/reference/accept'</td>
        <td>接受作业子页面中的已翻译内容</td>
    </tr>
    <tr>
        <td>POST</td>
        <td>'/bin/guides/v1/translation/reference/reject'</td>
        <td>拒绝作业子页面中的已翻译内容</td>
    </tr>
    <tr>
        <td>POST</td>
        <td>'/bin/guides/v1/translation/reference/sync'</td>
        <td>在目标文件夹中创建语言副本</td>
    </tr>
    <tr>
        <td>POST</td>
        <td>'/bin/guides/v1/translation/reference/baseline/export'</td>
        <td>将翻译基线导出到目标语言</td>
    </tr>
    <tr>
        <td>POST</td>
        <td>'/bin/guides/v1/translation/reference/status/forcesync'</td>
        <td>强制将不同步的资产更新为不同步</td>
    </tr>
</table>
