# 氛围编程（Vibe Coding）：从零到精通

一个关于现代 AI 辅助软件开发的完整开源知识库。

---

# 什么是氛围编程？

Vibe Coding 是一种现代软件开发方式：开发者与 AI 系统协作，以更快的速度设计、编写、调试、优化、测试、部署和扩展软件。

开发者不再逐行手动编写每一行代码，而是：

* 描述意图
* 引导架构
* 优化输出
* 验证逻辑
* 与 AI 一起调试
* 编排工具
* 专注于系统与产品

Vibe Coding 不是：

* 盲目复制粘贴 AI 代码
* 取代工程基础
* 跳过架构/设计
* 回避调试

一名优秀的氛围编程者理解：

* 软件工程
* 提示
* 架构
* 调试
* 基础设施
* 产品思维
* 部署
* 自动化
* AI 的局限

目标是：

> 在保持质量的同时，更快地构建软件。

---

# 仓库愿景

本仓库应当成为：

* 一本完整的 Vibe Coding 手册
* AI 原生软件工程路线图
* 从入门到进阶的指南
* 开源学习中心
* 基于项目的学习系统
* 工具生态参考
* 提示工程知识库
* 部署 + DevOps 指南
* 离线 AI 开发实验室

---

# 推荐的仓库结构

```txt
vibe-coding-zero-to-hero/
│
├── README.md
├── LICENSE
├── CONTRIBUTING.md
├── ROADMAP.md
├── RESOURCES.md
│
├── 00-introduction/
├── 01-what-is-vibe-coding/
├── 02-how-to-start/
├── 03-hardware-guide/
├── 04-ai-models/
├── 05-ai-tools/
├── 06-ides-editors/
├── 07-prompt-engineering/
├── 08-frontend/
├── 09-backend/
├── 10-databases/
├── 11-devops-cloud/
├── 12-hosting-platforms/
├── 13-testing-debugging/
├── 14-security/
├── 15-offline-vibe-coding/
├── 16-open-source-projects/
├── 17-real-world-workflows/
├── 18-monetization/
├── 19-freelancing/
├── 20-system-design/
├── 21-mobile-development/
├── 22-ai-agents/
├── 23-rag-vector-databases/
├── 24-automation/
├── 25-cheat-sheets/
├── 26-awesome-prompts/
├── 27-case-studies/
├── 28-failure-patterns/
├── 29-interview-prep/
└── assets/
```

---

# README 结构

README 是仓库的首页。

它应当包括：

* 什么是 Vibe Coding？
* 本仓库面向谁？
* 学习路线图
* 工具生态
* 入门路线图
* 进阶路线图
* 推荐技术栈
* AI 编程工作流
* 贡献指南
* 社区部分
* 资源链接
* 架构图
* 演示截图

---

# 01 — 什么是氛围编程

本节讲解：

## 主题

* 软件开发的演进
* AI 辅助工程
* 人与 AI 的协作
* 提示驱动开发
* AI 原生工作流
* 智能体编程
* 多模型工作流
* AI 的局限
* 幻觉
* 上下文窗口
* 推理与自动补全
* 为什么基础知识依然重要

## 包含内容

* 图解
* 示例
* 工作流
* 入门讲解
* 架构可视化

---

# 02 — 如何开始

## 入门路径

### 第 1 步 — 学习基础知识

理解：

* Git
* GitHub
* Linux 基础
* 终端
* API
* JSON
* HTTP
* 前端基础
* 后端基础

### 第 2 步 — 学习提示

学习：

* 结构化提示词
* 角色提示
* 思维链
* 调试提示词
* 架构提示词
* 重构提示词

### 第 3 步 — 开始构建

从以下项目开始：

* 待办应用
* 个人作品集
* 仪表盘
* API 项目
* 博客 CMS
* AI 聊天机器人

### 第 4 步 — 学习部署

学习：

* Vercel
* Netlify
* Railway
* Docker
* VPS 部署

### 第 5 步 — 学习调试

大多数氛围编程者都在这里失败。

学习：

* 日志
* 堆栈跟踪
* 浏览器调试
* API 调试
* 终端调试
* AI 调试提示词

---

# 03 — 硬件指南

讲解硬件要求。

## 入门配置

* 16GB 内存
* Ryzen 5 / Intel i5
* SSD 存储
* 良好的网络

## 推荐配置

* 32GB 内存
* Ryzen 7 / Intel i7
* RTX 显卡（可选）
* 双显示器配置

## 本地 AI 配置

对于本地模型：

* 建议 32GB+ 内存
* 建议 NVIDIA 显卡
* Apple Silicon 非常适合本地 AI

## GPU 推荐

### 预算档

* RTX 3060 12GB
* RTX 4060

### 中端档

* RTX 4070
* RTX 4080

### 高端档

* RTX 4090
* Mac Studio M 系列

## 讲解内容

* VRAM
* 量化
* token 生成
* 推理速度
* 内存要求
* CPU 与 GPU 推理对比

---

# 04 — AI 模型

这是最重要的章节之一。

## 讲解模型类型

### 前沿模型

* GPT
* Claude
* Gemini
* Grok

### 开源模型

* DeepSeek
* Qwen
* Llama
* Mistral
* Phi
* Gemma

### 编程模型

* DeepSeek Coder
* Qwen Coder
* Codestral
* Codex
* Claude Code

## 讲解概念

* 上下文窗口
* 推理
* 推断
* 延迟
* 编程质量
* 幻觉
* 工具使用
* RAG
* 智能体
* 多模态

## 如何选择模型

### 前端

最适合：

* UI 生成
* React
* Tailwind
* 动画
* 组件系统

### 后端

最适合：

* API
* 架构
* 优化
* 调试

### DevOps

最适合：

* Docker
* Kubernetes
* Terraform
* CI/CD

### 安全

最适合：

* 代码审查
* 漏洞分析
* 威胁建模

## 对比表

为以下方面制作表格：

* 速度
* 成本
* 编程质量
* 上下文长度
* 开源可用性
* 本地支持
* 推理能力

---

# 05 — AI 工具

创建独立的 Markdown 文件。

## 涵盖的工具

* Claude
* ChatGPT
* Codex
* DeepSeek
* Cursor
* Devin Desktop（前身为 Windsurf）
* Continue
* Aider
* OpenCode
* Kiro
* Dyad
* Antigravity
* Roo Code
* Cline
* Augment
* Bolt
* Lovable
* v0
* Replit

## 每个工具包括

* 它是什么
* 功能
* 优点
* 缺点
* 定价
* 最佳使用场景
* 安装指南
* 截图
* 工作流示例
* 提示词示例

---

# 06 — IDE 与编辑器

## 编辑器

* VS Code
* Zed
* Neovim
* JetBrains
* Cursor
* Devin Desktop（前身为 Windsurf）

## AI 原生 IDE

* Cursor
* Devin Desktop（前身为 Windsurf）
* Kiro
* Dyad
* Antigravity
* OpenCode

## 讲解内容

* 安装
* 扩展
* AI 集成
* 工作流
* 调试配置
* 终端集成
* Git 集成
* 本地模型支持

## VS Code 扩展

* GitLens
* Error Lens
* Thunder Client
* Docker
* ESLint
* Prettier
* Continue
* Roo Code
* Cline

---

# 07 — 提示工程

专门讲授面向软件开发的提示技巧。

## 提示词类型

* 架构提示词
* 调试提示词
* 前端提示词
* 后端提示词
* 优化提示词
* 安全提示词
* 重构提示词
* 文档提示词
* 部署提示词
* 数据库提示词

## 提示词模板

提供可复用的模板。

示例：

```txt
You are a senior backend engineer.

Build a scalable Express.js API with:
- JWT authentication
- PostgreSQL
- Redis caching
- rate limiting
- Docker support
- production logging
```

---

# 08 — 前端开发

## 技术

* React
* Next.js
* Vue
* Nuxt
* Svelte
* Tailwind
* TypeScript
* Shadcn UI

## 主题

* 组件架构
* 状态管理
* 路由
* 动画
* 性能优化
* 无障碍
* 响应式设计
* SEO
* SSR
* hydration

## 包含内容

* 项目结构
* 入门模板
* AI 工作流
* 调试指南

---

# 09 — 后端开发

## 技术

* Node.js
* Express
* FastAPI
* Go
* Rust
* Django
* Spring Boot

## 主题

* REST API
* GraphQL
* 身份验证
* 授权
* 微服务
* 队列
* 缓存
* 可扩展性
* API 安全
* 日志

---

# 10 — 数据库

## SQL

* PostgreSQL
* MySQL
* SQLite

## NoSQL

* MongoDB
* Redis
* Cassandra

## AI 数据库

* Pinecone
* Weaviate
* Chroma
* Qdrant
* Milvus

## 概念

* 索引
* 复制
* 缓存
* 向量嵌入
* RAG 流水线

---

# 11 — DevOps 与云

本节可能会非常庞大。

## 主题

* Linux
* Docker
* Kubernetes
* Helm
* Terraform
* Ansible
* GitHub Actions
* GitLab CI
* ArgoCD
* 可观测性
* Prometheus
* Grafana
* OpenTelemetry
* 安全
* 密钥管理

## 云平台

* AWS
* Azure
* GCP
* Cloudflare
* DigitalOcean

---

# 12 — 托管平台

## 入门托管

* Vercel
* Netlify
* Railway
* Render
* Fly.io

## VPS 托管

* Hetzner
* Contabo
* OVH
* DigitalOcean
* Vultr
* Linode

## 主题

* 域名配置
* 反向代理
* nginx
* SSL 证书
* Docker 部署
* CI/CD 部署
* 监控
* 备份

---

# 13 — 测试与调试

关键章节。

## 调试主题

* 浏览器开发者工具
* 网络调试
* API 调试
* 内存泄漏
* 性能分析
* 终端日志
* Docker 日志
* Kubernetes 调试
* 追踪

## 测试

* 单元测试
* 集成测试
* 端到端测试
* Playwright
* Cypress
* Jest
* Vitest

## AI 调试工作流

讲授：

* 如何分享堆栈跟踪
* 如何隔离 bug
* 如何向 AI 提出恰当的调试问题
* 如何复现问题

---

# 14 — 安全

## 主题

* 身份验证
* 授权
* JWT
* OAuth
* 密钥管理
* API 安全
* 依赖扫描
* 容器安全
* 云安全
* AI 安全风险
* 提示注入

---

# 15 — 离线氛围编程

最重要的章节之一。

## Ollama

讲解：

* 安装
* 拉取模型
* 本地运行模型
* GPU 使用
* CPU 推理
* 量化模型

## 本地模型

* DeepSeek
* Qwen
* Llama
* Phi
* Mistral
* Gemma

## 工具

* Ollama
* LM Studio
* Jan
* Open WebUI
* Continue
* AnythingLLM
* LocalAI
* llama.cpp

## 本地 AI IDE 配置

* VS Code + Continue
* Ollama + Open WebUI
* 本地嵌入
* 离线智能体

## 隐私优势

* 本地推理
* 私有代码库
* 无云端依赖
* 长期成本更低

---

# 16 — 开源项目

包括项目创意。

## 入门级

* 待办应用
* 天气应用
* 个人作品集
* 博客 CMS

## 中级

* AI 聊天机器人
* 仪表盘
* SaaS 入门套件
* 短链接
* 认证系统

## 高级

* Kubernetes 仪表盘
* AI 智能体平台
* RAG 系统
* DevOps 平台
* 监控系统

---

# 17 — 真实世界工作流

讲授完整的工作流。

## 示例工作流

创意 → 提示词 → 架构 → 编程 → 测试 → 部署 → 监控 → 扩展

## 包含内容

* 截图
* 图解
* 提示词
* 终端命令
* 部署流水线

---

# 18 — 变现

讲授氛围编程者如何赚钱。

## 主题

* SaaS
* 自由职业
* 咨询
* 模板
* UI 套件
* 开源赞助
* 课程
* 内容创作
* 独立开发

---

# 19 — 自由职业

## 主题

* 客户获取
* 提案撰写
* 定价
* MVP 构建
* 快速原型
* 维护
* 沟通

---

# 20 — 系统设计

## 主题

* 可扩展性
* 负载均衡
* 缓存
* 队列
* 分布式系统
* 微服务
* 可观测性
* CDN
* 边缘计算

---

# 21 — 移动开发

## 技术

* React Native
* Flutter
* Kotlin
* Swift
* Expo

## AI 工作流

* UI 生成
* 调试
* 部署
* 测试

---

# 22 — AI 智能体

## 主题

* 自主智能体
* 工具调用
* 多智能体系统
* 工作流
* 记忆系统
* MCP
* 编排

---

# 23 — RAG 与向量数据库

## 主题

* 嵌入
* 分块
* 检索
* 向量搜索
* 混合搜索
* 重排序
* 语义搜索

---

# 24 — 自动化

## 主题

* GitHub Actions
* CI/CD
* 脚本
* AI 自动化
* 工作流编排
* 无代码自动化

---

# 25 — 速查表

包括快速参考。

## 示例

* Git 命令
* Docker 命令
* Kubernetes 命令
* 提示速查表
* Linux 命令
* 正则表达式速查表

---

# 26 — 精选提示词

极具价值的章节。

## 分类

* 前端提示词
* 后端提示词
* 调试提示词
* DevOps 提示词
* 架构提示词
* 优化提示词
* 安全提示词
* UI 提示词

---

# 27 — 案例研究

分析真实系统。

## 示例

* Netflix 架构
* Vercel 架构
* GitHub 扩展
* Cloudflare 边缘网络
* Kubernetes 生态

---

# 28 — 失败模式

讲授不该做什么。

## 示例

* 盲目信任 AI
* 过度工程化
* 忽视测试
* 跳过安全
* 超大提示词
* 没有架构规划
* 糟糕的 Git 实践

---

# 29 — 面试准备

## 主题

* 前端面试
* 后端面试
* DevOps 面试
* AI 工程面试
* 系统设计面试

---

# 推荐技术栈

## 前端

* React
* Next.js
* TypeScript
* Tailwind
* Shadcn

## 后端

* Node.js
* FastAPI
* Go

## 数据库

* PostgreSQL
* Redis

## 部署

* Docker
* Railway
* Hetzner
* Vercel

## AI

* Ollama
* Open WebUI
* Claude
* DeepSeek
* Continue

---

# 文档风格

使用：

* 图解
* 截图
* 架构可视化
* 终端示例
* 入门讲解
* 进阶深入
* 表格
* 对比图表
* 项目演练

---

# 添加视觉素材

放在 `/assets` 内

包括：

* 架构图
* 工作流图
* 截图
* AI 工作流图片
* 提示流可视化
* 部署图

---

# 贡献指南

允许社区贡献。

## 添加

* Issue 模板
* PR 模板
* 贡献规则
* Markdown 标准
* 文件夹标准

---

# 最佳实践

## 重要理念

教导用户：

* AI 是助手
* 基础知识很重要
* 调试很重要
* 架构很重要
* 安全很重要
* 部署很重要
* 测试很重要

---

# 仓库的最终目标

学完本仓库后，学习者应当了解：

* 如何用 AI 构建软件
* 如何调试 AI 生成的代码
* 如何部署项目
* 如何扩展系统
* 如何使用云/DevOps
* 如何使用本地 AI 模型
* 如何创建生产就绪的应用
* 如何成为一名 AI 原生工程师

---

# 建议的未来扩展

未来新增内容：

* AI 生成的架构图
* YouTube 教程
* 交互式示例
* 入门模板
* 样板代码
* CLI 工具
* AI 智能体
* Kubernetes 部署示例
* SaaS 模板
* 本地 AI 实验室

---
