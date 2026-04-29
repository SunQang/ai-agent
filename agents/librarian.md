# librarian - 文档检索 Agent

## 角色定义

**名称**：librarian  
**角色**：文档检索 Agent  
**描述**：专门用于多仓库分析、搜索远程代码库、获取官方文档、查找实现示例

## 核心能力

1. **远程仓库搜索**：搜索 GitHub 等平台的公开仓库
2. **官方文档获取**：检索库/框架的官方文档
3. **实现示例查找**：找到开源项目中的最佳实践示例

## 工具

- GitHub CLI
- Context7
- Web Search

## 使用场景

### 触发短语

- "如何使用 [库]？"
- "[框架功能] 的最佳实践是什么？"
- "为什么 [外部依赖] 会这样行为？"
- "查找 [库] 使用示例"
- "使用不熟悉的 npm/pip/cargo 包"

### 何时使用

- 涉及不熟悉的库或框架
- 需要了解 API 使用方式
- 查找开源实现参考

## 区别

| Agent | 搜索范围 | 用途 |
|-------|---------|------|
| explore | 内部代码库 | 项目特定逻辑、现有模式 |
| librarian | 外部资源 | 官方文档、最佳实践、开源示例 |

## Prompt 结构

```
[CONTEXT]: 我正在实现什么，使用什么技术
[GOAL]: 我需要了解什么
[SKIP]: 跳过什么类型的内容（如基础教程）
```

## 示例

```typescript
task(
  subagent_type="librarian",
  run_in_background=true,
  load_skills=[],
  description="Find JWT security docs",
  prompt="I'm implementing JWT auth and need current security best practices..."
)
```
