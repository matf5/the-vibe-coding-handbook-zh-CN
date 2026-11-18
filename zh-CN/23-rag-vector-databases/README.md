[English 原文](../../23-rag-vector-databases/README.md)

# RAG 与向量数据库与 AI

检索增强生成（RAG）将 LLM 与外部知识库结合起来，以提供准确、最新的回答。

## 目录
- [理解 RAG](#understanding-rag)
- [向量数据库](#vector-databases)
- [嵌入](#embeddings)
- [构建 RAG 系统](#building-rag-systems)
- [高级技术](#advanced-techniques)
- [评估](#evaluation)
- [生产考量](#production-considerations)
- [RAG 提示词](#prompts-for-rag)
- [实践项目](#practice-projects)

## 理解 RAG

### 什么是 RAG？

RAG = 检索 + 生成
1. **检索**：从知识库中检索相关文档
2. **增强**：用检索到的上下文增强提示词
3. **生成**：使用带有上下文的 LLM 生成答案

### 何时使用 RAG

- 训练数据中没有的领域专属知识
- 频繁变化的信息
- 需要来源引用
- 减少幻觉
- 成本优化（用上下文搭配更小的模型）

## 向量数据库

### 热门选择

| 数据库 | 类型 | 最适合 | 定价 |
|----------|------|----------|---------|
| Pinecone | 托管 | 生产、易用 | 付费 |
| Weaviate | 开源 | 灵活性、GraphQL | 免费/付费 |
| Chroma | 开源 | 本地开发 | 免费 |
| Qdrant | 开源 | 性能、过滤 | 免费/付费 |
| Milvus | 开源 | 大规模 | 免费 |
| pgvector | PostgreSQL 扩展 | 已有 Postgres 用户 | 免费 |

### 配置示例

```
Prompt: "Set up ChromaDB for document storage:
1. Initialize collection
2. Add documents with metadata
3. Configure embedding function
4. Implement similarity search
5. Handle updates and deletions"
```

## 嵌入

### 选择嵌入模型

```
Prompt: "Compare embedding models for RAG:
- text-embedding-ada-002 (OpenAI)
- embeddings (Cohere)
- all-MiniLM-L6-v2 (Sentence Transformers)
- bge-large (BAAI)

Consider: quality, speed, cost, dimensions."
```

### 嵌入策略

- 恰当地切分文档（256-512 个 token）
- 用重叠切块保持上下文连续性
- 存储元数据以供过滤
- 对向量归一化以计算余弦相似度

## 构建 RAG 系统

### 基础 RAG 流水线

```
Prompt: "Build end-to-end RAG system:
1. Document loading (PDF, web, database)
2. Text splitting with smart chunking
3. Embedding generation
4. Vector storage
5. Retrieval with filtering
6. Prompt augmentation
7. Response generation
8. Source citation"
```

### 高级检索

```
Prompt: "Implement hybrid search:
- Dense vector similarity
- Sparse keyword matching (BM25)
- Reciprocal Rank Fusion
- Metadata filtering
- Time-decay scoring"
```

## 高级技术

### 查询转换

```
Prompt: "Add query enhancement:
- Query expansion (synonyms, related terms)
- Step-back prompting (generate broader query)
- HyDE (Hypothetical Document Embeddings)
- Multi-query retrieval"
```

### RAG 融合

```
Prompt: "Implement RAG-Fusion:
1. Generate multiple queries from original
2. Retrieve documents for each
3. Reciprocal rank fusion
4. Re-rank results
5. Generate final answer"
```

### 自我 RAG

```
Prompt: "Add self-reflection to RAG:
- Critique retrieved documents
- Assess relevance scores
- Generate reflection tokens
- Iterative retrieval if needed"
```

## 评估

### 指标

```
Prompt: "Define RAG evaluation metrics:
- Context precision
- Context recall
- Answer relevance
- Faithfulness (groundedness)
- End-to-end accuracy"
```

### 测试框架

```
Prompt: "Create evaluation dataset:
- Question-answer pairs
- Expected sources
- Edge cases
- Adversarial examples
- Performance benchmarks"
```

## 生产考量

### 扩展

```
Prompt: "Plan for production scale:
- Index sharding strategies
- Caching frequent queries
- Async retrieval pipelines
- Rate limiting
- Monitoring and alerting"
```

### 安全

```
Prompt: "Implement RAG security:
- Access control for documents
- Query sanitization
- PII detection and redaction
- Audit logging
- Data encryption"
```

## RAG 提示词

### 调试 RAG

```
Prompt: "Debug poor RAG performance:
'Retrieved documents are irrelevant to queries'

Analyze:
1. Embedding quality
2. Chunk size appropriateness
3. Query formulation
4. Similarity threshold
5. Metadata filtering"
```

### 优化

```
Prompt: "Optimize RAG latency:
Current: 3s response time
Target: <1s

Suggest improvements in:
- Embedding caching
- Parallel retrieval
- Model selection
- Infrastructure"
```

## 实践项目

1. **文档聊天机器人**：公司文档问答
2. **法律研究助手**：判例法检索
3. **医疗信息系统**：研究论文问答（附免责声明）
4. **代码库助手**：仓库文档
5. **新闻分析**：带来源的实时新闻

---

## 结论

RAG 弥合了 LLM 与特定知识之间的鸿沟。从简单开始、严格衡量，并根据用户反馈迭代。
