[English 原文](../../08-frontend/README.md)

# 用 AI 做前端开发

## 简介
随着 AI 辅助编码的出现，前端开发经历了彻底的变革。曾经需要深入掌握 CSS 细节、JavaScript 框架和响应式设计模式的工作，如今可以通过自然语言提示来加速。本节介绍如何利用 AI 构建现代、响应式且无障碍的用户界面。

## AI 驱动的前端工作流

### 1. 组件生成
AI 擅长为 UI 组件生成样板代码。你无需手动编写 HTML 结构和 CSS 类，只需描述组件的用途和外观。

**提示策略：**
> "Create a responsive navigation bar using Tailwind CSS. It should have a logo on the left, links in the center, and a 'Sign In' button on the right. On mobile, it should collapse into a hamburger menu."

**最佳实践：**
- 指明框架（React、Vue、Svelte）和样式库（Tailwind、Bootstrap、Styled Components）。
- 定义状态需求（例如“当前链接高亮”“下拉切换”）。
- 明确要求无障碍功能（ARIA 标签、键盘导航）。

### 2. 样式与设计系统
AI 可以通过生成符合特定设计系统的样式，帮助你在整个应用中保持一致性。

**使用场景：**
- **主题转换：** "Convert this light mode color palette to a dark mode equivalent while maintaining contrast ratios."
- **CSS 优化：** "Refactor this CSS to use CSS variables for colors and spacing to make it themeable."
- **Tailwind 工具类生成：** "Generate the Tailwind classes for a card component with a shadow-lg, rounded-xl, and hover:scale-105 effect."

### 3. 状态管理
在复杂的前端应用中管理状态可能非常冗长。AI 可以根据简单的描述生成 Redux 切片、Zustand store 或 Context provider。

**示例提示词：**
> "Create a Zustand store for a shopping cart. It needs actions for addItem, removeItem, updateQuantity, and clearCart. The state should persist to localStorage."

## 框架专属指南

### React 与 Next.js
React 仍然是主流库，AI 工具针对它做了大量优化。
- **Hook 生成：** 让 AI 创建用于数据获取、表单处理或本地存储同步的自定义 Hook。
- **服务端组件：** 提示 AI 给出从客户端组件迁移到 Next.js 13+ 服务端组件的策略。
- **性能：** 在适当的地方要求实现 `React.memo`、`useMemo` 和 `useCallback`，以防止不必要的重渲染。

### Vue 与 Nuxt
- **组合式 API：** AI 可以轻松地把选项式 API 代码翻译成组合式 API（`setup` 脚本）。
- **响应式：** 根据数据需求生成响应式状态对象和计算属性。

### Svelte 与 SvelteKit
- **简洁：** Svelte 的语法简洁，非常适合 AI 生成。与 React 相比，提示词往往能得到更干净、样板代码更少的产出。
- **Store：** 生成用于全局状态管理的可写 store 和派生 store。

## 响应式设计与无障碍

### 移动优先
AI 可以自动生成媒体查询和灵活的网格布局。
- **提示词：** "Create a grid layout that shows 1 column on mobile, 2 on tablets, and 4 on desktops. Use CSS Grid."

### 无障碍（a11y）
不要默认 AI 生成的代码就是无障碍的，一定要主动提示。
- **检查清单提示词：**
  - "Add ARIA labels to all buttons without text content."
  - "Ensure color contrast ratios meet WCAG AA standards."
  - "Implement keyboard navigation for this custom dropdown."
  - "Add skip-to-content links for screen readers."

## 集成设计工具
- **Figma 转代码：** 使用 AI 插件，或用文字描述 Figma 设计来生成对应的代码。
- **截图转代码：** 先进的多模态模型可以分析网站截图，并生成用于复现的 HTML/CSS 结构。

## 常见陷阱与解决方案

### 1. 过度设计
AI 有时会为简单问题给出复杂的解决方案。
- **解决办法：** 在提示词中加上约束：“保持方案简单，避免外部库，尽可能使用原生 JS。”

### 2. 凭空编造的类名/属性
AI 可能会为某个库编造不存在的属性，或使用过时的语法。
- **解决办法：** 始终对照你所用库版本的官方文档核对生成的代码。

### 3. 性能臃肿
生成的代码可能包含不必要的重渲染或过大的包体积。
- **解决办法：** 让 AI“针对性能优化”，并检查输出中渲染循环里是否有重型计算。

## 必备工具与扩展
- **v0.dev：** Vercel 的生成式 UI 工具，可即时生成 React/Tailwind 组件。
- **Locofy：** 把 Figma 设计转换为前端代码。
- **Cursor/VS Code Copilot：** 用于行内补全和重构。
- **Shadcn/UI：** AI 与 Shadcn 的复制粘贴式组件架构配合得非常好。

## 实践练习
1. **构建落地页：** 提示 AI 生成包含 Hero、功能、用户评价和页脚区块的完整落地页。
2. **创建仪表盘：** 创建一个带侧边栏、顶部导航和数据可视化占位的管理后台布局。
3. **表单校验：** 使用 Zod 和 React Hook Form 实现一个带实时校验的复杂多步骤表单。

## 结论
AI 驱动的前端开发把重心从记忆语法转移到了架构思考和设计打磨上。掌握面向 UI 生成的提示工程后，开发者可以更快地做原型、保持更高的一致性，并把更多精力放在用户体验和交互逻辑上。
