# 氛围编程（Vibe Coding）速查表

常见任务、命令与模式的快速参考指南。

## 提示工程速查

### 基本结构
```
CONTEXT + TASK + CONSTRAINTS + FORMAT = Effective Prompt
```

### 快速模板
| 任务 | 模板 |
|------|----------|
| 代码审查 | "Review for [bugs/performance/security]" |
| 调试 | "Error: [X]. Expected: [Y]. Fix it." |
| 测试 | "Write tests for [edge cases/errors]" |

## 工具命令

### Cursor/Windsurf
- `Cmd+K`：生成/编辑代码
- `Cmd+L`：与代码库对话
- `@file`：引用文件
- `#symbol`：跳转到符号

### Git 快速参考
```bash
git status          # Check state
git add -p          # Stage interactively
git commit -m ""    # Commit
git push            # Push
git reset --hard    # Discard changes
git reflog          # Find lost commits
```

## HTTP 状态码
| 代码 | 含义 |
|------|---------|
| 200 | 正常 |
| 201 | 已创建 |
| 400 | 错误请求 |
| 401 | 未授权 |
| 404 | 未找到 |
| 500 | 服务器错误 |

## SQL 模式
```sql
SELECT * FROM table WHERE condition LIMIT 10;
SELECT col, COUNT(*) FROM table GROUP BY col;
SELECT * FROM t1 JOIN t2 ON t1.id = t2.fk;
```

---

**提示**：根据你的工作流定制这些速查表！
