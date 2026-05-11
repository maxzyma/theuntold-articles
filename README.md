# theuntold-articles

> 站点 [theuntold.ai](https://theuntold.ai/) 的**文章源 + 修订史**——以 git 为单一可信源（git-as-source-of-truth），每篇文章作为独立 markdown，每次修订作为独立 commit。

---

## 为什么独立公开仓库

theuntold.ai 声称是 _AI 时代批判性媒体监督_——一个用 LLM 做信源核查、省略标注、立场分析的内容站点。但 AI 写出的"AI 内容批判"本身也是一种二手内容生产链。**读者凭什么相信这个站不是黑箱？**

唯一可执行的答案：让**内容**和**它的修订史**对所有人可读、不可篡改。这个仓库就是这个承诺的具体形态：

| 透明层 | 在本仓库里如何被审计 |
|--------|---------------------|
| **文章发表版本** | `articles/untold-{nnn}.md` — 你在 [theuntold.ai/u/untold-{nnn}](https://theuntold.ai/) 看到的内容，与本仓库 markdown 字字相符（站点用 `git_commit_hash` 锚定渲染版本） |
| **每一次修订** | `git log articles/untold-{nnn}.md` — 改动时间、改动者、commit message、diff 完整可看 |
| **撤稿 / 重大更正** | 该篇 markdown 的 commit 应带 `revoke:` / `correction:` 前缀，diff 即解释 |
| **产出主体** | 每篇 frontmatter / DB 的 `model` 字段：`human-baseline` = 站长手写；`openai-codex` 等 = 对应 LLM 模型；任何撤稿 / 替换都在 commit message 中说明 |
| **原始稿留底** | `baselines/` 目录留两篇站长手写原稿，作为 LLM eval 的离线对照样本（与已发表的 untold-001/002 同源但独立留存） |

theuntold 的 Web 应用源码目前**私有**——所以这个 articles 仓库是站点**唯一**对外公开的事实层。代码层的审计将在源码达到稳定 v1 时单独开源。当下，所有读者可立即验证的是：内容修订史。

---

## 当前文章索引

| Slug | 标题 | model | 发布日 | URL |
|------|------|-------|--------|-----|
| `untold-001` | 吴恩达：最快的团队，人人都是产品经理 | `human-baseline` | 2026-04-28 | [→](https://theuntold.ai/u/untold-001) |
| `untold-002` | Anthropic 产品负责人：从 6 个月到 1 天的发版秘密，harness 会被模型当早餐吃掉 | `human-baseline` | 2026-04-28 | [→](https://theuntold.ai/u/untold-002) |

> `model` 字段标注每篇文章的产出主体：`human-baseline` = 站长手写；`openai-codex` 等 = 对应 LLM 模型产出。读者可凭此判断信息来源链路；站点不在文章卡片上做"作者亲笔 vs AI"标签，避免主张分级。

> **历史注**：早期发布的 `untold-003` / `untold-004` 是 LLM 对相同上游素材的二次产出，与 001/002 标题完全重复——保留两份对读者构成噪声而非信号，已在 2026-05-11 撤下。完整 diff 仍可通过 git history（commit `<待提交>` 之前的版本）取回，作为 LLM-vs-Human 风格研究的离线参考样本。

---

## 目录结构

```
theuntold-articles/
├── README.md                    # 本文件
├── LICENSE                      # CC BY-NC-SA 4.0（内容许可，不允许商用、衍生品同许可）
├── articles/                    # 站点发表内容
│   ├── untold-001.md            # 与站点 /u/untold-001 渲染对应
│   └── untold-002.md
└── baselines/                   # 站长亲笔原稿（与 articles/untold-001/002 同源，独立留存供未来 LLM eval 对照）
    ├── wechat-andrewng-pm-bottleneck-critique.md
    └── wechat-anthropic-katwu-podcast-critique.md
```

---

## 修订史怎么读

### 站点内（最方便）

在文章页 [theuntold.ai/u/untold-001](https://theuntold.ai/u/untold-001/) 等的底部，点 **REVISION HISTORY ▾** 折叠区——直接看到该篇所有 commit（SHA + 时间 + message + 跳 GitHub diff 链接）。

### 命令行（本仓库 clone）

```bash
git clone https://github.com/maxzyma/theuntold-articles.git
cd theuntold-articles

# 看某篇所有修订
git log --oneline articles/untold-001.md

# 看具体一次修订的 diff
git show <commit-sha> -- articles/untold-001.md

# 看任意两个版本差异
git diff <commit-a> <commit-b> -- articles/untold-001.md
```

---

## 引用规则（重要）

本仓库内容采用 **[Creative Commons BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/)** 许可：

| 你可以 | 必须 | 不可以 |
|--------|------|--------|
| 复制 / 引用 / 改编 | **署名**: 注明 "theuntold.ai" 和文章 URL | 商业使用（含付费墙、订阅服务、训练商用 AI 模型） |
| 用于研究、教育、新闻评论 | **同许可**: 衍生品继续 BY-NC-SA | 隐去出处 |
| 自架本仓库的镜像 | 保留 LICENSE + 修订史 | 删除或篡改 commit history |

### 关于 LLM 训练数据

本仓库的 `untold-{nnn}.md` markdown **不允许**直接进入商用 AI 模型（OpenAI / Anthropic / Google 等）的训练集——CC BY-NC-SA 的 _NC_（NonCommercial）禁止。但学术 / 非商用研究的 fine-tune / eval 是允许的（必须注明出处 + 衍生 dataset 同许可）。

---

## 与 theuntold.ai 站点的关系

```
[读者] —GET—> theuntold.ai/u/untold-001
              │
              ├─ DB: SELECT git_commit_hash FROM articles WHERE slug='untold-001'
              │
              └─ fetch raw.githubusercontent.com/maxzyma/theuntold-articles/{commit_hash}/articles/untold-001.md
                                                                          ↑
                                                                  本仓库 git-tracked
```

- 站点 URL 永久指向**某个 commit hash 的 markdown**——后续 commit 不会破坏旧 URL 内容（除非 DB 显式更新 git_commit_hash）
- 文章更正：站长 push 新 commit 到本仓库 → 站点更新 DB 的 git_commit_hash → 读者刷新页面看到新版（同时 RevisionHistory 累计一条 commit）

---

## 反馈 / 报错 / 信源问题

如果你在某篇文章里发现：
- **事实错误** / 信源链接失效 / 引用失真
- **省略关键事实** / 立场判定不准
- **markdown 渲染问题**（表格 / 引用 / 链接）

请直接[提 issue](https://github.com/maxzyma/theuntold-articles/issues/new)，附上 article slug + 具体段落 / 信源链接。我们会按 [theuntold.ai/docs/quality-disclosure](https://theuntold.ai/docs/quality-disclosure) 披露的流程处理（重要更正会作为独立 commit + commit message 注明 `correction:` 前缀）。

涉及 DMCA / 法律异议走 [theuntold.ai/takedown-log](https://theuntold.ai/takedown-log) — 我们的政策是**公示**而非自动下线（媒体出版者抗辩）。

---

## 姐妹仓库

- [theuntold.ai](https://theuntold.ai/) — 主站点（理由的当下版本：审计透明的产品定位 + 5+2 防线）
- [trending.theuntold.ai](https://trending.theuntold.ai/) — sister site，每日 GitHub Trending 深度分析（共享 brand DNA）
- _theuntold 主站源码_：当前**私有**，未对外开放；达到稳定 v1 后单独 license 开源。
