# AI Career Copilot PRD v0.2

## 版本说明

本版本根据 Product Decision Log v0.2 修订。

核心变化：

-   冻结MVP范围
-   明确P0/P1/P2
-   调整AI能力设计
-   降低MVP开发复杂度

# 1. 产品定位

AI Career Copilot 是一个基于用户职业数据沉淀的 AI 求职助手。

长期目标：

帮助用户完成：

职业规划 → 简历优化 → 岗位匹配 → 投递管理 → 面试复盘 → Offer决策 →
职业成长

# 2. MVP范围

## MVP v1.0

只实现核心求职闭环：

    用户画像

    ↓

    AI职业规划

    ↓

    AI简历助手

    ↓

    JD智能匹配

    ↓

    Application投递管理

    ↓

    AI面试复盘

## P1版本

后续实现：

-   Offer决策助手
-   Growth Center

## P2版本

长期能力：

-   高级Memory
-   RAG
-   AI Agent

# 3. 核心功能需求

# Feature 1 用户画像

目标：

建立用户职业上下文。

字段：

-   当前状态
-   所在城市
-   目标城市
-   教育经历
-   技能
-   项目经历
-   职业目标

AI输出：

-   职业画像
-   优势
-   不足
-   推荐方向

# Feature 2 AI职业规划

输入：

用户画像

输出：

-   推荐岗位
-   匹配度
-   能力差距
-   能力提升建议

取消：

行动计划。

# Feature 3 AI简历助手

MVP支持：

-   文本简历输入
-   简历内容分析
-   JD匹配优化

暂缓：

复杂PDF/DOCX解析。

输出：

-   简历问题
-   优化建议
-   匹配结果

# Feature 4 Application管理

Application作为核心业务对象。

结构：

    Application

    ↓

    JD

    ↓

    Resume

    ↓

    Interview

状态：

用户展示：

-   待投递
-   已投递
-   面试中
-   Offer
-   已结束

详细过程：

通过Timeline记录：

-   HR沟通
-   一面
-   二面
-   终面

# Feature 5 AI面试复盘

MVP输入：

文本记录。

用户填写：

-   面试问题
-   自己回答

AI输出：

-   总结
-   优势
-   不足
-   改进建议

后续：

V1.5支持音频转文字。

V2支持录屏分析。

# 4. AI能力要求

所有AI功能必须定义：

-   输入
-   输出结构
-   异常处理
-   用户纠正机制

示例：

JD分析输出：

``` json
{
"match_score":85,
"strengths":["产品经验"],
"gaps":["LLM基础"],
"suggestions":["补充AI项目"]
}
```

# 5. Memory设计

MVP实现：

结构化上下文记忆。

包括：

-   User Profile
-   Application记录
-   Interview记录
-   决策记录

暂不实现：

-   自动向量记忆
-   Agent Memory

# 6. 非目标范围

MVP暂不开发：

-   自动投递
-   招聘网站爬虫
-   实时面试辅助
-   视频分析
-   复杂Agent

# 7. 成功标准

用户能够完成：

建立画像

↓

获得职业建议

↓

优化简历

↓

分析岗位

↓

管理申请

↓

完成面试复盘
