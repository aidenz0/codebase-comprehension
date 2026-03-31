# 代码库理解

一个用于系统化代码探索和理解的 Claude Code 技能。

## 概述

`codebase-comprehension` 提供了一种系统化的方法来理解任意规模的代码库。它引导 AI 代理通过 L1→L2→L3→L4 渐进式深度来高效构建完整的认知模型。

## 适用场景

- 加入新项目时快速了解代码
- 理解大型系统架构
- 在大型代码库中定位特定功能
- 分析关键路径以便修改
- 任何需要理解"这个代码是怎么工作的"的场景

## 安装

```bash
# 克隆到 Claude Code skills 目录
cd ~/.claude/skills
git clone https://github.com/YOUR_USERNAME/codebase-comprehension.git
```

或使用 Claude 插件：

```bash
claude plugin marketplace add https://github.com/YOUR_USERNAME/codebase-comprehension
claude plugin install codebase-comprehension@codebase-comprehension --scope user
```

## 快速开始

告诉 Claude 分析一个代码库：

> "帮我理解这个项目" 或 "探索这个代码库的架构"

技能将自动应用 L1→L2→L3→L4 渐进式分析。

## 方法论

### L1: 全局扫描

建立整体认知：
- 识别技术栈
- 定位入口文件
- 分析目录结构
- 估算代码规模

### L2: 模块划分

理解系统边界：
- 从入口文件追踪依赖关系
- 识别核心模块（被引用最多的）
- 分析模块职责
- 生成 Mermaid 依赖图

### L3: 数据流追踪

理解系统运行机制：
- 追踪请求生命周期
- 分析数据在各层的转换
- 梳理状态管理机制
- 生成 Mermaid 序列图

### L4: 深度钻取

理解核心逻辑：
- 识别关键路径
- 找出边界条件（超时、重试、并发）
- 评估修改风险
- 生成决策点表格

## 输出

该技能生成全面的 Markdown 报告，包含：

- 技术栈分析
- 模块依赖图（Mermaid）
- 数据流图（Mermaid）
- 代码统计
- 风险评估（针对修改场景）

## 基于规模的策略

| 代码库规模 | 策略 |
|-----------|------|
| 小型 (<10K 行) | 全量扫描 + 重点阅读 |
| 中型 (10K-100K) | 分区扫描 + 关联分析 |
| 大型 (>100K) | 优先级驱动 + 增量探索 |

## Mermaid 兼容性

此技能生成的 Mermaid 图表具有最大兼容性：

- 仅使用英文标签
- 非 ASCII 文本使用双引号
- 不使用 subgraph（支持度不高）
- 序列图使用 `participant` 语法

示例：

```mermaid
graph TD
    A["root/"] --> B["src/"]
    B --> C["components/"]

sequenceDiagram
    participant User
    participant System
    User->>System: request
```

## 项目结构

```
codebase-comprehension/
├── SKILL.md              # 技能主定义
├── README.md             # 英文说明
└── README-cn.md          # 中文说明
```

## License

MIT

## 灵感来源

- [web-access](https://github.com/eze-is/web-access) - Claude Code 联网能力 skill
- Superpowers skills 框架