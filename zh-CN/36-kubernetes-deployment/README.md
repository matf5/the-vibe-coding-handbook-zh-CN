[English 原文](../../36-kubernetes-deployment/README.md)

# ☸️ 36 - Kubernetes 部署：Vibe Coding 构建的应用

> **AI 可以生成应用代码，但无法为其在生产环境中的运行负责。** Kubernetes 为你提供编排能力，让 AI 构建的服务能够可靠地部署、扩缩容和运行——前提是配置正确。
> **本节介绍如何将 AI 生成的应用容器化、部署到 Kubernetes，并安全地运维。**

**难度：** 🔴 高级 · **阅读时间：** 约 16 分钟

---

## 📖 目录

- [为什么 AI 构建的应用需要 Kubernetes](#-why-kubernetes-for-ai-built-apps)
- [将 AI 生成的代码容器化](#-containerizing-ai-generated-code)
- [Vibe Coding 应用的 Kubernetes 清单](#-kubernetes-manifests-for-vibe-coded-apps)
- [部署到托管 Kubernetes 服务](#-deploying-to-a-managed-kubernetes-service)
- [AI 构建工作负载的安全加固](#-security-hardening-for-ai-built-workloads)
- [扩缩容、自动扩缩容与发布](#-scaling-autoscaling-and-rollouts)
- [监控、可观测性与回滚](#-monitoring-observability-and-rollback)
- [实践清单](#-practical-checklist)
- [要点总结](#-key-takeaways)
- [下一步](#-next-steps)

---

## 🎯 为什么 AI 构建的应用需要 Kubernetes

AI 生成的代码交付很快，但往往未经测试、缺乏监控、难以回滚。Kubernetes 为你提供：

- **声明式部署**——用 YAML 定义期望状态，像代码一样评审它
- **回滚**——`kubectl rollout undo` 可在几秒内撤销一次有问题的智能体生成发布
- **扩缩容**——无需人工干预即可应对流量高峰
- **自愈**——自动重启失败的容器
- **安全边界**——命名空间、网络策略、非 root 容器

**何时使用 Kubernetes：** 当你有多个服务、需要自动扩缩容，或需要生产级的发布控制时。对于单个前端，更简单的平台（Vercel、Railway、Fly）可能更好——见第 12 节。

---

## 📦 将 AI 生成的代码容器化

### 1. 编写 Dockerfile

AI 智能体可以生成 Dockerfile，但你必须评审它。未经检查，绝不要使用智能体生成的 Dockerfile：

```dockerfile
# Example: Node.js + TypeScript app
FROM node:20-alpine AS builder
WORKDIR /app
COPY package*.json ./
RUN npm ci
COPY . .
RUN npm run build

FROM node:20-alpine AS runner
WORKDIR /app
ENV NODE_ENV=production
RUN addgroup --system --gid 1001 nodejs
RUN adduser --system --uid 1001 nextjs
COPY --from=builder /app/public ./public
COPY --from=builder --chown=nextjs:nodejs /app/.next ./.next
COPY --from=builder /app/node_modules ./node_modules
COPY --from=builder /app/package.json ./package.json
USER nextjs
EXPOSE 3000
ENV PORT=3000
CMD ["node", "server.js"]
```

**智能体生成 Dockerfile 的安全评审清单：**

- [ ] 使用具体的 base 镜像标签（而非 `:latest`）
- [ ] 以非 root 用户运行（`USER` 指令）
- [ ] 不把密钥或 `.env` 复制进镜像
- [ ] 使用多阶段构建，排除开发依赖
- [ ] 设置 `NODE_ENV=production` 或等效配置

### 2. 构建并推送

```bash
# Build
docker build -t ghcr.io/yourusername/my-app:latest .

# Push to a registry
docker push ghcr.io/yourusername/my-app:latest
```

---

## ☸️ Vibe Coding 应用的 Kubernetes 清单

创建这些清单，并在应用之前评审它们：

### Deployment

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: my-app
  labels:
    app: my-app
    team: vibe-coding
spec:
  replicas: 2
  selector:
    matchLabels:
      app: my-app
  template:
    metadata:
      labels:
        app: my-app
    spec:
      containers:
      - name: my-app
        image: ghcr.io/yourusername/my-app:latest
        imagePullPolicy: IfNotPresent
        ports:
        - containerPort: 3000
        env:
        - name: NODE_ENV
          value: "production"
        - name: DATABASE_URL
          valueFrom:
            secretKeyRef:
              name: app-secrets
              key: database-url
        resources:
          requests:
            memory: "128Mi"
            cpu: "100m"
          limits:
            memory: "512Mi"
            cpu: "500m"
        livenessProbe:
          httpGet:
            path: /health
            port: 3000
          initialDelaySeconds: 15
          periodSeconds: 10
        readinessProbe:
          httpGet:
            path: /ready
            port: 3000
          initialDelaySeconds: 5
          periodSeconds: 5
        securityContext:
          runAsNonRoot: true
          runAsUser: 1001
          allowPrivilegeEscalation: false
```

### Service

```yaml
apiVersion: v1
kind: Service
metadata:
  name: my-app
spec:
  selector:
    app: my-app
  ports:
  - protocol: TCP
    port: 80
    targetPort: 3000
  type: ClusterIP
```

### HorizontalPodAutoscaler

```yaml
apiVersion: autoscaling/v2
kind: HorizontalPodAutoscaler
metadata:
  name: my-app
spec:
  scaleTargetRef:
    apiVersion: apps/v1
    kind: Deployment
    name: my-app
  minReplicas: 2
  maxReplicas: 10
  metrics:
  - type: Resource
    resource:
      name: cpu
      target:
        type: Utilization
        averageUtilization: 70
```

---

## ☁️ 部署到托管 Kubernetes 服务

| 提供商 | 服务 | 最适合 |
|----------|---------|----------|
| AWS | EKS | AWS 生态、企业级 |
| Google Cloud | GKE | GCP 生态、AI/ML 工作负载 |
| Azure | AKS | Azure 生态、企业级 |
| DigitalOcean | DOKS | 小团队、定价更简单 |
| Linode | LKE | 对成本敏感的项目 |

### 典型流程

```bash
# 1. Create cluster (via provider console or CLI)
# 2. Connect kubectl
aws eks update-kubeconfig --region us-east-1 --name my-cluster

# 3. Apply manifests
kubectl apply -f k8s/deployment.yaml
kubectl apply -f k8s/service.yaml
kubectl apply -f k8s/hpa.yaml

# 4. Verify rollout
kubectl rollout status deployment/my-app

# 5. Check pods
kubectl get pods -l app=my-app
```

---

## 🔒 AI 构建工作负载的安全加固

AI 生成的代码是集群中风险最高的工作负载。需要加固：

| 加固步骤 | 重要性 |
|----------------|----------------|
| **非 root 容器** | 防止被攻破的应用发生容器逃逸 |
| **只读根文件系统** | 阻止攻击者写入恶意软件 |
| **资源限制** | 防止失控的智能体生成进程耗尽节点资源 |
| **网络策略** | 限制哪些 Pod 可以与你的 AI 构建应用通信 |
| **通过 Kubernetes Secrets 注入密钥** | 绝不在 YAML 中硬编码数据库密码或 API 密钥 |
| **Pod 安全标准** | 按命名空间强制执行 baseline/restricted 策略 |

### 示例：受限的安全上下文

```yaml
securityContext:
  runAsNonRoot: true
  runAsUser: 1001
  runAsGroup: 1001
  fsGroup: 1001
  seccompProfile:
    type: RuntimeDefault
  capabilities:
    drop:
    - ALL
```

---

## 📈 扩缩容、自动扩缩容与发布

### AI 生成变更的金丝雀部署

AI 生成的代码应逐步发布：

```bash
# 1. Deploy new version to 10% of traffic
kubectl set image deployment/my-app my-app=ghcr.io/yourusername/my-app:v2

# 2. Monitor error rate and latency
kubectl top pods -l app=my-app

# 3. If healthy, increase to 100%
# 4. If unhealthy, roll back immediately
kubectl rollout undo deployment/my-app
```

### AI 工作负载的 HPA 调优

AI 生成的代码可能有不可预测的 CPU/内存模式。起步时保守一些：

- `minReplicas: 2`（高可用）
- `maxReplicas: 10`（成本控制）
- CPU 目标设为 70%——为流量高峰留出余量

---

## 📊 监控、可观测性与回滚

### 关键指标

| 指标 | 告警阈值 |
|--------|---------------|
| 错误率（5xx） | 5 分钟内 > 1% |
| 延迟（p95） | > 2 秒 |
| Pod 重启 | 10 分钟内 > 3 次 |
| CPU/内存使用率 | > 上限的 80% |

### 回滚流程（上线生产前先测试）

```bash
# View rollout history
kubectl rollout history deployment/my-app

# Undo to previous revision
kubectl rollout undo deployment/my-app

# Undo to specific revision
kubectl rollout undo deployment/my-app --to-revision=3

# Verify rollback
kubectl rollout status deployment/my-app
```

**原则：** 如果 AI 生成的发布引发故障，先回滚，再调查。不要在生产环境中调试。

---

## ✅ 实践清单

- [ ] Dockerfile 已评审（非 root、无密钥、base 镜像已固定版本）
- [ ] Kubernetes 清单在 `kubectl apply` 之前已由人工评审
- [ ] 所有容器都设置了资源请求与上限
- [ ] 已配置存活探针与就绪探针
- [ ] 密钥通过 Kubernetes Secrets 注入，而非 YAML 中的环境变量
- [ ] HorizontalPodAutoscaler 已配置最小/最大副本数
- [ ] 已为 AI 生成的变更规划金丝雀发布
- [ ] 回滚流程已在预发布环境测试
- [ ] 监控与告警已配置（错误、延迟、重启）
- [ ] 网络策略限制了 Pod 之间的通信

---

## 🔑 要点总结

- **Kubernetes 为 AI 构建的应用提供生产级控制**——发布、回滚、扩缩容、自愈
- **像评审应用代码一样仔细评审智能体生成的 Dockerfile 和清单**
- **以非 root 运行容器并设置资源限制**——AI 构建的代码风险更高
- **通过金丝雀发布 AI 生成的变更**——先监控，再扩大或回滚
- **先回滚，再调查**——绝不要在生产环境中调试线上故障

---

## 🚀 下一步

- **阅读第 [37 节——自我评估与认证路径](./37-self-assessment/)**，验证你的 Kubernetes 知识
- **阅读第 [32 节——AI 智能体安全与治理](./32-agent-safety-governance/)**，在部署智能体编写的代码之前了解会话级智能体控制
- **阅读第 [11 节——DevOps 与云](./11-devops-cloud/)**，了解 CI/CD 流水线与云基础知识

---

<center>

*最后更新：2026 年 11 月*

</center>
