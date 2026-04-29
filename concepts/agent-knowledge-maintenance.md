---
title: Agent 知识维护
created: 2026-04-29
updated: 2026-04-29
type: concept
tags: [technology, methodology]
sources: [raw/articles/neat-skill-open-source-agent-knowledge-maintenance.md]
confidence: high
---

# Agent 矨识维护

与 AI Agent 协作开发时，项目矨识会随着迭代逐渐腐败——这被称为**上下文腐败**（context corruption）。矨识维护的目标是确保持久化文档始终反映"此刻最准确的真相"，而不是依赖对话上下文。

## 项目矨识三层模型

| 层级 | 位置 | 受众 | 职责 |
|---|---|---|---|
| 第一层 | Agent 记忆系统 | Agent 自己 | 过去对话、隐性矨识 |
| 第二层 | `CLAUDE.md` / `.cursorrules` | AI | 项目约定、结构、红线、路由清单 |
| 第三层 | `docs/` 、`README` | 人类/下游开发者 | 接入指南、架构说明、运维手册 |

关键区别：CLAUDE.md 写"新增了五个路由"是提醒 AI，而 docs/integration-guide.md 写"下游怎么接这五个路由"是教别人。两者不可互相替代。

## 上下文腐败的典型表现

- 代码迭代了 7、8 轮，文档还是 1.0.0 版本。
- 数据库从 SQLite 切换到 PostgreSQL 后，CLAUDE.md 里仍写着 SQLite。
- 模型读到过期信息后，基于错误前提行动，产生"莫名其妙的错误"。

## 断舍离原则

- **合并优于追加**：避免文档冗余。
- **删除优于保留**：过期记忆比空白更危险——没有记忆时 AI 至少知道自己不知道，但看到错误信息会误以为它是对的。

## 与其他工具的关系

- **洁癖.Skill**（[[neat-skill]]）：任务结束后自动执行五步整理流程。
- **llm-wiki**：持久化矨识库的另一种实现，通过 markdown 目录结构管理笔记。

## 参考

- 微信文章：开源「洁癖.skill」，让你的Agent越用越聪明 ^[raw/articles/neat-skill-open-source-agent-knowledge-maintenance.md]
- 相关实体：[[neat-skill]]
