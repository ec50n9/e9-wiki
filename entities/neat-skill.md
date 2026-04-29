---
title: 洁癖.Skill
created: 2026-04-29
updated: 2026-04-29
type: entity
tags: [ai-agent, tool, skill]
sources: [raw/articles/neat-skill-open-source-agent-knowledge-maintenance.md]
confidence: high
---

# 洁癖.Skill

由卡兹克开源的 Agent Skill，用于在每次任务结束后自动审查和整理项目的文档体系、记忆文件与 AI 约束文件（如 CLAUDE.md）。核心原则是**合并优于追加，删除优于保留**。

## 支持平台

- Claude Code
- OpenAI Codex
- OpenCode
- OpenClaw

## 使用方式

在任务收尾时运行：

```
/neat
```

或自然语言触发："审查一下"、"整理一下"。

## 五步流程

1. **强制机械式盘点**：列出项目内所有 md 文件，逐个阅读，不漏任何一个。
2. **变更影响矩阵**：识别新事实波及的文档层级，检查是否跨项目依赖。
3. **直接修改**：按顺序执行——先 `docs/`，再 `CLAUDE.md`，最后整理记忆。
4. **自检清单**：确认新增环境变量是否在 runbook 和 CLAUDE.md 中同步，检查相对时间遗留等。
5. **输出变更摘要**：生成一份可阅读的变更报告。

## 核心原则

- **合并优于追加**：避免文档冗余。
- **删除优于保留**：过期记忆比空白更危险——AI 看到错误信息会基于错误前提行动。

## 与其他机制的对比

| 特性 | 洁癖.Skill | Claude Code AutoDream |
|---|---|---|
| 整理范围 | 文档 + 约束 + 记忆 | 仅记忆 |
| 跨项目依赖 | 检查 | 不检查 |
| 文档层级 | 区分 docs/ 与 CLAUDE.md | 不区分 |

## 参考

- 开源仓库：https://github.com/KKKKhazix/khazix-skills
- 微信文章：开源「洁癖.skill」，让你的Agent越用越聪明 ^[raw/articles/neat-skill-open-source-agent-knowledge-maintenance.md]
- 相关概念：[[agent-knowledge-maintenance]]
