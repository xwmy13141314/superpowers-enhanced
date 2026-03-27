# 贡献指南

感谢你考虑为 Superpowers Enhanced 贡献！

## 如何贡献

### 报告 Bug

如果你发现了 Bug，请：

1. 检查 [Issues](https://github.com/your-org/superpowers-enhanced/issues) 是否已有人报告
2. 如果没有，创建新的 Issue，包含：
   - 清晰的标题
   - 详细的问题描述
   - 复现步骤
   - 预期行为
   - 实际行为
   - 环境信息（OpenClaw 版本、操作系统等）

### 提交新技能

如果你想添加新技能：

1. Fork 本仓库
2. 创建特性分支 (`git checkout -b feature/new-skill`)
3. 在对应层级目录下创建技能文件夹
4. 创建 `SKILL.md` 文件，遵循模板
5. 提交更改 (`git commit -m 'Add some AmazingSkill'`)
6. 推送到分支 (`git push origin feature/new-skill`)
7. 创建 Pull Request

### 技能模板

```markdown
# Skill Name - 技能名称

**当以下情况时使用此 Skill**：
- 触发条件 1
- 触发条件 2

## 核心原则

**核心原则描述**

## 工作流程

### 阶段 1: 阶段名称

#### 步骤 1: 步骤名称

**做什么：**
- 步骤 1
- 步骤 2

**输出：**
- 输出 1
- 输出 2

### 阶段 2: ...

## 使用方法

### 触发示例

```
用户：示例对话
```

### Agent 响应流程

```
1. 步骤 1
2. 步骤 2
```

## 输出模板

### 模板名称

```markdown
模板内容
```

## 质量标准

### 质量检查

- [ ] 检查项 1
- [ ] 检查项 2

### 常见错误

❌ 避免：
- 错误 1

✅ 应该：
- 正确 1

## 与其他技能的配合

### 输入来源

- 技能 1
- 技能 2

### 输出到

- 技能 3
- 技能 4

## 示例对话

```
用户：示例输入

Agent: [执行流程]
→ 输出 1
→ 输出 2
```

---

**技能口号**
```

### 技能规范

1. **文件结构**
   - 每个技能一个独立文件夹
   - 文件夹名称使用小写字母和连字符
   - 必须包含 `SKILL.md` 文件

2. **SKILL.md 格式**
   - 使用 Markdown 格式
   - 包含以上所有章节
   - 保持简洁明了

3. **技能层级**
   - 产品层：市场、需求、竞品、用户、战略
   - 创意层：创意生成、验证、方案
   - 设计层：产品、前端、技术
   - 开发层：计划、TDD、API、子代理
   - 质量层：评审、调试、性能、安全
   - 运营层：数据、反馈、迭代、验证
   - 项目层：规划、风险、利益相关者

### 改进文档

如果你想改进文档：

1. Fork 本仓库
2. 创建特性分支 (`git checkout -b feature/docs-improvement`)
3. 修改文档
4. 提交更改 (`git commit -m 'Improve documentation'`)
5. 推送到分支 (`git push origin feature/docs-improvement`)
6. 创建 Pull Request

### 代码规范

- 使用中文编写技能文档
- 保持专业、清晰的语气
- 提供具体示例
- 包含输出模板

## Pull Request 流程

1. 确保 PR 描述清晰说明了更改内容
2. 确保 PR 通过所有检查（如果有）
3. 等待维护者审核
4. 根据反馈进行修改
5. 合并后删除分支

## 开发环境

### 本地测试

```bash
# 克隆仓库
git clone https://github.com/your-org/superpowers-enhanced.git
cd superpowers-enhanced

# 复制到 OpenClaw 工作空间
cp -r . ~/.openclaw/workspace/skills/superpowers-enhanced-dev/

# 重启 OpenClaw
# 在 OpenClaw 中测试技能
```

### 技能测试清单

- [ ] 技能能够正确触发
- [ ] 工作流程完整
- [ ] 输出格式正确
- [ ] 文档完整清晰
- [ ] 与其他技能协作正常

## 社区行为准则

### 我们的承诺

为了营造开放和友好的环境，我们承诺：

- 尊重不同的观点和经验
- 优雅地接受建设性批评
- 关注对社区最有利的事情
- 对其他社区成员表示同理心

### 不可接受的行为

- 使用性化语言或图像
- 恶意攻击或侮辱性评论
- 骚扰或恶意行为
- 未经许可发布他人私人信息

## 联系方式

如有问题，请联系：
- Email: support@example.com
- Discord: [加入社区](https://discord.gg/Jd8Vphy9jq)

---

再次感谢你的贡献！🎉
