---
kicker: 批判 · 播客转述
claimant: Boris Cherny · 微信公众号
claimant_slug: boris-cherny
upstream_subject: Sequoia AI Ascent 2026 Boris Cherny 与 Lauren Reeder 对谈 + How Boris Uses Claude Code
verdict_summary: “编程已经结束”是把 Boris 对自己代码库、自己工作流的判断扩写成行业结论；150 PR、几千 Agent、100 行 harness 是舞台叙事，不是可迁移生产方法。
findings_count: 5
---

# 公众号文章批判：Claude Code 访谈如何被包装成“编程终结论”

## 1. 基本信息

| 项目 | 内容 |
|---|---|
| 原文链接 | https://mp.weixin.qq.com/s/OUc02wmVtH9RQMhYhZGIdg |
| 标题 | Claude Code 之父最新访谈：编程已经结束、harness 将消失，Claude Code 将只有 100 行代码，loop 才是未来 |
| 公众号作者 | Boris Cherny |
| 发表时间 | 2026-05-07 18:32 CST |
| 原始信源 | [Sequoia AI Ascent 2026 对谈](https://www.youtube.com/watch?v=SlGRN8jh2RI)、[How Boris Uses Claude Code](https://howborisusesclaudecode.com/)、[Claude Code 官方产品页](https://claude.ai/code) |

## 2. 文章核心论点

1. Claude Code 的诞生来自 Anthropic Labs 对“模型能力溢出”的产品化尝试。
2. Boris 认为至少对他自己的代码库而言，coding 已经基本解决，2026 年自己不再手写代码。
3. 他的工作流从多终端并行，进一步变成手机上调度多个 Claude Code 会话和子 Agent。
4. `/loop` 与后台例行任务会成为 AI 编程的新形态：自动修 CI、整理反馈、定期报告。
5. 未来团队会出现跨学科通才，产品、设计、财务等角色都会“写代码”。
6. 随着模型变强，harness 会变薄，Claude Code 本身甚至会收缩到 100 行代码。
7. MCP、Computer Use 与程序化接入会让知识工作中的工具边界下降。

## 3. 信源核查

### 3.1 “coding is solved”的限定语被标题吃掉

> **原文复述**：标题写“编程已经结束”；正文写 Boris 曾说过“coding is solved”，并补一句“对他自己而言，这个数字是 100%”。

**公开报道交叉对照**：Sequoia 视频简介的表述是“why he believes coding is effectively solved — at least for the code he writes”，关键限定是“至少对他写的代码而言”。同一简介也把议题限定在 Claude Code 与编码未来，而不是全行业软件工程终结。[来源](https://www.youtube.com/watch?v=SlGRN8jh2RI)

> **判定**：关键省略
>
> 中文标题把“at least for the code he writes”压扁成“编程已经结束”。正文虽保留了一点限定，但标题和收尾仍在推动行业级结论。

### 3.2 “150 PR/天、几千 Agent”缺少独立可核验口径

> **原文复述**：文章开头写“一个人，一天提交 150 个 PR，全部用手机完成”；正文写“晚上，他会让几千个 Agent 跑更深层的任务”。

**公开报道交叉对照**：Sequoia 视频简介只确认“dozens of PRs a day from his phone”，没有在摘要层面确认“150 PR”或“几千 Agent”的统计口径。How Boris Uses Claude Code 记录的是 5 个终端实例、5-10 个网页会话、手机发起会话等工作流细节，也没有给出“几千 Agent”的可复现定义。[来源](https://www.youtube.com/watch?v=SlGRN8jh2RI)、[来源](https://howborisusesclaudecode.com/)

> **判定**：无独立验证
>
> 这些数字来自访谈舞台叙述，不能等同于生产环境指标。PR 是提交、合并、有效变更还是机器人生成草稿，文章没有拆开。

### 3.3 “内部没有手写代码”与公开工作流并不完全一致

> **原文复述**：文章写“Anthropic 内部现在已经没有手写代码了。所有 SQL 都是模型写的。”

**公开报道交叉对照**：How Boris Uses Claude Code 显示的是 Claude Code 团队维护 CLAUDE.md、使用 Plan mode、review 中让 @claude 补充规则、通过 hooks 自动格式化、用 permissions 预授权命令。这是一套高度工程化的人机协同流程，而不是“人类完全退出编码”。[来源](https://howborisusesclaudecode.com/)

> **判定**：精度膨胀
>
> “不亲手敲代码”不等于“没有工程判断”。计划、权限、review、规范沉淀、CI 兜底仍是人工制度设计。

### 3.4 “harness 会消失”与当前产品事实存在张力

> **原文复述**：文章写“prompt injection 防护、命令静态验证、权限模式、human-in-the-loop 未来都会不那么重要”，并称“一年后 Claude Code 的产品外壳可能只需要 100 行代码”。

**公开报道交叉对照**：How Boris Uses Claude Code 反而展示了大量 harness：CLAUDE.md、slash commands、subagents、PostToolUse hook、permissions、MCP 配置。Claude Code 官方页也把 Claude Code、Cowork、连接器、MCP 等作为不同套餐里的产品能力，而非“100 行脚本”即可替代的免费壳层。[来源](https://howborisusesclaudecode.com/)、[来源](https://claude.ai/code)

> **判定**：关键省略
>
> “harness 变薄”是预测，“当前靠 harness 维持可靠性”是事实。文章把预测写成趋势确定性，弱化了安全、权限和组织流程的现有重量。

## 4. 批判性切片

### 4.1 标题诱饵：原访谈是“Boris 的工作流”，中文包装成“编程终结”

原始视角是一个产品创造者在投资人大会上展示 Claude Code 的使用方式：手机、多会话、loop、MCP、团队 dogfooding。中文标题把它倒置成“编程已经结束”。这不是语气差异，而是对象转换：从“Boris 如何用 Claude Code”变成“所有人如何面对编程终结”。

> **反例**：How Boris Uses Claude Code 的核心不是“没有 harness”，而是 5 个 checkout、CLAUDE.md、Plan mode、GitHub Action、hooks、permissions、MCP。它描述的是高配置工作流，不是零门槛编程消失。

### 4.2 论证循环：模型强，所以产品会变薄；产品变薄，所以模型强

文章的因果链是：模型更强 → Claude Code 增长 → harness 变薄 → 编程门槛消失 → 更多人写代码 → 证明模型更强。循环里最关键的默认假设是：模型能力提升会自动替代安全、上下文管理、权限、审计和团队协作。

> **反例**：Boris 自己的公开工作流依赖 permissions 白名单、PostToolUse hook、CLAUDE.md 规则库和 PR review。这些不是模型能力的装饰品，而是模型进生产系统前的控制面。

### 4.3 样本偏差：Claude Code 团队不是普通软件团队

Claude Code 团队拥有内部模型知识、Anthropic 平台权限、最短反馈链路、最强 dogfooding 动机。它的工作方式是赢家在已经占据优势位置上的工作方式，不是普通 SaaS 团队复制后也能获得同样结果的“配方”。

> **反例**：一个金融、医疗或政企软件团队即使用 Claude Code，也要面对审计日志、变更审批、数据出境、权限隔离和回滚责任。150 个 PR/天在这些环境里不是效率指标，反而会制造 review 队列和合规债务。

### 4.4 浅观察：把“写代码”误当成“交付软件”的全部

文章不断强化“人人写代码”，但软件交付的瓶颈常常不在代码生成，而在需求澄清、线上责任、数据权限、测试覆盖、迁移窗口、客户支持和事故复盘。Agent 能写 SQL，不代表能承担错误 SQL 造成的数据污染责任。

> **反例**：CI 自动修复 flaky test 听起来高效，但在大型系统里 flaky test 往往暴露时序、并发、外部依赖和测试隔离问题。让 loop 自动“修绿”会把真实缺陷改写成测试规避。

### 4.5 乐观滤镜：把“快”的负向尾部藏起来

“手机就是工位”“几千 Agent 夜间运行”制造了强烈的未来感，但并发 Agent 的负面尾部也随之放大：错误提交、权限误用、成本失控、上下文污染、重复修复、自动化之间相互打架。文章只写了速度，没有写控制成本。

> **反例**：一个 loop 每 30 分钟抓取 X 用户反馈并聚类，若接入 Slack、BigQuery、Sentry 和 GitHub，它同时触碰外部数据、内部日志和代码变更。任何权限配置错误都不再是单次误操作，而是定时放大的事故机制。

## 5. 独特视角

### 5.1 这不是反编程宣言，而是 Claude Code 的客户教育

这篇转述最有效的地方，是把具体功能翻译成未来工作方式：loop、MCP、phone sessions、subagents、routines。它看上去在讨论编程未来，实际在教育读者接受 Claude Code 的产品范式：不要把它当 IDE 插件，要把它当持续运行的工作层。

### 5.2 Boris 的位置决定了叙事边界

Boris 不是外部中立观察者，而是 Claude Code 的创造者；Sequoia 不是学术会议，而是资本与创业者共振的舞台。访谈中的判断天然服务于产品信心、开发者动员和生态扩张。中文转述没有标出这一层利益位置。

### 5.3 中文读者要补回三个限定

第一，“solved”限定在 Boris 熟悉的代码库和工具链。第二，“不手写代码”不等于“不做工程”。第三，“harness 会变薄”是 Anthropic 对自身模型路线的押注，不是安全、权限、审计都会消失。

### 5.4 一句话总结

一个产品创造者的工作流，传播到中文 AI 媒体里就是客户教育素材。

## 6. 交叉验证文件（无）

本次输入未提供独立 transcript、PR 记录、内部指标或第三方报道；涉及“150 PR”“几千 Agent”“内部没有手写代码”的部分，只能按公开候选信源做限定性核查。

## 7. 公开报道信源

### Sequoia 访谈

- [Sequoia AI Ascent 2026: Boris Cherny 与 Lauren Reeder 对谈](https://www.youtube.com/watch?v=SlGRN8jh2RI)

### Boris 工作流

- [How Boris Uses Claude Code](https://howborisusesclaudecode.com/)

### Claude Code 产品信息

- [Anthropic: Claude Code 官方产品页](https://claude.ai/code)