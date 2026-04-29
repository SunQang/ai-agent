# AGENTS.md

## AI Agent 协作开发平台配置

本项目定义了一套多 Agent 协作的开发平台配置，用于指导 AI Agent 进行企业级软件开发。

## 运行环境

- 平台：OpenCode / Claude Code
- 模型：GLM-5 / Claude
- 语言：中文优先

## Agent 调度规则

### 意图识别（Intent Gate）

每次用户请求首先进行意图分类：

| 意图类型 | 处理方式 |
|---------|---------|
| 研究/理解 | explore/librarian → 综合回答 |
| 实现 | plan → delegate or execute |
| 调查 | explore → 报告发现 |
| 评估 | evaluate → 等待确认 |
| 修复 | diagnose → 最小化修复 |
| 开放式 | 评估代码库 → 提出方案 |

### Agent 分工

**explore**：代码库内部搜索
- 触发：需要了解代码结构、实现模式、文件位置
- 模式：并行启动多个 explore Agent 搜索不同维度

**librarian**：外部资源检索
- 触发：涉及不熟悉的库、框架、API
- 工具：GitHub CLI、Context7、Web Search

**oracle**：架构决策咨询
- 触发：复杂架构设计、技术选型、安全/性能问题
- 模式：只读咨询，不直接修改代码

**metis**：需求预分析
- 触发：复杂任务开始前
- 输出：隐藏约束、歧义点、潜在风险

**momus**：质量评审
- 触发：工作计划制定后
- 输出：清晰度、可验证性、完整性评估

### 强制约束（Hard Blocks）

以下行为被严格禁止：

- 类型错误抑制（`as any`、`@ts-ignore`）
- 空 catch 块
- 删除失败测试以"通过"
- 提交未经请求的代码
- 无验证交付

## 技能加载

项目支持以下技能：

| 技能 | 用途 |
|------|------|
| cudt-specification | 企业开发规范检查 |
| git-master | Git 操作 |
| frontend-ui-ux | 前端开发 |
| review-work | 代码审查 |

## 持久记忆

- `memory`：技术规则、行为规范
- `user`：用户偏好、习惯
- `identity`：Agent 角色定义
- `tools`：工具使用经验

## 会话延续

通过 `session_id` 保持跨会话上下文：

```
# 延续会话
task(session_id="ses_xxx", prompt="继续修复...")
```
