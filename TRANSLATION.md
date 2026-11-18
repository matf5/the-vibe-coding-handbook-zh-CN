# 翻译说明 / TRANSLATION.md

> 本仓库是 [hacrex/the-vibe-coding-handbook](https://github.com/hacrex/the-vibe-coding-handbook) 的 Fork 翻译仓库：Fork 保留上游全部 commit 历史，在此基础上做多语言翻译，简体中文（zh-CN）为第一个完整语言。
> This repository is a fork of [hacrex/the-vibe-coding-handbook](https://github.com/hacrex/the-vibe-coding-handbook) for multilingual translation. Simplified Chinese (zh-CN) is the first complete locale.

## 上游来源与版本

- 上游仓库：https://github.com/hacrex/the-vibe-coding-handbook
- 上游提交（翻译基准）：`b2fb5aa`（`Fix completion tracking: roadmap regex, localStorage merge, In Progress filter`）
- 上游许可：MIT License，原文见根目录 `LICENSE`，翻译版同样遵循 MIT 许可，署名归原作者及贡献者所有。
- 翻译基准核查（2026-11-18）：上游共 57 个 Markdown 文件、约 87,229 英文词；46 节（`00`–`45`）+ `glossary` + `README.md` / `Blueprint.md` / `CONTRIBUTING.md` / `RESOURCES.md` / `ROADMAP.md`。上游仓库内无中文版；其 7 个 fork 在核查时均无中文翻译。
- 本仓库：https://github.com/matf5/the-vibe-coding-handbook-zh-CN（2026-11-18 由单 commit 镜像仓库重建为 Fork：先删旧仓库，再 Fork 上游并改名，翻译作为一个 commit 接在上游 `b2fb5aa` 之上；Fork 前历史共 56 个 commit 全保留）
- 国际化（i18n）结构见 [TRANSLATIONS.md](./TRANSLATIONS.md)：英文原文为唯一事实来源，`zh-CN/` 为首个语言目录，任意语言按同一模式新增 `<locale>/` 目录 + `README.<locale>.md` 即可接入，不改英文原文、不改其他语言。

## 目录结构（业界多语言文档做法）

参考 `system-design-primer` 的 `TRANSLATIONS` 模式与 `README.zh-CN.md` / `docs/zh-CN` 镜像模式：

- 根目录保留上游英文文件原样不动（`README.md`、`00-introduction/` … `45-multi-modal-vibe-coding/`、`glossary/`、`Blueprint.md` 等），作为英文原文对照。
- 根目录新增 `README.zh-CN.md`：`README.md` 的完整中文版，其内部章节链接指向 `zh-CN/` 下的中文版。
- 新增 `zh-CN/` 目录，1:1 镜像全部内容，目录名、文件名、顺序与英文版完全一致：
  - `zh-CN/00-introduction/README.md` … `zh-CN/45-multi-modal-vibe-coding/README.md`
  - `zh-CN/glossary/terms.md`、`zh-CN/Blueprint.md`、`zh-CN/CONTRIBUTING.md`、`zh-CN/RESOURCES.md`、`zh-CN/ROADMAP.md`
- `site/` 为网站代码（HTML/JS/CSS），不翻译；`vercel.json`、`.gitignore` 不翻译。
- 英文原文是唯一事实来源（Source of Truth）；中英文不一致时以英文原文为准。

## 翻译铁律

1. 只译正文、标题、表格文字、列表文字；不译、不改代码块、命令、终端输出、URL、链接目标、文件名/路径、变量名、徽章、frontmatter。
   例外：Mermaid 图（```mermaid）内的英文标签可译，但图结构、节点 ID、箭头、语法不变，例如 `A[Describe Intent]` → `A[描述意图]`。
2. 标题数、表格行数、列表项数、代码块数必须与原文逐文件一致；翻译完用脚本逐文件校验并记录差异、修复。
3. 术语统一，见下表；首次出现时按表中“首次”写法，之后按“之后”写法。
4. 不增删段落、不加自己的观点、不改原意、不把“进行中（In Progress）”改成已完成；原仓库所有节均为 In Progress，照实保留。
5. 数字、百分比、统计来源、年份、产品版本号、价格不动。
6. 内部链接：锚文本翻译，链接目标原则上不动；同级章节间的相对链接（如 `../01-what-is-vibe-coding/`）在 `zh-CN/` 内保持原样即自动指向中文版；指向根目录文件的链接（如 `../CONTRIBUTING.md`）改为指向 `zh-CN/` 内对应中文版（如存在），否则改为指向英文根目录的相对路径，并在各批次汇报中注明改动处。
7. 保留原文的 emoji、✅/❌/🟢/🟡/🔴 等标记、复选框 `- [ ]` / `- [x]` 原样。

## 术语表（Glossary）

| 英文 | 首次出现 | 之后 |
|---|---|---|
| Vibe Coding | 氛围编程（Vibe Coding） | Vibe Coding |
| vibe coding（小写） | 氛围编程（vibe coding） | 氛围编程 |
| Zero to Hero | 从零到精通（Zero to Hero） | 从零到精通 |
| AI-assisted development | AI 辅助开发 | AI 辅助开发 |
| AI-assisted software development | AI 辅助软件开发 | AI 辅助软件开发 |
| AI-native | AI 原生 | AI 原生 |
| AI-native software engineering | AI 原生软件工程 | AI 原生软件工程 |
| prompt engineering | 提示工程 | 提示工程 |
| prompt（提示词条目） | 提示词 | 提示词 |
| large language model / LLM | 大语言模型（LLM） | LLM |
| local LLM | 本地大语言模型 | 本地 LLM |
| retrieval-augmented generation / RAG | 检索增强生成（RAG） | RAG |
| vector database | 向量数据库 | 向量数据库 |
| AI agent | AI 智能体（AI Agent） | AI 智能体 |
| autonomous agent | 自主智能体 | 自主智能体 |
| spec-driven development | 规格驱动开发 | 规格驱动开发 |
| frontend | 前端 | 前端 |
| backend | 后端 | 后端 |
| full-stack | 全栈 | 全栈 |
| system design | 系统设计 | 系统设计 |
| microservices | 微服务 | 微服务 |
| DevOps | DevOps | DevOps |
| CI/CD | 持续集成/持续部署（CI/CD） | CI/CD |
| containerization | 容器化 | 容器化 |
| cloud deployment | 云部署 | 云部署 |
| monorepo | Monorepo | Monorepo |
| open source | 开源 | 开源 |
| cheat sheet | 速查表 | 速查表 |
| case study | 案例研究 | 案例研究 |
| failure pattern | 失败模式 | 失败模式 |
| interview prep | 面试准备 | 面试准备 |
| starter kit | 入门套件 | 入门套件 |
| self-assessment | 自我评估 | 自我评估 |
| monetization | 变现 | 变现 |
| freelancing | 自由职业 | 自由职业 |
| MVP | 最小可行产品（MVP） | MVP |
| SaaS | SaaS | SaaS |
| API | API | API |
| IDE | IDE | IDE |
| In Progress | 进行中（In Progress） | 进行中 |

专有名词保留英文，不翻译：Cursor、Windsurf、Kiro、Copilot、Claude、ChatGPT、DeepSeek、Ollama、LM Studio、Lovable、Bolt、v0、Replit、React、Next.js、Vue、TypeScript、JavaScript、Python、Go、Rust、Kubernetes、Docker、Vercel、GitHub、Git、VS Code、JetBrains、Google、Sonar、Stack Overflow、Escape.tech、Lovable 等产品/公司/技术名；以及 RAG、MCP、GPU、CPU、SSD、RAM、ARR、PV 等缩写（首次出现时可按上下文加中文注释，但缩写本身保留）。

## 同步方法

上游更新时：先 `git fetch` 上游对应提交，逐文件比对英文原文的 diff，只把有变化的段落重新翻译，保持 `zh-CN/` 与英文版结构、标题数、表格行数一致；同步后更新本文件“上游提交”一节并重新跑校验脚本。建议在上游每个 release / 明显更新后同步一次，不要逐 commit 跟随。

## 贡献方式

- 只改一个语言版本的一次 PR 只改一种语言；中文翻译的改动只改 `zh-CN/` 与 `README.zh-CN.md`，不要同时改英文原文。
- 改动内容先改英文原文再译中文的原则适用于上游；本镜像内如发现翻译错误，直接提 Issue / PR 修正中文版，并注明对应的英文原文段落。
- 翻译审校：术语以本文件为准；发现术语冲突先在 Issue 中讨论，统一后再批量修改。

## 校验

逐文件校验：标题数（`#` 行）、表格行数（以 `|` 开头的行）、列表项数（以 `-` / `*` / 数字序号开头的行）、代码块数（``` 围栏对数）与英文原文一致。校验脚本与结果见协调员的最终汇报；如有差异须逐项修复或注明原因（例如仅链接目标按第 6 条改动）。

## 已知问题 / 待决事项（2026-11-18 全量初版）

- 目录（TOC）与页内锚点目标按第 6 条保留英文原文；中文标题在 GitHub 渲染后生成的锚点与之不同，这些目录/跳转链接在中文版中无法定位。如要修复，需全库统一把锚点改为中文标题对应的锚点，属较大改动，待用户决定后再做。
- Mermaid 图分支边标签 `|Yes|` / `|No|` / `|Mismatch|` / `|Match|`（42、43、45 章）保留英文，视为图内条件标记。
- `runbook` 在不同章节译法未完全统一：17 章“运维手册”、42 章“运行手册”、11 章提示词分类“应急手册”，均为上下文译法，待定统一词后再批量改。
- 上游笔误：30 章第 293 行原文为 `Write the definition of down`，同文件第 45、123 行均为 `definition of done`，中文版按原意译为“完成定义”，未保留错词；可向上游提 Issue。
- 15 章原文 Best Local Models 一节第 4 项后多出一个无标题的 `ollama pull llama3.2:7b` 代码块，疑似原文排版遗留，中文版原样保留。
- `.github/` 模板与 `site/` 网站代码未翻译，不在本次范围。
- 26 章提示词示例、30 章规格示例句、各章代码块内的英文提示词按铁律保留英文原文，只译说明文字。
