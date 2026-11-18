# 🤝 贡献指南

感谢你为 **氛围编程：从零到精通（Vibe Coding: Zero to Hero）** 做贡献！本指南将帮助你为这个社区驱动的知识库做出有效的贡献。

---

## 📖 目录

- [行为准则](#-code-of-conduct)
- [我能如何贡献？](#-how-can-i-contribute)
- [开始上手](#-getting-started)
- [Markdown 标准](#-markdown-standards)
- [内容指南](#-content-guidelines)
- [Pull Request 流程](#-pull-request-process)
- [Issue 报告](#-issue-reporting)
- [有疑问？](#-questions)

---

## 🎯 行为准则

请在所有互动中保持尊重与包容。我们欢迎各种背景和经验水平的贡献者。

**期望的行为：**
- 使用热情友好的包容性语言
- 尊重不同的观点
- 优雅地接受建设性批评
- 以社区的最佳利益为重

**不可接受的行为：**
- 骚扰或歧视
- 挑衅或侮辱性言论
- 公布他人的私人信息

---

## 👐 我能如何贡献？

### 1. 📝 撰写内容

为任意章节添加指南、教程或示例：
- 扩展现有主题
- 添加缺失的章节
- 创建代码示例
- 撰写案例研究

### 2. 🎨 制作视觉素材

让内容更易理解：
- 架构图
- 工作流图表
- 带标注的截图
- 信息图

### 3. 🐛 报告问题

发现问题？请告诉我们：
- 拼写错误和语法错误
- 不正确或过时的信息
- 失效链接
- 缺失的上下文

### 4. 🔍 审阅与编辑

改进现有内容：
- 澄清令人困惑的解释
- 更新过时的信息
- 补充缺失的示例
- 改进格式

### 5. 💡 建议主题

有新内容的想法？
- 提交一个 Issue 说明你的建议
- 提供大纲
- 自愿撰写（可选）

---

## 🚀 开始上手

### 第 1 步：Fork 仓库

```bash
# 在 GitHub 上点击 "Fork"，然后克隆你的 fork
git clone https://github.com/YOUR_USERNAME/vibe-coding-zero-to-hero.git
cd vibe-coding-zero-to-hero
```

### 第 2 步：创建分支

```bash
# 为你的改动创建一个分支
git checkout -b feature/add-your-content-name
```

### 第 3 步：进行改动

按照下方的标准编辑现有文件或创建新文件。

### 第 4 步：本地测试

预览你的 Markdown：
- 在 VS Code 中使用 Markdown 预览扩展
- 检查链接是否有效
- 验证代码块渲染是否正确

### 第 5 步：提交改动

```bash
# 暂存你的改动
git add .

# 用清晰的信息提交
git commit -m "docs: add guide to prompt engineering templates"
```

### 第 6 步：推送并创建 PR

```bash
# 推送到你的 fork
git push origin feature/add-your-content-name

# 然后在 GitHub 上提交一个 Pull Request
```

---

## 📐 Markdown 标准

### 文件结构

每个章节都应当有一个结构如下的 `README.md`：

```markdown
# Section Title

Brief introduction (2-3 sentences).

---

## 📖 Table of Contents

- [Subsection 1](#-subsection-1)
- [Subsection 2](#-subsection-2)

---

## 🎯 Subsection 1

Content here...

---

## Next Steps

Links to related sections.
```

### 格式规则

#### 标题

使用 emoji + 描述性标题：

```markdown
## 🎯 Main Section
### 📋 Subsection
#### ✅ Details
```

#### 代码块

务必注明语言：

````markdown
```javascript
// Good example
const greeting = "Hello, Vibe Coder!";
```

```bash
# Command line examples
npm install package-name
```
````

#### 表格

使用表格进行对比：

```markdown
| Tool | Best For | Pricing |
|------|----------|---------|
| Cursor | Full AI integration | $20/mo |
| VS Code | Flexibility | Free |
```

#### 链接

内部引用使用相对链接：

```markdown
[Previous Section](../06-ides-editors/)
[Next Section](../08-frontend/)
```

#### 图片

将图片放在 `/assets` 文件夹中：

```markdown
![Description](../assets/section-name/image-name.png)
```

---

## ✍️ 内容指南

### 写作风格

✅ **要做到：**
- 用清晰、简单的英语写作
- 使用主动语态
- 包含实际示例
- 解释原因（_why_），而不只是讲是什么（_what_）
- 链接到相关章节
- 添加对新手友好的解释

❌ **不要：**
- 不加解释地使用过于专业的技术术语
- 假定读者已有相关知识
- 写大段文字（要用标题！）
- 留下拼写错误或语法错误
- 从其他来源复制粘贴

### 内容质量检查清单

提交前请核对：

- [ ] 信息准确且最新
- [ ] 代码示例按预期运行
- [ ] 所有链接均有效
- [ ] 标题遵循 emoji 格式
- [ ] 内容为原创（无抄袭）
- [ ] 解释对新手友好
- [ ] 无拼写/语法错误
- [ ] 外部资源已恰当注明来源

### 示例质量等级

**🟢 优秀：**
- 结构清晰，带有目录
- 多个实际示例
- 在有帮助的地方配图
- 链接到资源
- 指出常见陷阱

**🟡 良好：**
- 解释清晰
- 至少有一个示例
- 格式正确
- 没有错误

**🔴 需要改进：**
- 不清晰或含糊
- 没有示例
- 格式差
- 包含错误

---

## 🔄 Pull Request 流程

### 提交前

1. 通读本指南
2. 检查是否存在类似的 PR
3. 确保你的分支是最新的
4. 在本地预览你的改动

### PR 标题格式

使用约定式提交（conventional commits）风格：

```
docs: add prompt engineering templates
feat: new offline AI setup guide
fix: correct Docker installation steps
chore: reorganize section structure
```

### PR 描述

使用我们的模板，并包括：
- 你改了什么
- 为什么需要改
- 影响了哪些章节
- 任何相关的 Issue

### 审阅时间

- 维护者将在 3–5 天内审阅
- 你可能被要求修改
- 通过后，你的 PR 将被合并

### 合并后

- 你的贡献将成为项目的一部分
- 你会被列为贡献者
- 欢迎提交更多 PR！

---

## 🐛 Issue 报告

### 提交 Issue 前

1. 搜索已有的 Issue（避免重复）
2. 检查问题是否已在 main 分支中修复
3. 收集相关信息

### Issue 模板

我们提供以下模板：
- 🐛 Bug 报告
- 🚀 功能请求
- 📝 内容补充

选择合适的模板并完整填写。

### 好的 Issue 标题

✅ "Fix broken link in prompt-engineering section"
✅ "Add guide for local LLM setup with Ollama"
✅ "Update React section to include React 19 features"

❌ "Something's wrong"
❌ "Add more stuff"
❌ "Help!"

---

## ❓ 有疑问？

### 在哪里提问

- **一般问题**：提交一个 [Discussion](../../discussions)
- **与贡献相关的问题**：在相关的 Issue/PR 下留言
- **紧急事项**：直接联系维护者

### 资源

- [README.md](../../README.zh-CN.md) - 项目概览
- [Blueprint.md](Blueprint.md) - 愿景与结构
- [ROADMAP.md](ROADMAP.md) - 开发时间线

---

## 🏆 致谢

贡献者会在以下位置得到认可：
- README.md 的贡献者部分
- GitHub Contributors 页面
- 发布说明（针对重大贡献）

**感谢你让 Vibe Coding 变得更好，惠及每一个人！** 🙏

---

<div align="center">

**准备好贡献了吗？**

[Fork the Repo](https://github.com/yourusername/vibe-coding-zero-to-hero/fork) · [View Open Issues](../../issues) · [阅读蓝图](Blueprint.md)

</div>
