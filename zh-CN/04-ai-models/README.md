[English 原文](../../04-ai-models/README.md)

# AI 模型与氛围编程

一份关于软件开发 AI 模型的综合指南，涵盖前沿模型、开源模型、编码专用模型，以及如何为每项任务选择合适的模型。

> **最后更新：2026 年 11 月**——反映当前模型阵容（Claude 5.5/Fable 5.1、GPT-6、Gemini 4、Kimi K3、GLM-5.3、DeepSeek V4）、当前定价与 2026 年 11 月的基准测试结果。

---

## 目录

1. [模型类型](#model-types)
2. [前沿模型](#frontier-models)
3. [开源模型](#open-source-models)
4. [编码专用模型](#coding-specific-models)
5. [关键概念](#key-concepts)
6. [如何选择模型](#how-to-choose-models)
7. [对比表](#comparison-tables)
8. [本地模型配置](#local-model-setup)
9. [成本分析](#cost-analysis)
10. [最佳实践](#best-practices)

---

## 模型类型

软件开发 AI 模型分为三大类：

### 1. 前沿模型

来自主要 AI 实验室的大规模专有模型，能力处于最前沿：

- **GPT 系列**（OpenAI）
- **Claude 系列**（Anthropic）
- **Gemini 系列**（Google）
- **Grok 系列**（xAI）

这些模型提供：
- 最大的上下文窗口（旗舰模型如今标配 100 万 token）
- 最强的推理能力
- 最强的通用知识
- 最高的每 token 成本
- 仅 API 访问（无法本地部署）

### 2. 开源模型

可本地运行或自托管的公开模型：

- **Kimi 系列**（Moonshot AI）
- **GLM 系列**（Z.ai）
- **DeepSeek 系列**（DeepSeek）
- **Qwen 系列**（阿里巴巴）
- **Mistral 系列**（Mistral AI）
- **Llama 系列**（Meta）
- **Gemma 系列**（Google）

优点：
- 免费使用
- 可本地运行，保护隐私
- 可定制、可微调
- 硬件投入后无 API 成本
- 社区驱动的改进

### 3. 编码专用模型

专注于代码生成与理解的模型（注意：2026 年，通用旗舰模型已登顶编码排行榜——见下文[编码专用模型](#coding-specific-models)）：

- **DeepSeek V4.1 Flash / V4 Pro**
- **Qwen3.8 / Qwen3.8 Max**（阿里巴巴）
- **Codestral**（Mistral）
- **Kimi K3**（Moonshot AI）
- **GLM-5.3**（Z.ai）

专长：
- 代码补全
- Bug 修复
- 代码翻译
- 文档生成
- 测试用例生成

---

## 前沿模型

### GPT 系列（OpenAI）

#### GPT-6 Astra / GPT-6.1 Sol / GPT-6.1 Terra / GPT-6 Luna

**上下文窗口：** 约 100 万 token  
**适用场景：** 复杂推理、多文件智能体编程、通用编程

**2026 年 GPT-6 阵容：**
- **GPT-6 Astra** — 每 100 万输入 10 美元，每 100 万输出 50 美元：复杂推理与编程的旗舰
- **GPT-6.1 Sol** — 约 2-4 美元/10-20 美元：以大幅降低的成本接近 Astra 的性能
- **GPT-6.1 Terra** — 2 美元/10 美元：日常编程性价比最高
- **GPT-6 Luna** — 0.10 美元/0.50 美元：快速、高频任务

**优点：**
- 在所有语言上都有出色的代码生成能力
- 对大型变更集有多步推理能力
- 善于解释复杂概念
- 广泛的工具集成生态
- API 可靠、正常运行时间好

**缺点：**
- 大规模使用时 Astra 的定价累积很快
- 免费版有速率限制
- 无法本地运行
- 偶有知识截止日期问题

**最佳用例：**
- 架构设计讨论
- 复杂算法实现
- 代码审查与优化
- 学习新技术

**关于“推理模型”的一点说明：**
扩展思考如今已内置于 GPT-6 和 Claude 系列中——没有单独的推理模型档位可供选择。你只需选择能力档位（旗舰、日常或快速/高性价比），模型会根据任务需要进行相应深度的推理。

### Claude 系列（Anthropic）

#### Claude Opus 5.5 / Claude Sonnet 5.5 / Claude Fable 5.1 / Claude Haiku 5.5

**上下文窗口：** 100 万 token  
**适用场景：** 长时间运行的智能体编程、代码库范围的重构、文档

**2026 年 Claude 阵容：**
- **Claude Opus 5.5** — 每 100 万输入 4 美元，每 100 万输出 20 美元：旗舰，最适合长时间运行的智能体编程
- **Claude Sonnet 5.5** — 2 美元/10 美元：日常编程主力
- **Claude Fable 5.1** — 10 美元/50 美元：最难的推理与长周期工作
- **Claude Haiku 5.5** — 0.10 美元/0.50 美元：高频、对延迟敏感的任务

**优点：**
- BenchLeader 编码指数第 1 名（Opus 5.5，80.9 分，2026 年 11 月）
- Terminal-bench 4.0 最佳成绩（Sonnet 5.5，70.6%）
- 100 万上下文，理解整个仓库
- 善于遵循指令
- 安全意识强
- 适合遗留代码现代化

**缺点：**
- Opus/Fable 定价较高
- 简单任务比 Haiku 档位的模型慢
- 仅 Anthropic 生态（无开放权重）

**最佳用例：**
- 完整仓库分析
- 大规模重构项目
- 技术文档
- 安全审计

### Gemini 系列（Google）

#### Gemini 4 Argon / Gemini 4 Carbon

**上下文窗口：** 100 万 token  
**适用场景：** 真实世界软件工程、大规模上下文处理、多模态任务

**2026 年 Gemini 阵容：**
- **Gemini 4 Argon** — 每 100 万输入约 2 美元，每 100 万输出约 10 美元（推广价）：为真实世界软件工程打造的旗舰
- **Gemini 4 Carbon** — 8 美元/8 美元：编码分数高（BenchLeader 75.2 分）
- **Gemini Flash 系列** — 约 0.75 美元/3.75 美元：快速且便宜

**优点：**
- DeepSWE v1.1 最佳成绩（Argon，77.9%）
- 100 万上下文，原生多模态理解
- 与 Google Cloud 和 Antigravity 良好集成
- 定价有竞争力

**缺点：**
- Argon 定价为推广价，可能上涨
- API 可用性因地区而异
- 编码智能体生态不如 Anthropic/OpenAI 成熟

### Grok 系列（xAI）

**适用场景：** 实时信息、非常规问题解决

**优点：**
- 可访问实时 X/Twitter 数据
- 回答限制较少
- 近期版本中编码性能有竞争力

**缺点：**
- 编码不是主要焦点
- 编码生态比 Claude/GPT/Gemini 小
- 大规模重构的代码质量不稳定

---

## 开源模型

### Kimi 系列（Moonshot AI）

#### Kimi K3

**上下文窗口：** 100 万+ token  
**定价：** 每 100 万输入 3 美元，每 100 万输出 15 美元  
**适用场景：** 在开放权重模型上进行长上下文智能体编程

**优点：**
- 100 万+ 上下文窗口，可处理整个仓库
- 强大的智能体/工具使用性能
- 开放权重（可自托管，也提供 API）
- 可与专有中端模型媲美

### GLM 系列（Z.ai）

#### GLM-5.3

**上下文窗口：** 100 万 token  
**定价：** 每 100 万输入 1.40 美元，每 100 万输出 4.40 美元  
**适用场景：** 以旗舰模型一小部分的成本获得高质量编程能力

**优点：**
- 价格极低，编码性能出色
- 100 万上下文
- 开放权重，商业友好的许可
- 强大的社区工具与量化支持

### DeepSeek 系列

#### DeepSeek V4 Pro / DeepSeek V4.1 Flash

**上下文窗口：** 100 万 token  
**定价：** V4 Pro 每 100 万 token 为 0.66 美元/1.98 美元，V4.1 Flash 为 0.15 美元/0.60 美元  
**适用场景：** 对成本敏感的高频编程

**优点：**
- 混合专家（MoE）架构（高效推理）
- 个人开发者的成本几乎为零
- 出色的数学与编程能力
- 开放权重 + 便宜的托管 API

**性能：**
- 在编码基准上可与中端专有模型媲美
- 得益于 MoE 架构，推理更快
- 生产使用的最佳性价比档位

### Qwen 系列（阿里巴巴）

#### Qwen3.8 / Qwen3.8 Max

**上下文窗口：** 100 万 token  
**适用场景：** 编程任务、多语言支持、本地部署

**优点：**
- Qwen3.8 家族整体编码能力出色
- 强大的多语言支持
- 多种尺寸（小型变体可在消费级 GPU 上运行）
- 高效推理与良好的量化支持

### Mistral 系列（Mistral AI）

#### Mistral Large 4

**上下文窗口：** 100 万级别  
**适用场景：** 欧洲部署、高效推理

**优点：**
- 出色的效率（MoE 架构）
- 强大的欧洲语言支持
- 商业友好的许可
- 良好的编码能力

### Llama 系列（Meta）

**适用场景：** 通用、本地部署、社区微调

**优点：**
- 多代产品提供多种尺寸选择
- 庞大的社区生态与微调
- 可在消费级硬件上运行（小型变体）
- 允许商业使用

### Gemma 系列（Google）

**适用场景：** 轻量应用、设备端实验

**优点：**
- Google 的开放模型产品
- 每参数性能良好
- 易于微调
- 强大的安全训练

---

## 编码专用模型

### 2026 年的现实：旗舰模型领先

专用代码模型已不再登顶排行榜——通用旗舰模型才是。Claude Opus 5.5（80.9 分）和 Gemini 4 Carbon（75.2 分）位居 BenchLeader 编码指数前列，Claude Sonnet 5.5（72.7 分）等日常模型也超过了昨天的代码专家。按能力档位而非“编码”标签选择模型。

真正仍有专业性的模型：

### DeepSeek V4.1 Flash / V4 Pro

**上下文窗口：** 100 万 token  
**定价：** 每 100 万 token，Flash 为 0.15 美元/0.60 美元，Pro 为 0.66 美元/1.98 美元

**能力：**
- 高吞吐代码生成
- Bug 修复与重构
- 代码解释与测试生成
- 100 万上下文，适用于大型文件和仓库

**性能：**
- 以最低价格档位实现接近前沿的编码能力
- MoE 架构保持推理快速且便宜
- 自托管或 API 使用的极佳性价比

### Qwen3.8 / Qwen3.8 Max（阿里巴巴）

**优点：**
- 全栈开发与 API 设计
- 数据库查询与 DevOps 脚本
- 强大的 TypeScript/JavaScript 与 Python 支持
- 多种尺寸，从本地到 Max 档 API

### Codestral（Mistral）

**专长：**
- 代码补全
- 中间填充（FIM）
- 80+ 种编程语言

**性能：**
- 推理快速
- 出色的 IDE 集成
- 允许商业使用

### Kimi K3 与 GLM-5.3

**优点：**
- 开放权重模型，强大到足以支撑智能体编程工作流
- 100 万上下文窗口
- 自托管便宜或通过 API 调用便宜
- 因合规需要开放权重时的良好替代选择

---

## 关键概念

### 上下文窗口

模型在单次请求中能处理的最大 token 数。

**为什么重要：**
- 上下文越大，一次能分析的代码越多
- 理解完整文件或仓库
- 长对话中更好的一致性

**典型尺寸（2026）：**
- 小型/快速模型：128K-256K token
- 中端模型：256K-512K token
- 旗舰模型：100 万 token（如今已成标准）
- 长上下文档位：100 万+ token（Kimi K3，以及所有 Claude/GPT/Gemini 旗舰）

**Token 估算：**
- 1 个 token ≈ 4 个英文字符
- 1 个 token ≈ 0.75 个单词
- 100 行代码 ≈ 500-1000 个 token

### 推理 vs 补全

**补全模型：**
- 基于模式预测下一个 token
- 快速，但可能缺乏深层理解
- 适合自动补全、简单任务

**推理模型：**
- 思维链处理
- 更适合复杂问题
- 更慢但更准确
- 示例：Claude Fable 5.1、Claude Opus 5.5、GPT-6 Astra（扩展思考）

### 推理方法

**云端 API：**
- 优点：无需配置、始终是最新版本、可扩展
- 缺点：成本、延迟、隐私顾虑

**本地推理：**
- 优点：隐私、无持续成本、可定制
- 缺点：硬件投入、配置复杂

**量化：**
- 降低模型精度（FP16 → INT8 → INT4）
- 更小的内存占用
- 质量略有取舍
- 让更大的模型能在消费级硬件上运行

### 延迟考量

**首 token 时间（TTFT）：**
- 云端 API：200ms-2s
- 本地小型模型：50ms-500ms
- 本地大型模型：1s-5s

**每秒 token 数：**
- 云端 API：50-200 token/秒
- 本地 RTX 4090：20-100 token/秒（取决于模型）
- 本地 CPU：2-20 token/秒

### 幻觉模式

AI 代码生成中的常见问题：

1. **不存在的 API：** 编造库函数
2. **错误的导入：** 从错误的包导入
3. **过时的语法：** 使用已弃用的模式
4. **逻辑错误：** 代码能运行但行为错误
5. **安全漏洞：** 缺少身份验证检查、SQL 注入

**缓解策略：**
- 始终审查生成的代码
- 立即运行测试
- 用 AI 做脚手架，而非最终代码
- 与文档交叉核对
- Sonar 2026 年调查（1,149 名专业人士）发现 96% 的人不完全信任 AI 生成的代码——但只有 48% 的人总是在提交前检查它。要成为另外那 48%。

### 工具使用

现代模型可以使用外部工具：

- **代码执行：** 运行代码验证输出
- **Web 搜索：** 查找最新文档
- **文件操作：** 读写项目文件
- **终端命令：** 执行 shell 命令
- **API 调用：** 与外部服务交互

### RAG（检索增强生成）

用你的代码库增强模型：

1. 将代码库索引到向量数据库
2. 检索相关片段作为上下文
3. 包含在模型提示词中
4. 获得上下文感知的回答

**工具：**
- Chroma、Pinecone、Weaviate（向量数据库）
- LangChain、LlamaIndex（编排）

### 多模态能力

部分模型可以处理：
- 代码截图 → 可运行代码
- 架构图 → 实现计划
- 错误截图 → 调试帮助
- UI  mockup → 前端代码

---

## 如何选择模型

### 2026 年路由规则

各厂商如今提供相同的三个档位，因此选择模式很简单：

- **复杂多文件 / 智能体工作** → 旗舰档位（Claude Opus 5.5、Claude Fable 5.1、GPT-6 Astra、Gemini 4 Argon）
- **日常编程** → 中端（Claude Sonnet 5.5、GPT-6.1 Sol、Gemini 4 Flash）
- **长上下文、大批量或对成本敏感的工作** → 高性价比档位（Claude Haiku 5.5、GPT-6.1 Terra、GPT-6 Luna、DeepSeek V4.1 Flash、GLM-5.3）

### 前端开发

**推荐：** Claude Sonnet 5.5、GPT-6.1 Terra、Gemini 4 Argon

**任务：**
- 组件生成 → 任意编程模型
- Tailwind CSS → Claude（出色的 CSS 理解）
- React 模式 → GPT-6.1 Sol 或 Claude Sonnet 5.5
- 动画 → GPT-6.1 Terra（有创意的解决方案）
- 无障碍 → Claude（强大的规范知识）

**本地替代：** GLM-5.3、Qwen3.8（开放权重）

### 后端开发

**推荐：** Claude Sonnet 5.5、DeepSeek V4 Pro、GPT-6.1 Terra

**任务：**
- API 设计 → Claude（清晰的架构）
- 数据库查询 → GPT-6.1 Terra 或 DeepSeek
- 身份验证 → Claude（注重安全）
- 微服务 → GPT-6 Astra（系统设计）
- 性能优化 → DeepSeek V4 Pro

**本地替代：** DeepSeek V4 Pro、GLM-5.3

### DevOps 与基础设施

**推荐：** GPT-6.1 Sol、Claude Sonnet 5.5、Mistral Large 4

**任务：**
- Docker 文件 → 任意编程模型
- Kubernetes 清单 → GPT-6.1 Sol（复杂 YAML）
- Terraform → Claude（结构化配置）
- CI/CD 流水线 → GPT-6.1 Terra
- 监控配置 → Claude Sonnet 5.5

**本地替代：** GLM-5.3、Qwen3.8

### 安全审计

**推荐：** Claude Opus 5.5、GPT-6 Astra

**任务：**
- 漏洞扫描 → Claude Opus 5.5（彻底分析）
- 渗透测试计划 → GPT-6 Astra
- 安全最佳实践 → Claude
- 合规检查 → GPT-6.1 Sol

**注意：** 始终结合自动化安全工具使用

### 学习与教育

**推荐：** GPT-6.1 Terra、Claude Sonnet 5.5、Claude Haiku 5.5

**任务：**
- 概念解释 → GPT-6.1 Terra（清晰的教学）
- 代码讲解 → Claude（详细）
- 练习题 → 任意模型
- 快速提问 → Claude Haiku 5.5 / GPT-6 Luna（快速、便宜）

### 生产系统

**考量：**
- 可靠性 > 前沿性
- 输出一致
- 良好的错误处理
- SLA 保证

**推荐：** GPT-6.1 Sol、Claude Sonnet 5.5、DeepSeek V4.1 Flash（高性价比）

### 隐私敏感项目

**选项：**
1. 本地模型（Ollama、LM Studio）
2. 在私有基础设施上自托管开放权重模型
3. 与数据保护相关的企业协议

**推荐本地模型（开放权重）：**
- GLM-5.3（质量/尺寸平衡最佳）
- DeepSeek V4.1 Flash（快速、轻量）
- Qwen3.8（多种尺寸、多语言）
- Kimi K3（长上下文，如果硬件允许）

---

## 对比表

### 整体能力对比

| 模型 | 编程质量 | 推理 | 速度 | 上下文 | 成本 | 本地 |
|-------|---------------|-----------|-------|---------|------|-------|
| Claude Opus 5.5 | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ | ⭐⭐⭐ | 1M | $$ | ❌ |
| Claude Sonnet 5.5 | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐ | 1M | $ | ❌ |
| Claude Fable 5.1 | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ | ⭐⭐ | 1M | $$$ | ❌ |
| Claude Haiku 5.5 | ⭐⭐⭐⭐ | ⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ | 1M | $ | ❌ |
| GPT-6 Astra | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ | ⭐⭐⭐ | 1M | $$$ | ❌ |
| GPT-6.1 Sol | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐ | 1M | $$ | ❌ |
| GPT-6.1 Terra | ⭐⭐⭐⭐ | ⭐⭐⭐⭐ | ⭐⭐⭐⭐ | 1M | $ | ❌ |
| GPT-6 Luna | ⭐⭐⭐⭐ | ⭐⭐⭐ | ⭐⭐⭐⭐⭐ | 1M | $ | ❌ |
| Gemini 4 Argon | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐ | 1M | $ | ❌ |
| Gemini 4 Carbon | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐ | ⭐⭐⭐⭐ | 1M | $$ | ❌ |
| Kimi K3 | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐ | ⭐⭐⭐⭐ | 1M+ | $$ | ✅ |
| GLM-5.3 | ⭐⭐⭐⭐ | ⭐⭐⭐⭐ | ⭐⭐⭐⭐ | 1M | $ | ✅ |
| DeepSeek V4 Pro | ⭐⭐⭐⭐ | ⭐⭐⭐⭐ | ⭐⭐⭐⭐ | 1M | $ | ✅ |
| DeepSeek V4.1 Flash | ⭐⭐⭐⭐ | ⭐⭐⭐ | ⭐⭐⭐⭐⭐ | 1M | $ | ✅ |
| Qwen3.8 Max | ⭐⭐⭐⭐ | ⭐⭐⭐⭐ | ⭐⭐⭐⭐ | 1M | $ | ✅ |
| Mistral Large 4 | ⭐⭐⭐⭐ | ⭐⭐⭐⭐ | ⭐⭐⭐⭐ | 1M 级 | $$ | ✅ |

*本地 = 提供开放权重，可自托管（需承担硬件成本）*

### 编程基准分数

**BenchLeader 编码指数（2026 年 11 月 5 日）：**

| 排名 | 模型 | 分数 |
|------|-------|-------|
| #1 | Claude Opus 5.5 | 80.9 |
| #2 | Gemini 4 Carbon | 75.2 |
| #3 | Claude Sonnet 5.5 | 72.7 |
| #4 | GPT-6.1 Sol | 72.1 |

**Terminal-bench 4.0（智能体终端编程）：**

| 模型 | 分数 |
|-------|-------|
| Claude Sonnet 5.5 | 70.6% |
| Claude Opus 5.5 | 66.4% |
| GPT-6 Astra | 57.9% |

**DeepSWE v1.1（真实世界软件工程）：**

| 模型 | 分数 |
|-------|-------|
| Gemini 4 Argon | 77.9% |
| Claude Opus 5.5 | 74.2% |

*基准测试变化很快——在选定模型前请重新核查排行榜*

### 成本对比（每 100 万 token）

| 模型 | 输入 | 输出 | 每月 1000 万 token* |
|-------|-------|--------|-------------------|
| Claude Opus 5.5 | 4 美元 | 20 美元 | 120 美元 |
| Claude Sonnet 5.5 | 2 美元 | 10 美元 | 60 美元 |
| Claude Fable 5.1 | 10 美元 | 50 美元 | 300 美元 |
| Claude Haiku 5.5 | 0.10 美元 | 0.50 美元 | 3 美元 |
| GPT-6 Astra | 10 美元 | 50 美元 | 300 美元 |
| GPT-6.1 Sol | 约 2-4 美元 | 约 10-20 美元 | 约 60-120 美元 |
| GPT-6.1 Terra | 2 美元 | 10 美元 | 60 美元 |
| GPT-6 Luna | 0.10 美元 | 0.50 美元 | 3 美元 |
| Gemini 4 Argon | 约 2 美元 | 约 10 美元 | 约 60 美元 |
| Gemini 4 Carbon | 8 美元 | 8 美元 | 80 美元 |
| Gemini Flash | 约 0.75 美元 | 约 3.75 美元 | 约 23 美元 |
| Kimi K3 | 3 美元 | 15 美元 | 90 美元 |
| GLM-5.3 | 1.40 美元 | 4.40 美元 | 29 美元 |
| DeepSeek V4 Pro | 0.66 美元 | 1.98 美元 | 13 美元 |
| DeepSeek V4.1 Flash | 0.15 美元 | 0.60 美元 | 4 美元 |

*假设输入/输出 token 各占 50%；本地模型：每 100 万 token 约 0.02-0.10 美元（仅电费）

### 本地模型的硬件要求

| 模型类别 | 显存（4-bit） | 显存（8-bit） | 内存（CPU） | 最低 GPU |
|-------------|-------------|-------------|-----------|---------|
| 小型（3-8B） | 3-6GB | 5-10GB | 8-16GB | 无 / GTX 1660 |
| 中型（14-32B） | 10-20GB | 18-36GB | 32-48GB | RTX 3090 |
| 大型（70B） | 42GB | 80GB | 96GB | 2x RTX 3090 |
| MoE 旗舰（开放权重，如 GLM-5.3、Kimi K3） | 48GB+* | 90GB+ | 128GB+ | 2x RTX 4090 |

*MoE 模型推理时所需的显存比参数量暗示的要少

---

## 本地模型配置

### Ollama 安装

**macOS：**
```bash
brew install ollama
ollama serve
```

**Linux：**
```bash
curl -fsSL https://ollama.com/install.sh | sh
ollama serve
```

**Windows：**
从 https://ollama.com/download 下载

**拉取模型：**
```bash
ollama pull glm-5.3
ollama pull deepseek-v4.1-flash
ollama pull qwen3.8
ollama pull codestral
```

**运行模型：**
```bash
ollama run glm-5.3
ollama run deepseek-v4.1-flash "Explain async/await in JavaScript"
```

### LM Studio

**功能：**
- 用户友好的 GUI
- 内置模型库
- 聊天界面
- 本地 API 服务器
- 无需命令行

**配置：**
1. 从 https://lmstudio.ai 下载
2. 安装并启动
3. 搜索并下载模型
4. 开始聊天或启用本地 API

### Continue.dev（VS Code 扩展）

**配置：**
1. 在 VS Code 中安装 Continue 扩展
2. 配置模型（云端 + 本地）：

```json
{
  "models": [
    {
      "title": "Claude Sonnet 5.5",
      "provider": "anthropic",
      "model": "claude-sonnet-5-5",
      "apiKey": "YOUR_KEY"
    },
    {
      "title": "GPT-6.1 Terra",
      "provider": "openai",
      "model": "gpt-6.1-terra"
    },
    {
      "title": "GLM-5.3 (local)",
      "provider": "ollama",
      "model": "glm-5.3",
      "apiBase": "http://localhost:11434"
    }
  ]
}
```

3. 使用 Cmd/Ctrl + L 与代码上下文聊天

### vLLM（生产部署）

**高性能服务：**

```bash
pip install vllm

python -m vllm.entrypoints.api_server \
    --model deepseek-ai/DeepSeek-V4.1-Flash \
    --tensor-parallel-size 2 \
    --max-model-len 1048576
```

---

## 成本分析

### 每月使用场景

**休闲开发者（每月 100 万 token）：**
- GPT-6.1 Terra：约 6 美元/月
- Claude Sonnet 5.5：约 6 美元/月
- 本地模型：约 0.10 美元/月（电费）

**活跃开发者（每月 1000 万 token）：**
- Claude Sonnet 5.5：约 60 美元/月
- GPT-6.1 Terra：约 60 美元/月
- GPT-6 Astra（仅旗舰工作流）：约 300 美元/月
- DeepSeek V4.1 Flash API：约 4 美元/月
- 本地模型：约 1 美元/月

**5 人团队（每月 5000 万 token）：**
- Claude Sonnet 5.5：约 300 美元/月
- Claude Opus 5.5（智能体密集型）：约 600 美元/月
- GPT-6 Astra（仅旗舰）：约 1,500 美元/月
- DeepSeek V4.1 Flash API：约 20 美元/月
- 本地配置：约 500 美元一次性硬件 + 约 5 美元/月

**企业（每月 5 亿 token）：**
- 协商定制 API 定价
- 考虑自托管开放权重模型（GLM-5.3、DeepSeek V4）
- 混合方案（高峰用云端，基线用本地）

**⚠️ 警惕按 token 计价：** Gartner（2026 年 6 月）警告称，按 token 计价使成本难以预测——没有预算和路由规则，到 2028 年 AI 编程支出可能超过开发者的平均薪资。把简单工作路由到高性价比档位的模型，把旗舰留给难题。

### ROI 计算

**节省时间：**
- 普通开发者：50-100 美元/小时
- AI 提升 2-5 倍生产力
- 每周节省 10 小时 = 每月 2000-4000 美元价值

**结论：** 即使是昂贵的旗舰用量也能回本——但前提是把日常工作路由到中端和高性价比档位的模型

---

## 最佳实践

### 模型选择指南

1. **从中端模型开始**（Claude Sonnet 5.5、GPT-6.1 Sol、Gemini 4 Argon）
2. **针对特定任务使用专门档位：**
   - 快速自动补全 → 小型本地模型 / Claude Haiku 5.5 / GPT-6 Luna
   - 复杂多文件智能体工作 → Claude Opus 5.5 / GPT-6 Astra / Claude Fable 5.1
   - 代码审查 → Claude Sonnet 5.5
   - 学习 → GPT-6.1 Terra

3. **实施回退策略：**
   - 首选：Claude Sonnet 5.5
   - 回退：GPT-6.1 Sol
   - 应急：本地模型（GLM-5.3 / DeepSeek V4.1 Flash）

4. **监控用量与成本：**
   - 设定月度预算（token 定价增长很快）
   - 跟踪 token 消耗
   - 优化提示词以减少 token

### 提示词优化

**减少 token 用量：**
- 请求要简洁
- 删除不必要的上下文
- 在清晰的前提下使用缩写
- 引用文件而非粘贴

**提升质量：**
- 提供清晰的示例
- 预先说明约束
- 包含要处理的错误情况
- 定义输出格式

### 安全考量

**切勿与云端模型分享：**
- API 密钥与机密
- 专有算法
- 客户 PII 数据
- 安全漏洞（修补前）

**在以下场景使用本地模型：**
- 敏感代码库
- 政府/国防项目
- 医疗数据（HIPAA）
- 金融系统

### 保持模型更新

**保持了解：**
- 关注模型发布公告
- 在基准任务上测试新模型
- 监控社区反馈
- 检查安全更新

**评估工作流：**
1. 创建典型任务测试集
2. 在新模型版本上运行
3. 比较质量/速度/成本
4. 有显著改进则更新

---

## 速查

### 最佳整体模型

| 类别 | 模型 |
|----------|-------|
| 最佳代码质量 | Claude Opus 5.5 |
| 最佳智能体 / 长时间运行编程 | Claude Opus 5.5 / Claude Fable 5.1 |
| 最佳推理 | Claude Fable 5.1 / GPT-6 Astra |
| 最佳日常编程 | Claude Sonnet 5.5 |
| 最佳性价比 | GPT-6.1 Terra / DeepSeek V4.1 Flash |
| 最佳开放权重 | Kimi K3 / GLM-5.3 |
| 最佳上下文 | 100 万已成标准——Claude Sonnet 5.5 / Gemini 4 Argon |
| 最适合学习 | GPT-6.1 Terra |
| 最适合生产 | Claude Sonnet 5.5 / GPT-6.1 Sol |
| 最适合隐私 | GLM-5.3（自托管） |
| 最适合高频 / 低延迟 | Claude Haiku 5.5 / GPT-6 Luna |

### 推荐入门配置

**初级：**
- 首选：ChatGPT 免费版 / Claude 免费版
- 备用：GPT-6.1 Terra 或 Claude Haiku 5.5（便宜的 API）
- 本地：通过 Ollama 使用 GLM-5.3

**中级：**
- 首选：Claude Sonnet 5.5（通过 Pro/Max 订阅或 API）
- 备用：GPT-6.1 Sol
- 本地：通过 Ollama 使用 DeepSeek V4.1 Flash

**高级：**
- 首选：Claude Opus 5.5，用于复杂智能体任务
- 次选：Claude Sonnet 5.5，用于日常工作
- 长周期推理：Claude Fable 5.1 或 GPT-6 Astra
- 本地：GLM-5.3 或 Kimi K3（开放权重）
- 高性价比/大批量：DeepSeek V4.1 Flash 或 Qwen3.8 Max

---

## 资源

### 模型仓库

- Hugging Face：https://huggingface.co/models
- Ollama Library：https://ollama.com/library
- LM Studio Models：内置
- Replicate：https://replicate.com/explore

### 基准测试网站

- BenchLeader（编码指数）：https://benchleader.ai
- Terminal-bench（智能体编程）：https://terminal-bench.io
- LMArena（Chatbot Arena）：https://lmarena.ai
- SWE-bench / DeepSWE：https://www.swebench.com
- Artificial Analysis：https://artificialanalysis.ai

### 社区资源

- r/LocalLLaMA（Reddit）
- Hugging Face Discord
- Ollama Discord
- 各模型专属 GitHub 讨论区

---

*最后更新：2026 年 11 月*
