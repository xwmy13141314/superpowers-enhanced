# Code Review - 代码评审技能

**当以下情况时使用此 Skill**：
- 完成任务后
- 实现主要功能后
- 合并到主分支之前
- 卡住需要新鲜视角

## 核心原则

**尽早评审，经常评审。**

在问题级联之前捕获它们。

## 触发条件

- `subagent-driven-development` 中每个任务完成后
- 主要功能实现完成
- 用户要求"评审我的代码"
- 准备合并之前

## 何时请求评审

### 必须评审
- 子代理开发中的每个任务之后
- 完成主要功能后
- 合并到 main 之前

### 可选但有价值
- 卡住时（新鲜视角）
- 重构之前（基线检查）
- 修复复杂 bug 后

## 评审流程

### 1. 获取 git SHA

```bash
BASE_SHA=$(git rev-parse HEAD~1)  # 或 origin/main
HEAD_SHA=$(git rev-parse HEAD)
```

### 2. 准备评审上下文

创建评审请求，包含：

```markdown
## 评审请求

### 实现了什么
[简要描述刚刚构建的内容]

### 计划/需求
[应该做什么 - 引用任务或设计文档]

### 变更范围
- Base SHA: `abc1234`
- Head SHA: `def5678`
- 修改文件：[列表]

### 自评
- [ ] 所有测试通过
- [ ] 遵循设计文档
- [ ] 没有占位符
- [ ] 代码已格式化
```

### 3. 分派评审子代理

使用 `sessions_spawn` 创建评审子代理：

```python
sessions_spawn(
    runtime="subagent",
    task=f"""代码评审任务：

**实现了什么：** {what_was_implemented}
**计划/需求：** {plan_or_requirements}
**Base SHA:** {base_sha}
**Head SHA:** {head_sha}

请评审代码变更，检查：
1. 是否符合计划/设计
2. 代码质量问题
3. 潜在的 bug
4. 测试覆盖度

按严重性报告问题：
- Critical: 阻塞性问题，必须立即修复
- Important: 应该在继续之前修复
- Minor: 可以稍后修复的问题
""",
    mode="run"
)
```

### 4. 处理反馈

**Critical 问题** → 立即修复

**Important 问题** → 在继续之前修复

**Minor 问题** → 记录供稍后处理

**如果评审错了** → 用技术推理反驳，展示代码/测试证明它有效

## 问题严重性定义

### Critical（严重）
- 安全漏洞
- 数据损坏风险
- 核心功能完全损坏
- 测试失败

**行动：** 立即修复，不能继续

### Important（重要）
- 功能不完整
- 边界情况未处理
- 性能问题
- 缺少关键测试

**行动：** 在继续之前修复

### Minor（次要）
- 命名可以改进
- 代码风格问题
- 文档缺失
- 小优化机会

**行动：** 记录，稍后处理

## 与工作流程集成

### 子代理驱动开发
- 每个任务后评审
- 在问题复合之前捕获
- 修复后再进行下一个任务

### 执行计划
- 每批（3 个任务）后评审
- 获取反馈，应用，继续

### 临时开发
- 合并前评审
- 卡住时评审

## 红旗 - 永远不要

- ❌ 因为"很简单"而跳过评审
- ❌ 忽略 Critical 问题
- ❌ 带着未修复的 Important 问题继续
- ❌ 与有效的技术反馈争论

## 示例评审请求

```markdown
## 代码评审请求

**任务：** 任务 2 - 添加验证功能

**实现了什么：**
- 添加了 `verify_index()` 函数
- 添加了 `repair_index()` 函数
- 支持 4 种问题类型的检测和修复

**计划/需求：**
来自 `docs/superpowers/plans/deployment-plan.md` 任务 2

**变更范围：**
- Base SHA: `a7981ec`
- Head SHA: `3df7661`
- 修改文件：
  - `src/index_manager.py` (新建)
  - `tests/test_index_manager.py` (新建)

**自评：**
- [x] 所有测试通过 (8/8)
- [x] 遵循设计文档
- [x] 没有占位符
- [x] 代码已格式化

---
请评审代码质量和设计合规性。
```

## 示例评审反馈

```markdown
## 评审结果

### 优点
- 清晰的架构
- 真实的测试
- 良好的错误处理

### 问题

**Important:**
- 缺少进度指示器 - 长时间操作应该报告进度

**Minor:**
- 魔法数字 (100) 用于报告间隔 - 应该提取为常量
- 函数名 `verify_and_repair` 太长 - 考虑拆分

### 评估
✅ 可以继续到任务 3

### 建议修复
```python
# 添加进度回调
def verify_index(callback=None):
    for i, item in enumerate(items):
        if callback and i % 100 == 0:
            callback(i, len(items))
```
```

## 与 OpenClaw 集成

### 使用 sessions_spawn 进行评审

```python
# 主代理继续工作，评审在子代理中进行
review_session = sessions_spawn(
    runtime="subagent",
    task="评审代码变更...",
    mode="run"
)

# 同时可以继续其他工作
# 稍后 poll 评审结果
```

### 使用 read 工具读取变更

```python
# 读取修改的文件
diff = exec(command="git diff HEAD~1 HEAD", workdir=project_path)
read(path="src/modified_file.py")
```

## 相关文件

- `test-driven-development/SKILL.md` - 测试要求
- `writing-plans/SKILL.md` - 计划合规性检查
- `systematic-debugging/SKILL.md` - 发现问题时的调试
