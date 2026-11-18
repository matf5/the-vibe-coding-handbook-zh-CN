# AI 辅助开发中的安全

*最后更新：2026 年 11 月*

## 简介
安全在软件开发中至关重要，而 AI 辅助编码既带来了机遇，也带来了挑战。AI 可以帮助发现漏洞、生成安全代码模式并自动化安全测试，但也需要仔细监督，以防引入新的风险。本节介绍如何利用 AI 构建安全的应用，同时了解它的局限性。

## AI 代码安全的现状（2026 年）

AI 如今编写了世界上很大一部分代码——而它产出的数据令人警醒。在学习下面的技巧之前，先了解你所面对的基线：

| 研究 / 来源 | 发现 |
|----------------|-----------------|
| **Escape.tech** — 扫描了 1,400+ 个氛围编程（vibe coding）生产应用 | **65%** 存在安全问题；**58%** 至少存在一个*严重*问题 |
| **Veracode** — 测试了 100+ 个模型生成的代码 | 针对常见漏洞类别的通过率仅为 **55%**——两年来模型多次迭代也未改变。约 **45%** 的样本带有可被利用的缺陷 |
| **CodeRabbit** — 分析了 470 个开源拉取请求 | 与 AI 相关的 PR 总体问题数约为 **1.7 倍**；在某些类别中，安全发现最高达 **2.74 倍** *(注意：AI 的参与须从 PR 中推断)* |
| **佐治亚理工学院研究人员** — 在 3 个月窗口内扫描了 43,000 条安全公告 | **74 个漏洞**可直接追溯到 AI 生成的代码，其中 **14 个严重**；他们估计真实数字要**高 5–10 倍**，因为只有*已披露的* AI 生成代码才能被追溯 |
| **OWASP** — 生成式 AI 应用的风险 | 强调应用漏洞和**对 AI 生成输出的不当依赖**是使用 AI（及基于 AI）构建的团队面临的长期风险 |
| **Sonar**（2026 年） | **96%** 的开发者不完全信任 AI 生成的代码在功能上正确；只有 **48%** 在提交前总会检查它；**61%** 表示 AI 经常产出*看起来*正确但不可靠的代码 |
| **Gartner**（2026 年 11 月）——*"Vibe Coding Is Cool, Until It Doesn't Work"* | 公民开发者会陷入提示/排查/返工的循环；企业领导者必须建立**护栏、治理和支持模式** |

**要点：** 快速写出的代码不等于安全的代码。模型一代代在进步，但 Veracode 的通过率两年来纹丝不动——因此要把每一行 AI 生成的代码都当作不可信，直到有人审过它、测试跑过它、扫描器放行它。

## 用 AI 生成安全代码

### 输入校验与净化
AI 擅长生成全面的输入校验逻辑，以防止注入攻击。

**常见模式：**
- **SQL 注入防护：** "Generate a parameterized query for this user search function instead of string concatenation."
- **XSS 防护：** "Create a sanitization function that escapes HTML entities in user-generated content before rendering."
- **命令注入：** "Refactor this shell command execution to use safe subprocess calls with argument arrays."

**最佳实践：**
- 始终在客户端和服务端同时校验
- 使用白名单而非黑名单
- 绝不信任用户输入，即使来自已认证用户

### 身份验证与授权
AI 可以实现健壮的身份验证系统，但需要仔细审查。

**实现领域：**
- **密码处理：** "Implement password hashing using bcrypt with cost factor 12 and salt generation."
- **会话管理：** "Create a secure session middleware with HTTP-only cookies, CSRF tokens, and expiration."
- **多因素认证：** "Design a TOTP-based 2FA flow with backup codes and recovery options."

**关键审查点：**
- 验证令牌生成是否使用密码学安全的随机数
- 确保密码重置令牌一次性有效且有时限
- 检查每个受保护路由是否都执行了授权检查

### 加密与数据保护
AI 帮助正确实现加密，而加密是出了名的容易出错。

**场景：**
- **静态数据：** "Show me how to encrypt sensitive user data in PostgreSQL using pgcrypto with AES-256."
- **传输中的数据：** "Configure HTTPS with TLS 1.3 and strong cipher suites for this Node.js Express app."
- **密钥管理：** "Implement envelope encryption using AWS KMS for encrypting database credentials."

## 漏洞检测与修复

### 结合 AI 的静态分析
AI 增强了传统的 SAST（静态应用安全测试）工具。

**工作流：**
1. **代码扫描：** "Analyze this codebase for OWASP Top 10 vulnerabilities."
2. **上下文感知检测：** AI 理解业务逻辑，能发现传统扫描器漏掉的问题
3. **修复建议：** "Generate a patch for this SQL injection vulnerability in the login function."

**常见发现：**
- 硬编码的凭据和 API 密钥
- 不安全的直接对象引用（IDOR）
- 敏感端点缺少限流
- 错误处理不当，暴露堆栈跟踪

### 依赖安全
AI 帮助管理复杂的依赖关系。

**任务：**
- **漏洞扫描：** "Check package.json for dependencies with known CVEs and suggest secure versions."
- **许可证合规：** "Audit all dependencies for license compatibility with our commercial product."
- **供应链攻击：** "Identify dependencies with suspicious recent updates or maintainer changes."

**工具集成：**
- Snyk、Dependabot、npm audit
- 软件物料清单（SBOM）生成

## 安全测试自动化

### 渗透测试辅助
AI 增强了手动渗透测试工作。

**能力：**
- **测试用例生成：** "Create a checklist of payloads to test for SQL injection in this search endpoint."
- **模糊测试：** "Generate fuzzing inputs to test buffer overflow vulnerabilities in this C++ parser."
- **报告编写：** "Draft a penetration test report with severity ratings and remediation steps for these findings."

### 自动化安全扫描
把 AI 驱动的扫描集成到 CI/CD 流水线中。

**流水线阶段：**
```yaml
security-scan:
  - dependency-check
  - sast-analysis
  - secret-detection
  - container-scanning
  - dast-scan (staging only)
```

**CI 提示词：**
> "Add a GitHub Actions job that runs Trivy for container scanning and fails the build if critical vulnerabilities are found."

**2026 年基线：** 这些扫描要在*每一次*拉取请求上运行，而不只是每夜构建——智能体编写的变更如今已占进入仓库内容的一大半（见[保障编码智能体安全](#securing-coding-agents-2026-consensus-practices)）。

## AI 代码中的常见安全陷阱

### 1. 虚假的安全感
**风险：** 默认认为 AI 生成的代码是安全的
**缓解措施：**
- 把所有 AI 代码当作不可信，直到审查通过
- 使用针对你技术栈的安全检查清单
- 实施纵深防御
- 记住 2026 年的基线：58% 的氛围编程生产应用至少存在一个严重问题（Escape.tech）

### 2. 凭空编造的安全函数
**风险：** AI 编造不存在的安全库或方法
**缓解措施：**
- 对照官方文档核对所有导入
- 彻底测试安全函数
- 使用成熟、维护良好的库

### 3. 过时的模式
**风险：** AI 推荐已弃用的加密算法或协议
**缓解措施：**
- 指定当前标准：“使用 Argon2id 做密码哈希，而不是 MD5”
- 定期更新安全依赖
- 订阅你所用技术栈的安全公告

### 4. 逻辑漏洞
**风险：** AI 漏掉可导致越权的业务逻辑缺陷
**缓解措施：**
- 手动审查授权逻辑
- 测试权限系统中的边界情况
- 实施全面的审计日志

## 结合 AI 的安全最佳实践

### 安全的提示工程
你告诉 AI 的内容对安全很重要：

**应该做：**
- "Generate code following OWASP ASVS Level 2 requirements"
- "Implement this feature with principle of least privilege"
- "Add input validation, output encoding, and CSRF protection"

**不要做：**
- 在提示词中分享真实凭据、API 密钥或机密信息
- 未考虑保密协议就粘贴专有安全策略
- 要求 AI“为了测试目的”绕过安全控制

### 代码审查清单
审查 AI 生成的安全代码时：

- [ ] 所有输入都经过校验和净化了吗？
- [ ] 敏感操作需要身份验证吗？
- [ ] 授权检查实现正确吗？
- [ ] 密钥是否安全存储（不在代码中）？
- [ ] 敏感数据在静态和传输中都加密了吗？
- [ ] 错误信息是否通用（没有信息泄露）？
- [ ] 是否有限流以防止滥用？
- [ ] 安全头是否配置正确？
- [ ] 是否为安全事件实现了日志记录？
- [ ] 依赖是否最新且无漏洞？

## 保障编码智能体安全：2026 年共识实践

随着编码智能体从自动补全发展为自主多文件运行，安全社区已经形成了一套实用的基线。无论你使用 Claude Code、Cursor 智能体、Copilot 编码智能体，还是自己的脚手架，2026 年的共识是：

1. **每次拉取请求都做自动化扫描**——SAST、依赖检查和密钥检测为*每一次*变更把关，无论是人写的还是智能体写的。
2. **编码智能体的权限最小化**——默认最小权限：把智能体的访问范围限定在当前任务内，并在沙箱/隔离环境中运行。
3. **保护凭据和 API 密钥**——绝不把密钥粘贴到模型上下文或提示词中；改用密钥管理器，配合短期、有作用域的令牌。
4. **生产变更和敏感操作须经人工批准**——任何智能体都不得未经审查就直接推送到生产环境或触碰受监管数据。
5. **针对可能安全威胁的测试**——以威胁建模驱动的测试，针对*你的*应用可能被攻击的具体方式，而不只是理想路径。
6. **长时智能体运行的检查点与回滚**——可逆的变更和恢复点，让上百步的智能体运行可以在任意一步撤销。
7. **不可逆或对外操作前的审批关卡**——发送邮件、删除数据、花钱和部署，始终需要人类明确说“可以”。

**智能体安全检查清单：**
- [ ] 每个 PR（人或智能体提交的）都通过自动化安全扫描
- [ ] 智能体使用最小权限凭据，在隔离/沙箱环境中运行
- [ ] 密钥绝不进入提示词/上下文——只有密钥管理器可以接触它们
- [ ] 人工批准所有生产和敏感变更
- [ ] 以威胁建模驱动的测试覆盖应用可能的攻击路径
- [ ] 长时智能体运行有检查点和经过测试的回滚路径
- [ ] 不可逆和对外操作都要经过审批关卡

## AI 糟粕（AI Slop）与治理：为机器生成的代码负责

> "The majority of code is now machine-generated." — Oracle SVP, 2026

机器生成的代码仍然是*你的*代码：有人必须维护它、审计它，并在它出问题时负责。这让 AI 糟粕成为治理问题，而不只是质量问题。

- **治理产出，而不只是提示词。** 臃肿蔓延的生成代码会埋没意图，让审计更难。Oracle 的 APEXlang 方法（2026 年 11 月）主张用紧凑的意图级定义——用小而可审查的规格描述应用*应该*做什么——这比数千行生成的样板代码容易审计得多。
- **公民开发者的护栏。** Gartner（2026 年 11 月）建议企业领导者在氛围编程规模化之前建立护栏、治理和支持模式：谁可以生成什么、谁来审查、谁可以部署。
- **所有权不会转移给模型。** 无论代码是人敲的还是智能体敲的，发布应用的团队都要为它的漏洞、合规状况和故障负责。
- **为维护做预算。** 几分钟生成的代码，维护可能要花几年；从第一天起就把 AI 密集型代码库当作遗留代码对待（可读的结构、测试、文档、清晰的边界）。

## 合规与监管考量

### GDPR、CCPA、HIPAA
AI 可以帮助实现合规要求：

**数据隐私：**
- "Generate a function to anonymize personal data for GDPR right-to-be-forgotten requests"
- "Create a data retention policy implementation that automatically deletes old records"
- "Implement consent management for cookie tracking compliance"

### 审计跟踪
- "Design an immutable audit log system for tracking all access to sensitive medical records (HIPAA)"
- "Create a tamper-evident log using hash chains for financial transactions"

## 结合 AI 的事件响应

### 检测与分析
- **日志分析：** "Analyze these server logs to identify signs of a brute force attack"
- **异常检测：** "Build a machine learning model to detect unusual API access patterns"

### 遏制与清除
- "Generate a script to block these malicious IP addresses across our firewall and load balancer"
- "Create a rollback plan to restore from clean backups after ransomware detection"

### 事后
- "Help me write a post-mortem report following the NIST incident response framework"
- "Generate lessons learned and updated security policies based on this breach"

## AI 增强的安全工具

### IDE 插件
- **GitHub Copilot Security：** 编码时实时检测漏洞
- **Snyk Code：** AI 驱动的静态分析，检测安全缺陷
- **Semgrep：** 用自然语言创建自定义规则

### 运行时保护
- **WAF 配置：** "Generate ModSecurity rules to block SQL injection attempts"
- **RASP：** 带异常检测的运行时应用自我保护

### 威胁情报
- "Summarize the latest threat intelligence reports for e-commerce platforms"
- "Generate indicators of compromise (IOCs) to monitor based on recent attack patterns"

## 实践练习
1. **安全代码审查：** 分析 AI 生成的代码，找出 10 个常见漏洞
2. **渗透测试：** 用 AI 生成测试用例，并利用一个故意留有漏洞的应用（OWASP Juice Shop）
3. **事件响应：** 模拟一次数据泄露，用 AI 协助检测、遏制和报告
4. **合规实施：** 用 AI 构建一个符合 GDPR 的用户数据管理系统

## 结论
AI 是构建安全应用的强大盟友，但它不能替代安全专业知识。把 AI 生成代码、检测漏洞和自动化测试的能力，与人类的判断和安全最佳实践结合起来，开发者可以更快地创建更安全的软件。关键在于保持健康的怀疑态度，验证所有安全关键代码，并持续了解不断演变的威胁与防御手段。

2026 年的证据让这种怀疑态度有了具体依据：65% 的受扫描氛围编程生产应用存在安全问题，生成的代码通过常见漏洞检查的概率只有一半左右，且与模型代际无关，而如今进入世界的大部分代码都是机器生成的。快速生成让安全变得*更*重要，而不是不重要——扫描每一次拉取请求、约束智能体权限、让人守住审批关卡，这些做法才能把 AI 的速度转化为可交付、可信赖的软件。
