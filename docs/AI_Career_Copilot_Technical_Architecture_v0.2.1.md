# AI Career Copilot Technical Architecture v0.2.1

版本：v0.2.1

依据：

-   Product Decision Log v0.2
-   PRD v0.2.1
-   AI Output Specification

------------------------------------------------------------------------

# 1. MVP架构目标

实现：

    用户画像

    ↓

    AI职业规划

    ↓

    简历分析

    ↓

    JD匹配

    ↓

    Application管理

    ↓

    面试复盘

------------------------------------------------------------------------

# 2. 系统架构

    Frontend

    ↓

    Backend API

    ↓

    Business Service

    +

    AI Service

    ↓

    PostgreSQL

    ↓

    Model Provider

------------------------------------------------------------------------

# 3. 后端模块

MVP模块：

    Auth Module

    User Module

    Career Module

    Resume Module

    Application Module

    Interview Module

    AI Module

    Report Module

暂不包含：

-   Offer Module
-   Growth Module
-   RAG Module
-   Agent Module

------------------------------------------------------------------------

# 4. 数据模型

## User

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

## Education

    id

    user_id

    school

    major

    degree

    graduation_year

------------------------------------------------------------------------

## Experience

    id

    user_id

    type

    title

    description

    skills

------------------------------------------------------------------------

## Skill

    id

    user_id

    skill_name

    level

------------------------------------------------------------------------

## Resume

关系：

    User

    ↓

    Resume

    ↓

    ResumeVersion

------------------------------------------------------------------------

## ResumeVersion

字段：

    id

    resume_id

    content

    target_role

    created_time

------------------------------------------------------------------------

## Application

字段：

    id

    user_id

    company

    position

    jd_content

    status

    custom_status

    resume_version_id

    created_time

说明：

resume_version_id用于记录申请该岗位时使用的简历版本。

custom_status用于用户自定义状态。

------------------------------------------------------------------------

## ApplicationTimeline

字段：

    id

    application_id

    event_type

    description

    event_time

------------------------------------------------------------------------

## Interview

字段：

    id

    application_id

    questions

    answers

    ai_report_id

------------------------------------------------------------------------

## AIReport

字段：

    id

    user_id

    type

    input_snapshot

    output_json

    model

    prompt_version

    created_time

------------------------------------------------------------------------

## UserCorrection

字段：

    id

    report_id

    correction

    created_time

------------------------------------------------------------------------

# 5. AI架构

    Business Layer

    ↓

    AI Service

    ↓

    Model Provider Interface

    ↓

    LLM Provider

支持未来：

-   GPT
-   Qwen
-   DeepSeek

------------------------------------------------------------------------

# 6. JD匹配设计

不使用：

match_score。

使用：

    Match Level

    Confidence

    Evidence

避免虚假精确。

------------------------------------------------------------------------

# 7. 安全设计

要求：

-   用户数据隔离
-   API资源所有权校验
-   日志脱敏
-   数据删除机制

------------------------------------------------------------------------

# 8. Sprint 1技术范围

实现：

-   项目初始化
-   数据库基础结构
-   用户系统
-   User Profile

不开发后续Sprint功能。
