[English 原文](../../35-starter-kits/README.md)

# 🧩 35 - 入门套件与样板

> **不要从空白仓库开始。从一个久经考验的入门套件开始，它已经配置好了 AI 护栏、测试、安全扫描与部署。**
> **样板把氛围编程从周末实验变成可交付的产品——而且更快。**

**难度：** 🟡 中级 · **阅读时间：** 约 14 分钟

---

## 📖 目录

- [为什么入门套件存在](#-why-starter-kits-exist)
- [一个好的 AI 原生入门套件包含什么](#-what-a-good-ai-native-starter-includes)
- [按技术栈推荐的入门套件](#-recommended-starter-kits-by-stack)
- [氛围编程入门模板](#-the-vibe-coding-starter-template)
- [定制入门套件](#-customizing-a-starter-kit)
- [AI 专用的样板文件](#-ai-specific-boilerplate-files)
- [部署就绪清单](#-deployment-ready-checklist)
- [实践清单](#-practical-checklist)
- [关键要点](#-key-takeaways)
- [下一步](#-next-steps)

---

## 🎯 为什么入门套件存在

空白仓库是速度的敌人。每次开始一个氛围编程项目，你都要面对同样的决策：文件夹结构、测试配置、CI/CD、密钥管理、智能体指令、部署配置。入门套件把这些决策一次性做好，让你专注于产品。

2026 年，最好的入门套件是 **AI 原生**的——它们假定智能体会与你一起编写、审查与部署代码。它们开箱即用，包含 `AGENTS.md`、安全扫描、测试脚手架与一键部署。

---

## 🧩 一个好的 AI 原生入门套件包含什么

| 组件 | 为什么重要 |
|-----------|---------------|
| `AGENTS.md` / `CLAUDE.md` | 每个智能体在工作前都会阅读的权威指令 |
| `.cursor/rules/` 或 `.github/copilot-instructions.md` | 工具专用的智能体规则 |
| 测试脚手架（Vitest、Playwright、pytest） | 测试与实现同步编写 |
| 安全扫描（SAST、密钥、依赖） | 严重发现阻止合并 |
| 功能开关 | 无需重新部署即可禁用 AI 构建的功能 |
| 一键部署 | `vercel deploy` / `fly deploy` / `docker compose up` |
| 回滚流程 | 有文档记录的 `git revert` + 部署回滚 |
| 密钥 `.gitignore` | `.env`、`*.key`、`secrets.json` 永不提交 |

---

## 📦 按技术栈推荐的入门套件

| 技术栈 | 入门套件 | 最适用 | AI 原生特性 |
|-------|-------------|----------|-------------------|
| React + Next.js | [shadcn/ui](https://ui.shadcn.com) + Next.js | 前端为主的应用 | Tailwind，可生成组件 |
| Next.js + AI | [Vercel AI SDK starter](https://vercel.com/templates) | AI 聊天应用 | 内置流式 UI、工具调用 |
| 全栈 TypeScript | [T3 Stack](https://create.t3.gg) | 类型安全的应用程序 | tRPC、Prisma、NextAuth |
| Python + FastAPI | [FastAPI template](https://fastapi.tiangolo.com/) | 后端 API | 自动文档、pytest 脚手架 |
| Go | [Go kit](https://github.com/go-kit/kit) | 微服务 | 模块化、可测试 |
| 全栈 AI 原生 | [Lovable / Replit templates](https://lovable.dev) | 非开发者 | 一键部署、智能体已配置 |

> 这些只是起点，不是硬性规定。选择最接近你技术栈的那个，再加上下面 AI 专用的样板。

---

## 🏗️ 氛围编程入门模板

把这个结构复制到你的新项目中：

```
my-app/
├── .github/
│   └── copilot-instructions.md   # GitHub Copilot agent rules
├── .cursor/
│   └── rules/
│       └── project.mdc           # Cursor agent rules
├── AGENTS.md                     # Cross-tool agent instructions (REQUIRED)
├── CLAUDE.md                     # Claude Code instructions
├── .env.example                  # Copy to .env, never commit .env
├── .gitignore                    # Excludes .env, node_modules, dist
├── .github/workflows/
│   └── ci.yml                    # Tests + security scan on every PR
├── tests/                        # Test scaffolding
├── src/
│   ├── lib/
│   ├── components/               # or routes/, services/, etc.
│   └── main.tsx / main.py        # Entry point
├── README.md                     # Human-readable project docs
├── package.json / pyproject.toml # Dependencies + scripts
└── docker-compose.yml            # Local dev environment
```

**`AGENTS.md` 示例：**

```
# Project: My App

## Stack
- Frontend: React + TypeScript + Tailwind
- Backend: Node.js + Express
- Database: PostgreSQL

## Agent Rules
- Always write tests alongside implementation
- Never commit secrets or credentials
- Run `npm test` before marking a task complete
- All changes on feature branches; PR required for main
- Security scan on every PR (GitHub CodeQL)

## Context
- Authentication: JWT in httpOnly cookies
- API style: REST, JSON
- Deploy: Vercel (frontend), Railway (backend)
```

---

## ✏️ 定制入门套件

1. **从你选择的入门套件克隆或生成**
2. **替换 `AGENTS.md`**，写入你项目的技术栈、规则与部署目标
3. **添加 `.env.example`**，包含所有必需的环境变量（不写真实值）
4. **配置 CI**，在每个 PR 上运行测试 + 安全扫描
5. **为任何面向客户的 AI 构建功能设置功能开关**
6. **在 README 中记录回滚流程**

---

## 🤖 AI 专用的样板文件

### `.github/copilot-instructions.md`

```
You are a coding assistant for this project.
- Follow the stack defined in AGENTS.md
- Write tests for every new feature
- Never suggest committing secrets
- Prefer small, focused changes over large refactors
```

### `.cursor/rules/project.mdc`

```
# Project rules
- TypeScript strict mode required
- All PRs need human review before merge
- Tests must pass before commit
- Security scan blocks merge on critical findings
```

### `tests/ai-generated.test.ts`（示例）

```
import { describe, it, expect } from 'vitest'

describe('AI-generated feature', () => {
  it('handles edge cases gracefully', () => {
    // Write this test BEFORE trusting generated code
  })
})
```

---

## 🚀 部署就绪清单

- [ ] 入门套件已克隆，依赖已安装
- [ ] `AGENTS.md` 已按你的技术栈与规则更新
- [ ] `.env.example` 已创建；`.env` 在 `.gitignore` 中
- [ ] CI 工作流在 PR 上运行测试 + 安全扫描
- [ ] 已为 AI 构建的功能配置功能开关
- [ ] 一键部署已测试（`vercel deploy` 或等效命令）
- [ ] 回滚流程已记录并测试
- [ ] 生产监控/告警已配置

---

## ✅ 实践清单

在基于入门套件开始构建之前：

- [ ] 选择了匹配你技术栈的入门套件
- [ ] `AGENTS.md` 已编写并提交
- [ ] 密钥管理已规划（`.env` + 密钥管理器）
- [ ] 测试脚手架已就位
- [ ] PR 上已启用安全扫描
- [ ] 部署目标已选定并测试
- [ ] 回滚流程已记录
- [ ] AI 构建功能的功能开关已就绪

---

## 🔑 关键要点

- **从入门套件开始，而不是从空白仓库开始**——节省数小时的配置时间
- **AI 原生入门套件包含 `AGENTS.md`、测试、安全扫描与部署配置**
- **先定制 `AGENTS.md`**——它是每个智能体都会阅读的文档
- **绝不要提交密钥**——使用 `.env.example` + 密钥管理器
- **尽早部署、频繁部署**——一键部署让迭代变得便宜

---

## 🚀 下一步

- **阅读 [36 — Vibe 编码应用的 Kubernetes 部署](./36-kubernetes-deployment/)**，了解生产容器编排
- **阅读 [34 — 社区案例研究](./34-community-case-studies/)**，了解入门套件的真实成功与失败故事
- **阅读 [31 — AI 成本工程](./31-ai-cost-engineering/)**，为入门套件的 Token 用量做预算

---

<center>

*最后更新：2026 年 11 月*

</center>