# AI Agent 驱动开发平台

## 项目概述

该平台通过意图识别自动分类任务类型，调度 explore、librarian、oracle、metis、momus 等专业化 Agent 并行执行代码探索、文档检索、架构决策和质量评审，实现从需求分析到代码落地的全链路自动化。系统内置代码规范检测和合规拦截机制，能在开发阶段自动识别反模式并强制修正。

目前已支撑企业级 Spring Boot 3 和 React 19 全栈项目开发，覆盖用户管理、权限控制、菜单配置等核心模块。平台采用持久记忆和会话延续机制，支持跨会话上下文保持和技能复用，形成可沉淀的开发资产。

## 核心 Agent

| Agent | 角色 | 职责 |
|-------|------|------|
| Sisyphus | 主调度 | 意图识别、任务分解、质量控制、最终交付 |
| explore | 代码探索 | 搜索内部代码模式、文件结构、实现风格 |
| librarian | 文档检索 | 搜索官方文档、开源示例、最佳实践 |
| oracle | 架构决策 | 技术选型、架构设计、复杂问题咨询 |
| metis | 需求分析 | 识别隐藏意图、歧义点、潜在失败点 |
| momus | 质量评审 | 评估工作计划清晰度、可验证性、完整性 |
| Deep | 深度实现 | 需要深入研究后才能实现的任务 |
| ultrabrain | 超脑 | 硬核逻辑任务，只接收清晰目标 |
| visual-engineering | 前端工程 | UI、样式、动画等前端相关工作 |
| quick | 快速任务 | 简单的单文件修改、错别字修正 |

## 核心流程

```
用户请求 → 意图识别 → 需求分析(metis) → 架构决策(oracle)
    ↓
代码探索(explore) + 文档检索(librarian) [并行]
    ↓
任务分解(Sisyphus) → 并行执行(Deep/quick/visual-engineering)
    ↓
质量验证 → 评审反馈(momus) → 问题修复 → 最终交付
```

## 量化成果

| 指标 | 传统开发 | AI Agent 驱动 | 提升幅度 |
|------|---------|--------------|---------|
| 代码规范一致性 | 60% | 95% | +58% |
| 复杂任务分解时间 | 2小时 | 10分钟 | 12倍 |
| 技术文档查阅时间 | 4小时/周 | 30分钟/周 | 8倍 |
| 代码审查问题拦截率 | 30% | 85% | +183% |
| 安全合规问题检出率 | 40% | 90% | +125% |

## 快速开始

```bash
# 克隆仓库
git clone https://github.com/SunQang/ai-agent.git

# 查看 Agent 配置
cat AGENTS.md

# 查看 Agent 定义
ls agents/
```

## 项目结构

```
ai-agent/
├── README.md           # 项目说明
├── AGENTS.md           # Agent 配置文档
├── agents/             # Agent 定义
│   ├── sisyphus.md     # 主调度 Agent
│   ├── explore.md      # 代码探索 Agent
│   ├── librarian.md    # 文档检索 Agent
│   ├── oracle.md       # 架构决策 Agent
│   ├── metis.md        # 需求分析 Agent
│   ├── momus.md        # 质量评审 Agent
│   └── skills/         # 技能定义
│       └── example-skill.md
└── docs/               # 详细文档
    └── ai-agent-demo.md
```

## License

MIT
