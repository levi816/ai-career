# AI Career Copilot Technical Architecture

## 1. 架构目标

本项目目标是快速实现一个可用于 AI 产品经理作品集展示的 MVP。

技术架构需要满足：

-   快速开发
-   易于迭代
-   支持 AI 能力扩展
-   支持未来模型切换
-   保持代码结构清晰

------------------------------------------------------------------------

# 2. 整体系统架构

采用：

前后端分离 + AI Service Layer + 数据层

    User

    ↓

    Frontend (Next.js)

    ↓

    Backend API (NestJS)

    ↓

    ---------------------

    Business Service

    AI Service

    ---------------------

    ↓

    Database + Vector Database

    ↓

    LLM Provider

------------------------------------------------------------------------

# 3. 前端架构

## 技术选型

-   Next.js
-   React
-   TypeScript
-   Tailwind CSS
-   shadcn/ui

## 页面模块

    Frontend

    ├── Dashboard

    ├── Profile

    ├── Resume Center

    ├── Application Center

    ├── Interview Review

    ├── Offer Center

    └── Growth Center

------------------------------------------------------------------------

# 4. 后端架构

## 技术选型

-   Node.js
-   NestJS

## 模块设计

    Backend

    ├── Auth Module

    ├── User Module

    ├── Resume Module

    ├── Application Module

    ├── Interview Module

    ├── Offer Module

    ├── Growth Module

    └── AI Module

------------------------------------------------------------------------

# 5. 数据库设计

数据库：

PostgreSQL

## 核心数据对象

## User

存储用户职业画像。

字段：

-   id
-   name
-   status
-   province
-   city
-   target_city
-   education
-   skills
-   career_goal
-   profile_summary

------------------------------------------------------------------------

## Resume

存储用户简历。

字段：

-   id
-   user_id
-   version
-   content
-   file_url
-   ai_feedback

------------------------------------------------------------------------

## Application

核心业务对象。

字段：

-   id
-   user_id
-   company
-   position
-   city
-   jd_content
-   status
-   resume_id
-   match_score

------------------------------------------------------------------------

## Interview

字段：

-   id
-   application_id
-   round
-   transcript
-   score
-   summary

------------------------------------------------------------------------

## Offer

字段：

-   id
-   application_id
-   company
-   position
-   salary
-   city
-   ai_analysis

------------------------------------------------------------------------

# 6. AI Service架构

AI能力统一封装。

不要在业务代码中直接调用模型。

结构：

    AI Service

    ├── Career Planner

    ├── Resume Analyzer

    ├── JD Analyzer

    ├── Interview Reviewer

    ├── Offer Advisor

    └── Memory Manager

------------------------------------------------------------------------

# 7. AI模型架构

MVP：

使用：

GPT-4.1 / GPT-4o API

设计：

    Backend

    ↓

    AI Service

    ↓

    Model Provider

未来：

增加模型路由：

    AI Router

    ↓

    GPT

    Qwen

    DeepSeek

    Claude

------------------------------------------------------------------------

# 8. Memory设计

用于实现长期职业助手。

## Profile Memory

用户基础信息。

## Experience Memory

项目和工作经历。

## Interview Memory

历史面试经验。

## Decision Memory

Offer选择和职业决策。

------------------------------------------------------------------------

# 9. RAG设计

目标：

增强职业领域知识。

流程：

    用户问题

    ↓

    Embedding

    ↓

    Vector Search

    ↓

    相关资料召回

    ↓

    Prompt组合

    ↓

    LLM生成

------------------------------------------------------------------------

# 10. 文件处理

支持：

-   简历PDF
-   Word
-   面试音频

流程：

    Upload

    ↓

    Storage

    ↓

    Parser

    ↓

    AI Analysis

    ↓

    Database

------------------------------------------------------------------------

# 11. 部署方案

MVP推荐：

Frontend:

Vercel

Backend:

Railway / Render

Database:

Supabase PostgreSQL

AI:

OpenAI API

------------------------------------------------------------------------

# 12. 架构原则

1.  MVP优先验证产品价值。
2.  AI能力模块化。
3.  支持未来多模型切换。
4.  数据结构支持长期用户成长。
