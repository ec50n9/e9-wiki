---
title: Kotlin Coroutines Skill
created: 2026-04-28
updated: 2026-04-28
type: concept
tags: [programming, methodology, tool]
sources: [raw/articles/kotlin-coroutines-skill-official-release.md]
confidence: high
---

# Kotlin Coroutines Skill

一份开源的 Agent Skill（v2.0.0），属于 Structured Coroutines 项目。它把 Kotlin 协程的正确做法编码成结构化文件，让 AI 在生成协程代码时"查手册"而非"凭印象"。

## 核心问题

AI 写协程代码最常犯的错误，不是"不会写"，而是"用了看起来能跑但长期有害的写法"。训练数据里充斥着 StackOverflow 和早期官方示例中的"能跑但不推荐"模式，没有明确规范就会持续复读。

## 内容结构

- **SKILL.md**：入口文件，包含 Agent 行为契约和分诊表（topic/error → 对应参考文件）
- **references/**：32 个 Markdown 文件，每个对应一条实践，结构统一：Bad / Recommended / Why / Quick fix

## 覆盖范围

v2.0.0 包含 32 条实践和 34 条分诊规则，按 9 个主题组织：

| 主题 | 关键实践 |
|---|---|
| Scope 与结构化并发 | 禁止 GlobalScope；async 必须 await；并发任务用 awaitAll |
| 取消与异常 | 不得吞掉 CancellationException；正确处理 Job 生命周期 |
| Flow | 冷流 vs 热流的选择；正确使用 buffer/背压 |
| Channel | 避免漏关闭；正确处理 close 与 cancel |
| 调度器 | 避免在约束上直接使用 Dispatchers.Default |
| 资源管理 | 正确使用 withContext 切换上下文 |

## 与 Hermes Skill 的关系

这份 Skill 的设计理念与 Hermes 的 skill 机制高度共鸣：都是把领域知识固化为可检索、可触发的结构化文件，让 agent 在需要时查手册而非凭记忆。

## 参考

- 微信文章：根治协程劣习！官方级协程Skill发布 ^[raw/articles/kotlin-coroutines-skill-official-release.md]
- 相关概念：[[structured-concurrency]]
- 相关实体：[[kotlin-coroutines]]
