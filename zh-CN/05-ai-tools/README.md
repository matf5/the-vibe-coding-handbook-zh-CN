# AI 工具与氛围编程

2026 年最佳 AI 驱动开发工具的综合对比与指南。

> **最后更新：2026 年 11 月**——涵盖当前工具格局（Claude Code、Cursor Composer 2.5、Codex、Antigravity 2.0、Devin Desktop）与 2026 年定价。

---

## 目录

- [总览](#overview)
- [AI 聊天界面](#ai-chat-interfaces)
- [AI 原生 IDE](#ai-native-ides)
- [编码智能体](#coding-agents)
- [IDE 扩展与插件](#ide-extensions--plugins)
- [代码生成平台](#code-generation-platforms)
- [本地 AI 工具](#local-ai-tools)
- [专业工具](#specialized-tools)
- [工具对比矩阵](#tool-comparison-matrix)
- [配置指南](#setup-guides)
- [工作流示例](#workflow-examples)
- [最佳实践](#best-practices)

---

## 总览

AI 工具生态正在快速演进。本指南涵盖主要类别：

```
┌─────────────────────────────────────────────────────────┐
│                  AI Development Tools                    │
├─────────────────────────────────────────────────────────┤
│  Chat Interfaces    →  Claude, ChatGPT, Gemini          │
│  AI-Native IDEs     →  Cursor, Devin Desktop, Kiro      │
│  Coding Agents      →  Claude Code, Codex, Antigravity  │
│  Extensions         →  Continue, Cline, Copilot         │
│  Code Platforms     →  Bolt, Lovable, v0, Replit        │
│  Local Tools        →  Ollama, LM Studio, Jan           │
│  Specialized        →  Aider, Augment, Mintlify         │
└─────────────────────────────────────────────────────────┘
```

**2026 年格局数据：**
- **72%** 的开发者每天使用 AI 工具；约 **42%** 的已提交代码由 AI 生成或辅助生成（Sonar 2026 年调查，1,149 名专业人士）
- **96%** 的专业人士并不完全信任 AI 代码——而且只有 **48%** 的人总是在提交前检查它（Sonar 2026）
- **84%** 的开发者使用或计划使用 AI 工具，但 **72%** 表示纯氛围编程*不是*他们工作流程的一部分（Stack Overflow 2025）
- 约 **63%** 的氛围编程平台用户不是开发者
- 2025 年 5 月至 9 月，编码智能体生成的超过 **100 万个 PR** 在 GitHub 上被合并（Octoverse 2025）
- **2026 年的胜出模式：** 将 IDE 助手（Cursor 或 Copilot）与终端智能体（Claude Code 或 Codex）搭配使用

---

## AI 聊天界面

用于通用编程辅助的 Web 或桌面聊天应用。

### 1. Claude（Anthropic）

**网站：** https://claude.ai

**是什么：**
领先的 AI 助手，以出色的推理能力、长上下文和安全的输出著称。

**功能：**
- 模型：Claude Opus 5.5（旗舰）、Sonnet 5.5、Fable 5.1、Haiku 5.5
- 100 万上下文窗口（整个代码库）
- 用于代码预览的 Artifact 视图
- 文件上传（PDF、TXT、代码文件）
- Web 搜索集成
- 团队协作功能
- 用于自动化的 API 访问
- 与 Claude Code（Anthropic 的编码智能体）联动

**优点：**
✅ BenchLeader 编码指数第 1 名（Opus 5.5）
✅ 一流的代码质量
✅ 善于重构
✅ 100 万上下文理解
✅ 安全、可靠的输出
✅ 出色的文档编写能力
✅ 强大的安全意识

**缺点：**
❌ 完整访问需要付费订阅
❌ 免费版有速率限制
❌ Fable/Opus 用量成本上升很快
❌ 定制化有限

**定价：**
- 免费：每日消息有限
- Pro：约 20 美元/月（更多用量）
- Max：更高档位（约 100-200 美元/月），适用于重度使用和 Claude Code
- Team：25-30 美元/用户/月
- Enterprise：定制价格

**最佳用例：**
- 架构设计
- 代码审查
- 文档编写
- 复杂重构
- 安全分析
- 学习新技术

**配置指南：**
1. 访问 https://claude.ai
2. 用邮箱或 Google 注册
3. 立即开始聊天
4. 通过回形针图标上传文件
5. 使用 `/` 命令执行特殊操作

**示例工作流：**
```markdown
Prompt: "Review this authentication middleware for security issues.
         Consider OWASP Top 10, rate limiting, and session management."

[Upload: auth-middleware.js]

Claude analyzes → Identifies vulnerabilities → Suggests fixes → 
Provides corrected code → Explains each change
```

**专业提示：**
- 使用“Artifacts”功能预览 React 组件
- 让 Claude 创建 Mermaid 图表来说明架构
- 对存疑的建议要求标注不确定性
- 通过上传多个文件提供项目上下文

---

### 2. ChatGPT（OpenAI）

**网站：** https://chatgpt.com

**是什么：**
最受欢迎的 AI 聊天机器人，具备强大的编码能力与多模态功能。

**功能：**
- GPT-6 Astra、GPT-6.1 Sol/Terra 和 GPT-6 Luna 模型
- 约 100 万上下文窗口
- 代码解释器（Advanced Data Analysis）
- 图像输入与图像生成
- 用于专门任务的自定义 GPT
- 语音模式（移动端）
- 用于编写和运行代码的 Codex 智能体

**优点：**
✅ 多才多艺、富有创意
✅ 在众多领域都很强
✅ 代码执行沙箱
✅ 视觉能力
✅ 自定义 GPT 市场
✅ 适合头脑风暴

**缺点：**
❌ 可能编造库/API
❌ 代码质量不稳定
❌ Astra 档位用量昂贵
❌ 有时过于啰嗦
❌ 安全过滤器可能过于严格

**定价：**
- 免费：带有限制的 GPT-6 Luna 级访问
- Go：轻度使用的低成本档位
- Plus：约 20 美元/月（GPT-6.1 模型）
- Pro：最高限额的高级档位（GPT-6 Astra）
- Team/Enterprise：定制

**最佳用例：**
- 快速原型
- 学习概念
- 多模态任务（图像 + 代码）
- 创造性问题解决
- 数据分析
- 生成测试数据

**配置指南：**
1. 访问 https://chatgpt.com
2. 创建账号
3. 升级到 Plus 以使用 GPT-6.1 模型
4. 在商店中探索自定义 GPT
5. 为数据任务启用代码解释器

**示例提示词：**
```markdown
"You are a senior full-stack developer. Build a complete Next.js 14 
app with App Router, TypeScript, Tailwind CSS, and PostgreSQL.

Include:
- Authentication with NextAuth
- Dashboard with charts
- CRUD operations
- API routes
- Error boundaries
- Loading states

Provide file structure first, then implement each file."
```

---

### 3. DeepSeek

**网站：** https://deepseek.com

**是什么：**
高性价比的中国 AI 模型，编码性能出色。

**功能：**
- DeepSeek V4 Pro 和 V4.1 Flash 模型
- 100 万上下文
- 混合专家（MoE）架构
- 极低的 API 成本
- 强大的多语言支持
- 针对代码的专门训练

**优点：**
✅ 超高性价比（比旗舰模型便宜 95% 以上）
✅ 出色的编码基准
✅ 100 万上下文支持
✅ 响应速度快
✅ 良好的 API 文档
✅ 提供免费版

**缺点：**
❌ 在西方市场知名度较低
❌ 偶有语言上的小问题
❌ 社区较小
❌ 集成有限
❌ 部分用户有隐私顾虑

**定价：**
- 免费版：请求有限
- V4.1 Flash：每 100 万输入 0.15 美元，每 100 万输出 0.60 美元
- V4 Pro：每 100 万输入 0.66 美元，每 100 万输出 1.98 美元
- 对个人开发者来说基本免费

**最佳用例：**
- 大批量代码生成
- 批量处理
- 对成本敏感的项目
- API 集成
- 快速迭代

**配置指南：**
1. 访问 https://platform.deepseek.com
2. 注册账号
3. 获取 API 密钥
4. 与 OpenAI 兼容的客户端一起使用
5. 或直接在网站上聊天

**API 示例：**
```python
from openai import OpenAI

client = OpenAI(
    api_key="YOUR_KEY",
    base_url="https://api.deepseek.com"
)

response = client.chat.completions.create(
    model="deepseek-v4.1-flash",
    messages=[{"role": "user", "content": "Write a Python decorator..."}]
)
```

---

### 4. Gemini（Google）

**网站：** https://gemini.google.com

**是什么：**
Google 的旗舰 AI，拥有超大上下文窗口与多模态能力。

**功能：**
- Gemini 4 Argon、Gemini 4 Carbon 和 Gemini Flash 模型
- 100 万 token 上下文（旗舰标配）
- 原生 Google 集成
- 高级视觉能力
- 代码执行
- YouTube 视频分析

**优点：**
✅ DeepSWE v1.1 最佳成绩（Gemini 4 Argon，77.9%）
✅ 出色的多模态理解
✅ Google 生态集成
✅ 免费版慷慨
✅ 快速的 Gemini Flash 选项
✅ 善于解释概念

**缺点：**
❌ 代码质量因档位而异
❌ 有时过于谨慎
❌ 集成复杂
❌ 隐私顾虑
❌ 可用性不稳定

**定价：**
- 免费：Gemini Flash
- Google AI Pro：约 20 美元/月（Gemini 4 Argon）
- Google AI Ultra：约 100 美元/月（最高限额）
- API：按量付费（Argon 每 100 万 token 约 2 美元/10 美元，推广价）

**最佳用例：**
- 分析大型代码库
- 处理文档
- 视频教程 → 代码转换
- Google Cloud 集成
- 研究任务

---

### 5. Grok（xAI）

**网站：** https://grok.x.ai

**是什么：**
来自 Elon Musk 的 xAI 的 AI，集成了实时 X（Twitter）。

**功能：**
- 实时信息访问
- 限制较少的回答
- X 平台集成
- 编码能力不断提升
- 有趣的人格模式

**优点：**
✅ 最新信息
✅ 过滤较少
✅ X/Twitter 集成
✅ 快速改进
✅ 独特视角

**缺点：**
❌ 需要 X Premium
❌ 编码不是主要焦点
❌ 知识库较小
❌ 企业功能有限

**定价：**
- X Premium：约 8-16 美元/月，包含 Grok

**最佳用例：**
- 实时技术新闻
- 热门话题
- 非常规解决方案
- 社交媒体集成

---

## AI 原生 IDE

围绕 AI 构建的完整集成开发环境。

### 1. Cursor

**网站：** https://cursor.com

**是什么：**
领先的 AI 优先代码编辑器，基于 VS Code 分叉，深度集成 AI。

**功能：**
- 基于 VS Code（熟悉的界面）
- 用于多文件变更的 Composer 2.5 智能体
- 并行云端智能体（同时运行多个任务）
- Bugbot 自动化代码审查
- 带代码库上下文的聊天侧栏
- 行内 AI 编辑（Cmd+K）
- Tab 自动补全
- Git 集成
- 本地模型支持（Ollama）
- 终端集成

**优点：**
✅ 一流的 AI 集成
✅ 理解整个代码库
✅ 流畅的工作流
✅ 兼容 VS Code 扩展
✅ 用于长时间运行任务的云端智能体
✅ 本地 + 云端模型
✅ 出色的用户体验

**缺点：**
❌ 无限 AI 需要付费
❌ 专有软件
❌ 资源占用高
❌ 功能有学习曲线

**定价：**
- Hobby：免费（AI 有限）
- Pro：约 20 美元/月
- 更高档位：重度智能体使用最高约 200 美元/月
- Business：约 40 美元/用户/月

*注：Cursor 收购了 Continue.dev，将这个流行的开源扩展并入其平台。*

**配置指南：**
```bash
# Download from https://cursor.com
# Install like any application

# Configure AI:
Settings → AI → Choose model (Claude, GPT-6, or local)
Settings → AI → Enable index for codebase search

# Keyboard shortcuts:
Cmd+K: Inline edit
Cmd+L: Chat sidebar
Cmd+Shift+A: Agent mode
Tab: Accept autocomplete
```

**工作流示例：**
```markdown
1. Open project folder
2. Cmd+L: "Explain the authentication flow in this app"
3. Cursor analyzes codebase → Provides explanation
4. Cmd+K on function: "Add error handling and logging"
5. Review diff → Accept changes
6. Cmd+Shift+A: "Create a new API endpoint for user profiles"
7. Agent creates multiple files → Review → Commit
```

**专业提示：**
- 为代码库建立索引以获得更好的上下文
- 在聊天中使用 @file 引用
- 将智能体模式与人工审查结合使用
- 在设置中配置自定义指令
- 对隐私敏感的工作使用本地模型

---

### 2. Devin Desktop（前身为 Windsurf）

**网站：** https://devin.ai

**是什么：**
AI 原生 IDE（前身为 Windsurf，2026 年 6 月 2 日更名为 Devin Desktop），由 Cognition 的 Devin 智能体驱动。

**功能：**
- Devin Local 智能体（在你的机器上运行）
- Devin Cloud 智能体（在云端运行，你离开时也能工作）
- 深入的代码库理解
- 多文件编辑
- 终端集成
- Git 工作流
- 自动补全与行内编辑

**优点：**
✅ 强大的智能体能力
✅ 快速的自动补全
✅ 良好的代码库感知
✅ 提供免费版
✅ 现代界面
✅ 高效的工作流

**缺点：**
❌ 近期更名/遗留品牌令人困惑
❌ 社区比 Cursor 小
❌ 扩展有限
❌ 偶有 bug

**定价：**
- 免费：基础功能
- Pro：约 15-20 美元/月
- Teams：定制

**最佳用例：**
- 快速原型
- 重构项目
- 学习代码库
- 自动化测试

---

### 3. Kiro

**网站：** https://kiro.dev

**是什么：**
AWS 的 AI 驱动 IDE，规格驱动开发的一流支持。

**功能：**
- 规格驱动开发（规格 → 实现）
- 用于项目级上下文与规则的 Steering 文件
- 在文件事件上运行的 Hooks
- AWS 服务集成
- CloudFormation/Terraform 生成
- 支持 MCP 的智能体模式

**优点：**
✅ 非常适合 AWS 开发
✅ 规格让智能体与意图保持一致
✅ 生成的代码遵循最佳实践
✅ 深厚的 AWS 知识
✅ 适合基础设施即代码

**缺点：**
❌ 以 AWS 为中心（通用性较弱）
❌ 较新的工具
❌ 非 AWS 功能有限
❌ 学习曲线较陡

**定价：**
- 约 20-40 美元/月（提供免费版）

**最佳用例：**
- AWS 应用开发
- 基础设施即代码
- Serverless 架构
- 云迁移项目

---

### 4. Dyad

**网站：** https://dyad.sh

**是什么：**
用于快速全栈开发的 AI 优先 IDE。

**功能：**
- 一键部署
- 全栈脚手架
- 数据库集成
- 身份验证模板
- 实时预览
- 组件库

**优点：**
✅ 原型速度极快
✅ 内置部署
✅ 模板良好
✅ 可视化预览
✅ 对初学者友好

**缺点：**
❌ 定制需求灵活性较弱
❌ 厂商锁定顾虑
❌ 高级功能有限
❌ 定价不明确

**最佳用例：**
- MVP 开发
- 创业原型
- 黑客松项目
- 学习全栈开发

---

## 编码智能体

以终端为先的云端智能体，可跨整个仓库规划、编辑和运行代码。2026 年的胜出模式是将其中一个与 IDE 助手（Cursor 或 Copilot）搭配使用。

### 1. Claude Code（Anthropic）

**网站：** https://claude.com/claude-code

**是什么：**
Anthropic 的官方智能体编程工具——在终端、VS Code、JetBrains、Web 和移动端运行。

**功能：**
- CLAUDE.md 项目记忆文件
- Skills、hooks 与 subagents
- MCP（Model Context Protocol）支持
- 多文件编辑、测试运行、git 操作
- 可在终端、VS Code、JetBrains、Web 和移动端使用

**优点：**
✅ 最佳智能体编程性能（Claude Opus 5.5 居 BenchLeader 榜首）
✅ 善于长时间运行的多文件任务
✅ 深厚的代码库感知
✅ 由 skills 和 hooks 组成的庞大社区生态

**缺点：**
❌ 真正使用需要付费订阅
❌ 仅支持 Anthropic 模型
❌ 大任务的 token 用量增长很快

**定价：**
- 包含在 Claude Pro/Max 中：约 20-200 美元/月

**适用场景：**
- 复杂多文件功能
- 长时间运行的重构
- 测试驱动的迭代

---

### 2. OpenAI Codex

**网站：** https://openai.com/codex

**是什么：**
OpenAI 的编码智能体，提供 CLI、桌面命令中心和云端智能体。

**功能：**
- 用于终端工作流的 CLI
- 用于管理任务的桌面命令中心
- 云端智能体并行运行任务
- AGENTS.md 项目指令
- 带可审查 diff 的沙箱执行

**优点：**
✅ 包含在 ChatGPT 套餐中
✅ 云端智能体在你离开时也能工作
✅ 与 GPT-6 模型紧密集成

**缺点：**
❌ 仅当你已为 ChatGPT 付费时性价比最佳
❌ 仅支持 OpenAI 模型

**定价：**
- 包含在 ChatGPT Plus/Pro/Go 套餐中

**适用场景：**
- 并行云端任务
- 以 OpenAI 为中心的工作流
- 可审查的沙箱变更

---

### 3. Antigravity 2.0（Google）

**网站：** https://antigravity.google

**是什么：**
Google 的智能体优先开发平台，于 2026 年 5 月 Google I/O 上发布。它取代了 Gemini CLI。

**功能：**
- 多智能体编排
- 用于验证 UI 变更的内置浏览器
- CLI 与 SDK
- Gemini 4 Argon/Carbon 模型
- 与编辑器无关（可与你的 IDE 并行工作）

**优点：**
✅ 提供免费版
✅ 用于并行任务的多智能体工作流
✅ 深度的 Gemini 集成

**缺点：**
❌ 较新的平台，生态仍在成熟
❌ 最佳体验以 Google 生态为中心

**定价：**
- 免费版 / Google AI Pro 约 20 美元/月 / Google AI Ultra 100 美元/月

**适用场景：**
- 智能体优先工作流
- 在真实浏览器中验证变更
- Google 生态团队

---

### 4. OpenCode

**网站：** https://opencode.ai

**是什么：**
开源的、基于终端的 AI 编程智能体，注重透明度。

**功能：**
- 开源核心
- 支持 75+ 提供商/模型
- 自带密钥（对隐私友好）
- 社区驱动
- 可扩展架构

**优点：**
✅ 开源透明
✅ 可自托管
✅ 提供商自由（无锁定）
✅ 社区贡献
✅ 免费

**缺点：**
❌ 需要配置
❌ 不如商业智能体精致
❌ 功能较少
❌ 仅社区支持

**定价：**
- 免费（开源）

**最佳用例：**
- 隐私敏感项目
- 自定义工作流
- 为开源作贡献
- 自托管环境

---

### 5. OpenHands（All Hands AI）

**网站：** https://github.com/all-hands-ai/OpenHands

**是什么：**
MIT 许可的自主软件开发智能体。

**功能：**
- 自主任务执行
- 浏览器、终端与编辑器访问
- 可自托管
- 自带模型

**优点：**
✅ MIT 许可（完全开源）
✅ 端到端的自主工作
✅ 本地运行或在自己的云上运行

**缺点：**
❌ 自主性需要仔细审查
❌ 自托管需要配置

**适用场景：**
- 自主修复 issue
- 开源贡献
- 自托管智能体工作流

---

## IDE 扩展与插件

为现有编辑器添加 AI 能力。

### 1. Continue

**网站：** https://continue.dev

**是什么：**
面向 VS Code 和 JetBrains IDE 的开源 AI 自动驾驶助手。

**功能：**
- 支持任意模型（Ollama、OpenAI、Anthropic 等）
- 聊天侧栏
- 行内编辑
- Tab 自动补全
- 本地模型支持
- 可定制的提示词
- 开源

**优点：**
✅ 完全免费且开源
✅ 支持任意模型提供商
✅ 出色的本地模型支持
✅ 高度可定制
✅ 积极开发中
✅ 注重隐私

**缺点：**
❌ 需要配置
❌ 无内置模型
❌ 配置复杂
❌ 用户体验因模型而异

**配置指南：**
```bash
# In VS Code:
1. Extensions → Search "Continue" → Install
2. Click Continue icon in sidebar
3. Edit config.ts or config.json

# Example config for multiple models:
{
  "models": [
    {
      "title": "Claude Sonnet 5.5",
      "provider": "anthropic",
      "model": "claude-sonnet-5-5",
      "apiKey": "YOUR_KEY"
    },
    {
      "title": "GLM-5.3 (local)",
      "provider": "ollama",
      "model": "glm-5.3",
      "apiBase": "http://localhost:11434"
    },
    {
      "title": "GPT-6.1 Terra",
      "provider": "openai",
      "model": "gpt-6.1-terra"
    }
  ],
  "tabAutocompleteModel": {
    "provider": "ollama",
    "model": "deepseek-v4.1-flash"
  }
}
```

**用法：**
- `Cmd/Ctrl + L`：打开聊天
- `Cmd/Ctrl + I`：行内编辑
- `Tab`：接受自动补全
- `@file`：引用特定文件

**适用场景：**
- 想要灵活性的开发者
- 本地 AI 爱好者
- 注重隐私的团队
- 多模型工作流

---

### 2. Cline

**网站：** https://cline.bot

**是什么：**
开源的、自主的 VS Code AI 编程智能体，支持自带密钥。

**功能：**
- 自主完成任务
- 多文件编辑
- 终端命令
- 浏览器自动化
- 文件创建/修改
- Git 操作
- MCP（Model Context Protocol）支持
- 自带 API 密钥（Anthropic、OpenAI、Google、本地）

**优点：**
✅ 真正的自主智能体
✅ 可执行命令
✅ 浏览器交互
✅ 复杂任务处理
✅ 免费且开源
✅ 积极开发中

**缺点：**
❌ 可能自主犯错
❌ 需要仔细审查
❌ 安全考量
❌ 学习曲线

**配置指南：**
```bash
# VS Code Extensions → Search "Cline" → Install

# Configure:
1. Add API keys (Anthropic, OpenAI, etc.)
2. Set permissions for file/terminal access
3. Configure MCP servers if needed
```

**示例工作流：**
```markdown
User: "Create a login page with form validation, 
       connect it to our auth API, and add tests"

Cline:
1. Creates login.jsx with form
2. Adds validation logic
3. Creates API integration
4. Writes Jest tests
5. Runs tests in terminal
6. Reports results
```

**适用场景：**
- 自动化重复任务
- 多步骤实现
- 测试生成
- 脚手架创建

---

### 3. GitHub Copilot

**网站：** https://github.com/features/copilot

**是什么：**
来自 GitHub/Microsoft 的 AI 结对编程助手——如今约有 1500 万开发者使用。

**功能：**
- 代码补全
- 聊天界面
- 智能体模式与 CLI 集成
- IDE 插件（VS Code、JetBrains、Vim 等）
- 拉取请求摘要
- 代码解释

**优点：**
✅ 行业标准
✅ 出色的自动补全
✅ 广泛的 IDE 支持
✅ GitHub 原生（PR、issue、Actions）
✅ 可靠
✅ 企业功能

**缺点：**
❌ 付费订阅
❌ 聊天能力不如竞争对手
❌ 闭源
❌ 训练数据顾虑

**定价：**
- 个人：10 美元/月
- Business：19 美元/用户/月
- Enterprise：39 美元/用户/月
- 学生：免费

**适用场景：**
- 日常编程辅助
- 企业采用
- GitHub 重度工作流
- 标准自动补全需求

---

### 4. Supermaven

**网站：** https://supermaven.com

**是什么：**
拥有 100 万 token 上下文的超快 AI 自动补全。

**功能：**
- 100 万 token 上下文窗口
- 极快（<10ms 延迟）
- 全代码库感知
- 配置简单
- 支持 VS Code 和 JetBrains

**优点：**
✅ 极快
✅ 超大上下文
✅ 使用简单
✅ 免费版良好
✅ 资源占用低

**缺点：**
❌ 聊天不如人意
❌ 较新的公司
❌ 自动补全之外的功能有限
❌ 知名度较低

**定价：**
- 免费：基础自动补全
- Pro：10 美元/月（完整功能）

**适用场景：**
- 注重速度的开发者
- 大型代码库
- 偏好最少配置

---

### 5. Tabnine

**网站：** https://tabnine.com

**是什么：**
注重隐私的 AI 自动补全工具。

**功能：**
- 本地模型选项
- 云端模型
- 整行补全
- IDE 插件
- 团队功能
- 本地部署

**优点：**
✅ 注重隐私
✅ 本地推理选项
✅ 企业级就绪
✅ 成熟产品
✅ 合规性好

**缺点：**
❌ 不如新工具先进
❌ 团队版昂贵
❌ 创新较慢
❌ 聊天功能有限

**定价：**
- Basic：免费（有限）
- Pro：12 美元/月
- Enterprise：定制

**适用场景：**
- 注重隐私的组织
- 合规要求
- 本地部署需求

---

### 6. Sourcegraph Cody

**网站：** https://sourcegraph.com/cody

**是什么：**
具备深度代码库搜索能力的 AI 助手。

**功能：**
- 全代码库搜索
- 上下文感知回答
- 多模型支持
- 聊天与自动补全
- 开源组件
- 企业功能

**优点：**
✅ 出色的代码库搜索
✅ 来自整个仓库的上下文
✅ 多模型
✅ 适合大型代码库
✅ 企业支持

**缺点：**
❌ 自托管配置复杂
❌ 资源密集
❌ 学习曲线
❌ 团队定价

**定价：**
- 免费：有限
- Pro：9 美元/月
- Enterprise：定制

**适用场景：**
- 大型现有代码库
- 理解遗留代码
- 企业搜索需求

---

## 代码生成平台

全栈 AI 应用构建器。

### 1. Bolt（bolt.new）

**网站：** https://bolt.new

**是什么：**
由 StackBlitz 推出的浏览器端 AI 全栈开发者。

**功能：**
- 即时浏览器环境
- 全栈应用生成
- 实时预览
- 一键部署
- NPM 包支持
- 浏览器内文件系统

**优点：**
✅ 零配置
✅ 即时出结果
✅ 全栈能力
✅ 实时预览
✅ 免费起步
✅ 可分享的 URL

**缺点：**
❌ 浏览器限制
❌ 不如本地 IDE 可控
❌ 厂商锁定
❌ 复杂应用可能出问题

**定价：**
- 免费：生成次数有限
- Pro：约 20 美元/月

**最佳用例：**
- 快速原型
- 演示与 mockup
- 学习项目
- 黑客松

**示例：**
```markdown
Prompt: "Build a Pomodoro timer with task management,
         dark mode, and localStorage persistence"

→ Bolt generates complete app in seconds
→ Live preview updates instantly
→ Deploy with one click
→ Share URL with team
```

---

### 2. Lovable

**网站：** https://lovable.dev

**是什么：**
通过描述构建 Web 应用的 AI 平台。

**功能：**
- 自然语言转应用
- React + Tailwind 生成
- Supabase 集成
- 实时编辑
- 包含部署
- 模板库

**优点：**
✅ 易于使用
✅ 精美的 UI
✅ 数据库集成
✅ 快速迭代
✅ 适合非开发者

**缺点：**
❌ 定制有限
❌ 平台依赖
❌ 定价累积
❌ 不适合复杂应用

**定价：**
- 提供免费版
- 付费套餐约 20 美元/月起

**适用场景：**
- MVP
- 内部工具
- 非技术创始人
- 快速落地页

---

### 3. v0（由 Vercel 推出）

**网站：** https://v0.dev

**是什么：**
来自 Vercel 的生成式 UI 平台。

**功能：**
- 文本转 React 组件
- Tailwind CSS 生成
- Shadcn UI 集成
- 复制粘贴即用的代码
- 迭代优化
- Vercel 部署

**优点：**
✅ 生产质量代码
✅ Shadcn UI 专长
✅ Vercel 集成
✅ 免费使用
✅ 适合 UI 组件
✅ 代码结构良好

**缺点：**
❌ 仅专注 UI
❌ 非全栈
❌ 需要手动集成
❌ 后端逻辑有限

**定价：**
- 免费（限额慷慨）
- Pro：即将推出

**适用场景：**
- UI 组件生成
- 仪表盘布局
- 落地页
- 设计系统

**示例：**
```markdown
Prompt: "Create a pricing page with three tiers,
         feature comparison table, and FAQ section.
         Use Shadcn UI components with Tailwind."

→ v0 generates complete React component
→ Iterate: "Make the middle tier highlighted"
→ Copy code → Paste into your project
```

---

### 4. Replit AI

**网站：** https://replit.com

**是什么：**
集成 AI 能力的云端 IDE。

**功能：**
- 浏览器端 IDE
- Replit Agent（根据提示词构建并部署应用）
- 自动补全与聊天
- 多语言支持
- 包含托管
- 协作功能
- 移动应用

**优点：**
✅ 一体化平台
✅ 无需本地配置
✅ 适合学习
✅ 即时部署
✅ 协作编程
✅ 50+ 种语言

**缺点：**
❌ 性能限制
❌ 厂商锁定
❌ 认真使用时定价较高
❌ 需要联网

**定价：**
- 免费：基础版
- Core：20 美元/月
- Teams：40 美元/用户/月

**适用场景：**
- 教育
- 快速实验
- 协作项目
- 多语言探索

---

## 本地 AI 工具

在自己的硬件上运行 AI 模型。

### 1. Ollama

**网站：** https://ollama.com

**是什么：**
本地运行大语言模型最简单的方式。

**功能：**
- 一条命令安装模型
- 优化的推理
- REST API
- Modelfile 定制
- GPU 加速
- 广泛的模型选择

**优点：**
✅ 配置极其简单
✅ 性能快
✅ 庞大的模型库
✅ 积极开发中
✅ 文档出色
✅ 免费且开源

**缺点：**
❌ GUI 有限（以 CLI 为主）
❌ 模型管理基础
❌ 高级功能需要配置
❌ 大模型资源占用高

**配置指南：**
```bash
# Install (Mac/Linux)
curl -fsSL https://ollama.com/install.sh | sh

# Install (Windows)
# Download from ollama.com

# Pull models
ollama pull glm-5.3
ollama pull deepseek-v4.1-flash
ollama pull qwen3.8
ollama pull codestral

# Run interactively
ollama run glm-5.3

# Use API
curl http://localhost:11434/api/generate -d '{
  "model": "glm-5.3",
  "prompt": "Write a Python function to sort a list",
  "stream": false
}'

# List models
ollama list

# Remove model
ollama rm glm-5.3
```

**集成：**
- VS Code：Continue 扩展
- JetBrains：Ollama 插件
- Web UI：Open WebUI
- CLI：原生命令

**适用场景：**
- 本地开发
- 隐私敏感工作
- 离线编码
- 降低成本

---

### 2. LM Studio

**网站：** https://lmstudio.ai

**是什么：**
用于本地 AI 模型的用户友好桌面应用。

**功能：**
- 精美的 GUI
- 模型浏览器与下载器
- 聊天界面
- 本地 API 服务器
- 无需编码
- 跨平台

**优点：**
✅ 极其用户友好
✅ 内置模型搜索
✅ 无需命令行
✅ 性能良好
✅ 可视化界面
✅ 包含 API 服务器

**缺点：**
❌ 闭源
❌ 高级功能较少
❌ 下载较大
❌ 定制性较弱

**配置指南：**
```bash
# Download from lmstudio.ai
# Install application
# Open LM Studio

# Steps:
1. Click "Search" tab
2. Find model (e.g., "GLM-5.3")
3. Click Download
4. Go to "Chat" tab
5. Select downloaded model
6. Start chatting!

# Enable local server:
1. Click "<->" icon (Developer)
2. Start Server
3. Use OpenAI-compatible API
```

**适用场景：**
- 非技术用户
- 快速本地 AI 配置
- 视觉学习者
- 测试不同模型

---

### 3. Jan

**网站：** https://jan.ai

**是什么：**
LM Studio 的开源替代品。

**功能：**
- 开源
- 桌面应用
- 模型管理
- 聊天界面
- API 服务器
- 扩展

**优点：**
✅ 开源
✅ 界面简洁
✅ 积极开发中
✅ 社区驱动
✅ 免费

**缺点：**
❌ 较新的项目
❌ 模型选择较少
❌ 不够精致
❌ 偶有 bug

**适用场景：**
- 开源倡导者
- 定制需求
- 社区参与

---

### 4. Open WebUI

**网站：** https://openwebui.com

**是什么：**
面向 Ollama 及其他后端的自托管 Web 界面。

**功能：**
- 类似 ChatGPT 的界面
- Ollama 集成
- 多模型支持
- 用户管理
- RAG 能力
- Docker 部署
- 插件系统

**优点：**
✅ 精美的 Web UI
✅ 多用户支持
✅ 内置 RAG
✅ 自托管
✅ 功能丰富
✅ 活跃社区

**缺点：**
❌ 需要 Docker 知识
❌ 比桌面应用配置更多
❌ 资源密集
❌ 需要维护

**配置指南：**
```bash
# Docker installation
docker run -d -p 3000:8080 \
  --add-host=host.docker.internal:host-gateway \
  -v open-webui:/app/backend/data \
  --name open-webui \
  ghcr.io/open-webui/open-webui:main

# Access at http://localhost:3000
# Create admin account
# Connect to Ollama backend
```

**适用场景：**
- 需要共享 AI 的团队
- 自托管部署
- RAG 应用
- 自定义工作流

---

### 5. AnythingLLM

**网站：** https://anythingllm.com

**是什么：**
一体化的 RAG 与本地 AI 平台。

**功能：**
- 文档摄入
- 向量数据库
- 多模型支持
- Web 界面
- API 访问
- 工作区管理

**优点：**
✅ 非常适合 RAG
✅ 文档问答
✅ 多工作区
✅ 配置简单
✅ 适合团队

**缺点：**
❌ 资源占用较重
❌ 简单需求下过于复杂
❌ 学习曲线
❌ 配置时间

**适用场景：**
- 基于文档的工作流
- 知识库
- 团队协作
- 自定义数据集

---

### 6. LocalAI

**网站：** https://localai.io

**是什么：**
开源的、API 兼容的本地模型服务器。

**功能：**
- OpenAI API 兼容
- 多种模型格式
- GPU 加速
- Docker 支持
- 自托管
- 社区模型

**优点：**
✅ OpenAI 的直接替代品
✅ 多种模型格式
✅ 生产就绪
✅ 积极开发中
✅ 文档良好

**缺点：**
❌ 技术配置
❌ 资源密集
❌ 需要排错
❌ 配置复杂

**适用场景：**
- 替换 OpenAI API
- 生产自托管
- 自定义部署
- 企业使用

---

## 专业工具

### 1. Aider

**网站：** https://aider.chat

**是什么：**
基于 CLI 的 AI 结对编程工具。

**功能：**
- 基于终端
- Git 集成
- 多文件编辑
- 支持任意 LLM
- 自动提交
- 运行测试

**优点：**
✅ 轻量快速
✅ 感知 Git
✅ 可在任意编辑器中使用
✅ 可编写脚本
✅ 免费且开源

**缺点：**
❌ 仅 CLI（无 GUI）
❌ 需要熟悉终端
❌ 视觉反馈较少
❌ 手动配置

**配置指南：**
```bash
# Install
pip install aider-chat

# Usage
cd my-project
aider --model claude-sonnet-5-5

# Commands in aider:
/add file.py          # Add file to context
/git diff             # Show changes
/commit               # Auto-commit
/run pytest           # Run tests
```

**适用场景：**
- 终端爱好者
- Git 重度工作流
- 自动化脚本
- 极简配置

---

### 2. Augment

**网站：** https://augment.com

**是什么：**
企业级 AI 编程平台，深度理解代码库。

**功能：**
- 全代码库上下文
- 企业安全
- 自定义模型训练
- 合规功能
- 团队协作
- 分析

**优点：**
✅ 企业级
✅ 注重安全
✅ 深度集成
✅ 合规就绪
✅ 分析仪表盘

**缺点：**
❌ 企业定价
❌ 配置复杂
❌ 不适合个人
❌ 需要走销售流程

**适用场景：**
- 大型企业
- 受监管行业
- 安全敏感组织
- 团队部署

---

### 3. Cogram

**网站：** https://cogram.com

**是什么：**
面向 SQL 与数据工程的 AI。

**功能：**
- 自然语言转 SQL
- 查询优化
- 模式理解
- 数据库集成
- Jupyter 支持

**优点：**
✅ SQL 专业化
✅ 查询优化
✅ 感知数据库
✅ 适合分析师

**缺点：**
❌ 关注面窄
❌ SQL 之外能力有限
❌ 定价

**适用场景：**
- 数据工程师
- SQL 重度工作
- 分析团队

---

### 4. Mintlify

**网站：** https://mintlify.com

**是什么：**
AI 驱动的文档生成器。

**功能：**
- 从代码自动生成文档
- API 文档
- Markdown 支持
- 包含托管
- 搜索功能

**优点：**
✅ 节省文档时间
✅ 始终保持最新
✅ 外观专业
✅ SEO 良好

**缺点：**
❌ 仅用于文档
❌ 可能需要手动编辑
❌ 团队定价

**适用场景：**
- API 文档
- 项目文档
- 团队知识库

---

## 工具对比矩阵

### 功能对比

| 工具 | 类型 | 价格 | 适用场景 | 本地模型 | 代码库上下文 |
|------|------|-------|----------|--------------|------------------|
| Cursor | IDE | 约 20 美元/月 | 综合最佳 | ✅ | ✅ |
| Claude | 聊天 | 约 20 美元/月 | 代码质量 | ❌ | ⚠️（上传） |
| ChatGPT | 聊天 | 约 20 美元/月 | 多才多艺 | ❌ | ⚠️（上传） |
| Claude Code | 智能体 | 20-200 美元/月 | 智能体编程 | ❌ | ✅ |
| Codex | 智能体 | 包含在 ChatGPT 中 | 云端任务 | ❌ | ✅ |
| Antigravity 2.0 | 智能体 | 免费 / 20-100 美元/月 | 多智能体 | ❌ | ✅ |
| Continue | 扩展 | 免费 | 灵活性 | ✅ | ✅ |
| Cline | 扩展 | 免费（自带密钥） | 自主 | ✅ | ✅ |
| GitHub Copilot | 扩展 | 10 美元/月 | 自动补全 | ❌ | ⚠️ |
| Kiro | IDE | 20-40 美元/月 | 规格驱动 | ⚠️ | ✅ |
| Devin Desktop | IDE | 约 15 美元/月 | 智能体 | ⚠️ | ✅ |
| Bolt | 平台 | 免费增值 | 原型 | ❌ | ❌ |
| v0 | 平台 | 免费 | UI 组件 | ❌ | ❌ |
| Ollama | 本地 | 免费 | 隐私 | ✅ | ❌ |
| LM Studio | 本地 | 免费 | 易用本地 | ✅ | ❌ |
| Replit | 平台 | 20 美元/月 | 学习 | ❌ | ✅ |

---

### 能力矩阵

| 工具 | 聊天 | 自动补全 | 智能体模式 | 文件编辑 | 终端 | Git | 部署 |
|------|------|--------------|------------|-----------|----------|-----|--------|
| Cursor | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ⚠️ |
| Devin Desktop | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ⚠️ |
| Claude Code | ✅ | ❌ | ✅ | ✅ | ✅ | ✅ | ❌ |
| Codex | ✅ | ❌ | ✅ | ✅ | ✅ | ✅ | ⚠️ |
| Continue | ✅ | ✅ | ⚠️ | ✅ | ❌ | ⚠️ | ❌ |
| Cline | ✅ | ❌ | ✅ | ✅ | ✅ | ✅ | ❌ |
| Copilot | ✅ | ✅ | ✅ | ⚠️ | ✅ | ✅ | ❌ |
| Bolt | ✅ | ❌ | ⚠️ | ✅ | ❌ | ❌ | ✅ |
| Replit | ✅ | ✅ | ⚠️ | ✅ | ✅ | ✅ | ✅ |
| v0 | ✅ | ❌ | ❌ | ❌ | ❌ | ❌ | ✅ |
| Ollama | ✅ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ |

图例：✅ 是 | ⚠️ 有限 | ❌ 否

---

### 定价对比

| 类别 | 免费选项 | 最具性价比 | 高级 |
|----------|-------------|------------|---------|
| 聊天 | DeepSeek、Gemini | Claude Pro（约 20 美元） | Google AI Ultra（100 美元） |
| IDE | Cursor（有限） | Cursor Pro（约 20 美元） | Devin Desktop / Kiro |
| 智能体 | OpenCode（免费） | Claude Code（包含在内，20-200 美元） | Codex（包含在 ChatGPT 中） |
| 扩展 | Continue、Cline | Copilot（10 美元） | Augment（企业） |
| 平台 | v0、Bolt（有限） | Bolt Pro（20 美元） | Replit Teams |
| 本地 | Ollama、LM Studio | 不适用（全部免费） | 硬件成本 |

---

## 配置指南

### 完整入门配置

**初学者（每月 20 美元预算）：**
```bash
1. Sign up for Claude Pro or ChatGPT Plus
2. Install VS Code
3. Add Continue or Cline extension (free, bring-your-own-key)
4. Configure your extension with your Claude/OpenAI key
5. Install Ollama for local fallback
6. Pull a small model: ollama pull deepseek-v4.1-flash
7. Start coding!
```

**2026 年的胜出搭配：**
```bash
IDE assistant:  Cursor Pro or GitHub Copilot  (autocomplete + inline edits)
Terminal agent: Claude Code or Codex          (multi-file, long-running tasks)
```

**注重隐私的开发者：**
```bash
1. Install Ollama
2. Pull models:
   - ollama pull glm-5.3 (reasoning)
   - ollama pull deepseek-v4.1-flash (fast completions)
3. Install LM Studio for GUI
4. Install Continue or Cline extension
5. Configure it for Ollama (or use OpenCode with 75+ providers)
6. Optional: Set up Open WebUI for team access
```

**团队：**
```bash
1. Evaluate: Cursor Teams, GitHub Copilot Business, Augment
2. Set up shared model access
3. Configure codebase indexing
4. Establish usage guidelines
5. Train team on best practices
6. Monitor usage and optimize
```

**企业：**
```bash
1. Contact: Augment, Tabnine Enterprise, GitHub Copilot Enterprise
2. Security review
3. Compliance check
4. Pilot program
5. Roll out with training
6. Ongoing monitoring
```

---

## 工作流示例

### 1. 构建新功能

```markdown
Step 1: Planning (Claude Sonnet 5.5 / GPT-6.1 Sol)
"Design a rate-limiting middleware for Express.js with Redis backend.
Consider distributed systems, edge cases, and security."

Step 2: Implementation (Cursor + Claude)
- Open project in Cursor
- Cmd+L: "Show me where to add rate limiting"
- Review suggested locations
- Cmd+K: "Implement Redis-based rate limiter here"
- Review diff, accept changes

Step 3: Testing (Cline)
"@cline Write Jest tests for the rate limiter covering:
- Normal requests
- Rate limit exceeded
- Edge cases
- Concurrent requests"

Step 4: Review (Claude)
Upload test results → "Analyze failures and suggest fixes"

Step 5: Documentation (Mintlify or Claude)
"Generate API documentation for the rate limiter endpoint"
```

---

### 2. 调试会话

```markdown
Step 1: Understand Error (Continue)
Paste error → "Explain this error and common causes"

Step 2: Locate Issue (Cursor)
Cmd+L: "Where could this null pointer come from?"

Step 3: Fix (Cursor inline)
Cmd+K on problematic code → "Fix null handling"

Step 4: Verify (Local model)
Run tests → If fail, ask Ollama for quick iteration

Step 5: Learn (Claude)
"Why did this bug occur? How can I prevent similar issues?"
```

---

### 3. 学习新技术

```markdown
Step 1: Overview (ChatGPT/Claude)
"Explain Kubernetes Pods, Services, and Deployments like I'm 15"

Step 2: Hands-on (Bolt/Replit)
"Create a simple Kubernetes manifest for a Node.js app"

Step 3: Deep Dive (Claude with uploads)
Upload manifests → "Review these for best practices"

Step 4: Practice (Local model)
Use Ollama for unlimited questions without cost concerns

Step 5: Build Project (Cursor)
Apply learning to real project with AI assistance
```

---

### 4. 代码审查流程

```markdown
Step 1: Initial Review (Claude)
Upload PR diff → "Review for bugs, security issues, and style"

Step 2: Security Scan (Claude or specialized tool)
"Check for OWASP vulnerabilities and suggest fixes"

Step 3: Performance (GPT-6 Astra)
"Identify performance bottlenecks and optimization opportunities"

Step 4: Documentation Check (Mintlify or Claude)
"Are all functions documented? Generate missing docs"

Step 5: Final Pass (Human + AI pair)
Review AI feedback → Make decisions → Approve/reject
```

---

## 最佳实践

### 工具选择指南

```
Simple autocomplete → GitHub Copilot or Continue/Cline (free, BYOK)
Serious development → Cursor Pro (~$20) paired with Claude Code or Codex
Budget conscious → Continue + Ollama (free)
Privacy critical → Local models only
Enterprise → Augment or Copilot Enterprise
Learning → Replit or free tiers
Prototyping → Bolt or Lovable
UI work → v0
```

### 成本优化

1. **策略性地使用免费版**
   - DeepSeek 用于批量编程
   - 本地模型用于迭代
   - 把高级 token 留给复杂任务

2. **分层使用工具**
   ```
   Autocomplete: Local (free)
   Chat: Free tier or DeepSeek
   Complex tasks: Claude Pro
   ```

3. **缓存与复用**
   - 保存好的提示词
   - 收藏有用的回答
   - 创建提示词模板

4. **监控用量**
   - 跟踪 API 消耗
   - 设定月度预算
   - 超支时告警
   - Gartner（2026 年 6 月）：按 token 计价的成本难以预测——不受管理的 AI 编程支出到 2028 年可能超过开发者的薪资

### 安全最佳实践

1. **切勿提交 API 密钥**
   - 使用环境变量
   - 定期轮换密钥
   - 每个工具使用单独的密钥

2. **谨慎处理敏感代码**
   - 对专有代码使用本地模型
   - 分享前去除机密信息
   - 审查工具的隐私政策

3. **审查 AI 生成的代码**
   - 未经审查切勿部署
   - 运行安全扫描器
   - 彻底测试
   - Sonar 2026 年调查：96% 的专业人士并不完全信任 AI 代码，但只有 48% 的人总是在提交前检查——要成为另外那 48%

4. **企业考量**
   - 数据驻留要求
   - 合规（SOC2、HIPAA、GDPR）
   - 审计日志
   - 访问控制

### 效率提示

1. **学习键盘快捷键**
   - Cursor：Cmd+K、Cmd+L、Cmd+Shift+A
   - Continue：Cmd+L、Cmd+I
   - 掌握这些，进入心流状态

2. **创建提示词模板**
   ```markdown
   /review: "Review this code for [criteria]"
   /test: "Write tests for [functionality]"
   /docs: "Generate documentation for [module]"
   /refactor: "Refactor this to improve [aspect]"
   ```

3. **有效使用上下文**
   - 引用特定文件（@filename）
   - 提供相关背景
   - 逐字包含错误信息

4. **快速迭代**
   - 先宽泛，再细化
   - 要求澄清
   - 不要盲目接受第一次输出

5. **组合使用工具**
   - Claude 用于规划
   - Cursor 用于实现
   - 本地模型用于测试
   - 每个工具都有其优势

### 应避免的常见陷阱

❌ **盲目信任 AI**
   → 始终审查与测试

❌ **过度依赖自动补全**
   → 理解你接受的内容

❌ **忽视安全**
   → 扫描 AI 生成的代码

❌ **不学习基础知识**
   → AI 是辅助，而非知识的替代品

❌ **用错工具**
   → 按任务匹配工具

❌ **分享敏感数据**
   → 清楚自己发送了什么

❌ **没有版本控制**
   → 频繁提交、审查 diff

---

## 速查

### 安装命令

```bash
# Ollama
curl -fsSL https://ollama.com/install.sh | sh

# Continue (VS Code)
# Extensions → Search "Continue" → Install

# Cursor
# Download from cursor.com

# LM Studio
# Download from lmstudio.ai

# Aider
pip install aider-chat

# Open WebUI (Docker)
docker run -d -p 3000:8080 ghcr.io/open-webui/open-webui:main
```

### 键盘快捷键

| 操作 | Cursor | Continue | VS Code + Copilot |
|--------|--------|----------|-------------------|
| 聊天 | Cmd+L | Cmd+L | Cmd+I |
| 行内编辑 | Cmd+K | Cmd+I | Cmd+I |
| 智能体模式 | Cmd+Shift+A | - | - |
| 接受补全 | Tab | Tab | Tab/Cmd+→ |
| 拒绝补全 | Esc | Esc | Esc |

### API 端点

```bash
# Ollama
POST http://localhost:11434/api/generate

# LM Studio Server
POST http://localhost:1234/v1/chat/completions

# OpenAI
POST https://api.openai.com/v1/chat/completions

# Anthropic
POST https://api.anthropic.com/v1/messages

# DeepSeek
POST https://api.deepseek.com/chat/completions
```

---

## 更多资源

- [Awesome AI Coding Tools](https://github.com/topics/ai-coding)
- [r/LocalLLaMA](https://reddit.com/r/LocalLLaMA)
- [Cursor Documentation](https://docs.cursor.com)
- [Claude Code Documentation](https://docs.claude.com/en/docs/claude-code)
- [Continue Documentation](https://docs.continue.dev)
- [Ollama Documentation](https://ollama.com/help)
- [AI Engineer Discord](https://discord.gg/ai-engineering)

---

## 结论

最佳 AI 工具配置取决于你的需求：

- **个人开发者**：Cursor Pro 搭配 Claude Code（或 Codex），外加 Ollama 作为本地后备
- **团队**：Cursor Teams 或 GitHub Copilot Business，外加共享智能体
- **注重隐私**：Ollama + LM Studio + Continue/Cline（或 OpenCode）
- **企业**：Augment 或定制方案
- **学习者**：Replit + 免费版
- **预算有限**：Ollama + Continue + DeepSeek 的全免费组合

记住：工具放大你的技能，但不能替代基础。用 AI 加速学习和生产力，而不是逃避理解自己的代码。

---

*最后更新：2026 年 11 月 | 由 Vibe Coding 社区贡献*
