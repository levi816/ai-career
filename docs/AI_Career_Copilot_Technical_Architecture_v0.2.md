# AI Career Copilot Technical Architecture v0.2

版本：v0.2

更新依据：

-   Product Decision Log v0.2
-   PRD v0.2
-   AI Output Specification v0.1

本版本作为 MVP 开发阶段的技术实施依据。

------------------------------------------------------------------------

# 1. 架构目标

AI Career Copilot MVP 的目标：

快速验证 AI 求职助手核心闭环。

核心能力：

    用户画像

    ↓

    AI职业规划

    ↓

    AI简历分析

    ↓

    JD匹配

    ↓

    Application管理

    ↓

    AI面试复盘

技术原则：

1.  优先验证产品价值。
2.  保持架构可扩展。
3.  AI能力模块化。
4.  支持未来模型切换。
5.  保证用户数据安全。

------------------------------------------------------------------------

# 2. MVP系统架构

采用：

前后端分离 + AI Service Layer + 数据存储。

    User

    ↓

    Frontend

    (Next.js)

    ↓

    Backend API

    (NestJS)

    ↓

    ---------------------

    Business Service

    AI Service

    ---------------------

    ↓

    PostgreSQL

    ↓

    LLM Provider

------------------------------------------------------------------------

# 3. 技术选型

## Frontend

技术：

-   Next.js
-   React
-   TypeScript
-   Tailwind CSS
-   shadcn/ui

原因：

-   适合SaaS Dashboard产品
-   组件生态成熟
-   方便Codex生成代码

------------------------------------------------------------------------

## Backend

技术：

-   Node.js
-   NestJS

原因：

-   模块化结构
-   API开发效率高
-   与前端TypeScript统一

------------------------------------------------------------------------

## Database

技术：

PostgreSQL

推荐：

Supabase PostgreSQL

原因：

-   关系数据适合求职流程
-   支持JSON字段
-   后续支持向量扩展

------------------------------------------------------------------------

# 4. 后端模块设计

MVP模块：

    Backend

    ├── Auth Module

    ├── User Module

    ├── Career Module

    ├── Resume Module

    ├── Application Module

    ├── Interview Module

    ├── AI Module

    └── Report Module

------------------------------------------------------------------------

暂不实现：

    Offer Module

    Growth Module

    RAG Module

    Agent Module

原因：

属于P1/P2阶段。

------------------------------------------------------------------------

# 5. 核心数据模型

## User

用户基础信息。

字段：

    id

    name

    email

    status

    province

    city

    target_city

    career_goal

    created_time

------------------------------------------------------------------------

# Education

教育经历。

字段：

    id

    user_id

    school

    major

    degree

    graduation_year

------------------------------------------------------------------------

# Experience

项目/工作经历。

字段：

    id

    user_id

    type

    title

    description

    skills

    created_time

------------------------------------------------------------------------

# Skill

技能标签。

字段：

    id

    user_id

    skill_name

    level

------------------------------------------------------------------------

# Resume

用户简历对象。

关系：

    User

    ↓

    Resume

    ↓

    ResumeVersion

字段：

    id

    user_id

    title

    created_time

------------------------------------------------------------------------

# ResumeVersion

简历版本。

字段：

    id

    resume_id

    content

    target_role

    created_time

作用：

支持不同岗位简历版本管理。

------------------------------------------------------------------------

# Application

核心业务对象。

关系：

    Application

    ↓

    JD

    ↓

    ResumeVersion

    ↓

    Interview

字段：

    id

    user_id

    company

    position

    jd_content

    status

    created_time

------------------------------------------------------------------------

# ApplicationTimeline

记录求职过程。

字段：

    id

    application_id

    event_type

    description

    event_time

示例：

    HR沟通

    一面完成

    二面完成

------------------------------------------------------------------------

# Interview

面试记录。

字段：

    id

    application_id

    questions

    answers

    ai_report_id

    created_time

------------------------------------------------------------------------

# AIReport

AI分析结果。

字段：

    id

    user_id

    type

    input_snapshot

    output_json

    model

    prompt_version

    created_time

用途：

保存：

-   AI输入
-   AI输出
-   使用模型
-   Prompt版本

------------------------------------------------------------------------

# UserCorrection

用户纠正AI结果。

字段：

    id

    report_id

    correction

    created_time

用途：

形成AI优化数据闭环。

------------------------------------------------------------------------

# 6. AI Service架构

所有AI调用必须经过：

    Backend

    ↓

    AI Service

    ↓

    Model Provider

禁止：

业务代码直接调用模型API。

------------------------------------------------------------------------

## AI Service结构

    AI Service

    ├── CareerPlanner

    ├── ResumeAnalyzer

    ├── JDMatcher

    ├── InterviewReviewer

    └── ReportManager

------------------------------------------------------------------------

# 7. 模型架构

MVP：

支持一个主要模型Provider。

例如：

GPT API。

架构：

    AI Service

    ↓

    Model Interface

    ↓

    Provider

    ↓

    GPT / Qwen / DeepSeek

------------------------------------------------------------------------

优势：

未来可替换模型。

------------------------------------------------------------------------

# 8. AI输出处理流程

    User Input

    ↓

    Backend

    ↓

    AI Service

    ↓

    LLM

    ↓

    JSON Schema Validation

    ↓

    AIReport保存

    ↓

    Frontend展示

------------------------------------------------------------------------

要求：

所有AI输出必须符合：

AI Output Specification。

------------------------------------------------------------------------

# 9. 文件处理策略

MVP调整：

不实现复杂文件链路。

暂不支持：

-   PDF解析
-   DOCX解析
-   OCR
-   音频处理
-   视频处理

------------------------------------------------------------------------

MVP输入：

优先：

文本输入。

原因：

快速验证AI价值。

------------------------------------------------------------------------

# 10. 主动AI建议设计

MVP不实现Agent。

采用：

规则触发 + AI生成建议。

示例：

规则：

7天无更新Application。

↓

AI生成：

求职进度提醒。

------------------------------------------------------------------------

# 11. 安全设计

## 用户数据隔离

所有资源访问必须验证：

user_id。

------------------------------------------------------------------------

## 权限控制

用户只能访问：

自己的：

-   简历
-   Application
-   Interview

------------------------------------------------------------------------

## 数据删除

采用：

软删除。

字段：

    deleted_at

------------------------------------------------------------------------

## 数据脱敏

日志禁止记录：

-   联系方式
-   简历全文
-   薪资隐私

------------------------------------------------------------------------

# 12. 部署方案

MVP：

Frontend：

Vercel

Backend：

Railway / Render

Database：

Supabase PostgreSQL

AI：

LLM API

------------------------------------------------------------------------

# 13. MVP技术范围总结

实现：

✅ 用户系统

✅ 用户画像

✅ AI职业规划

✅ AI简历分析

✅ JD匹配

✅ Application管理

✅ AI面试复盘

暂缓：

❌ Offer

❌ Growth

❌ RAG

❌ Agent

❌ 音视频分析

------------------------------------------------------------------------

# 14. 架构原则总结

    简单可靠的MVP

    ↓

    结构化AI输出

    ↓

    可追踪AI结果

    ↓

    用户反馈闭环

    ↓

    未来扩展模型和Agent
