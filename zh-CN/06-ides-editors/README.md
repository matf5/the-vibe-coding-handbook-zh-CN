# IDE 与编辑器与氛围编程

面向 AI 辅助开发优化的代码编辑器与 IDE 综合指南，涵盖带 AI 扩展的传统编辑器、原生 AI 优先 IDE 与终端编程智能体。

---

## 目录

1. [编辑器类别](#editor-categories)
2. [带 AI 的传统编辑器](#traditional-editors-with-ai)
3. [AI 原生 IDE](#ai-native-ides)
4. [终端编程智能体](#terminal-coding-agents)
5. [VS Code 配置](#vs-code-setup)
6. [Cursor IDE](#cursor-ide)
7. [Devin Desktop（前身为 Windsurf）](#devin-desktop-formerly-windsurf)
8. [Zed 编辑器](#zed-editor)
9. [Kiro](#kiro)
10. [Google Antigravity 2.0](#google-antigravity-20)
11. [Neovim AI 配置](#neovim-ai-setup)
12. [JetBrains IDE](#jetbrains-ides)
13. [编辑器对比](#editor-comparison)
14. [工作流推荐](#workflow-recommendations)

---

## 编辑器类别

### 传统编辑器 + AI 扩展

通过扩展增强 AI 能力的成熟编辑器：

- **VS Code** + Copilot/Continue/Cline/Claude Code CLI
- **Neovim** + copilot.lua/Continue/终端智能体
- **Sublime Text** + AI 插件
- **JetBrains IDE** + JetBrains AI Assistant / Copilot 插件

**优点：**
- 成熟的生态
- 丰富的插件库
- 熟悉的工作流
- 强大的调试工具
- 出色的版本控制集成

**缺点：**
- AI 功能感觉像是附加的
- 可能需要多个扩展
- 上下文感知因扩展而异

### AI 原生 IDE

从零开始构建、以 AI 为核心功能：

- **Cursor**（Composer 2.5、并行云端智能体、Bugbot 审查）
- **Devin Desktop**（前身为 Windsurf——本地 + 云端智能体委派）
- **Zed**（带 AI 功能）
- **Kiro**（规格驱动开发：规格 → 设计 → 任务）
- **Google Antigravity 2.0**（带多智能体编排的智能体优先平台）

**优点：**
- 深度的 AI 集成
- 更好的上下文理解
- 精简的 AI 工作流
- 内置模型访问
- 为 AI 结对优化的用户体验

**缺点：**
- 较新、不够成熟
- 插件生态较小
- 潜在的厂商锁定
- 订阅成本

---

## 带 AI 的传统编辑器

### Visual Studio Code

**市场份额：** 约 70% 的开发者  
**适用场景：** 大多数用例、最佳生态

**AI 扩展：**

1. **GitHub Copilot** - GitHub 官方 AI 结对编程助手（10–39 美元/月）
2. **Continue** - 开源 AI 助手（自带密钥，任意模型）
3. **Cline** - 自主编程智能体，每步审批（开源）
4. **Tabnine** - AI 自动补全
5. **Sourcegraph Cody** - 感知代码库的 AI

*（Codeium 已更名为 Windsurf，再更名为 Devin Desktop——见 Devin Desktop 一节。请从你的配置中删除任何独立的 Codeium 引用。）*

**配置优先级：**

1. 安装 VS Code Insiders（最新功能）
2. 添加 Continue 扩展（开源灵活性）或 Copilot
3. 通过 Continue 为本地模型（Ollama）配置
4. 安装终端智能体（Claude Code / Codex）用于繁重的自主工作
5. 为 AI 操作设置快捷键

### Neovim

**适用场景：** 终端爱好者、极简主义者、性能

**AI 插件：**

1. **copilot.lua** - GitHub Copilot 集成
2. **continue.nvim** - Continue.dev 移植版
3. **ai.nvim** - 在编辑器内与 AI 聊天
4. **ollama.nvim** - 本地模型访问

**配置示例：**

```lua
-- copilot.lua setup
require('copilot').setup({
  panel = { enabled = false },
  suggestion = { enabled = true },
  filetypes = {
    python = true,
    javascript = true,
    typescript = true,
  },
})

-- Keybinding for AI chat
vim.keymap.set('n', '<leader>ai', ':Continue<CR>')
```

**替代方案：完全跳过插件，在 Neovim 旁边的终端窗格中运行 Claude Code 或 Codex。** 这是 2026 年高级用户的模式：编辑器用于编辑，终端智能体用于自主多文件工作。

### JetBrains IDE

**产品：** IntelliJ IDEA、WebStorm、PyCharm、GoLand 等  
**适用场景：** 企业开发、特定语言

**AI 功能：**

1. **JetBrains AI Assistant** - 官方 AI 集成
2. **GitHub Copilot** - 通过插件提供
3. **Code With Me** - 协作开发

**优势：**

- 深厚的语言理解
- 重构工具
- 数据库集成
- 性能分析与调试
- 企业支持

---

## AI 原生 IDE

### Cursor

**网站：** https://cursor.com  
**定价：** 免费版 + Pro 20 美元/月  
**适用场景：** 通用开发、最佳整体 AI IDE

**关键功能：**

- **与代码库聊天：** 询问关于整个项目的问题
- **Tab 补全：** 智能代码补全
- **Cmd+K：** 用 AI 指令编辑代码
- **Composer 2.5：** 多文件编辑与并行智能体
- **智能体模式：** 自主完成任务
- **Bugbot：** 对拉取请求进行 AI 代码审查
- **模型选择：** 在 Claude Sonnet 5.5、Claude Opus 5.5、GPT-6 Sol/Terra、自定义模型之间切换
- **.cursor/rules / `AGENTS.md`：** 智能体遵循的团队标准

**配置：**

1. 从 cursor.com 下载
2. 导入 VS Code 设置（自动）
3. 安装 VS Code 扩展（兼容）
4. 配置 API 密钥或使用包含的额度
5. 在项目根目录添加 `AGENTS.md`，作为共享的智能体指令

**工作流：**

**代码生成：**
```
Cmd+K → "Create a React component for user profile card
with avatar, name, bio, and social links"
```

**调试：**
```
Select error → Cmd+K → "Fix this TypeScript error
and explain what went wrong"
```

**重构：**
```
Select function → Cmd+K → "Refactor this to use async/await
and add proper error handling"
```

**专业提示：**

- 在聊天中使用 `@files` 引用特定文件
- 仅对非关键代码启用“无需审查始终应用编辑”
- 对多文件变更使用 Composer
- 通过 `.cursor/rules` 或 `AGENTS.md` 为团队风格设置自定义规则
- 将 Cursor 与 **Claude Code**（终端智能体）搭配，用于繁重的自主工作——这是 2026 年的胜出组合

---

## 终端编程智能体

终端智能体检查你的仓库、修改多个文件、运行命令和测试，并准备好变更供你审查。它们对于超出编辑器内自动补全范围的繁重自主工作至关重要。

### Claude Code

**网站：** https://claude.com/code  
**定价：** 按用量分档，20–200 美元/月  
**适用场景：** 深度仓库工作、长时间运行的智能体任务、终端优先的开发者

Claude Code 是 Anthropic 的编程智能体。它读取代码库、编辑文件、运行测试，并从终端、VS Code、JetBrains、Web、移动端、GitHub 或 Slack 处理多步骤任务与迁移。

**核心概念：** `CLAUDE.md` 项目指令、skills（可复用的能力）、hooks（生命周期自动化）、subagents（并行独立工作）、MCP（工具与上下文）。将复杂多文件工作路由给使用 Opus 5.5 的 Claude Code；日常编辑使用 Sonnet 5.5。

**用法：**
```bash
# Start a session in your repo
claude

# With a specific task
claude "Refactor the authentication module and add unit tests"

# Resume a previous session
claude --resume <session-id>
```

### OpenAI Codex

**网站：** https://openai.com/codex  
**定价：** 包含在 ChatGPT 套餐中，或 API 用量  
**适用场景：** 已使用 OpenAI 技术栈的团队、委派任务、并行智能体工作

Codex 是 OpenAI 的编程智能体——可在 ChatGPT 桌面应用、Codex CLI、IDE 扩展、Web 和移动端使用，提供云端任务、GitHub 代码审查与 Slack/Linear 集成。它使用 `AGENTS.md` 作为项目指令。

**用法：**
```bash
# Codex CLI
codex "Add user settings page with profile form and password change"

# Cloud task (delegated, returns a PR)
codex --cloud "Investigate the login timeout bug"
```

### Google Antigravity 2.0

**网站：** https://antigravity.google  
**定价：** 免费版 / Google AI Pro 约 20 美元/月 / AI Ultra 100 美元/月  
**适用场景：** 多智能体编排、基于浏览器的测试、智能体优先工作流

Antigravity 是 Google 的智能体优先开发平台，于 2026 年 5 月 I/O 大会发布。它取代了 Gemini CLI。你可以编排多个智能体（内置 Chromium 浏览器用于测试）、安排后台任务，并使用 Antigravity CLI（Go）与公开 SDK，在第三方基础设施上托管自定义智能体。

**用法：**
```bash
# Antigravity CLI
antigravity agent spawn "Build the checkout flow"
```

**差异化：** 多智能体编排、动态 subagents、定时后台任务、内置浏览器、模型选择器（免费套餐提供 Gemini + Claude + 开放权重模型）。

---

## Devin Desktop（前身为 Windsurf）

**网站：** https://devin.ai  
**定价：** 免费版 + 付费套餐  
**适用场景：** 类 Cursor 的编辑体验 + 本地与云端智能体委派

Windsurf 于 2026 年 6 月 2 日更名为 **Devin Desktop**（Codeium 作为独立品牌已停用）。它将兼容 VS Code 的编辑器与智能体命令中心配对，运行 Devin Local、Devin Cloud 以及 Codex 和 Claude Agent 等第三方智能体。

**关键功能：** 智能体命令中心、worktrees、云端交接（委派繁重工作并获得一个 PR）、`AGENTS.md` 支持、`windsurf/` → `.devin/` 规则迁移。

**配置：**

1. 从 https://devin.ai 下载
2. 登录（原 Codeium 账号——如有现有 Codeium 登录请迁移）
3. 导入 VS Code 设置

**用法：**
```
# Quick question
Cmd+L → "What does this function do?"

# Generate code
Type comment → Tab to complete

# Fix bug
Select code → Cmd+K → "Fix the null pointer issue"

# Delegate to cloud agent
Cmd+Shift+D → "Investigate the checkout timeout and open a PR"
```

---

## Zed 编辑器

**网站：** https://zed.dev  
**定价：** 免费（开源）  
**适用场景：** 性能爱好者、Rust 开发者

**关键功能：**

- **极快：** GPU 加速渲染
- **内置 AI：** 原生 AI 集成
- **协作：** 实时结对编程
- **扩展：** 不断增长的生态
- **基于 Rust：** 高性能

**AI 配置：**

```json
// settings.json
{
  "ai": {
    "provider": "ollama",
    "model": "deepseek-v4-flash",
    "auto_complete": true
  }
}
```

**优势：**

- 最快的编辑器
- 简洁、极简的 UI
- 良好的 Vim 模式
- 原生 AI 支持
- 积极开发中

**劣势：**

- 仅支持 macOS/Linux（Windows 为测试版）
- 扩展生态较小
- 较新、不够稳定

---

## Kiro

**网站：** https://kiro.dev（AWS）  
**定价：** 20–40 美元/月  
**适用场景：** 希望先写规格再写代码的团队

Kiro 是唯一将**一流规格驱动开发**作为主流的智能体 IDE：编写规格 → 生成设计 → 拆解为任务 → 让智能体逐个实现任务，并逐一对照规格检查。它包含 steering 文件、hooks 与并行 Specs。

**差异化：** 规格是一等公民，而非事后补充。完整工作流见 `30-spec-driven-development` 章节。

**用法：**
```
# Create a spec
kiro spec create "User booking system"

# Generate design from spec
kiro design from-spec booking-spec.md

# Implement tasks one at a time
kiro task implement --next
```

---

## Google Antigravity 2.0

*（配置见“终端编程智能体”一节。）*

Antigravity 2.0 于 2026 年 5 月 Google I/O 大会发布，是一个**智能体优先开发平台**：Antigravity IDE、CLI、SDK 与扩展。它将多智能体编排与内置 Chromium 浏览器结合，让智能体可以在真实浏览器中测试你的应用。免费套餐运行 Gemini 模型以及 Anthropic 与开放权重模型；付费档位（Google AI Pro 约 20 美元/月、AI Ultra 100 美元/月）提高限额。

**何时选择 Antigravity：** 基于浏览器的测试很重要、你希望开箱即用的多智能体编排，或你想要最低的入门门槛（免费版）。

**何时谨慎：** Google 已多次重写限额规则（值得注意的是 2026 年 5 月那次）——今天的免费版评估下个月可能不再成立。

---

## VS Code 配置

### 必备 AI 扩展

**1. Continue（推荐）**
```json
// settings.json
{
  "continue.models": [
    {
      "title": "Ollama",
      "provider": "ollama",
      "model": "deepseek-v4-flash"
    },
    {
      "title": "Claude",
      "provider": "anthropic",
      "model": "claude-sonnet-5-5",
      "apiKey": "YOUR_KEY"
    }
  ]
}
```

**键盘快捷键：**
```json
// keybindings.json
[
  {
    "key": "cmd+l",
    "command": "continue.continueGUIView.focus"
  },
  {
    "key": "cmd+i",
    "command": "continue.inlineEdit"
  }
]
```

**2. GitHub Copilot**
```bash
# Install via Extensions panel
# Sign in with GitHub account
# Free for students, OSS maintainers
# $10/month otherwise
```

**3. Cline（自主智能体）**
```json
// settings.json
{
  "cline.apiKey": "YOUR_ANTHROPIC_KEY",
  "cline.model": "claude-sonnet-5-5",
  "cline.autoApprove": false
}
```

### 推荐扩展组合

**核心 AI：**
- Continue（主要 AI 界面）
- GitHub Copilot（自动补全）

**增强功能：**
- Error Lens（行内错误）
- GitLens（Git 增强）
- Thunder Client（API 测试）
- Docker（容器管理）
- Remote - SSH（远程开发）

**语言专属：**
- ESLint + Prettier（JavaScript/TypeScript）
- Python（ms-python.python）
- Rust Analyzer（rust-lang.rust-analyzer）
- Go（golang.go）

### 设置优化

```json
{
  "editor.quickSuggestions": {
    "other": "on",
    "comments": "off",
    "strings": "off"
  },
  "editor.inlineSuggest.enabled": true,
  "github.copilot.enable": {
    "*": true,
    "plaintext": false,
    "markdown": false,
    "scminput": false
  },
  "continue.allowAnonymous": false,
  "continue.telemetry": "off"
}
```

---

## Cursor IDE

### 深入配置

**安装：**

1. 从 https://cursor.com 下载
2. 选择导入 VS Code 设置（推荐）
3. 在现有 VS Code 配置之上安装

**模型配置：**
```json
// settings.json
{
  "cursor.ai.model": "claude-sonnet-5-5",
  "cursor.ai.fastModel": "gpt-6-1-terra",
  "cursor.ai.customModels": [
    {
      "name": "Local DeepSeek",
      "provider": "ollama",
      "model": "deepseek-v4-flash",
      "baseUrl": "http://localhost:11434"
    }
  ]
}
```

### 关键工作流

**1. 与代码库聊天**
```
Cmd+L → "@workspace How does authentication work
in this project?"
```

**2. 行内编辑**
```
Select code → Cmd+K → "Add input validation
and error handling"
```

**3. 多文件变更**
```
Cmd+Shift+A (Composer) →
"Add user settings page with:
- Profile form
- Password change
- Notification preferences
Update routes, components, and API endpoints"
```

**4. 用 AI 调试**
```
Select error → Right-click → "Explain with AI"
or
Cmd+L → "Why is this test failing?"
```

**5. 生成测试**
```
Select function → Cmd+K →
"Generate comprehensive unit tests
including edge cases"
```

### Cursor Rules

创建 `.cursor/rules` 文件（或在仓库根目录添加 `AGENTS.md`）作为团队标准：

```
# Code Style
- Always use TypeScript strict mode
- Prefer functional components with hooks
- Use async/await over promises
- Add JSDoc comments for public APIs

# Testing
- Write tests for all new features
- Aim for 80%+ coverage

# Security
- Never commit API keys
- Validate all user inputs
- Use parameterized queries
```

### 专业提示

1. **使用 @ 引用：**
   - `@file.py` - 引用特定文件
   - `@folder/` - 引用目录
   - `@docs` - 引用文档

2. **用 Composer 做大变更：**
   - 拆解复杂任务
   - 应用前审查变更
   - 频繁使用版本控制

3. **智能体模式：**
   - 对常规任务启用
   - 对关键代码禁用
   - 始终审查最终输出

4. **键盘效率：**
   - `Cmd+L` - 打开聊天
   - `Cmd+K` - 行内编辑
   - `Cmd+Shift+A` - Composer
   - `Cmd+Enter` - 接受建议

---

## Neovim AI 配置

### 最小配置

**使用 lazy.nvim：**

```lua
-- copilot.lua
return {
  {
    "zbirenbaum/copilot.lua",
    cmd = "Copilot",
    event = "InsertEnter",
    build = ":Copilot auth",
    opts = {
      suggestion = { enabled = true },
      panel = { enabled = false },
    },
  },
  {
    "ContinuumHQ/continue",
    lazy = false,
    config = function()
      require("continue").setup({
        models = {
          {
            title = "Ollama",
            provider = "ollama",
            model = "deepseek-v4-flash",
          },
        },
      })
    end,
  },
}
```

### 快捷键

```lua
-- Continue.nvim mappings
vim.keymap.set('n', '<leader>cc', ':ContinueChat<CR>', 
  { desc = 'Continue Chat' })
vim.keymap.set('v', '<leader>ce', ':ContinueEdit<CR>', 
  { desc = 'Continue Edit' })
vim.keymap.set('n', '<leader>ca', ':ContinueAccept<CR>', 
  { desc = 'Continue Accept' })

-- Copilot mappings
vim.keymap.set('i', '<C-j>', 'copilot#accept("\<CR>")', 
  { expr = true, replace_keycodes = false })
```

### 工作流

**以终端为中心的 AI 编程：**

1. 在 Neovim 中打开文件
2. `<leader>cc` 打开聊天
3. 请求实现
4. 行内审查建议
5. `<leader>ca` 接受

**高级用户模式：** 在终端窗格（`tmux` 分屏）中与 Neovim 并行运行 Claude Code 或 Codex——编辑器用于精确编辑，终端智能体用于自主多文件工作。

---

## JetBrains IDE

### AI Assistant 配置

**启用 AI 功能：**

1. Settings → Tools → AI Assistant
2. 用 JetBrains 账号登录
3. 启用功能：
   - 代码补全
   - 聊天
   - 文档生成
   - 提交信息生成

**使用示例：**

**聊天：**
```
Alt+Enter → AI Assistant →
"Generate a Spring Boot controller for user management"
```

**文档：**
```
Select class → Alt+Enter →
"Generate JavaDoc"
```

**重构：**
```
Select code → Right-click →
"Refactor with AI" → "Extract method"
```

### 最佳用例

**企业开发：**

- 大型代码库
- 团队协作
- 数据库集成
- 微服务
- 遗留代码现代化

---

## 编辑器对比

### 功能矩阵

| 功能 | VS Code | Cursor | Devin Desktop | Zed | Neovim | Claude Code | Codex | Antigravity | Kiro |
|---------|---------|--------|---------------|-----|--------|-------------|-------|-------------|------|
| AI 质量 | ⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ | ⭐⭐⭐ | ⭐⭐⭐ | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐ | ⭐⭐⭐⭐ | ⭐⭐⭐⭐ |
| 速度 | ⭐⭐⭐ | ⭐⭐⭐⭐ | ⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ | ⭐⭐⭐ | ⭐⭐⭐⭐ | ⭐⭐⭐ | ⭐⭐⭐ |
| 扩展 | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐ | ⭐⭐⭐⭐ | ⭐⭐ | ⭐⭐⭐ | N/A | N/A | N/A | N/A |
| 免费版 | ✅ | 有限 | ✅ | ✅ | ✅ | 试用 | 试用 | ✅ | 试用 |
| 本地模型 | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ |
| 学习曲线 | 低 | 低 | 低 | 中 | 高 | 中 | 中 | 中 | 中 |
| 适用场景 | 所有人 | AI 优先功能工作 | 本地+云端委派 | 性能 | 终端 | 深度仓库工作 | OpenAI 技术栈团队 | 多智能体编排 | 规格驱动团队 |

### 定价对比

| 编辑器 / 智能体 | 免费版 | Pro 版 | 企业版 |
|----------------|-----------|----------|------------|
| VS Code | ✅ 完整 | 不适用 | 不适用 |
| Cursor | 50 条消息/月 | 20 美元/月 | 定制 |
| Devin Desktop | ✅ 有限 | 付费套餐 | 团队 |
| Zed | ✅ 完整 | 不适用 | 不适用 |
| Neovim | ✅ 完整 | 不适用 | 不适用 |
| JetBrains | 30 天 | 8–20 美元/月 | 30–50 美元/月 |
| Claude Code | 试用 | 20–200 美元/月 | 联系销售 |
| Codex | 试用（ChatGPT） | ChatGPT 套餐 | 联系销售 |
| Antigravity | ✅ 免费版 | Google AI Pro 约 20 美元/月 | AI Ultra 100 美元/月 |
| Kiro | 试用 | 20–40 美元/月 | 联系销售 |

---

## 工作流推荐

### 初学者配置

**推荐：** VS Code + Continue + Ollama

```bash
# 1. Install VS Code
# 2. Install Continue extension
# 3. Install Ollama
brew install ollama  # macOS
curl -fsSL https://ollama.com/install.sh | sh  # Linux

# 4. Pull model
ollama pull deepseek-v4-flash

# 5. Configure Continue
# Open ~/.continue/config.json
```

**config.json：**
```json
{
  "models": [
    {
      "title": "DeepSeek V4 Flash",
      "provider": "ollama",
      "model": "deepseek-v4-flash"
    }
  ],
  "tabAutocompleteModel": {
    "title": "DeepSeek V4 Flash",
    "provider": "ollama",
    "model": "deepseek-v4-flash"
  }
}
```

### 中级配置

**推荐：** Cursor Pro + 本地后备

```bash
# 1. Subscribe to Cursor Pro ($20/mo)
# 2. Set primary model: Claude Sonnet 5.5
# 3. Configure local fallback:

# settings.json
{
  "cursor.ai.model": "claude-sonnet-5-5",
  "cursor.ai.fallbackModel": {
    "provider": "ollama",
    "model": "deepseek-v4-flash"
  }
}

# 4. Install Ollama for offline work
ollama pull deepseek-v4-flash
```

### 高级/团队配置

**推荐：** 混合方案——IDE 助手 + 终端智能体（2026 年的胜出模式）

```yaml
# Team Configuration
primary_ide: Cursor Pro
terminal_agent: Claude Code
local_models: Ollama cluster (deepseek-v4-flash, glm-5.3)
ci_cd: GitHub Actions + AI review
code_quality: Automated AI review + Bugbot
security: Local models for sensitive code; scan every PR
```

**团队规则（`.cursor/rules` 或 `AGENTS.md`）：**
```
# Team Standards
- TypeScript strict mode required
- All PRs reviewed by AI first, then human
- Test coverage > 80%
- Security scan before merge
- Document public APIs
- Agents need human approval before production changes
```

### 专业工作流

**前端开发：**
```
Primary: Cursor + Claude Sonnet 5.5
Tasks:
- Component generation
- Tailwind CSS
- State management
- Testing

Setup:
- v0.dev for UI inspiration
- Cursor for implementation
- Playwright for E2E tests
```

**后端开发：**
```
Primary: Cursor + Claude Sonnet 5.5
Tasks:
- API design
- Database schemas
- Authentication
- Deployment configs

Setup:
- Cursor with multiple models
- Local DeepSeek for quick tasks
- Claude Opus 5.5 for complex architecture
```

**DevOps：**
```
Primary: VS Code + Cline (agent) or Claude Code
Tasks:
- Infrastructure as Code
- CI/CD pipelines
- Monitoring setup
- Security hardening

Setup:
- Cline / Claude Code for autonomous work
- Terraform/Ansible extensions
- Kubernetes tools
```

**规格驱动团队：**
```
Primary: Kiro
Tasks: Specs → design → tasks → agent implementation

Setup:
- Kiro Pro ($20–40/mo)
- AGENTS.md for cross-tool consistency
- Human review at each task boundary
```

---

## 快速上手指南

### 5 分钟配置（VS Code）

```bash
# 1. Install VS Code
# 2. Install Continue extension
# 3. Install Ollama
# 4. Pull model
ollama pull deepseek-v4-flash

# 5. Start coding!
# Cmd+L to chat
# Cmd+I to inline edit
```

### 15 分钟配置（Cursor）

```bash
# 1. Download Cursor
# 2. Import VS Code settings
# 3. Sign up for free tier
# 4. Configure preferred model (Claude Sonnet 5.5)
# 5. Try workflows:
#    - Cmd+L: Chat
#    - Cmd+K: Edit
#    - @workspace: Codebase questions
```

### 高级用户配置（1 小时）

```bash
# 1. Install Cursor Pro
# 2. Install Claude Code terminal agent
# 3. Set up Ollama with multiple models
ollama pull deepseek-v4-flash
ollama pull glm-5.3
ollama pull kimi-k3

# 4. Configure Cursor rules
# 5. Set up keyboard shortcuts
# 6. Create workflow templates
# 7. Test with real project
# 8. Pair Cursor with Claude Code for autonomous work
```

---

## 资源

### 扩展链接

- Continue：https://continue.dev
- GitHub Copilot：https://github.com/features/copilot
- Cline：https://cline.bot
- Claude Code：https://claude.com/code
- OpenAI Codex：https://openai.com/codex
- Kiro：https://kiro.dev
- Antigravity：https://antigravity.google
- Devin Desktop：https://devin.ai

### IDE 下载

- Cursor：https://cursor.com
- Devin Desktop：https://devin.ai
- Zed：https://zed.dev
- VS Code：https://code.visualstudio.com

### 社区

- r/cursor_ai（Reddit）
- Continue Discord
- Zed Discord
- VS Code Slack
- Anthropic Claude Code 社区

---

*最后更新：2026 年 11 月*
