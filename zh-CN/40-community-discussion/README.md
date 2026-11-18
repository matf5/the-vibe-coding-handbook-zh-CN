[English 原文](../../40-community-discussion/README.md)

# 🤝 40 - 社区讨论与贡献工具

> **手册由社区驱动，但社区需要讨论的地方和协作的工具。** 本节介绍如何与其他构建者讨论氛围编程（Vibe Coding）、为手册做贡献，以及使用让项目保持健康的贡献工具。
> **加入讨论。改进手册。帮助他人学习。**

**难度：** 🟢 初学者 · **阅读时间：** 约 10 分钟

---

## 📖 目录

- [在哪里讨论氛围编程](#-where-to-discuss-vibe-coding)
- [社区规范与礼仪](#-community-norms--etiquette)
- [如何为手册做贡献](#-how-to-contribute-to-the-handbook)
- [贡献工具](#-contribution-tooling)
- [案例研究投稿](#-case-study-contributions)
- [视频教程投稿](#-video-tutorial-contributions)
- [评审与合并流程](#-review--merge-process)
- [致谢与徽章](#-recognition--badges)
- [实践清单](#-practical-checklist)
- [要点总结](#-key-takeaways)
- [下一步](#-next-steps)

---

## 💬 在哪里讨论氛围编程

手册社区聚集在几个地方。选择适合你风格的那一个：

| 平台 | 最适合 | 加入方式 |
|----------|----------|-------------|
| **GitHub Discussions** | 手册问题、功能请求、元讨论 | `github.com/hacrex/the-vibe-coding-handbook/discussions` |
| **GitHub Issues** | Bug 报告、错别字、内容缺口 | `github.com/hacrex/the-vibe-coding-handbook/issues` |
| **Discord** | 实时聊天、快速提问、结对编程 | 手册 README 中的链接（即将推出） |
| **Twitter/X** | 公开构建、分享项目、#vibecoding | 带 #vibecoding 发帖并 @ 手册 |
| **Reddit** | r/cursor_ai、r/vibecoding、r/LocalLLaMA | 工具专属社区 |

**提示：** 发帖前先搜索。关于模型、工具和报错信息的许多问题已经有人回答过。

---

## 🤝 社区规范与礼仪

氛围编程同时吸引初学者和专家。请保持讨论友好：

- **先假设对方是善意的**——每个人都在学习
- **不因使用 AI 而羞辱他人**——手册拥抱 AI 辅助开发
- **聚焦安全与评审**——温和地引导他人走向测试与安全
- **分享失败，而不只是成功**——一次失败的部署比一次完美的部署更能教会人
- **分享前先匿名化**——从截图和代码中删除公司名称、URL 和凭证
- **注明来源**——如果某个技巧是从别人那里学到的，请提及他们

---

## 📝 如何为手册做贡献

手册位于 `github.com/hacrex/the-vibe-coding-handbook`。欢迎各种规模的贡献。

### 贡献类型

| 类型 | 工作量 | 适合 |
|------|--------|----------|
| **错别字修复** | 5 分钟 | 新贡献者 |
| **内容更新** | 30 分钟 | 让各节保持最新 |
| **新案例研究** | 1–2 小时 | 分享真实经验 |
| **视频演示** | 2–4 小时 | 通过演示教学 |
| **新章节** | 4+ 小时 | 扩大覆盖范围 |
| **工具改进** | 不定 | 脚本、Lint、CI |

### 贡献工作流

1. **Fork 仓库**——创建你自己的副本
2. **创建分支**——`git checkout -b your-description`
3. **做出修改**——编辑 Markdown、添加文件
4. **本地测试**——构建网站（`node site/build.js`）并检查链接
5. **发起 Pull Request**——说明改了什么、为什么改
6. **处理评审反馈**——维护者可能要求修改
7. **合并**——获批后，你的贡献即上线

---

## 🛠️ 贡献工具

手册使用轻量工具，让贡献保持一致：

### 构建脚本（`site/build.js`）

根据 `README.md`、`ROADMAP.md` 和 `glossary/terms.md` 重新生成 `site/data.js`：

```bash
node site/build.js
```

在提交改变章节结构或新增章节的 PR 之前，先运行它。

### Markdown 风格指南

- **H1 格式：** `# 📖 38 - Section Title`（emoji + 编号 + 标题）
- **引言：** H1 下的一行引用
- **难度徽章：** `**Difficulty:** 🟢 Beginner · **Reading time:** ~X minutes`
- **目录：** `## 📖 Table of Contents`，带锚点链接
- **表格：** 使用竖线加表头分隔行
- **Emoji：** 适度使用，用于章节标题和状态徽章
- **最后更新：** H1 下的 `*Last updated: November 2026*`

### 链接检查

发起 PR 之前，请验证：
- 所有内部链接都能解析（章节之间、手册到章节）
- 外部链接没有损坏
- 图片能正常渲染（如果有）

### 提交信息规范

```
type: description

Examples:
- docs: update model table to November 2026 landscape
- feat: add section 34 community case studies
- fix: correct broken link in section 06 IDEs
- chore: regenerate site data.js
```

---

## 📋 案例研究投稿

案例研究是最受重视的社区内容（第 34 节）。投稿方式：

1. **Fork 仓库**
2. **创建文件**，路径为 `27-case-studies/contributions/your-story.md`
3. **使用第 34 节的案例研究模板**
4. **匿名化**——删除公司名称、URL、凭证
5. **提交 PR**，打上 `case-study` 标签

投稿在合并前会经过质量、匿名性和实用性评审。

---

## 🎥 视频教程投稿

欢迎视频演示投稿（第 39 节）。投稿方式：

1. **录制屏幕**，记录你用 AI 构建的过程
2. **讲解决策**——提示词、接受、拒绝、修复
3. **展示评审**——测试、安全扫描、部署
4. **托管在 YouTube/Vimeo**
5. **向 `39-video-tutorials/` 提交 PR**，附上链接和摘要

---

## 🔍 评审与合并流程

每个 PR 都会经过维护者评审：

1. **自动化检查**——运行构建脚本、验证链接
2. **维护者评审**——内容准确性、风格、安全性
3. **社区反馈**——在 PR 上公开讨论
4. **合并或要求修改**——由维护者决定
5. **部署**——合并的变更会构建并部署到网站

**评审周期：** 大多数 PR 会在 3–5 个工作日内收到初步反馈。

---

## 🏅 致谢与徽章

贡献者会在以下地方得到致谢：

- **README 致谢**——列出主要贡献者
- **贡献徽章**——如果你添加，可显示在你的个人主页上
- **案例研究署名**——你提交的故事上会署你的名字（或 handle）
- **认证名册**——如果你完成了第 37 节的级别

在你的 GitHub 个人主页上添加贡献徽章：

```markdown
![Vibe Coding Handbook Contributor](https://img.shields.io/badge/Vibe%20Coding-Contributor-blue)
```

---

## ✅ 实践清单

- [ ] 加入了至少一个社区渠道（GitHub Discussions、Discord 或 Reddit）
- [ ] 阅读了贡献工作流和风格指南
- [ ] 至少做过一次小贡献（错别字修复、链接更新或评论）
- [ ] 提交 PR 之前在本地运行了 `node site/build.js`
- [ ] 提交了案例研究或视频演示（可选，但鼓励）
- [ ] 评审过至少一位其他贡献者的 PR（将善意传递下去）

---

## 🔑 要点总结

- **手册由社区驱动**——你的贡献塑造了它
- **多个讨论渠道**——选择适合你风格的那一个
- **小贡献也很重要**——错别字、链接和建议都有帮助
- **先构建再提交 PR**——运行 `node site/build.js` 验证
- **分享失败与成功**——两者都能教会社区
- **评审他人的工作**——项目就是这样保持健康的

---

## 🚀 下一步

- **打开 GitHub Discussions**，介绍你自己
- **修复一个错别字或损坏的链接**，作为你的第一次贡献
- **提交一篇案例研究**，讲讲你自己的 AI 构建项目
- **阅读第 41 节**（生态系统集成），了解手册如何与更广泛的 AI 工具生态连接

---

<center>

*最后更新：2026 年 11 月*

</center>
