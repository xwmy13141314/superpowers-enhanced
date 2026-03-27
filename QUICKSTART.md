# Superpowers Enhanced - 安装与快速开始指南

**版本:** v2.0.0  
**发布日期:** 2026-03-27

---

## 📦 什么是 Superpowers Enhanced？

Superpowers Enhanced 是一套**全流程产品开发技能包**，覆盖从产品概念到最终交付的完整生命周期：

- **产品层**：市场调研、需求分析、竞品分析、用户研究、产品战略
- **创意层**：创意生成、创意验证、方案设计
- **设计层**：产品设计、UI/UX 设计、技术设计
- **开发层**：实施计划、TDD、API 开发、子代理驱动
- **质量层**：代码评审、系统调试、性能优化、安全审查
- **运营层**：数据分析、用户反馈、持续迭代、交付验证
- **项目管理层**：项目规划、风险管理、利益相关者管理

**总计：26 个技能**

---

## 🚀 快速安装（3 分钟）

### 方法 1: 直接复制（推荐）

如果你已经下载了 ZIP 文件：

```bash
# 解压到 OpenClaw 工作空间
unzip superpowers-enhanced-v2.0.0.zip -d ~/.openclaw/workspace/skills/

# 验证安装
ls ~/.openclaw/workspace/skills/superpowers-enhanced/
```

应该看到：
```
README.md
INSTALL.md
QUICKSTART.md
使用说明.md
market-research/
requirement-analysis/
competitive-analysis/
user-research/
product-strategy/
idea-generation/
idea-validation/
brainstorming/
product-design/
frontend-design/
technical-design/
writing-plans/
test-driven-development/
api-development/
subagent-driven-development/
code-review/
systematic-debugging/
performance-optimization/
security-review/
data-analytics/
user-feedback/
continuous-iteration/
verification-before-completion/
project-planning/
risk-management/
stakeholder-management/
templates/
```

### 方法 2: 手动创建目录

```bash
# 创建目录
mkdir -p ~/.openclaw/workspace/skills/superpowers-enhanced

# 复制所有文件到该目录
# (从解压的文件夹中复制)
```

---

## ✅ 安装验证

### 检查技能数量

```bash
# 统计技能数量
find ~/.openclaw/workspace/skills/superpowers-enhanced -name "SKILL.md" -type f | wc -l
```

应该输出：**26**

### 检查核心技能

```bash
# 检查核心技能文件
ls ~/.openclaw/workspace/skills/superpowers-enhanced/market-research/SKILL.md
ls ~/.openclaw/workspace/skills/superpowers-enhanced/idea-generation/SKILL.md
ls ~/.openclaw/workspace/skills/superpowers-enhanced/product-design/SKILL.md
ls ~/.openclaw/workspace/skills/superpowers-enhanced/data-analytics/SKILL.md
```

都应该存在。

---

## 🎯 5 分钟快速上手

### 场景：从零开始做一个产品

#### 第 1 步：市场调研

对 OpenClaw 说：

```
我想做一个 AI 写作助手，帮我分析一下市场
```

**预期结果：**
- Agent 会执行市场调研
- 生成市场调研报告（飞书文档）
- 呈现关键发现：市场规模、增长趋势、竞争格局

#### 第 2 步：创意生成

```
这个市场有哪些机会？帮我头脑风暴一下
```

**预期结果：**
- Agent 会生成 20-30 个创意
- 筛选出 3-5 个最佳创意
- 提供推荐理由

#### 第 3 步：产品设计

```
我选择"垂直领域深耕"这个创意，帮我设计产品
```

**预期结果：**
- Agent 会设计产品功能
- 定义用户流程
- 创建产品设计文档

#### 第 4 步：实施计划

```
设计看起来不错，帮我写实施计划
```

**预期结果：**
- Agent 会分解任务
- 创建可执行计划
- 提供代码示例

#### 第 5 步：开发执行

```
开始执行计划吧
```

**预期结果：**
- Agent 会使用 TDD 开发
- 编写测试、实现功能
- 代码评审

---

## 📚 技能速查表

### 产品层（5 个技能）

| 技能 | 触发词 | 用途 |
|------|--------|------|
| market-research | 市场调研、市场分析、市场机会 | 了解市场、评估可行性 |
| requirement-analysis | 需求分析、需求梳理 | 梳理需求、用户故事 |
| competitive-analysis | 竞品分析、竞争对手 | 竞品对比、差异化 |
| user-research | 用户研究、用户画像 | 了解用户、用户旅程 |
| product-strategy | 产品战略、路线图 | 产品定位、战略规划 |

### 创意层（3 个技能）

| 技能 | 触发词 | 用途 |
|------|--------|------|
| idea-generation | 头脑风暴、创意、想点子 | 生成创意、发散思维 |
| idea-validation | 创意验证、可行性 | 验证创意可行性 |
| brainstorming | 方案设计、技术方案 | 技术方案、架构设计 |

### 设计层（3 个技能）

| 技能 | 触发词 | 用途 |
|------|--------|------|
| product-design | 产品设计、功能设计 | 功能架构、用户流程 |
| frontend-design | UI设计、界面设计 | UI/UX 设计 |
| technical-design | 技术设计、架构设计 | 系统架构、技术选型 |

### 开发层（4 个技能）

| 技能 | 触发词 | 用途 |
|------|--------|------|
| writing-plans | 实施计划、任务分解 | 分解任务、创建计划 |
| test-driven-development | TDD、测试驱动 | 红-绿-重构循环 |
| api-development | API 开发、接口开发 | RESTful API、接口文档 |
| subagent-driven-development | 子代理开发 | 并行开发、任务分派 |

### 质量层（4 个技能）

| 技能 | 触发词 | 用途 |
|------|--------|------|
| code-review | 代码评审、代码审查 | 代码质量、最佳实践 |
| systematic-debugging | 调试、Bug 修复 | 根本原因分析 |
| performance-optimization | 性能优化 | 性能分析、优化方案 |
| security-review | 安全审查、安全检查 | 安全漏洞、安全加固 |

### 运营层（4 个技能）

| 技能 | 触发词 | 用途 |
|------|--------|------|
| data-analytics | 数据分析、数据报告 | 数据洞察、数据驱动 |
| user-feedback | 用户反馈、反馈分析 | 收集反馈、分析反馈 |
| continuous-iteration | 持续迭代、A/B 测试 | 迭代优化、数据验证 |
| verification-before-completion | 交付验证、验收测试 | 完整性检查、交付清单 |

### 项目管理层（3 个技能）

| 技能 | 触发词 | 用途 |
|------|--------|------|
| project-planning | 项目规划、项目计划 | 项目计划、里程碑 |
| risk-management | 风险管理 | 风险识别、风险应对 |
| stakeholder-management | 利益相关者管理 | 沟通计划、汇报机制 |

---

## 🎨 典型工作流

### 工作流 1: 新产品开发（完整流程）

```
1. market-research → 市场调研
2. competitive-analysis → 竞品分析
3. user-research → 用户研究
4. requirement-analysis → 需求分析
5. product-strategy → 产品战略
6. idea-generation → 创意生成
7. idea-validation → 创意验证
8. brainstorming → 方案设计
9. product-design → 产品设计
10. frontend-design → UI/UX 设计
11. technical-design → 技术设计
12. writing-plans → 实施计划
13. test-driven-development → 开发实现
14. code-review → 代码评审
15. data-analytics → 数据分析
16. continuous-iteration → 持续迭代
```

### 工作流 2: 功能开发（简化流程）

```
1. requirement-analysis → 需求分析
2. brainstorming → 方案设计
3. product-design → 产品设计
4. writing-plans → 实施计划
5. test-driven-development → 开发实现
6. code-review → 代码评审
7. verification-before-completion → 交付验证
```

### 工作流 3: Bug 修复（调试流程）

```
1. systematic-debugging → 根本原因分析
2. 修复 Bug
3. code-review → 代码评审
4. test-driven-development → 补充测试
```

### 工作流 4: 产品优化（数据驱动）

```
1. data-analytics → 数据分析
2. user-feedback → 用户反馈分析
3. idea-generation → 优化创意
4. continuous-iteration → A/B 测试
5. data-analytics → 效果验证
```

---

## 🛠️ 配置（可选）

### 飞书文档集成

如果你想自动创建飞书文档，确保：

1. 已安装并配置飞书插件
2. 已授权飞书文档权限
3. 设置默认文件夹：

```bash
# 在环境变量中设置
export FEISHU_DEFAULT_FOLDER_TOKEN="your_folder_token"
```

### Canvas 展示（UI 设计）

如果想使用 Canvas 展示设计稿，确保：

1. Canvas 功能已启用
2. 浏览器功能可用

### 子代理开发（并行开发）

如果想使用子代理并行开发，确保：

1. OpenClaw Gateway 已启动
2. 子代理权限已配置

---

## 📖 学习资源

### 文档

- **完整文档**: README.md
- **使用说明**: 使用说明.md
- **各技能文档**: skills/*/

### 示例对话

每个技能的 SKILL.md 文件都包含示例对话，可以参考学习。

### 最佳实践

1. **从产品层开始** - 先做市场调研，再谈技术
2. **数据驱动** - 用数据支持决策，不凭直觉
3. **小步快跑** - MVP 验证，快速迭代
4. **质量内建** - TDD、代码评审、自动化测试

---

## ⚠️ 常见问题

### Q1: 技能没有触发？

**A:**
1. 检查技能文件路径是否正确
2. 重启 OpenClaw
3. 检查 SKILL.md 格式是否正确

### Q2: 飞书文档创建失败？

**A:**
1. 检查飞书插件是否已授权
2. 检查 folder_token 是否正确
3. 查看错误日志

### Q3: 子代理启动失败？

**A:**
1. 检查 OpenClaw Gateway 是否运行
2. 检查子代理权限配置
3. 查看错误日志

---

## 🔄 更新技能

### 从 v1.0 升级到 v2.0

```bash
# 备份旧版本
mv ~/.openclaw/workspace/skills/superpowers ~/.openclaw/workspace/skills/superpowers.backup

# 安装新版本
unzip superpowers-enhanced-v2.0.0.zip -d ~/.openclaw/workspace/skills/

# 验证
find ~/.openclaw/workspace/skills/superpowers-enhanced -name "SKILL.md" -type f | wc -l
```

### 后续更新

```bash
cd ~/.openclaw/workspace/skills/superpowers-enhanced
git pull origin main  # 如果使用 Git
```

---

## 📞 获取帮助

- 查看各技能的 SKILL.md 文件
- 阅读 README.md 和使用说明.md
- 参考示例对话

---

**让产品 Agent 拥有 Superpowers Enhanced！** 🚀

**版本:** v2.0.0  
**发布日期:** 2026-03-27
