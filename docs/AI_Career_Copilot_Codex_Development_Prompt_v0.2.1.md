# AI Career Copilot Codex Development Prompt v0.2.1

版本：v0.2.1

用途：

指导Codex进行MVP开发。

------------------------------------------------------------------------

# 1. 文档读取顺序

开始开发前必须阅读：

1.  Document Governance
2.  Product Decision Log
3.  PRD v0.2.1
4.  AI Output Specification
5.  Technical Architecture v0.2.1
6.  Development Task Breakdown

如果发现冲突：

停止开发并提出问题。

禁止自行扩大范围。

------------------------------------------------------------------------

# 2. 当前MVP范围

必须实现：

1.  用户画像

2.  AI职业规划

3.  AI简历助手

4.  JD智能匹配

5.  Application管理

6.  AI面试复盘

暂不实现：

-   Offer
-   Growth
-   RAG
-   Agent
-   音频
-   视频

------------------------------------------------------------------------

# 3. 技术要求

Frontend：

-   Next.js
-   TypeScript
-   Tailwind CSS

Backend：

-   NestJS

Database：

-   PostgreSQL

AI：

必须通过AI Service调用模型。

禁止业务代码直接调用模型API。

------------------------------------------------------------------------

# 4. AI输出要求

所有AI接口必须符合AI Output Specification。

禁止：

返回不可解析文本。

禁止：

使用：

match_score

或：

85%匹配度。

必须使用：

    Match Level

    +

    Confidence

    +

    Evidence

------------------------------------------------------------------------

# 5. Sprint执行规则

一次只执行一个Sprint。

当前：

Sprint 1

目标：

-   项目初始化
-   基础数据库
-   User Profile模块

完成后：

输出：

1.  修改文件
2.  实现内容
3.  运行方式
4.  测试结果
5.  下一步建议

等待确认后进入下一Sprint。

------------------------------------------------------------------------

# 6. 开发原则

-   保持模块化
-   支持未来模型替换
-   保证用户数据隔离
-   不生成虚假AI结论
-   遵守文档优先级
