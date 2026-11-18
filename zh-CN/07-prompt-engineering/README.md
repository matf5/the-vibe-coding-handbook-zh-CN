[English 原文](../../07-prompt-engineering/README.md)

# 07 软件开发提示工程

掌握与 AI 沟通的艺术，更快地构建更好的软件。本节讲授专门针对编码、调试、架构和部署的提示技巧。

---

## 📖 目录

- [为什么提示工程重要](#-why-prompt-engineering-matters)
- [核心提示原则](#-core-prompting-principles)
- [按类别划分的提示词类型](#-prompt-types-by-category)
- [可复用的提示词模板](#-reusable-prompt-templates)
- [高级技巧](#-advanced-techniques)
- [常见错误](#-common-mistakes)
- [练习](#-practice-exercises)

---

## 🎯 为什么提示工程重要

好的提示词 = 更好的代码 = 更快的开发

| 糟糕的提示词 | 好的提示词 |
|------------|-------------|
| "Build a login system" | "Build a secure JWT authentication system with Express.js, bcrypt password hashing, rate limiting, and PostgreSQL storage" |
| "Fix this error" | "Analyze this stack trace, identify the root cause, and provide 3 possible solutions with pros/cons" |
| "Make it faster" | "Optimize this database query for 10K+ records. Add indexing strategy and explain the performance improvement" |

---

## 🧠 核心提示原则

### 1. 具体而详细

❌ **含糊：**
```
Create an API
```

✅ **具体：**
```
Create a RESTful API with Node.js and Express that:
- Handles user registration and login
- Uses JWT for authentication
- Validates input with Joi schema
- Returns proper HTTP status codes
- Includes error handling middleware
- Has rate limiting (100 requests/hour)
```

### 2. 提供上下文

始终包含：
- 你使用的**技术栈**
- 项目的**当前状态**
- **约束条件**（时间、预算、性能）
- **目标**（成功的样子）

示例：
```
Context: Building a SaaS dashboard for small businesses
Stack: Next.js 14, TypeScript, TailwindCSS, Supabase
Goal: Create a responsive analytics dashboard
Constraint: Must load in under 2 seconds
```

### 3. 使用角色提示

给 AI 指定一个具体角色：

```
You are a senior backend engineer with 10 years of experience 
in building scalable microservices. Review this architecture 
and identify potential bottlenecks.
```

```
You are a security expert specializing in web application 
security. Audit this code for OWASP Top 10 vulnerabilities.
```

### 4. 迭代与优化

第一次提示 → 得到输出 → 优化 → 得到更好的输出

```
Initial: "Create a React component for a button"

Refinement: "Make it accessible with ARIA labels"

Further: "Add loading state and disabled state variants"

Final: "Convert to TypeScript with proper prop types"
```

### 5. 要求解释

不要只接受代码——要理解它：

```
Explain this code line by line like I'm a junior developer.
What are the potential edge cases?
How would you test this?
```

---

## 📋 按类别划分的提示词类型

### 架构提示词

设计系统时使用：

```
Design a scalable architecture for a food delivery app with:
- Real-time order tracking
- Payment processing
- Driver dispatch system
- Customer notifications

Include:
- System components diagram
- Database schema
- API endpoints
- Caching strategy
- Scaling considerations
```

### 前端提示词

用于 UI/组件开发：

```
Build a responsive navigation component with:
- Mobile hamburger menu
- Dropdown submenus
- Active state highlighting
- Keyboard navigation
- WCAG 2.1 AA accessibility

Tech: React, TypeScript, TailwindCSS, Framer Motion
```

### 后端提示词

用于 API/服务端开发：

```
Create a production-ready Express.js API endpoint for file uploads:
- Accept multipart/form-data
- Validate file type (images only)
- Limit size to 5MB
- Store in S3 with CloudFront
- Generate thumbnails
- Return CDN URL

Include error handling and logging.
```

### 调试提示词

出问题时使用：

```
I'm getting this error: [paste error]

Here's my code: [paste code]

Here's what I've tried:
1. Cleared node_modules
2. Checked environment variables
3. Verified database connection

Please:
1. Identify the root cause
2. Explain why it's happening
3. Provide step-by-step fix
4. Suggest how to prevent this in future
```

### 优化提示词

用于提升性能：

```
Profile and optimize this React component:
[paste code]

Current issues:
- Slow re-renders
- Large bundle size
- Poor Lighthouse score

Suggest:
- Memoization strategies
- Code splitting approach
- Performance improvements
- Before/after metrics
```

### 安全提示词

用于安全审查：

```
Audit this authentication flow for security vulnerabilities:
[paste code]

Check for:
- Password storage
- Session management
- CSRF protection
- XSS prevention
- Rate limiting
- Token security

Provide severity ratings and fixes.
```

### 测试提示词

用于生成测试：

```
Write comprehensive tests for this function:
[paste code]

Include:
- Unit tests with Jest
- Edge cases
- Error scenarios
- Integration test example
- Mock external dependencies

Target 90%+ code coverage.
```

### 文档提示词

用于编写文档：

```
Generate documentation for this API:
[paste code/endpoints]

Format:
- Overview
- Authentication requirements
- Endpoint details with examples
- Request/response schemas
- Error codes
- Rate limits

Style: OpenAPI/Swagger compatible
```

---

## 🔧 可复用的提示词模板

复制并按需定制这些模板：

### 模板 1：新功能开发

```markdown
# Feature Request

## Context
Project: [project name/description]
Stack: [technologies used]
Current State: [what exists now]

## Requirements
Build a [feature name] that:
- [requirement 1]
- [requirement 2]
- [requirement 3]

## Constraints
- Time: [deadline]
- Performance: [requirements]
- Compatibility: [browsers/platforms]

## Deliverables
- [ ] Working code
- [ ] Tests
- [ ] Documentation
- [ ] Deployment instructions

## Success Criteria
[how you'll know it's working]
```

### 模板 2：代码审查

```markdown
# Code Review Request

## Code
[paste code or link to PR]

## What I Need
- [ ] Bug identification
- [ ] Performance analysis
- [ ] Security review
- [ ] Best practices check
- [ ] Refactoring suggestions

## Context
- Purpose: [what this code does]
- Concerns: [specific worries]
- Constraints: [limitations]

## Priority Areas
1. [most important concern]
2. [second concern]
3. [third concern]
```

### 模板 3：学习/理解

```markdown
# Learning Request

## Topic
I want to understand: [concept/technology]

## Current Level
Beginner / Intermediate / Advanced

## Learning Style
- [ ] Conceptual explanations first
- [ ] Hands-on examples first
- [ ] Compare with what I know: [familiar tech]

## Goals
After learning this, I want to: [build what?]

## Format
Please provide:
- High-level overview
- Key concepts explained simply
- Practical examples
- Common pitfalls
- Resources for deeper learning
```

### 模板 4：问题解决

```markdown
# Problem Solving

## The Problem
[describe what's broken/not working]

## Expected Behavior
[what should happen]

## Actual Behavior
[what actually happens]

## Environment
- OS: [operating system]
- Runtime: [Node version, etc.]
- Dependencies: [relevant packages]

## Steps Taken
1. [troubleshooting step 1]
2. [troubleshooting step 2]
3. [troubleshooting step 3]

## Logs/Errors
[paste relevant output]

## Hypothesis
I think the issue might be: [your theory]
```

### 模板 5：项目规划

```markdown
# Project Planning

## Project Vision
Build a [type of application] for [target users] that [value proposition]

## Features (MVP)
1. [core feature 1]
2. [core feature 2]
3. [core feature 3]

## Technical Requirements
- Stack preference: [preferred technologies]
- Must support: [scale/users/features]
- Must integrate with: [third-party services]

## Timeline
- MVP: [weeks/months]
- Full launch: [timeline]

## Deliverables Needed
- Architecture design
- Database schema
- API specification
- Component hierarchy
- Development roadmap
```

---

## 🚀 高级技巧

### 思维链提示

让 AI 一步一步思考：

```
Let's solve this problem step by step:

1. First, analyze the requirements
2. Then, identify potential challenges
3. Next, propose multiple solutions
4. Finally, recommend the best approach with justification
```

### 少样本学习

提供示例：

```
Here are examples of good commit messages:

feat(auth): add JWT token refresh endpoint
fix(api): resolve null pointer in user service
docs(readme): update installation instructions

Now write a commit message for: [your changes]
```

### 基于约束的提示

设定明确的边界：

```
Write a database migration script with these constraints:
- Must be reversible (have down() method)
- Zero downtime deployment compatible
- No table locks longer than 5 seconds
- Backwards compatible with current code
- Include rollback instructions
```

### 对比分析

要求做对比：

```
Compare these approaches for state management:
1. Redux Toolkit
2. Zustand
3. React Context + useReducer
4. Jotai

For each, provide:
- Bundle size impact
- Learning curve
- DevTools support
- TypeScript integration
- Best use cases
- When NOT to use

Then recommend one for my dashboard app with 50+ components.
```

### 迭代优化

逐步改进：

```
Round 1: "Create a basic todo app"
Round 2: "Add user authentication"
Round 3: "Implement real-time sync with WebSockets"
Round 4: "Add offline support with Service Workers"
Round 5: "Optimize for mobile with PWA features"
```

### 元提示

让 AI 帮你更好地写提示词：

```
I want to build [X] but I'm not sure how to ask.

Help me create the perfect prompt by asking me questions about:
- My requirements
- My constraints
- My technical stack
- My goals

Then generate the optimal prompt for me to use.
```

---

## ⚠️ 常见错误

### 1. 太含糊

❌ "Make a website"
✅ "Build a portfolio website with Next.js, featuring a projects gallery, blog section, and contact form"

### 2. 缺少上下文

❌ "This doesn't work, fix it"
✅ "Getting TypeError: Cannot read property 'map' of undefined in this React component when API returns empty array"

### 3. 忽视安全

❌ "Store user passwords"
✅ "Store user passwords securely using bcrypt with salt rounds, never store plain text"

### 4. 不测试

❌ 直接接受代码而不验证
✅ "Show me how to test this, including edge cases"

### 5. 盲目信任

❌ 认为 AI 代码完美无缺
✅ "Review this AI-generated code for bugs, security issues, and performance problems"

### 6. 过度复杂

❌ 500 词的提示词，事无巨细
✅ 清晰、结构化的提示词，只写关键要求

### 7. 不迭代

❌ 一次提示、一次尝试、放弃
✅ 迭代、优化、追问

---

## 💪 练习

### 练习 1：改进这些提示词

把这些提示词写得更好：

1. "Build login"
2. "My app is slow"
3. "Write tests"
4. "Deploy to server"

<details>
<summary>参考答案</summary>

1. "Build a secure login system with email/password, OAuth (Google/GitHub), 2FA option, session management, and password reset flow"
2. "My React dashboard takes 8 seconds to load with 1000 items. Profile performance, identify bottlenecks, suggest optimizations with virtual scrolling, lazy loading, and memoization"
3. "Write Jest unit tests for this payment processing function covering success, failure, edge cases, and mocking the Stripe API"
4. "Deploy this Dockerized Node.js app to AWS ECS with load balancer, auto-scaling, health checks, and CloudWatch monitoring"

</details>

### 练习 2：创建你自己的模板

根据你当前的项目，参照上面的结构创建一个自定义提示词模板。

### 练习 3：用 AI 调试

找一个你实际遇到过的 bug，参照提供的模板练习写调试提示词。

---

## 📊 提示词质量检查清单

发送提示词之前，先核对：

- [ ] **目标明确**：你想要什么？
- [ ] **上下文充分**：技术栈、当前状态、约束条件
- [ ] **要求具体**：功能、性能、安全需求
- [ ] **预期格式**：代码、解释、图表、对比？
- [ ] **提供了示例**：如适用
- [ ] **成功标准**：如何评估输出？

---

## 🔗 更多资源

- [Prompt Engineering Guide](https://www.promptingguide.ai)
- [OpenAI Prompt Best Practices](https://platform.openai.com/docs/guides/prompt-engineering)
- [Anthropic Prompting Guide](https://docs.anthropic.com/claude/docs/introduction-to-prompt-design)

---

## 下一步

1. ✅ 用上面的模板练习
2. 📖 前往 [08-frontend](../08-frontend/) 学习 React/Next.js 相关内容
3. 🔧 查看 [26-awesome-prompts](../26-awesome-prompts/) 获取更多示例
4. 🏗️ 在 [16-open-source-projects](../16-open-source-projects/) 中应用所学

---

<div align="center">

**💡 记住：** 输出的质量取决于输入的质量。花时间写好提示词！

</div>
