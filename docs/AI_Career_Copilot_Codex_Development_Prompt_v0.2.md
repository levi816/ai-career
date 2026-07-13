# AI Career Copilot Codex Development Prompt v0.2

## 项目任务

开发 AI Career Copilot MVP。

请优先阅读：

-   Product Brief
-   User Research
-   PRD v0.2
-   Product Decision Log v0.2
-   Technical Architecture

# 当前开发目标

不要一次开发完整产品。

严格按照Sprint执行。

# MVP范围

必须实现：

1.  用户画像

2.  AI职业规划

3.  AI简历助手

4.  JD智能匹配

5.  Application管理

6.  AI面试复盘

暂不实现：

-   Offer分析
-   Growth Center
-   Agent
-   RAG

# 技术要求

Frontend:

-   Next.js
-   TypeScript
-   Tailwind

Backend:

-   NestJS

Database:

-   PostgreSQL

AI:

通过统一AI Service调用模型。

禁止业务代码直接调用模型API。

# AI输出要求

所有AI接口必须返回结构化JSON。

例如：

{ "score":85, "strengths":\[\], "gaps":\[\], "suggestions":\[\] }

# 开发流程

Phase 1:

初始化项目

Phase 2:

用户画像

Phase 3:

AI职业规划

Phase 4:

简历与JD分析

Phase 5:

Application

Phase 6:

面试复盘

完成每个阶段后等待确认。

不要自动继续下一阶段。

# 开发原则

-   保持模块化
-   支持未来模型切换
-   保证用户数据隔离
-   不生成虚假AI结果
