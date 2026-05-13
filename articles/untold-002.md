---
slug: untold-002
model: human-baseline
published_at: 2026-04-25
kicker: 批判 · 微信公众号
claimant: J0hn · 微信公众号
claimant_slug: j0hn
upstream_subject: Lenny 播客访 Kat Wu（Anthropic 产品负责人）
verdict_summary: >-
  源码两次泄露的真因（Bun runtime bug + 缺 pre-publish CI + npmignore 配错）被压缩为「人为失误」；OpenClaw 事件的时间线政治（创始人 2-14 加入 OpenAI、Boris Cherny 是实际发言人）被完全省略。
findings_count: 6
source_count: 11
---

# 公众号文章批判：Anthropic 产品负责人「从 6 个月到 1 天的发版秘密，harness 会被模型当早餐吃掉」

## 1. 基本信息

| 字段 | 值 |
|---|---|
| 原文链接 | https://mp.weixin.qq.com/s/t09DBqWAlujcUOfa3iWtCQ |
| 标题 | Anthropic 产品负责人：从 6 个月到 1 天的发版秘密，harness 会被模型当早餐吃掉 |
| 公众号作者 | J0hn |
| 发表时间 | 2026-04-25 12:05 CST |
| 原始信源 | Lenny Rachitsky 播客采访 Kat Wu（Claude Code & Cowork 产品负责人） |

文末作者列出的相关链接：
- Lenny's Podcast 原文：https://www.lennysnewsletter.com/p/how-anthropics-product-team-moves
- YouTube 完整视频：https://www.youtube.com/watch?v=PplmzlgE0kg
- Kat Wu X：https://x.com/_catwu

## 2. 文章覆盖的 11 个段落

1. Kat Wu 是谁（与 Boris Cherny 搭档，80% 想法一致）
2. 从 6 个月到 1 天的发版节奏（清晰目标 / Research Preview / Launch Room）
3. 模型会"吃掉"你的产品（每出新模型先删 system prompt 中的拐杖功能）
4. 源码泄露事件回应（人为失误 / 流程问题 / 不追责）
5. OpenClaw 抉择（基础设施压力 / 给 credits 缓冲 / 优先第一方）
6. Cowork 被低估了（dogfooding 案例：1 小时生成 20 页 PPT）
7. PM 的未来（与工程师融合，但代价是产品一致性下降）
8. 问模型为什么犯错（让 LLM 自反指向 harness 改进方向）
9. 50 个 Claude 并行（路线图三阶段）
10. Just do things（Kat 的人生座右铭）
11. 别停在 95%（自动化要做就做到 100%）

## 3. 信源核查（关键省略）

J0hn 的转述基本忠实于 Kat Wu 在播客里说的话，但**几个高敏感事件的转述只用了 Anthropic 一方的 PR 措辞，没有交叉信源**。下面是核查结果。

### 3.1 源码泄露事件

**J0hn 复述的版本**：
> 「人为失误，有人用 Claude 写 PR 更新包发布流程时出错；经过两层人工审查还是漏了；Anthropic 文化是从中学习不追责。」

**公开报道交叉对照**（Axios / Fortune / The Register / The Hacker News，2026-03-31）：

- 事件时间：2026-03-31，Claude Code v2.1.88（npm 包 `@anthropic-ai/claude-code`）
- 真因（多重失效）：
  - npm package.json 的 `.npmignore` / `files` 字段配置错误
  - **Anthropic 自己 2025 年底收购的 Bun runtime 已知 bug #28001**——文档说生产构建不应该带 source map，但实际带了。bug 已开 20 天没修
  - **没有 pre-publish CI 检查**（source map 存在与否是几行脚本就能查的）
- 泄露规模：59.8 MB source map、500,000 行代码、1,900 文件
- 暴露内容：KAIROS / autoDream 等未发布功能的 feature flag 全部曝光
- **这是一周内的第二次重大泄露**——前一次（Fortune 报道）泄了 3000 个文件，包括代号 **Mythos / Capybara** 的下一代模型 blog 草稿
- 事件后续：重建 mirror 在 GitHub 几小时内拿到 84,000 星，Anthropic 发了 DMCA 但已扩散到几百个仓库

**Kat Wu 的"流程问题、已加防护"对应的就是上述这一连串失效**。J0hn 没做任何对照，等于把一份 PR 通稿照搬。

### 3.2 Mythos 模型的来历（叙事框架问题）

**J0hn 复述**：
> Lenny 追问"你们内部用了 Mythos 模型，是不是因为这个才快？" Kat 答："用了，加快了一点速度，但主要靠流程文化。"

**省略的关键背景**：

"Mythos" 这个代号本身就是从一周前的另一次泄露里曝光的（Fortune 报道，2026-03-31）。**Lenny 不是凭空知道这个代号，Kat Wu 也不是在透露内幕**——她是在已知的泄露事实上做语气缓和。

把这段当作"原汁原味的内部访谈"来读，等于把 PR 演练当成自然对话。J0hn 没标注这层信息差。

### 3.3 OpenClaw 事件（最严重的省略）

**J0hn 复述**：
> Anthropic 限制了第三方工具用 Claude 订阅额度，社区一片哗然。Kat 解释：第三方使用模式不同，给基础设施带来压力。Lenny 站队：你们补贴用户，公司也需要盈利。

**公开报道的版本**（TechCrunch / The Register / VentureBeat / TNW / HN，2026-04-04 到 04-10）：

#### 3.3.1 时间线政治
- **OpenClaw 创始人 Peter Steinberger 于 2026-02-14 加入了 OpenAI**，Sam Altman 公开点名"领导下一代个人 agent"
- Anthropic 在他离开几周后立即出手限制
- "这个时间线没逃过任何人的眼睛"（英文媒体原话）
- **J0hn 的转述完全没提**

#### 3.3.2 实际发言人
- Anthropic 的公开发言人是 **Boris Cherny（Claude Code 负责人，正是 Kat Wu 的搭档）**
- Kat 在播客里给的是软化版本，不是政策声明
- 把 Kat 的语气当成 Anthropic 立场全貌，会失真

#### 3.3.3 OpenClaw 视角
- Steinberger 公开回应："**先把流行功能抄进闭源 harness，然后锁掉开源**"
- Steinberger 和投资人 Dave Morin 试图谈判，只争取到延后一周
- 一周内 Steinberger 还被 Anthropic 以"可疑活动"暂时封号，X 公开发声后几小时才解封
- **这是叙事的高潮，被 J0hn 一笔抹掉**

#### 3.3.4 经济学数据
- HN/分析师估算 **OpenClaw 同等输出比 Claude Code 贵 5×~25×**（cache miss 结构差异）
- 135,000+ OpenClaw 实例在跑
- 这是 Anthropic"扛不住"的真实数字
- 但同时也说明 **Anthropic 之前的订阅价就是结构性误标**——不是用户行为不正常，是定价模型不正常

#### 3.3.5 合规问题
J0hn 让 Lenny "自然站队 Anthropic"，省略了一个关键合规问题：
**Anthropic 卖订阅时没说不能用第三方 client，事后单方面变更使用条款**。
这是商业实践上有争议的点，被中文转述彻底磨平。

### 3.4 Cowork 那一段是软广

**J0hn 复述（保留了完整的 dogfooding 叙事）**：
> Kat 用 Cowork 一个小时生成 20 页演讲稿、读起来像 Anthropic 设计师做的、Applied AI 团队是 token 消耗第二大。

这是经过精心设计的 dogfooding success story，在英语播客上是常态。J0hn 没标"以下为产品演示性质"，让中文读者把它当作"团队习惯"来读，**有效完成了对中文圈的二次推广**。

LLM 生成 20 页 PPT 这个动作，2026 年的任何 frontier 模型都能做——把它包装成 Cowork 独有能力，是产品营销框架。

## 4. 真有价值的部分

不是说这篇全无信息密度。下面这些是值得认真记的：

### 4.1 「新模型来了第一件事是删功能」
- to-do list 在 Opus 4 之前是必要的拐杖（模型改 5 个调用点就停了，明明有 20 个要改）
- Opus 4 之后模型自己会列清单、逐个完成，to-do list 变成可有可无
- **每次发版通读 system prompt，逐段反思"模型还需要这个提醒吗"，不需要就删**
- 这是真正反直觉、可迁移的工程纪律。值得抄进任何 LLM 应用团队的发版 checklist。

### 4.2 「问模型为什么犯错，反向修 harness」
- Kat 发现模型改了前端代码后跑测试，但不打开页面看 UI
- 直接问模型："你为什么不检查 UI 呢？"
- 模型回答：有时是 system prompt 里某段话造成困惑；有时是把验证委派给了 sub-agent，sub-agent 没做、模型也没检查
- **把 LLM 的自反作为产品流程的一部分，而不是 prompt engineering trick**——这是 harness 工程化的关键洞察

### 4.3 「别停在 95%」
- 两种极端：从来不做自动化 vs 沉迷折腾工具配置
- 更常见的问题：做到 95% 就放弃
- **不能 100% 工作的自动化不是真正的自动化**
- 比"通才崛起"那一段更有反思力度

### 4.4 50 个 Claude 并行的路线图
- 第一步：单任务稳定输出可合并代码 / 可分享文档
- 第二步：多任务并行（2025 年底 multi-coding 兴起，目前用户同时跑 6 个）
- 第三步：50~几百个 Claude 同时跑（本地内存不够，任务跑远端；模型自验证；自我改进）
- 这个路线图本身有信息含量——它对应的是 KAIROS / autoDream feature flag 在源码泄露中曝光的方向

## 5. 批判性切片

### 5.1 转述结构问题
J0hn 在转述上做得相当流畅：拎重点、有节奏、不跑题。但他的信源处理只到 **"Kat Wu 在播客里说了什么"** 这一层。

对照英语圈的报道，这场播客是发生在两个高敏事件（源码泄露 + OpenClaw 政策）刚过去不到一个月的时间点。Kat Wu 显然带着 PR 准备稿出场，**Lenny 的追问也是受控的**（Kat 是 Anthropic 内部人，Lenny 是友好访谈者）。

J0hn 把这场访谈当作 ground truth 来转述，没有在任何一个段落标注"以下为受访方视角"。

### 5.2 三个高敏事件，三种处理
| 事件 | Kat Wu 的措辞 | 公开报道 | J0hn 的处理 |
|---|---|---|---|
| 源码泄露 | "人为失误 / 经过两层审查 / 流程问题 / 已加防护" | npm 配置 + Bun bug 双重失效，无 CI 检查，一周内第二次 | 全盘照搬 |
| Mythos 模型 | "用了，加快了一点" | 来自前一次 3000 文件泄露的代号 | 没标背景 |
| OpenClaw 限制 | "基础设施压力 / 给了 credits 缓冲" | 创始人去 OpenAI 后封禁 / 创始人被暂时封号 / 5-25× 成本差 | 完全省略政治维度 |

**三个事件，J0hn 都选了 Anthropic 的版本。** 这不是恶意，是中文 AI 自媒体的默认产线设置。但读者需要知道。

### 5.3 「快」的代价被按下不表
Anthropic "40 天发 30 个功能" 的代价已经摆在桌上：
- 一周内两次重大源码泄露
- 单方面砍订阅条款
- 封禁竞品创始人账号

**"快"的另一面是"事故频率正比例上升"，但这部分被 Kat Wu 的"流程问题、从中学习"修辞按下不表**。

如果你照搬 Anthropic 的发版节奏却没有他们的现金流和媒体公关团队，下一个 Bun bug 就够你受的。

## 6. 独特视角

### 6.1 这场播客本身就是危机公关链路的一环
- 03-31：源码泄露
- 04-04：OpenClaw 限制生效
- 04-10：OpenClaw 创始人被短暂封号
- 04-?? ：Lenny's Podcast 录制（具体录制日期未知）
- 04-25：J0hn 中文转述上线

Lenny 选择此时邀请 Kat Wu 而不是 Boris Cherny（实际政策发言人），本身就是受控公关动作的一部分。Kat 的「我们不追责，从中学习」「我们也很纠结」这些柔性叙事，对应的是 Boris 在政策声明里的强硬措辞。**两个发言人覆盖两个温度区间**，这是成熟公司的标准操作。

J0hn 没做这个 PR meta-layer 的解读，就把柔性叙事当全貌传给了中文读者。

### 6.2 OpenClaw 事件揭示了 Claude 订阅经济学的真相
真正值得记的不是 Kat Wu 的"基础设施压力"，而是 5x-25x 的成本差这个数字。

它意味着：**Anthropic 此前以 200 美元/月 Max 订阅卖给重度用户的实际成本，至少是 1000-5000 美元/月**。

订阅模型本质是「人速」工作 token 的池化定价。一旦上 agentic、并发、第三方 harness，这个池子立刻穿底。

OpenClaw 不是"给基础设施带来压力"——它是把 Anthropic 错配的定价模型暴露在了阳光下。Anthropic 的反应（限第三方而不是涨订阅价）等于承认：**"这个补贴我可以做给我自己的用户拉新，但做给开源生态我不愿意"**。

这是合理商业决策，但和 Kat Wu 在播客里那种"我们也很为难"的人性化叙事是两回事。

### 6.3 J0hn 这个作者的位置
他是中文 AI 自媒体里**信息密度上乘的搬运者**：选题准、节奏快、自己观点克制（写文章 1 时偶尔反驳吴恩达"面对面"那段）、但**信源处理只到一手转述层**——有什么说什么，不交叉，不挖原始事件，不站到被批评对象（OpenClaw 社区）一侧追问。

这在中文 AI 自媒体里已经算品质上乘的，但读者要清楚：**这是经过友好包装的 Anthropic 视角合订本**。

### 6.4 一句话总结
> 一个公司的最佳实践，传播到行业里就是它的护城河。
> 一个公司的危机公关，传播到媒体里就是它的"内部文化"。
> 这篇文章在帮 Anthropic 完成后者。

## 7. 交叉验证文件

- `wechat-andrewng-pm-bottleneck-critique.md`：J0hn 在 04-28 写的姊妹篇（吴恩达 PM bottleneck 批判），与本文构成自引用循环
- `notes/02-调研/hermes-openclaw-claudecode-comparison.md`：OpenClaw 相关背景对比
- `notes/02-调研/claude-subscription-research.md`：Claude 订阅模式调研

## 8. 公开报道信源

### 源码泄露
- [The Great Claude Code Leak of 2026 — DEV](https://dev.to/varshithvhegde/the-great-claude-code-leak-of-2026-accident-incompetence-or-the-best-pr-stunt-in-ai-history-3igm)
- [Anthropic leaked Claude Code source — Axios (2026-03-31)](https://www.axios.com/2026/03/31/anthropic-leaked-source-code-ai)
- [Fortune: second security lapse, Mythos / Capybara model](https://fortune.com/2026/03/31/anthropic-source-code-claude-code-data-leak-second-security-lapse-days-after-accidentally-revealing-mythos/)
- [Claude Code Source Leaked via npm — The Hacker News](https://thehackernews.com/2026/04/claude-code-tleaked-via-npm-packaging.html)
- [The Register: Anthropic accidentally exposes Claude Code](https://www.theregister.com/2026/03/31/anthropic_claude_code_source_code/)

### OpenClaw 事件
- [TechCrunch: pay extra for OpenClaw support (2026-04-04)](https://techcrunch.com/2026/04/04/anthropic-says-claude-code-subscribers-will-need-to-pay-extra-for-openclaw-support/)
- [TechCrunch: temporarily banned OpenClaw creator (2026-04-10)](https://techcrunch.com/2026/04/10/anthropic-temporarily-banned-openclaws-creator-from-accessing-claude/)
- [VentureBeat: cuts off subscription use of OpenClaw](https://venturebeat.com/technology/anthropic-cuts-off-the-ability-to-use-claude-subscriptions-with-openclaw-and)
- [HN discussion 47633396](https://news.ycombinator.com/item?id=47633396)
- [The Register: closes door on subscription use](https://www.theregister.com/2026/04/06/anthropic_closes_door_on_subscription/)
- [Apiyi blog: 5 key impacts of policy](https://help.apiyi.com/en/anthropic-claude-subscription-third-party-tools-openclaw-policy-en.html)
