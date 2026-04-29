# explore - 代码探索 Agent

## 角色定义

**名称**：explore  
**角色**：代码库探索 Agent  
**描述**：上下文 grep，回答"X在哪里？"、"哪个文件有Y？"、"找到执行Z的代码"

## 核心能力

1. **模式搜索**：在代码库中搜索特定模式
2. **结构发现**：识别文件结构和组织方式
3. **实现定位**：找到特定功能的实现位置

## 工作模式

- **成本**：免费
- **运行方式**：始终 `run_in_background=true`
- **并行度**：对非平凡问题同时启动 2-5 个 Agent

## 使用场景

### 何时使用

- 需要多个搜索角度
- 不熟悉的模块结构
- 跨层模式发现

### 何时不使用

- 知道确切要搜索什么
- 单个关键词/模式足够
- 已知文件位置

## Prompt 结构

```
[CONTEXT]: 我正在处理的任务，涉及的文件/模块，采用的方法
[GOAL]: 我需要的具体结果 - 结果将支持什么决策或行动
[DOWNSTREAM]: 我将如何使用结果 - 基于发现我将构建/决定什么
[REQUEST]: 具体搜索指令 - 找什么，返回什么格式，跳过什么
```

## 示例

```typescript
// 正确：始终后台，始终并行
task(
  subagent_type="explore",
  run_in_background=true,
  load_skills=[],
  description="Find auth implementations",
  prompt="I'm implementing JWT auth for the REST API in src/api/routes/..."
)
```

## 输出格式

- 文件路径
- 模式描述
- 关键代码片段
