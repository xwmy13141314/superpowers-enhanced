# Test-Driven Development - 测试驱动开发技能

**当以下情况时使用此 Skill**：
- 实现任何新功能
- 修复 bug
- 重构代码
- 修改现有行为

## 核心原则

**铁律：没有失败的测试之前，绝不编写生产代码。**

```
NO PRODUCTION CODE WITHOUT A FAILING TEST FIRST
```

在测试之前编写的代码？删除它。重新开始。

## 触发条件

当开始实现任何任务时自动触发：
- `writing-plans` 技能执行中
- 用户要求"实现..."、"修复..."
- 任何涉及编写代码的场景

## Red-Green-Refactor 循环

### RED - 编写失败的测试

编写一个最小的测试，展示期望的行为。

**好测试的特征**：
- 单一行为（名字里有 "and"？拆分它）
- 清晰的名称（描述行为，不是 `test1`）
- 使用真实代码（避免 mock，除非不可避免）

**示例**：
```python
# ✅ 好
def test_retries_failed_operations_three_times():
    attempts = 0
    def operation():
        attempts += 1
        if attempts < 3:
            raise Exception("fail")
        return "success"
    
    result = retry_operation(operation)
    
    assert result == "success"
    assert attempts == 3

# ❌ 坏
def test_retry_works():  # 名称模糊
    mock = MagicMock()
    mock.side_effect = [Exception(), Exception(), "success"]
    retry_operation(mock)
    assert mock.call_count == 3  # 测试 mock 而不是代码
```

### 验证 RED - 看着它失败

**必须执行，绝不能跳过。**

```bash
pytest tests/path/to/test.py::test_name -v
```

确认：
- ✅ 测试失败（不是错误）
- ✅ 失败信息符合预期
- ✅ 失败原因是功能缺失（不是拼写错误）

**测试通过了？** 你在测试已存在的行为。修复测试。

**测试报错了？** 修复错误，重新运行直到正确失败。

### GREEN - 最小实现

编写最简单的代码让测试通过。

**原则**：
- 只实现当前测试需要的功能
- 不要添加额外功能（YAGNI）
- 不要重构其他代码
- 不要"改进"超出测试范围

```python
# ✅ 好 - 刚好够通过测试
async def retry_operation(fn, max_retries=3):
    for i in range(max_retries):
        try:
            return await fn()
        except Exception as e:
            if i == max_retries - 1:
                raise e

# ❌ 坏 - 过度设计
async def retry_operation(
    fn,
    max_retries=3,
    backoff='exponential',
    on_retry=None,
    retryable_exceptions=None
):
    # YAGNI - 这些都不需要
```

### 验证 GREEN - 看着它通过

**必须执行。**

```bash
pytest tests/path/to/test.py::test_name -v
```

确认：
- ✅ 测试通过
- ✅ 其他测试仍然通过
- ✅ 输出干净（无错误、警告）

**测试失败？** 修复代码，不是测试。

**其他测试失败？** 立即修复。

### REFACTOR - 重构

只有在 GREEN 之后才能重构：
- 移除重复
- 改进命名
- 提取辅助函数

保持测试绿色。不要添加行为。

### 重复

下一个失败的测试，下一个功能。

## 常见借口 vs 现实

| 借口 | 现实 |
|------|------|
| "太简单了不需要测试" | 简单的代码也会坏。测试只需 30 秒。 |
| "我稍后再写测试" | 测试立即通过证明不了什么。 |
| "我已经手动测试过了" | 手动测试是临时的，没有记录，无法重跑。 |
| "删除 X 小时的工作太浪费" | 沉没成本谬误。保持不可信的代码是技术债务。 |
| "TDD 太教条，我要务实" | TDD 就是务实：调试比测试慢得多。 |
| "先探索一下" | 可以。扔掉探索代码，用 TDD 重新开始。 |

## 红旗 - 停止并重新开始

如果出现以下情况，**删除代码，用 TDD 重新开始**：

- ❌ 代码在测试之前编写
- ❌ 测试在实现之后添加
- ❌ 测试立即通过
- ❌ 无法解释为什么测试失败
- ❌ "稍后"添加测试
- ❌ 合理化"就这一次"
- ❌ "我已经手动测试过了"
- ❌ "保持作为参考，先写测试"（你会"调整"它）
- ❌ "已经花了 X 小时，删除太浪费"

## 与 OpenClaw 集成

### 使用 exec 运行测试

```python
exec(command="pytest tests/test_file.py::test_name -v", workdir="/path/to/project")
```

### 使用子代理进行 TDD

```python
sessions_spawn(
    runtime="subagent",
    task="使用 TDD 实现任务 N：编写测试 → 看失败 → 实现 → 看通过 → 重构",
    mode="run"
)
```

### 验证清单

在标记工作完成前：

- [ ] 每个新函数/方法都有测试
- [ ] 看着每个测试失败后再实现
- [ ] 每个测试因预期原因失败（功能缺失，不是拼写错误）
- [ ] 为每个测试编写最小代码
- [ ] 所有测试通过
- [ ] 输出干净（无错误、警告）
- [ ] 测试使用真实代码（mock 仅在不可避免时）
- [ ] 边界情况和错误已覆盖

**不能勾选所有框？** 你跳过了 TDD。重新开始。

## Bug 修复流程

发现 bug 时：

1. **编写重现 bug 的失败测试**
2. **遵循 TDD 循环**
3. **测试证明修复并防止回归**

**永远不要不写测试就修复 bug。**

## 相关文件

- `writing-plans/SKILL.md` - 实施计划（包含 TDD 步骤）
- `systematic-debugging/SKILL.md` - 系统化调试
- `code-review/SKILL.md` - 代码评审
