# Subagent-Driven Development - 子代理驱动开发技能

**当以下情况时使用此 Skill**：
- 实施计划已创建并获得批准
- 用户选择"子代理驱动"执行方式
- 需要快速迭代开发

## 核心原则

**一个任务 = 一个新鲜子代理 + 两阶段评审**

- 每个任务分派给新的子代理
- 任务间进行评审（规范合规性 + 代码质量）
- 快速迭代，隔离上下文

## 触发条件

- `writing-plans` 技能完成后，用户选择"子代理驱动"
- 用户明确要求"用子代理执行"

## 执行流程

### 1. 任务分派

```python
sessions_spawn(
    runtime="subagent",
    task=f"""执行任务 {task_number}: {task_description}

**计划文件：** {plan_path}

**要求：**
1. 严格遵循 TDD 流程（红 - 绿 - 重构）
2. 每个步骤提交
3. 完成后请求代码评审

**验收标准：**
- 所有测试通过
- 符合设计规范
- 无 Critical/Important 问题
""",
    mode="run",
    attachments=[
        {"name": "plan.md", "content": plan_content},
        {"name": "design.md", "content": design_content}
    ]
)
```

### 2. 两阶段评审

**阶段 1：规范合规性评审**

检查：
- [ ] 是否实现计划中的所有要求
- [ ] 是否遵循设计文档
- [ ] 文件路径是否正确
- [ ] 测试是否覆盖所有场景

**阶段 2：代码质量评审**

检查：
- [ ] 代码是否清晰可读
- [ ] 是否有重复代码
- [ ] 命名是否恰当
- [ ] 错误处理是否完善
- [ ] 是否符合项目规范

### 3. 评审结果处理

```markdown
## 任务 N 评审结果

**规范合规性：** 通过 / 需修改

**代码质量：** 通过 / 需修改

**问题列表：**

| 严重性 | 问题描述 | 修复状态 |
|--------|---------|---------|
| Critical | ... | 已修复 |
| Important | ... | 已修复 |
| Minor | ... | 待修复 |

**结论：** 通过 / 需返工

**下一步：** 开始任务 N+1 / 重新执行任务 N
```

### 4. 任务完成

```markdown
## 任务 N 完成

**状态：** ✅ 完成

**提交记录：**
- commit 1: test: 添加 XX 测试
- commit 2: feat: 实现 XX 功能
- commit 3: refactor: 重构 XX

**测试结果：**
- 新增测试：N 个
- 通过率：100%

**评审状态：** 通过
```

## 与 OpenClaw 集成

### 使用 sessions_spawn 创建子代理

```python
# 分派任务
result = sessions_spawn(
    runtime="subagent",
    task="执行任务...",
    mode="run"
)

# 等待完成（子代理会自动报告）
# 完成后进行评审
```

### 使用 subagents 管理

```python
# 查看子代理状态
subagents(action="list")

# 如有需要，可以 steer 或 kill
subagents(action="steer", target="agent_id", message="请加快进度")
```

## 优势

| 方面 | 子代理驱动 | 内联执行 |
|------|-----------|---------|
| 上下文 | 隔离，不污染主会话 | 共享，可能混乱 |
| 速度 | 快速，可并行 | 顺序执行 |
| 质量 | 每任务评审 | 批次评审 |
| 适用 | 中大型项目 | 小型项目 |

## 相关文件

- `writing-plans/SKILL.md` - 计划编写
- `code-review/SKILL.md` - 代码评审
- `test-driven-development/SKILL.md` - TDD 流程
