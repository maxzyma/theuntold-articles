# 公众号文章批判：Anthropic 产品负责人：从 6 个月到 1 天的发版秘密，harness 会被模型当早餐吃掉

## 1. 基本信息

| 项目 | 信息 |
|---|---|
| 原文链接 | https://mp.weixin.qq.com/s/t09DBqWAlujcUOfa3iWtCQ |
| 标题 | Anthropic 产品负责人：从 6 个月到 1 天的发版秘密，harness 会被模型当早餐吃掉 |
| 公众号作者 | 未从截断正文中取得 |
| 发表时间 | 未从截断正文中取得 |
| 原始信源 | [20VC: Mike Krieger, Co-Founder of Instagram and CPO at Anthropic](https://www.thetwentyminutevc.com/mike-krieger/)；[Introducing Claude 3.7 Sonnet and Claude Code](https://www.anthropic.com/news/claude-3-7-sonnet)；[Introducing Claude 4](https://www.anthropic.com/news/claude-4) |

## 2. 文章核心论点

1. Anthropic 的产品发版节奏从过去约 6 个月缩短到约 1 天，背后是组织与产品流程变化。
2. 新模型发布后，团队不只是加功能，还会主动删除或重做旧功能。
3. 在模型能力快速提升后，很多外部工具、工作流和 agent harness 的价值会被基础模型吞掉。
4. 产品经理角色正在被重塑，PM 不再只是写 PRD，而要更贴近模型能力、评测和迭代。
5. Claude 从聊天机器人走向协作式工作空间、代码代理和企业工作流。

## 3. 信源核查

### 3.1 “从 6 个月到 1 天”的发版周期

> 原作者复述：Anthropic 如何把发版周期从半年压到一天。

**公开报道交叉对照**：候选一手信源中，20VC 页面确认 Mike Krieger 作为 Anthropic CPO 接受访谈，议题包括产品、模型、应用层与 Claude 消费端开发，但给出的页面摘要没有列出“6 个月到 1 天”这一具体数字。[20VC 页面](https://www.thetwentyminutevc.com/mike-krieger/)只能证明访谈存在，不能证明该数字的上下文。Anthropic 官方发布记录显示 2024-2025 年有 Claude 3.5 Sonnet、computer use、Claude 3.7、Claude 4、Claude Code 等密集发布，但这些是按重大版本披露，不等于“日更发版”。参见 [Claude 3.5 Sonnet](https://www.anthropic.com/news/claude-3-5-sonnet)、[computer use](https://www.anthropic.com/news/3-5-models-and-computer-use)、[Claude 3.7](https://www.anthropic.com/news/claude-3-7-sonnet)。

**判定**：无独立验证。中文标题把一个访谈中的组织经验包装成可量化“秘密”，但当前材料不能区分是内部小迭代、实验开关、Claude App 更新，还是模型级发布。

### 3.2 “新模型到了要先删功能”

> 原作者复述：为什么新模型到了要先删功能。

**公开报道交叉对照**：Anthropic 官方材料确实显示模型能力升级会改变产品形态。例如 Claude 3.5 Sonnet 发布时同步推出 Artifacts，把 Claude 从聊天界面推向“协作工作环境”；Claude 3.7 发布时推出 Claude Code；Claude 4 又把 Claude Code 从研究预览推进到一般可用，并加入 GitHub Actions、VS Code、JetBrains 等集成。[Claude 3.5 Sonnet](https://www.anthropic.com/news/claude-3-5-sonnet)、[Claude 3.7](https://www.anthropic.com/news/claude-3-7-sonnet)、[Claude 4](https://www.anthropic.com/news/claude-4)。但官方材料并未说明“先删功能”是固定原则，也没有列出被删除功能清单。

**判定**：精度膨胀。合理的产品经验被标题化成通用方法论，缺少对象、范围和反例。

### 3.3 “harness 会被模型当早餐吃掉”

> 原作者复述：harness 会被模型当早餐吃掉。

**公开报道交叉对照**：Anthropic 的公开路线并不是单纯让模型吞掉工具层，而是在同时强化模型与工具/agent 基础设施。Claude 3.5 Sonnet 的 computer use 是“public beta”，官方明确称其仍然实验性、笨拙且易出错；Claude 4 则发布 code execution tool、MCP connector、Files API、prompt caching 等 API 能力，说明 harness、工具协议和执行环境仍是产品化核心。[computer use](https://www.anthropic.com/news/3-5-models-and-computer-use)、[Claude 4](https://www.anthropic.com/news/claude-4)。

**判定**：关键省略。模型进步会压缩一部分薄封装价值，但并未消灭 harness；相反，越强的模型越需要权限、沙箱、状态、评测、审计和工具接口。

### 3.4 “PM 角色正在发生剧变”

> 原作者复述：PM 角色正在发生的剧变。

**公开报道交叉对照**：20VC 页面列出的访谈主题包含“Model Quality vs. Product UX”“Transitioning from Model Provider to Application Provider”“Balancing API and Consumer Products”，可以支持 Mike Krieger 讨论了模型公司产品化与 PM 工作变化。[20VC](https://www.thetwentyminutevc.com/mike-krieger/)。但候选材料没有提供完整逐字稿，也没有第三方报道验证 Anthropic 内部 PM 职能如何调整。

**判定**：一致但证据有限。把 Anthropic 的 CPO 视角翻译给中文读者有价值，但不能直接外推为所有 AI 公司 PM 的新范式。

### 3.5 “Claude 成为协作工作环境”的叙事

> 原作者复述：Claude 从聊天机器人走向协作式工作空间。

**公开报道交叉对照**：这一点有较强官方证据。Anthropic 在 Claude 3.5 Sonnet 中明确称 Artifacts 是 Claude 从 conversational AI 到 collaborative work environment 的开始；Claude 3.7 和 Claude 4 继续把编码、代理和 IDE 集成作为重点。[Claude 3.5 Sonnet](https://www.anthropic.com/news/claude-3-5-sonnet)、[Claude 3.7](https://www.anthropic.com/news/claude-3-7-sonnet)、[Claude 4](https://www.anthropic.com/news/claude-4)。

**判定**：一致。需要补充的是：这些材料本身是公司发布稿，带有客户背书和 benchmark 营销色彩，不能当成中立行业结论。

## 4. 批判性切片

### 4.1 标题诱饵：把组织经验压缩成增长神话

“6 个月到 1 天”是典型的效率神话标题：数字强、因果短、可转发。但真正关键的问题被遮住了：这是模型发布、客户端发版、灰度实验、提示词更新，还是内部 dogfood？不同层级的“发版”风险完全不同。AI 产品的迭代速度不能脱离安全评测、回滚机制、用户迁移成本和企业 SLA 单独赞美。

### 4.2 样本选择偏差：赢家讲的是已成立位置上的工作方式

Anthropic 是拥有前沿模型、云平台分发、企业客户和安全品牌的头部公司。它的“删功能”“快发版”“模型吃掉工具层”，不是普通创业公司的通用配方，而是赢家在已经拥有模型能力、资金、算力和渠道之后的工作方式。把这种叙事翻译成“AI 产品成功方法论”，就是 AI 时代版幸存者偏差。

### 4.3 乐观滤镜：安全政治被产品效率吞没

Anthropic 自身并不只讲效率。它的 Responsible Scaling Policy 明确强调更强模型带来灾难性误用、自主能力和部署门槛问题，并设置 ASL 风险分级。[RSP](https://www.anthropic.com/news/anthropics-responsible-scaling-policy)。如果中文转述只留下“快速发版”和“模型吞工具”，就把 Anthropic 最有政治含义的一部分磨平了。

## 5. 独特视角

### 5.1 这场叙事完成了什么

这类文章把 CPO 访谈、公司发布稿和行业焦虑缝合成一种“产品人必须立刻跟上”的动员文本。它的功能不是解释 Anthropic，而是给中文 AI 圈提供一个可模仿的姿态：更快、更少流程、更相信模型、更轻视既有工具层。

### 5.2 中文读者要清楚什么

Anthropic 的公开叙事有两条线：一条是 Claude 产品化加速，另一条是安全、评测、责任扩展和部署边界。只转第一条，会把一家强调安全治理的公司读成单纯效率机器。真正的问题不是 Anthropic 有没有变快，而是哪些东西可以快，哪些东西必须慢。

### 5.3 一句话总结

这篇转述的价值在于提示 Claude 产品化节奏正在加速，问题在于把头部公司的位置优势包装成人人可复制的“发版秘密”。

## 6. 交叉验证文件

本次可用材料中，没有完整 20VC 逐字稿、原公众号全文、Anthropic 内部发版数据或第三方独立报道。涉及“1 天发版”“先删功能”“harness 被吃掉”的强表述，均应等待逐字稿或更多一手材料复核。

## 7. 公开报道信源

### Mike Krieger 访谈

- [20VC: Mike Krieger, Co-Founder of Instagram and CPO at Anthropic](https://www.thetwentyminutevc.com/mike-krieger/)

### Claude 产品与模型发布

- [Anthropic: Introducing Claude 3.5 Sonnet](https://www.anthropic.com/news/claude-3-5-sonnet)
- [Anthropic: Introducing computer use, a new Claude 3.5 Sonnet, and Claude 3.5 Haiku](https://www.anthropic.com/news/3-5-models-and-computer-use)
- [Anthropic: Introducing Claude 3.7 Sonnet and Claude Code](https://www.anthropic.com/news/claude-3-7-sonnet)
- [Anthropic: Introducing Claude 4](https://www.anthropic.com/news/claude-4)
- [Anthropic Docs: Release notes](https://docs.anthropic.com/en/release-notes/overview)

### 安全与限制性材料

- [Anthropic’s Responsible Scaling Policy](https://www.anthropic.com/news/anthropics-responsible-scaling-policy)
- [Anthropic: Core views on AI safety](https://www.anthropic.com/research/core-views-on-ai-safety)