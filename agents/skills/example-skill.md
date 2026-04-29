# Skill 示例 - 代码规范检查

## 技能定义

**名称**：code-quality-check  
**描述**：代码质量检查技能，用于在开发阶段检测和修复常见问题

## 使用场景

- 代码提交前检查
- 技术债识别
- 代码审查辅助

## 检查项

### 硬约束（Hard Blocks）

| 检查项 | 说明 |
|--------|------|
| as any | 禁止使用 any 类型断言 |
| @ts-ignore | 禁止使用 TypeScript 忽略指令 |
| 空 catch | 禁止空异常处理块 |
| console.log | 生产代码禁止调试日志 |
| 硬编码密码 | 禁止密码硬编码 |

### 软约束（Soft Guidelines）

| 检查项 | 建议 |
|--------|------|
| 函数长度 | 建议 < 50 行 |
| 圈复杂度 | 建议 < 10 |
| 参数数量 | 建议 < 5 个 |

## 执行流程

```
1. 扫描目标文件/目录
2. 应用检查规则
3. 生成问题报告
4. 提供修复建议
```

## 配置示例

```json
{
  "name": "code-quality-check",
  "rules": {
    "hardBlocks": ["as-any", "ts-ignore", "empty-catch"],
    "softGuidelines": ["function-length", "cyclomatic-complexity"]
  }
}
```

## 输出格式

```
## 检查结果

### 硬约束违规
- [ERROR] file.ts:42 - 使用了 `as any` 类型断言
- [ERROR] file.ts:56 - 空 catch 块

### 软约束建议
- [WARN] service.ts:128 - 函数过长 (78行)
- [WARN] controller.ts:34 - 圈复杂度过高 (12)

### 修复建议
1. file.ts:42 - 使用具体类型替代 any
2. file.ts:56 - 添加错误处理逻辑
```
