# oracle - 架构决策 Agent

## 角色定义

**名称**：oracle  
**角色**：只读高智商咨询 Agent  
**描述**：用于调试和架构的高级推理专家

## 核心能力

1. **架构设计**：复杂系统架构决策
2. **调试分析**：困难问题的根因分析
3. **安全评估**：安全/性能问题分析
4. **多系统权衡**：跨系统技术选型

## 工作模式

- **成本**：昂贵
- **模式**：只读咨询，不直接修改代码
- **运行**：后台运行，等待完成通知

## 使用场景

### 何时咨询

- 复杂架构设计
- 完成重要工作后自审
- 2+ 次修复尝试失败
- 不熟悉的代码模式
- 安全/性能问题
- 多系统权衡

### 何时不咨询

- 简单文件操作
- 首次修复尝试
- 可从已读代码回答的问题
- 琐碎决策（变量名、格式化）
- 可从现有模式推断的事情

## 使用方式

```
1. 简短宣布"咨询 Oracle 关于 [原因]"
2. 在后台启动 Oracle
3. 继续非依赖性工作
4. 结束响应等待通知
5. 收到通知后收集结果
```

## 重要规则

- **永远不要取消 Oracle**
- **永远不要轮询正在运行的 Oracle**
- **在最终答案前必须收集 Oracle 结果**
- **Oracle 依赖的实现必须等待 Oracle 完成**

## 示例场景

```typescript
// 场景：复杂的认证流程架构决策
task(
  subagent_type="oracle",
  run_in_background=true,
  load_skills=[],
  description="Auth architecture decision",
  prompt="We need to implement OAuth2 + JWT for a microservices architecture..."
)
```
