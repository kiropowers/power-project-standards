# 项目规范生成器

[English](README.md) | [中文](README.zh-CN.md)

Kiro Power，用于生成项目文档、编码规范，以及从对话和代码中提炼知识。

## 功能

- 📥 **知识提炼** - 从对话、代码或按主题提炼 steering
- 🏗️ **基础文档** - 生成产品概述、技术栈、项目结构文档
- 📋 **规范生成** - 16 种编码规范和最佳实践

## 安装

在 Kiro IDE 中：

1. 打开 Powers 面板
2. 点击 "Add Power" → "From GitHub"
3. 输入：`https://github.com/kiropowers/power-project-standards`

## 激活关键词

当你提到以下内容时，此 Power 会被激活：

- `steering` / `template` / `模板`
- `standards` / `规范`
- `code review` / `naming`
- `documentation` / `project setup`
- `extract` / `generate` / `提炼`

## 可用命令

### 知识提炼
- `/extract-from-chat` - 从当前对话提炼
- `/extract-by-topic` - 按主题提炼
- `/extract-from-code` - 分析代码模式
- `/weekly-summary` - 周期性知识沉淀

### 基础文档
- `/generate-product` - 产品概述
- `/generate-tech` - 技术栈文档
- `/generate-structure` - 项目结构

### 规范生成（16 种）
- `/generate-code-review` - 代码审查清单
- `/generate-naming-conventions` - 命名规范
- `/generate-error-handling` - 错误处理规范
- `/generate-security` - 安全编码规范
- `/generate-git-workflow` - Git 工作流规范
- `/generate-api-standards` - API 设计规范
- `/generate-db-standards` - 数据库规范
- `/generate-test-standards` - 测试规范
- `/generate-logging-standards` - 日志规范
- `/generate-documentation` - 文档规范
- `/generate-performance` - 性能优化指南
- `/generate-async-patterns` - 异步编程规范
- `/generate-deployment` - 部署规范
- `/generate-monitoring` - 监控告警规范
- `/generate-dependency` - 依赖管理规范
- `/generate-versioning` - 版本控制配置

## 使用方法

直接使用斜杠命令：

```
/generate-product
```

Kiro 会引导你完成整个流程，并为你的项目生成 steering 文件。

## License

MIT
