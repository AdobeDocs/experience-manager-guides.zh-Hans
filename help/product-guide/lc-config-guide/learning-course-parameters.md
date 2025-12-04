---
title: 学习者进度和课程完成的SCORM关键指标
description: 了解学习者进度和课程完成的SCORM关键指标
feature: Authoring
role: Admin
level: Experienced
source-git-commit: 0dff380131dadc971f257eb464700392328164e5
workflow-type: tm+mt
source-wordcount: '279'
ht-degree: 1%

---

# 学习者进度和课程完成的SCORM关键指标

本文列出了在SCORM包中捕获的关键参数，以及相应的字段和示例。 这些参数可提供关于学习者进度、课程完成、互动详细信息和测验成绩的关键见解。 管理员可以使用此信息来验证跟踪、配置报表，并确保在LMS环境中进行准确的分析。 以下是SCORM包中显示的每个参数的示例值。

| **参数名称** | **描述** | **字段** | **示例** |
|---|---|---|---|
| **课程完成状态** | 指示课程是否已完成 | cmi.completion_status | 未完成 |
| **尝试计数** | 学习者尝试的次数 | LMS端尝试计数器/内容 | 尝试次数： 1 |
| **SCORM包的位置** | 课程中的当前书签或位置 | cmi.location | - |
| **进度完成** | 学习者进度 | cmi.progress_measure | 0.87 |
| **总时间（尝试）** | 当前尝试的总逗留时间 | cmi.total_time | 0000:01:09.87 |
| **目录可见性和主题计数** | 显示目录可见性和主题完成详细信息 | Project.HideTOC， Project.TotalTopics， Project.TopicsCompleted | - |
| **每个主题状态** | 每个主题的完成和通过状态 | 自定义每个课程的状态 | - |
| **每个问题选择状态** | 跟踪学习者为每个问题选择的选项 | value， generated_id，已选中 | - |
| **总体问题得分** | 在问题级别获得的分数和总数 | {&quot;score&quot;:0、&quot;maxScore&quot;:1}和% | &quot;score&quot;:33.33，&quot;maxScore&quot;:100，&quot;minScore&quot;:0 |
| 每个问题级别的&#x200B;**交互** | 每个问题的学习者互动详细信息 | id/type/timestamp/correct_response/learner_response/result/latency | - |
| **整个课程状态** | 指示通过/失败和总体进度 | success_status， completion_status，分数， progress_measure | 通过还是失败 |
| **学习者详细信息** | 按ID和名称标识学习者 | cmi.learner_id， cmi.learner_name | 阿尔伯特 |
| **测验参数** | 测验计时和及格分数配置 | cmi.max_time_allowed， cmi.scaled_passing_score， cmi.time_limit_action | 未定义或配置的值 |