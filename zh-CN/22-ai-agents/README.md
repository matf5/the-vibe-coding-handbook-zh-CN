# 用 AI 辅助构建 AI 智能体

*最后更新：2026 年 11 月*

AI 智能体代表了 AI 协助的下一个演进——能够以最少的人工干预规划、执行任务并做出决策的自主系统。

## 目录

- [什么是 AI 智能体？](#what-are-ai-agents)
- [智能体架构](#agent-architectures)
- [构建模块](#building-blocks)
- [热门框架](#popular-frameworks)
- [2026 年的编程智能体](#coding-agents-in-2026)
- [智能体标准与协议](#agent-standards--protocols)
- [使用场景](#use-cases)
- [记忆系统](#memory-systems)
- [工具集成](#tool-integration)
- [多智能体系统](#multi-agent-systems)
- [长期运行智能体的安全](#long-running-agent-safety)
- [评估与测试](#evaluation--testing)
- [自主运行的失败模式](#failure-modes-of-autonomous-runs)
- [伦理与安全](#ethics--safety)
- [智能体开发提示词](#prompts-for-agent-development)
- [实践项目](#practice-projects)

## 什么是 AI 智能体？

AI 智能体是这样的系统：
- 通过输入**感知**环境
- 围绕目标与约束进行**推理**
- 通过执行任务与工具采取**行动**
- 从反馈与结果中**学习**

### 智能体类型

| 类型 | 能力 | 复杂度 |
|------|-----------|------------|
| 简单反射型 | 对当前状态做出反应 | 低 |
| 基于模型型 | 维护内部状态 | 中 |
| 基于目标型 | 规划以实现目标 | 高 |
| 基于效用型 | 优化结果 | 很高 |
| 学习型 | 随时间改进 | 最高 |

## 智能体架构

### ReAct（推理 + 行动）

```
Prompt: "Create a ReAct agent that can:
1. Research topics using web search
2. Summarize findings
3. Cite sources
4. Answer follow-up questions

Include thought-action-observation loops."
```

### 规划-执行

```
Prompt: "Design an agent that plans a travel itinerary:
1. Break down into subtasks
2. Execute each step
3. Handle failures gracefully
4. Adjust plan based on results"
```

### 思维树

```
Prompt: "Implement Tree of Thoughts for complex problem solving:
1. Generate multiple solution paths
2. Evaluate each branch
3. Backtrack when needed
4. Converge on best solution"
```

## 构建模块

### 感知模块

```python
# Prompt: Create input processing for agent
- Text parsing and understanding
- Image recognition integration
- Audio transcription
- Structured data extraction
```

### 推理引擎

```python
# Prompt: Design reasoning component
- Chain-of-thought prompting
- Logical inference
- Constraint satisfaction
- Decision trees
```

### 行动执行器

```python
# Prompt: Build action execution system
- API calls
- File operations
- Database queries
- External tool integration
```

## 热门框架

### LangChain

```
Prompt: "Build a LangChain agent with:
- Chat model (GPT-4/Claude)
- Memory (conversation buffer)
- Tools (search, calculator, custom)
- Output parser
- Error handling"
```

### AutoGen

```
Prompt: "Create multi-agent conversation in AutoGen:
- User proxy agent
- Assistant agent
- Custom agent for specific task
- Termination conditions
- Human-in-the-loop"
```

### LlamaIndex

```
Prompt: "Set up LlamaIndex for RAG agent:
- Document loading
- Index creation
- Query engine
- Response synthesis
- Source tracking"
```

### 框架在 2026 年的位置

关于格局的一点说明：2026 年，大多数真实的编程智能体工作发生在**智能体运行框架（agent harnesses）**中——Claude Code、Codex、Antigravity、Cursor、Cline、OpenCode——而不是原始的编排框架中。运行框架开箱即用，提供了编程智能体所需的智能体循环、工具使用、权限与文件编辑功能。上述框架仍然适用于构建需要自有编排、检索与工具图的**定制领域智能体**（客服、研究、数据流水线）。

## 2026 年的编程智能体

从自动补全到智能体的转变，是自聊天界面本身以来 AI 辅助开发最大的变化：

- **自动补全**建议下一行代码。
- **智能体**检查仓库、修改多个文件、运行命令、运行测试，并为审查准备改动。

这不是预测——它现在已是默认工作流。GitHub 报告称，在 2025 年 5 月至 9 月期间合并了 **100 万以上由编程智能体提交的 Pull Request**。

### 一次智能体运行的构成

1. **检查**——阅读仓库、定位相关文件、建立对代码库的心智模型
2. **规划**——将任务拆解为步骤，通常写入规划或规范文件
3. **编辑**——一次性修改多个文件
4. **验证**——运行构建、代码检查与测试；失败时修正输出
5. **呈现**——整理出 diff 或 Pull Request，供人工审查

### 主流工具

| 工具 | 2026 年的形态 |
|------|---------------|
| **Claude Code** | 终端、IDE、Web 与移动端；CLAUDE.md、skills、hooks、subagents、MCP |
| **OpenAI Codex** | CLI + 桌面指挥中心 + 云端任务 |
| **Google Antigravity 2.0** | 多智能体编排、内置浏览器、定时后台任务、CLI、SDK——于 2026 年 5 月 I/O 大会上发布 |
| **Cursor** | Composer 2.5、并行云端智能体 |
| **GitHub Copilot** | 智能体模式 + 后台智能体 |
| **Kiro** | 规格驱动开发 |
| **Devin Desktop** | 本地工作与云端委派 |

值得了解的开源替代品：**Cline**、**OpenHands**、**aider** 与 **OpenCode**——它们都运行着相同的检查 → 编辑 → 测试 → 审查循环，只是模型由你选择。

### 是什么带来了不同

- **仓库级上下文**——智能体读取整个代码库，而不仅仅是打开的文件
- **真正的工具使用**——Shell、测试、代码检查与 git 都是一等公民的操作
- **持久性**——运行可以在本地或云端持续数分钟或数小时
- **以审查为先的输出**——交付物是待批准的 diff，而不是静默合并的代码

## 智能体标准与协议

随着编程智能体的增多，出现了一小套标准，让指令与工具可以在它们之间流通。

### MCP（Model Context Protocol，模型上下文协议）

MCP 是为智能体提供**工具与上下文**的标准方式。MCP 服务器以单一格式暴露资源与操作（数据库、Issue 跟踪器、浏览器、内部 API），任何支持 MCP 的智能体都可以使用——集成只需构建一次，就可以在 Claude Code、Cursor、Codex 等工具中复用，而不必为每个工具定制连接器。

### AGENTS.md

**AGENTS.md** 是项目指令的跨工具标准：位于仓库根目录的一个文件，告诉任何智能体项目如何构建、测试与修改。它被 **Cursor、Codex、Copilot、OpenCode、Cline、Antigravity 与 Devin Desktop** 读取，是最接近通用的“先读这个”文件。

### CLAUDE.md

**CLAUDE.md** 是 Claude Code 的项目记忆——在每次会话开始时加载的命令、约定与警告。团队通常将 AGENTS.md 作为共享的事实来源，并让 CLAUDE.md 引用或扩展它。

### Skills、Hooks 与 Subagents

| 机制 | 是什么 | 何时使用 |
|-----------|-----------|----------------|
| **Skills** | 可复用的能力包——按需加载的指令与资源文件夹 | 可重复的工作流：“我们如何发布”、“我们如何编写迁移脚本” |
| **Hooks** | 确定性的生命周期自动化——在固定事件（会话开始、工具使用、停止）上运行的脚本 | 不可协商的检查：格式化、密钥扫描、拦截危险命令 |
| **Subagents** | 拥有自己上下文窗口的专注智能体，用于并行处理独立工作 | 广泛的研究、大规模搜索、仓库中独立的区域 |

要记住的模式：**AGENTS.md 说明你是谁，MCP 说明你能触及什么，skills 说明如何完成重复性工作，hooks 强制执行规则，subagents 成倍提高吞吐量。**

## 使用场景

### 客服智能体

```
Capabilities:
- Understand customer queries
- Access knowledge base
- Process refunds
- Escalate complex issues
- Learn from interactions
```

### 研究助手

```
Capabilities:
- Literature search
- Paper summarization
- Citation management
- Hypothesis generation
- Experiment planning
```

### 代码开发智能体

```
Capabilities:
- Understand requirements
- Write code
- Run tests
- Debug issues
- Refactor improvements
```

## 记忆系统

### 短期记忆

```
Prompt: "Implement conversation memory:
- Store last N messages
- Context window management
- Important information extraction
- Summarization for long conversations"
```

### 长期记忆

```
Prompt: "Design vector database memory:
- Embedding generation
- Similarity search
- Memory consolidation
- Forgetting mechanism"
```

### 情景记忆

```
Prompt: "Create experience storage:
- Task outcomes
- Success/failure patterns
- Lesson learning
- Transfer to new situations"
```

## 工具集成

### API 工具

```
Prompt: "Create tool definitions for:
- Weather API
- Stock prices
- News search
- Email sending
- Calendar management

Include error handling and rate limiting."
```

### 自定义工具

```
Prompt: "Build custom tools for e-commerce:
- Product search
- Inventory check
- Order placement
- Tracking updates
- Return processing"
```

## 多智能体系统

### 协作智能体

```
Prompt: "Design team of agents for software development:
- Product Manager agent
- Developer agent
- Tester agent
- DevOps agent

Define communication protocols and handoffs."
```

### 竞争智能体

```
Prompt: "Create debate system with:
- Proponent agent
- Opponent agent
- Judge agent
- Evidence gathering
- Argument evaluation"
```

### 实践中的多智能体编排

2026 年多智能体开发的现实，看起来不像辩论俱乐部，而更像一支运转良好的团队：

- **并行子智能体与工作树**——每个子智能体拥有自己的上下文（通常还有自己的 git 工作树），可以在仓库的不同区域编辑而不会互相覆盖
- **编排器-工作者**——一个智能体拆解任务、分派专注的子智能体，并合并它们的结果
- **审查者-实现者**——一个智能体编写改动，另一个在改动到达人类之前对照规范审查它
- **指挥中心模式**——Google Antigravity 2.0 将多智能体运行呈现为指挥中心（任务看板、内置浏览器、定时后台任务），OpenAI Codex 则提供了一个多智能体桌面应用，本地与云端智能体并排运行

**何时不使用多个智能体：**注意共享上下文丢失（每个子智能体只看到自己的部分，因此跨领域的决策会漂移）与冲突编辑（两个智能体修改相同文件会产生合并冲突与重复工作）。对于小而紧密耦合的任务，一个带良好规划的智能体胜过一群智能体。

## 长期运行智能体的安全

智能体已经可以跨仓库工作、运行测试并修正自己的输出。更长的运行可以完成更大的任务——但也让错误有更多时间扩散。一次两小时任务开始五分钟时的错误假设，会在有人注意到之前浪费 token 并触及许多文件。

### 必备控制措施

| 控制措施 | 作用 |
|---------|--------------|
| **检查点** | 定期审查点，在工作进一步推进之前揭示其是否走在正轨上 |
| **支出上限** | 对 token 与工具用量的硬性上限，阻止失控的会话 |
| **隔离环境** | 沙箱容器与预览环境，保护生产环境 |
| **可逆改动** | Git 分支与快照，让糟糕的输出可以回滚而不是被辩护 |
| **人工批准** | 在敏感操作之前明确确认：部署、迁移、购买、删除数据 |

### 成本角度

按 token 计价让失控的智能体会话变得昂贵：一个在失败测试上循环的智能体，比人类注意到问题更快地烧掉预算。Gartner 警告称，**到 2028 年，AI 编码成本可能超过开发者的平均薪资**。把支出上限与检查点视为一等公民的安全功能，而非可选的锦上添花——这就是团队在长期运行中既保持可负担又保持安全的方式。

## 评估与测试

### 性能指标

```
Prompt: "Define KPIs for agent evaluation:
- Task completion rate
- Time to completion
- Resource usage
- User satisfaction
- Error recovery rate"
```

### 测试策略

```
Prompt: "Create test suite for agent:
- Unit tests for components
- Integration tests for workflows
- Edge case handling
- Adversarial testing
- A/B testing framework"
```

### 评估智能体输出

智能体生成的代码常常**看起来**正确，却隐藏着真正的问题：

- **Sonar（2026）：**61% 的受访者表示 AI 经常生成看起来正确但不可靠的代码，96% 的人不完全信任 AI 代码。
- **CodeRabbit（470 个开源 PR）：**与 AI 相关的 PR 携带的问题数量约为纯人工 PR 的 **1.7 倍**。

在实践中站得住脚的验证策略：

1. **Diff 审查**——人工阅读实际改动了什么，而不仅仅是智能体的总结
2. **对照规范测试**——验证所陈述的需求，而不仅仅是测试套件变绿
3. **合并前人工批准**——任何智能体都不能直接推送到 main 分支
4. **每个 PR 都进行自动扫描**——无论代码由谁编写，都运行代码检查、类型检查、SAST 与密钥扫描

## 自主运行的失败模式

长期自主运行会以特有的方式失败。了解这些模式可以让它们被更便宜地发现：

| 失败模式 | 症状 | 缓解措施 |
|--------------|---------|------------|
| **上下文漂移** | 随着上下文窗口被填满，智能体忘记早期的约束 | 在检查点重申目标；压缩或总结较旧的上下文；保持任务简报简短 |
| **目标漂移** | 优化代理指标而非实际目标 | 事先写明明确的成功标准；对照规范测试，而不是智能体的总结 |
| **静默范围蔓延** | 智能体在解决问题时“改进”了无关文件 | 限制文件列表；在 diff 审查中标记无关改动 |
| **凭证泄露** | 密钥被粘贴到代码、日志或提交中 | 沙箱环境、限定范围且短期有效的凭证、hooks 中的密钥扫描 |
| **子智能体之间的重复工作** | 并行智能体解决相同问题或编辑相同文件 | 明确的所有权边界、每个智能体一个工作树、编排器分配区域 |

大多数这类问题在检查点发现成本最低——这就是为什么[长期运行智能体的安全](#long-running-agent-safety)中的控制措施与[评估与测试](#evaluation--testing)中的检查属于同一个工作流，与运行本身密不可分。

## 伦理与安全

### 防护措施

```
Prompt: "Implement safety measures:
- Input validation
- Output filtering
- Harmful content detection
- Privacy protection
- Rate limiting"
```

### 透明度

```
Prompt: "Add explainability features:
- Decision logging
- Confidence scores
- Uncertainty communication
- Audit trails"
```

## 智能体开发提示词

### 智能体创建

```
Prompt: "Create an agent specification:
- Role and persona
- Capabilities and limitations
- Available tools
- Memory requirements
- Success criteria
- Failure handling"
```

### 调试智能体

```
Prompt: "Debug this agent behavior:
'Agent gets stuck in loop when searching for information'

Provide:
1. Root cause analysis
2. Fix strategies
3. Prevention mechanisms"
```

## 实践项目

### 初级

1. **天气机器人**：获取并报告天气
2. **计算器智能体**：用工具解决数学问题
3. **名言查找器**：搜索并返回励志名言

### 中级

4. **旅行规划器**：完整的行程规划智能体
5. **新闻摘要器**：带来源的每日简报
6. **个人研究员**：学术论文助手

### 高级

7. **全栈开发者智能体**：构建完整应用
8. **业务分析师智能体**：市场研究与报告
9. **健康助手**：带免责声明的症状检查器

---

## 结论

AI 智能体可以自动化复杂的工作流，但需要精心设计才能保证可靠性与安全性。在 2026 年，这意味着把编程智能体视为有防护措施的能干队友：标准的项目指令（AGENTS.md、MCP）、长期运行的检查点与支出上限，以及合并前对每个 diff 的验证。从简单开始、根据反馈迭代，并始终对关键决策保留人工监督。
