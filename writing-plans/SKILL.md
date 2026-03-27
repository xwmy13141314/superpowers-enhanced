# Writing Plans - 实施计划编写技能

**当以下情况时使用此 Skill**：
- 设计文档已获得用户批准
- 需要将设计分解为可执行的任务
- 用户要求创建实施计划
- 在开始编码之前

## 核心原则

**假设执行者是一个有技能但对项目零了解的初级工程师**。

文档需要包含他们需要的一切：
- 精确的文件路径
- 完整的代码示例
- 测试方法
- 验证步骤

## 触发条件

- `brainstorming` 技能完成后自动触发
- 用户明确要求"创建实施计划"
- 设计文档已批准，准备开始实施

## 计划文档结构

### 头部元数据

每个计划必须以以下头部开始：

```markdown
# [功能名称] 实施计划

**目标：** [一句话描述构建什么]

**架构：** [2-3 句关于方法的描述]

**技术栈：** [关键技术/库]

**关联设计：** [设计文档路径]

---
```

### 文件结构映射

在定义任务之前，先映射将创建或修改的文件：

```markdown
## 文件结构

| 文件 | 操作 | 职责 |
|------|------|------|
| `src/module.py` | 新建 | 核心功能实现 |
| `tests/test_module.py` | 新建 | 单元测试 |
| `src/existing.py` | 修改 (行 50-80) | 集成现有功能 |
```

**分解原则**：
- 每个文件有单一清晰的职责
- 一起变化的文件放在一起
- 遵循现有代码库的模式
- 避免过大的文件（如果文件过大，在计划中包含拆分）

### 任务粒度

**每个步骤是一个动作（2-5 分钟）**：

```markdown
### 任务 N: [组件名称]

**文件：**
- 新建：`exact/path/to/file.py`
- 修改：`exact/path/to/existing.py:123-145`
- 测试：`tests/exact/path/to/test.py`

- [ ] **步骤 1: 编写失败的测试**

```python
def test_specific_behavior():
    result = function(input)
    assert result == expected
```

- [ ] **步骤 2: 运行测试验证失败**

```bash
pytest tests/path/test.py::test_name -v
```
预期：FAIL，错误信息 "function not defined"

- [ ] **步骤 3: 编写最小实现**

```python
def function(input):
    return expected
```

- [ ] **步骤 4: 运行测试验证通过**

```bash
pytest tests/path/test.py::test_name -v
```
预期：PASS

- [ ] **步骤 5: 提交**

```bash
git add tests/path/test.py src/path/file.py
git commit -m "feat: add specific feature"
```
```

## 禁止占位符

以下都是**计划失败**的标志，绝对不能出现：

- ❌ "TBD"、"TODO"、"稍后实现"
- ❌ "添加适当的错误处理"（不展示具体代码）
- ❌ "添加验证"、"处理边界情况"（没有具体说明）
- ❌ "为上述内容编写测试"（没有实际测试代码）
- ❌ "类似任务 N"（重复代码——执行者可能乱序阅读）
- ❌ 描述做什么但不展示怎么做（代码步骤必须有代码块）
- ❌ 引用任何任务中未定义的类型、函数、方法

## 自检清单

计划完成后，进行自我评审：

### 1. 设计覆盖度
- 浏览设计文档的每个部分/需求
- 是否有任务实现它？
- 列出任何遗漏

### 2. 占位符扫描
- 搜索计划中的红旗模式
- 修复所有占位符

### 3. 类型一致性
- 后续任务中使用的类型、方法签名、属性名是否与前面定义的一致？
- 例如：任务 3 中叫 `clearLayers()` 但任务 7 中叫 `clearFullLayers()` 是 bug

发现问题时，直接内联修复，无需重新评审。

## 执行交接

计划完成后，提供执行选择：

```markdown
## 执行选项

计划已完成并保存到 `docs/superpowers/plans/<filename>.md`。

**选项 1: 子代理驱动（推荐）**
- 为每个任务分配一个新鲜的子代理
- 任务之间进行评审
- 快速迭代

**选项 2: 内联执行**
- 在当前会话中使用 `executing-plans` 技能
- 批量执行，设置检查点

请选择执行方式。
```

## 与 OpenClaw 集成

### 使用子代理执行计划

```python
sessions_spawn(
    runtime="subagent",
    task="执行计划中的任务 N：[任务描述]",
    mode="run",
    attachments=[{"name": "plan.md", "content": plan_content}]
)
```

### 使用飞书文档存储计划

在飞书环境中，使用 `feishu_create_doc` 创建计划文档：

```python
feishu_create_doc(
    title="[功能名称] 实施计划",
    markdown=plan_markdown,
    folder_token="docs_folder_token"  # 可选
)
```

## 任务跟踪

使用复选框语法跟踪进度：

```markdown
- [x] 任务 1: 基础架构
- [x] 任务 2: 核心功能
- [ ] 任务 3: 集成测试
- [ ] 任务 4: 文档
```

## 相关文件

- `brainstorming/SKILL.md` - 头脑风暴和设计
- `test-driven-development/SKILL.md` - 测试驱动开发
- `subagents` 工具 - 子代理管理
