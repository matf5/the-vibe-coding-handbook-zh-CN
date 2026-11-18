[English 原文](../../11-devops-cloud/README.md)

# 用 AI 做 DevOps 与云基础设施

## 简介
DevOps 与云工程涉及基础设施管理、CI/CD 流水线、监控和保障系统可靠性。这些领域需要大量的配置文件、脚本编写和对多种工具的了解。AI 在这里是改变游戏规则的存在，能够生成基础设施即代码（IaC）、调试流水线故障、优化云成本并自动化日常运维任务。

## 基础设施即代码（IaC）

### Terraform 与 Pulumi
编写 Terraform 配置可能非常冗长。AI 加速了资源配置。

**工作流：**
- **资源生成：** "Write a Terraform module to deploy an AWS EC2 instance with a security group allowing SSH and HTTP. Include an EBS volume."
- **状态管理：** "How do I import an existing AWS S3 bucket into my Terraform state file?"
- **重构：** "Convert this AWS CloudFormation YAML template into Terraform HCL."
- **最佳实践：** 让 AI“应用用于成本分摊的标签标准”或“使用 DynamoDB 实现远程状态锁定”。

### Kubernetes 与 Helm
Kubernetes 清单以 YAML 冗长著称。AI 简化了部署配置。

**能力：**
- **清单生成：** "Create a Kubernetes Deployment and Service for a Node.js app. Set resource limits, liveness probes, and readiness probes."
- **Helm Chart：** "Scaffold a Helm chart for a PostgreSQL database with configurable passwords and storage sizes."
- **故障排查：** 粘贴 `kubectl describe pod` 输出并问：“这个 Pod 为什么处于 CrashLoopBackOff？分析日志和事件。”

### Docker 与容器化
- **Dockerfile：** "Write a secure, multi-stage Dockerfile for a Python Django app. Use a slim base image and run as a non-root user."
- **Compose：** "Create a docker-compose setup for a local development environment with a React frontend, Go backend, and Redis cache."
- **优化：** "Analyze this Docker image layer history and suggest ways to reduce the image size."

## CI/CD 流水线

### GitHub Actions
- **工作流生成：** "Create a GitHub Actions workflow that runs linting and tests on PRs, and deploys to AWS Lambda on merge to main."
- **矩阵构建：** "Set up a matrix strategy to test the application on Node.js versions 16, 18, and 20 across Ubuntu and Windows."
- **缓存：** "Add caching for npm dependencies to speed up the build process."

### GitLab CI / Jenkins
- **流水线脚本：** "Write a `.gitlab-ci.yml` file that builds a Docker image, pushes it to the registry, and triggers a rolling update in Kubernetes."
- **Jenkinsfile：** "Generate a declarative Jenkinsfile for a Java Maven project with stages for Build, Test, and Deploy."

### 流水线调试
- **日志分析：** 粘贴失败的流水线日志。AI 可以识别步骤失败、超时问题或权限错误。
- **优化：** "This pipeline takes 20 minutes. Suggest parallelization strategies to reduce build time."

## 云厂商专属内容

### AWS（Amazon Web Services）
- **服务选型：** "I need a serverless queue for decoupling microservices. Compare SQS vs Kinesis for my use case."
- **IAM 策略：** "Write a least-privilege IAM policy for a Lambda function that needs to read from S3 and write to DynamoDB."
- **成本优化：** "Analyze my AWS bill structure (anonymized) and suggest savings plans or rightsizing opportunities."

### Azure
- **ARM/Bicep：** "Generate a Bicep template to deploy an Azure App Service with a linked Cosmos DB account."
- **Active Directory：** "Script the creation of an Azure AD group and assign it a role in the subscription."

### Google Cloud Platform（GCP）
- **Deployment Manager：** "Create a configuration file to set up a GKE cluster with autoscaling node pools."
- **BigQuery：** "Write a scheduled query to aggregate daily logs and store them in a partitioned table."

## 监控、日志与可观测性

### Prometheus 与 Grafana
- **查询：** "Write a PromQL query to calculate the 95th percentile latency for the `http_requests_total` metric over 5 minutes."
- **仪表盘：** "Generate a Grafana JSON dashboard configuration for monitoring CPU, Memory, and Disk I/O of a Linux server."
- **告警：** "Create an Alertmanager rule to notify Slack if the error rate exceeds 1% for more than 5 minutes."

### ELK Stack（Elasticsearch、Logstash、Kibana）
- **解析：** "Write a Logstash filter to parse this Nginx access log format and extract IP, status code, and response time."
- **查询：** "Construct a Kibana Lucene query to find all 500 errors originating from a specific IP range."

### 分布式追踪
- **OpenTelemetry：** "Show me how to instrument a Node.js Express app with OpenTelemetry to export traces to Jaeger."

## 站点可靠性工程（SRE）

### 事件响应
- **应急手册：** "Draft a runbook for handling a database failover event. Include steps for verification and rollback."
- **事后复盘：** "Help me write a blameless post-mortem template based on this incident timeline."

### 混沌工程
- **实验：** "Design a Chaos Mesh experiment to randomly kill pods in the staging environment to test resilience."

### 容量规划
- **预测：** "Based on this historical traffic data (CSV), forecast the required server capacity for the upcoming holiday season."

## DevOps 中的安全（DevSecOps）

### 漏洞扫描
- **集成：** "Add a step to the CI pipeline to run Trivy for container vulnerability scanning and fail the build if critical issues are found."
- **依赖检查：** "Configure Dependabot or Snyk to automatically open PRs for security patches."

### 密钥管理
- **工具：** "Show me how to inject secrets from AWS Secrets Manager into a Kubernetes pod using the CSI driver."
- **轮换：** "Script the rotation of RDS database credentials using AWS Lambda and Secrets Manager."

## 成本管理（FinOps）
- **标签策略：** "Propose a tagging strategy for a multi-project organization to track costs by team and environment."
- **Spot 实例：** "Write a Terraform configuration to use AWS Spot Instances for a batch processing worker pool with fallback to On-Demand."
- **闲置资源：** "Provide a CLI command to identify unattached EBS volumes and idle Elastic Load Balancers."

## AI 运维（AIOps）
- **异常检测：** "Explain how to use AWS Lookout for Metrics to detect anomalies in billing data."
- **自动修复：** "Design a Lambda function that automatically restarts a hung service when a CloudWatch alarm triggers."

## 实践练习
1. **全栈部署：** 编写 Terraform 脚本，配置 VPC、子网和 EKS 集群，然后通过 Helm 部署一个示例应用。
2. **CI/CD 流水线：** 构建一个 GitHub Actions 流水线，运行测试、扫描漏洞、构建 Docker 镜像并部署到云厂商。
3. **监控搭建：** 配置 Prometheus/Grafana 监控一个 Web 服务器，并为高 CPU 使用率设置告警。
4. **灾难恢复：** 编写脚本把数据库备份到对象存储，并模拟一次恢复流程。

## 结论
DevOps 与云工程非常适合 AI 自动化。从生成复杂的 Terraform 模块到调试晦涩的 Kubernetes 错误，AI 降低了工程师的认知负担。这让团队可以专注于架构、可靠性和创新，而不是与 YAML 语法和 CLI 参数较劲。然而，人工监督仍然至关重要，以确保安全策略得到执行、成本保持可控。
