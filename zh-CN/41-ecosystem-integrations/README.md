[English 原文](../../41-ecosystem-integrations/README.md)

# 🔌 41 - 生态系统集成

> **没有智能体是孤立工作的。** 氛围编程（Vibe Coding）生态系统通过 MCP 等标准、模板库和共享的智能体配置，把智能体与工具、数据和服务连接起来。本节介绍如何接入生态系统并为其做贡献。
> **明智地集成。分享你构建的东西。**

**难度：** 🟡 中级 · **阅读时间：** 约 12 分钟

---

## 📖 目录

- [什么是氛围编程生态系统](#-what-is-the-vibe-coding-ecosystem)
- [MCP——模型上下文协议](#-mcp---model-context-protocol)
- [MCP 服务器市场](#-mcp-server-marketplace)
- [智能体模板库](#-agent-template-gallery)
- [共享智能体配置](#-sharing-agent-configurations)
- [构建你自己的 MCP 服务器](#-building-your-own-mcp-server)
- [生态系统安全](#-ecosystem-security)
- [实践清单](#-practical-checklist)
- [要点总结](#-key-takeaways)
- [下一步](#-next-steps)

---

## 🎯 什么是氛围编程生态系统

生态系统是智能体周围让它变得有用的所有东西：

- **MCP 服务器**——为智能体提供工具和数据访问（文件系统、数据库、网络搜索、GitHub）
- **智能体模板**——针对常见任务的预配置智能体设置
- **AGENTS.md / CLAUDE.md**——共享的项目指令
- **Skills 与 hooks**——可复用的能力与生命周期自动化
- **注册中心与市场**——发现和发布集成的地方

2026 年，MCP 已成为把智能体连接到外部工具的主导标准。如果你正在构建 AI 辅助工作流，理解 MCP 至关重要。

---

## 🔌 MCP——模型上下文协议

**MCP（Model Context Protocol，模型上下文协议）** 是一项开放标准，让智能体能够一致地连接工具和数据源。MCP 提供通用接口，而不是让每个智能体各自发明集成方式：

```
Agent ←→ MCP Client ←→ MCP Server ←→ Tool/Data Source
```

### MCP 服务器能给智能体带来什么

| 服务器类型 | 示例用途 | 智能体能做什么 |
|-------------|-------------|----------------------|
| 文件系统 | 本地项目文件 | 读取、写入、搜索文件 |
| 数据库 | PostgreSQL、MongoDB | 查询表结构、读取数据 |
| GitHub | Issue、PR、仓库 | 创建 PR、评论、评审 |
| 网络搜索 | 最新文档、Stack Overflow | 查找最新信息 |
| Slack/邮件 | 团队沟通 | 发送消息、阅读会话 |
| Kubernetes | 集群管理 | 部署、检查 Pod、回滚 |

### MCP 为什么重要

- **互操作性**——一个 MCP 服务器可与 Claude Code、Cursor、Codex、Antigravity、Cline 以及其他兼容 MCP 的智能体配合使用
- **安全边界**——服务器控制智能体能访问什么；你只需配置一次权限
- **可发现性**——服务器会公布自身能力，因此智能体知道有哪些工具可用

---

## 🏪 MCP 服务器市场

有多个注册中心收录 MCP 服务器。选择服务器时：

| 考量因素 | 检查内容 |
|---------------|---------------|
| 发布者可信度 | 服务器是否来自已知、可靠的来源？ |
| 代码评审 | 安装前能否阅读服务器源码？ |
| 权限 | 它能访问哪些文件、数据库或网络？ |
| 维护情况 | 是否在积极更新？Open issue 是否有人回应？ |
| 许可证 | 能否在你的项目中使用（商业或非商业）？ |

**热门 MCP 服务器类别：**
- 官方服务器（文件系统、GitHub、Postgres、memory）
- 社区服务器（Slack、Notion、Linear、Jira、Docker、Kubernetes）
- 厂商服务器（云厂商集成）

**在哪里找服务器：**
- `modelcontextprotocol.io`——官方 MCP 服务器注册中心
- GitHub——搜索 `mcp-server` 查找社区服务器
- 智能体专属目录（Cursor、Claude Code 等）

---

## 📦 智能体模板库

智能体模板是针对常见氛围编程任务的预配置设置。它们让你不必从零开始：

| 模板类型 | 使用场景 | 包含内容 |
|---------------|----------|-----------------|
| 全栈 Web | Next.js + Supabase 应用 | `AGENTS.md`、Dockerfile、CI/CD、测试 |
| API 服务 | FastAPI/Express 后端 | 路由脚手架、认证、OpenAPI 文档 |
| 数据管道 | Python ETL | 抽取、转换、加载脚本 |
| 内部工具 | 管理后台 | CRUD 界面、认证、审计日志 |
| CLI 工具 | 命令行工具 | 参数解析、输出格式化 |

**在哪里找模板：**
- 入门套件仓库（第 35 节）
- 智能体模板市场（2026 年正在兴起）
- 你所在组织的模板库

**使用模板：**
1. 从模板克隆或生成
2. 评审 `AGENTS.md` 并按你的项目定制
3. 运行安装脚本（安装依赖、配置环境变量）
4. 用针对智能体的指令开始提示

---

## 🔧 共享智能体配置

让你的智能体设置可以在项目和团队之间复用：

### 要共享的文件

| 文件 | 用途 | 何时共享 |
|------|---------|---------------|
| `AGENTS.md` | 跨工具的项目指令 | 每个项目 |
| `CLAUDE.md` | Claude Code 专属指令 | Claude Code 项目 |
| `.cursor/rules/` | Cursor 智能体规则 | Cursor 项目 |
| `.github/copilot-instructions.md` | GitHub Copilot 指令 | GitHub Copilot 项目 |
| `.mcp.json` | MCP 服务器配置 | 使用 MCP 的项目 |
| `.kiro/steering/` | Kiro 引导文件 | Kiro 项目 |

### 共享的 `.mcp.json` 示例

```json
{
  "servers": {
    "filesystem": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-filesystem", "/path/to/project"]
    },
    "github": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-github"],
      "env": {
        "GITHUB_TOKEN": "${GITHUB_TOKEN}"
      }
    },
    "postgres": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-postgres"],
      "env": {
        "POSTGRES_CONNECTION_STRING": "${DATABASE_URL}"
      }
    }
  }
}
```

**最佳实践：** 把 `AGENTS.md` 和工具专属规则提交到仓库。MCP 服务器配置也可以放进版本控制，但**绝不要提交 token 或密钥**——使用环境变量引用。

---

## 🛠️ 构建你自己的 MCP 服务器

如果现有的 MCP 服务器都不符合需求，可以自己构建一个：

### 基础 MCP 服务器结构

```typescript
// Example: simple file-watcher MCP server
import { Server } from '@modelcontextprotocol/sdk/server/index.js';
import { StdioServerTransport } from '@modelcontextprotocol/sdk/server/stdio.js';
import { CallToolRequestSchema, ListToolsRequestSchema } from '@modelcontextprotocol/sdk/types.js';

const server = new Server(
  { name: 'example-server', version: '1.0.0' },
  { capabilities: { tools: {} } }
);

server.setRequestHandler(ListToolsRequestSchema, async () => ({
  tools: [{
    name: 'read_file',
    description: 'Read a file from the project',
    inputSchema: {
      type: 'object',
      properties: { path: { type: 'string' } },
      required: ['path']
    }
  }]
}));

server.setRequestHandler(CallToolRequestSchema, async (request) => {
  if (request.params.name === 'read_file') {
    const fs = await import('fs/promises');
    const content = await fs.readFile(request.params.arguments.path, 'utf-8');
    return { content: [{ type: 'text', text: content }] };
  }
  throw new Error('Unknown tool');
});

const transport = new StdioServerTransport();
await server.connect(transport);
```

### 发布之前

- [ ] 评审代码中的安全问题
- [ ] 为所有工具及其参数编写文档
- [ ] 添加权限要求（服务器访问什么）
- [ ] 附上智能体使用的示例
- [ ] 建立 issue 跟踪与维护机制
- [ ] 选择合适的开源许可证

---

## 🛡️ 生态系统安全

你添加的每个集成都是一个新的攻击面：

| 风险 | 缓解措施 |
|------|------------|
| 恶意 MCP 服务器外泄代码 | 只从受信任的发布者安装；评审源码 |
| 权限过大的服务器 | 只授予所需的最小访问权限 |
| 藏有后门的模板 | 使用前评审模板代码 |
| 内嵌密钥的共享 `AGENTS.md` | 绝不提交密钥；使用环境变量引用 |
| 存在漏洞的无人维护服务器 | 检查最后更新日期；优先选择积极维护的 |

**把每个 MCP 服务器和模板都当作以你的权限运行的不受信任代码。**

---

## ✅ 实践清单

- [ ] 已明确项目需要哪些 MCP 服务器
- [ ] 安装前已评审 MCP 服务器源码
- [ ] 已按最小权限配置 MCP 服务器
- [ ] 已把 `AGENTS.md` 和工具规则提交到仓库
- [ ] 从未把密钥提交到 MCP 配置或模板中
- [ ] 已找到 MCP 服务器市场并收藏
- [ ] 采用前已评估智能体模板
- [ ] 已考虑为内部工具构建 MCP 服务器
- [ ] 已在项目文档中记录生态系统集成

---

## 🔑 要点总结

- **MCP 是标准**，用于把智能体连接到工具和数据
- **市场帮助你发现**服务器和模板
- **分享你的配置**——`AGENTS.md`、规则文件、MCP 配置
- **现有方案不合适时，构建你自己的 MCP 服务器**
- **安全第一**——评审服务器、限制权限、绝不提交密钥
- **生态系统靠贡献成长**——发布你构建的东西

---

## 🚀 下一步

- **浏览 MCP 服务器市场**，为你的技术栈安装一个
- **如果还没有，给当前项目添加 `AGENTS.md`**
- **向社区贡献一个模板或 MCP 服务器**
- **阅读第 40 节**（社区讨论），了解生态系统讨论在哪里进行

---

<center>

*最后更新：2026 年 11 月*

</center>
