# 🤖 15 - 离线氛围编程（Vibe Coding）

> **在本地运行 AI 模型，实现私密、离线的开发，无需依赖云端。**  
> 本指南介绍 Ollama、LM Studio、Open WebUI、本地模型与完整的离线 AI 工作流。

---

## 📖 目录

- [为什么要离线氛围编程？](#why-offline-vibe-coding)
- [本地 AI 的好处](#benefits-of-local-ai)
- [Ollama 配置指南](#ollama-setup-guide)
- [LM Studio 指南](#lm-studio-guide)
- [Open WebUI 安装](#open-webui-installation)
- [最佳本地模型](#best-local-models)
- [IDE 集成](#ide-integration)
- [离线智能体工作流](#offline-agent-workflows)
- [性能优化](#performance-optimization)
- [隐私与安全](#privacy--security)
- [故障排查](#troubleshooting)
- [下一步](#next-steps)

---

## 🎯 为什么要离线氛围编程？

离线氛围编程意味着在本地硬件上运行 AI 模型，而不是依赖 Claude 或 ChatGPT 等云端 API。

### 何时离线

| 场景 | 云端 AI | 本地 AI |
|----------|----------|----------|
| **隐私敏感代码** | ❌ 有风险 | ✅ 完美 |
| **没有网络连接** | ❌ 无法工作 | ✅ 可用 |
| **高频使用** | 💰 昂贵 | ✅ 配置后免费 |
| **自定义微调** | ❌ 受限 | ✅ 完全可控 |
| **延迟关键** | 🌐 网络延迟 | ✅ 即时 |
| **学习/实验** | 💰 成本累积 | ✅ 无限 |

---

## ✨ 本地 AI 的好处

### 1. **完全隐私**
你的代码库永远不会离开你的机器。这对以下情况至关重要：
- 专有算法
- 客户数据处理
- 安全敏感项目
- 保密协议与合规要求

### 2. **没有用量限制**
云服务有速率限制与费用：
```
Cloud AI (Claude Pro): $20/month → ~1000 messages
Local AI: One-time hardware cost → Unlimited messages
```

### 3. **可定制**
- 在你的代码库上微调模型
- 创建自定义系统提示词
- 修改模型行为
- 构建专属智能体

### 4. **离线能力**
随时随地工作：
- 飞机上 ✈️
- 偏远地区 🏔️
- 网络中断 ⚡

### 5. **更低的长期成本**
```
Break-even calculation:
RTX 4060 Ti 16GB: $400
Monthly cloud AI: $20-200
Break-even: 2-20 months
After that: Pure savings!
```

---

## 🦙 Ollama 配置指南

### 什么是 Ollama？

Ollama 是在本地运行 LLM 最简单的方式。它负责处理：
- 模型下载
- 量化
- GPU 加速
- API 服务器
- 简单的 CLI 界面

### 安装

#### macOS
```bash
brew install ollama
# Or download from https://ollama.ai
```

#### Windows
```powershell
# Download installer from https://ollama.ai/download
# Run OllamaSetup.exe
```

#### Linux
```bash
curl -fsSL https://ollama.ai/install.sh | sh
```

### 验证安装
```bash
ollama --version
ollama list
```

### 拉取你的第一个模型
```bash
# Start with a small, fast model
ollama pull llama3.2:3b

# Medium-sized general purpose
ollama pull llama3.2:7b

# Coding specialist
ollama pull codellama:7b

# Large powerful model (needs 16GB+ VRAM)
ollama pull llama3.2:14b
```

### 运行模型
```bash
# Interactive chat
ollama run llama3.2:7b

# One-shot query
ollama run llama3.2:7b "Explain quantum computing in 3 sentences"

# With system prompt
ollama run llama3.2:7b "You are a senior Python developer. Review this code:" 

# Pass code via stdin
cat main.py | ollama run llama3.2:7b "Find bugs in this code"
```

### Ollama API 服务器
```bash
# Start server (runs on http://localhost:11434)
ollama serve

# API usage
curl http://localhost:11434/api/generate -d '{
  "model": "llama3.2:7b",
  "prompt": "Hello!",
  "stream": false
}'
```

### 热门编程模型

| 模型 | 大小 | 最低内存 | 速度 | 质量 | 最适合 |
|-------|------|---------|-------|---------|----------|
| **Phi-3-mini** | 3.8B | 4GB | ⚡⚡⚡ | ⭐⭐⭐ | 快速任务 |
| **Llama 3.2 3B** | 3B | 4GB | ⚡⚡⚡ | ⭐⭐⭐ | 通用 |
| **Llama 3.2 7B** | 7B | 8GB | ⚡⚡ | ⭐⭐⭐⭐ | 均衡 |
| **CodeLlama 7B** | 7B | 8GB | ⚡⚡ | ⭐⭐⭐⭐ | 代码生成 |
| **DeepSeek Coder 6.7B** | 6.7B | 8GB | ⚡⚡ | ⭐⭐⭐⭐⭐ | 最佳编程 |
| **Qwen 2.5 Coder 7B** | 7B | 8GB | ⚡⚡ | ⭐⭐⭐⭐⭐ | 出色 |
| **Llama 3.2 14B** | 14B | 16GB | ⚡ | ⭐⭐⭐⭐⭐ | 复杂任务 |
| **Mistral Large** | 123B | 64GB+ | 🐌 | ⭐⭐⭐⭐⭐⭐ | 最大算力 |

### 模型管理
```bash
# List downloaded models
ollama list

# Show model info
ollama show llama3.2:7b

# Delete a model
ollama rm llama3.2:7b

# Copy a model
ollama cp llama3.2:7b my-coding-model

# Export to GGUF format
ollama cp llama3.2:7b /path/to/export.gguf
```

### 自定义 Modelfile
创建定制版本：
```dockerfile
FROM llama3.2:7b

SYSTEM """
You are an expert software developer specializing in Python and JavaScript.
Always provide clean, production-ready code with comments.
Explain your reasoning step-by-step.
"""

PARAMETER temperature 0.7
PARAMETER top_p 0.9
```

构建它：
```bash
ollama create my-dev-assistant -f ./Modelfile
```

---

## 💻 LM Studio 指南

### 什么是 LM Studio？

LM Studio 是一个用户友好的本地 LLM 图形界面，具备：
- 精美的界面
- 内置模型发现
- 无需命令行
- 跨平台支持

### 安装

1. 从 https://lmstudio.ai/ 下载
2. 为你的操作系统安装（Windows/Mac/Linux）
3. 启动应用

### 下载模型

1. 点击 **"Discover"** 选项卡
2. 搜索模型（例如 "llama"、"codellama"）
3. 选择量化级别：
   - Q4_K_M：良好的平衡（推荐）
   - Q5_K_M：更好的质量、更大的体积
   - Q8_0：最佳质量、最大体积
4. 点击下载

### 聊天界面

1. 前往 **"Chat"** 选项卡
2. 从下拉菜单加载你的模型
3. 在设置中设置系统提示词
4. 开始聊天！

### 功能

- **多模型对比**：并排运行多个对话
- **预设**：保存不同的配置
- **本地 API 服务器**：作为兼容 OpenAI 的端点暴露
- **视觉模型**：支持图像分析
- **上下文定制**：调整上下文窗口大小

### 本地 API 服务器

LM Studio 可以作为 OpenAI 的直接替代品：

```python
from openai import OpenAI

client = OpenAI(
    base_url="http://localhost:1234/v1",
    api_key="not-needed"
)

response = client.chat.completions.create(
    model="local-model",
    messages=[
        {"role": "system", "content": "You are a coding assistant"},
        {"role": "user", "content": "Write a Python function to sort a list"}
    ]
)

print(response.choices[0].message.content)
```

---

## 🌐 Open WebUI 安装

### 什么是 Open WebUI？

Open WebUI 为本地模型提供类似 ChatGPT 的界面，具备：
- 精美的 Web 界面
- 对话历史
- 多模型支持
- RAG 功能
- 用户管理

### Docker 安装（推荐）

```bash
docker run -d \
  -p 3000:8080 \
  -v open-webui:/app/backend/data \
  --name open-webui \
  ghcr.io/open-webui/open-webui:main
```

访问地址：http://localhost:3000

### 直接安装

```bash
pip install open-webui
open-webui serve
```

### 连接 Ollama

1. Open WebUI 会自动检测 localhost:11434 上的 Ollama
2. 如果没有检测到，前往 Settings → Connections
3. 添加 Ollama 地址：http://host.docker.internal:11434（Docker）
4. 刷新模型

### 功能

- **聊天界面**：类似 ChatGPT 的体验
- **文档上传**：支持 PDF、文本文件的 RAG
- **网络搜索**：启用互联网访问
- **图像生成**：DALL-E 集成
- **语音输入/输出**：语音转文本支持
- **多用户**：基于角色的访问控制
- **模型切换**：轻松选择模型

---

## 🏆 最佳本地编程模型

### 热门推荐（2026）

#### 1. **DeepSeek V4 Flash** ⭐⭐⭐⭐⭐
- 大小：小型/密集变体
- 优势：最佳的开源权重编程性能、速度快
- 上下文：100 万 token

```bash
ollama pull deepseek-v4-flash
```

#### 2. **GLM-5.3** ⭐⭐⭐⭐⭐
- 大小：100 万上下文变体
- 优势：出色的代码理解能力、强大的长上下文
- 上下文：100 万 token

```bash
ollama pull glm-5.3
```

#### 3. **Kimi K3** ⭐⭐⭐⭐
- 大小：100 万以上上下文
- 优势：编程基准测试中排名靠前的开源权重模型
- 上下文：100 万以上 token

```bash
ollama pull kimi-k3
```

#### 4. **DeepSeek V4 Pro** ⭐⭐⭐⭐
- 通用编程能力强，是更大的变体
- 上下文：100 万 token

```bash
ollama pull deepseek-v4
```

```bash
ollama pull llama3.2:7b
```

#### 5. **Phi-3 Mini** ⭐⭐⭐
- 大小：3.8B
- 优势：最快，随处可运行
- 最适合：快速任务、低端硬件

```bash
ollama pull phi3:mini
```

### 模型选择指南

| 硬件 | 推荐模型 | 预期速度 |
|----------|------------------|----------------|
| **4GB 内存** | Phi-3-mini、TinyLlama | 30-50 token/秒 |
| **8GB 内存** | Llama 3.2 7B、DeepSeek 6.7B | 20-40 token/秒 |
| **16GB 内存** | Llama 3.2 14B、Qwen 14B | 10-25 token/秒 |
| **24GB 显存** | Mixtral 8x7B、CodeLlama 34B | 5-15 token/秒 |
| **32GB 以上内存** | Llama 3 70B（量化） | 2-5 token/秒 |

---

## 🔧 IDE 集成

### VS Code + Continue 扩展

Continue 是 VS Code 最好的开源 AI 扩展。

#### 安装
```bash
# In VS Code Extensions
Search: "Continue"
Install: Continue - Edit code with AI
```

#### 为本地 AI 配置
`.continue/config.json`：
```json
{
  "models": [
    {
      "title": "Ollama",
      "provider": "ollama",
      "model": "llama3.2:7b"
    },
    {
      "title": "LM Studio",
      "provider": "openai",
      "apiBase": "http://localhost:1234/v1",
      "model": "local-model"
    }
  ],
  "tabAutocompleteModel": {
    "title": "Autocomplete",
    "provider": "ollama",
    "model": "deepseek-v4-flash"
  }
}
```

#### 功能
- **Tab 自动补全**：内联代码建议
- **聊天侧边栏**：询问关于代码的问题
- **编辑命令**：选中代码 → Cmd+I → 描述改动
- **代码审查**：自动进行 PR 审查
- **文档**：根据代码生成文档

### Cursor IDE 与本地模型

Cursor 现在通过 Ollama 支持本地模型：

1. 前往 Settings → AI → Advanced
2. 启用 "Use Ollama"
3. 设置模型名称
4. 使用本地模型享受 AI 功能！

### Neovim + Copilot.lua

面向终端爱好者：
```lua
require('copilot').setup({
  servers = {
    {
      url = "http://localhost:11434",
      model = "deepseek-v4-flash"
    }
  }
})
```

---

## 🤖 离线智能体工作流

### 构建自主智能体

使用本地模型，你可以构建能够执行以下操作的智能体：
- 访问你的文件系统
- 运行命令
- 调用 API
- 完全离线工作

### 示例：代码审查智能体

创建 `agent.py`：
```python
from ollama import chat
import subprocess

def review_code(file_path):
    # Read the code
    with open(file_path, 'r') as f:
        code = f.read()
    
    # Prompt for review
    prompt = f"""Review this code for:
1. Bugs and errors
2. Security vulnerabilities  
3. Performance issues
4. Code style problems
5. Suggestions for improvement

Code:
{code}

Provide actionable feedback with examples."""

    # Get AI review
    response = chat(model='llama3.2:7b', messages=[
        {'role': 'user', 'content': prompt}
    ])
    
    return response['message']['content']

# Usage
review = review_code('main.py')
print(review)
```

### 示例：自动重构

```python
def refactor_file(file_path):
    with open(file_path, 'r') as f:
        code = f.read()
    
    prompt = f"""Refactor this code to:
- Improve readability
- Follow SOLID principles
- Add type hints
- Extract functions if too long
- Add error handling

Code:
{code}

Return only the refactored code, no explanations."""

    response = chat(model='deepseek-v4-flash', messages=[
        {'role': 'user', 'content': prompt}
    ])
    
    # Write back
    with open(file_path, 'w') as f:
        f.write(response['message']['content'])
```

### 多智能体系统

创建专属智能体：
```python
agents = {
    'architect': 'glm-5.3',  # High-level design, long context
    'coder': 'deepseek-v4-flash',  # Implementation
    'reviewer': 'kimi-k3',  # Code review
    'tester': 'deepseek-v4-flash'  # Test generation
}

def build_feature(requirement):
    # Architect designs
    design = agents['architect'].generate(f"Design: {requirement}")
    
    # Coder implements
    code = agents['coder'].generate(f"Implement: {design}")
    
    # Reviewer checks
    feedback = agents['reviewer'].generate(f"Review: {code}")
    
    # Tester creates tests
    tests = agents['tester'].generate(f"Test this: {code}")
    
    return {
        'design': design,
        'code': code,
        'feedback': feedback,
        'tests': tests
    }
```

---

## ⚡ 性能优化

### 加快推理速度

#### 1. 使用量化模型
```bash
# Q4 quantization (recommended)
ollama pull llama3.2:7b-q4_K_M

# Q3 for speed
ollama pull llama3.2:7b-q3_K_M

# Q5 for quality
ollama pull llama3.2:7b-q5_K_M
```

#### 2. GPU 加速
确保正在使用 GPU：
```bash
# Check during inference
nvidia-smi  # Should show ollama process
```

#### 3. 缩短上下文长度
```bash
ollama run llama3.2:7b "/set parameter num_ctx 2048"
# Default is 4096, reduce for speed
```

#### 4. 批量请求
不要多次调用，改为批量：
```python
# Bad: Sequential
for question in questions:
    ask(question)

# Good: Batch
ask_all(questions)
```

### 内存管理

#### 监控用量
```bash
# Linux
watch -n 1 nvidia-smi

# macOS
sudo powermetrics --samplers gpu_power -i 1000
```

#### 释放内存
```bash
# Stop Ollama
ollama serve  # Ctrl+C

# Clear GPU cache
echo 3 | sudo tee /proc/sys/vm/drop_caches
```

### 对你的配置做基准测试

```python
import time
from ollama import chat

def benchmark(model_name, prompt="Write a quicksort implementation"):
    start = time.time()
    response = chat(model=model_name, messages=[
        {'role': 'user', 'content': prompt}
    ])
    end = time.time()
    
    tokens = len(response['message']['content'].split())
    speed = tokens / (end - start)
    
    print(f"{model_name}: {speed:.1f} tokens/s")
    return speed

# Test different models
benchmark('phi3:mini')
benchmark('llama3.2:7b')
benchmark('deepseek-v4-flash')
```

---

## 🔒 隐私与安全

### 相比云端的优势

| 方面 | 云端 AI | 本地 AI |
|--------|----------|----------|
| **数据传输** | ❌ 通过互联网发送 | ✅ 保留在本地 |
| **用你的数据训练** | ❌ 可能 | ✅ 绝不 |
| **日志记录** | ❌ 服务商记录日志 | ✅ 无日志 |
| **合规** | ⚠️ 取决于服务商 | ✅ 完全可控 |
| **物理隔离** | ❌ 不可能 | ✅ 可能 |

### 安全最佳实践

#### 1. 防火墙配置
```bash
# Only allow localhost access
sudo ufw deny 11434
sudo ufw allow from 127.0.0.1 to any port 11434
```

#### 2. 模型验证
```bash
# Verify SHA256 checksums
sha256sum ~/.ollama/models/*
# Compare with official hashes
```

#### 3. 隔离环境
```bash
# Run in container
docker run --gpus all -p 127.0.0.1:11434:11434 ollama/ollama
```

#### 4. 审计日志
启用日志记录：
```bash
OLLAMA_DEBUG=1 ollama serve
```

---

## 🐛 故障排查

### 常见问题

#### 问题：模型加载缓慢
**解决方案：**
- 使用更小的量化（用 Q4 代替 Q8）
- 关闭其他应用
- 升级内存
- 使用更快的 SSD

#### 问题：内存不足
**解决方案：**
```bash
# Reduce context
ollama run llama3.2:7b "/set parameter num_ctx 1024"

# Use smaller model
ollama pull phi3:mini

# Close other GPU applications
```

#### 问题：Token 生成缓慢
**解决方案：**
- 确保正在使用 GPU（`nvidia-smi`）
- 尝试不同的模型（有些模型优化得更好）
- 将 Ollama 更新到最新版本
- 检查散热节流

#### 问题：Ollama 无法启动
**解决方案：**
```bash
# Check if port is in use
lsof -i :11434

# Kill existing process
killall ollama

# Restart service
sudo systemctl restart ollama
```

#### 问题：代码质量差
**解决方案：**
- 使用编程专用模型（DeepSeek、CodeLlama）
- 改进你的提示词
- 略微提高温度（0.7-0.8）
- 在提示词中提供更多上下文

### 获取帮助

- **Ollama 文档**：https://ollama.ai/docs
- **GitHub Issues**：https://github.com/ollama/ollama/issues
- **Discord**：https://discord.gg/ollama
- **Reddit**：r/Ollama

---

## 🎯 下一步

现在你已经搭建好了本地 AI：

1. ✅ **练习**：在日常编码任务中使用本地模型
2. ✅ **集成**：在 VS Code 中配置 Continue 扩展
3. ✅ **实验**：为不同任务尝试不同模型
4. ✅ **优化**：针对你的硬件做基准测试与调优
5. ✅ **构建**：为你的工作流创建自定义智能体

### 继续你的旅程：
- 📚 阅读 [22-AI 智能体](../22-ai-agents/)，了解高级智能体模式
- 🔧 探索 [24-自动化](../24-automation/)，了解工作流自动化
- 📖 查看 [05-AI 工具](../05-ai-tools/)，比较工具
- 💡 浏览 [26-精选提示词](../26-awesome-prompts/)，查看提示词示例

---

> **💡 专业提示**：从小模型（3-7B）开始以获得速度，只在需要时使用更大的模型（14B+）。大多数编程任务用 7B 模型就能很好地完成！

---

<div align="center">

**准备好离线编程了吗？**  
➡️ [下一步：开源项目](../16-open-source-projects/) ⬅️

[⬆️ 返回简介](../00-introduction/)

由 Vibe Coding 社区用 ❤️ 制作

</div>
