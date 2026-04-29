---
title: Kotlin Coroutines
created: 2026-04-28
updated: 2026-04-28
type: entity
tags: [programming, tool]
sources: [raw/articles/kotlin-coroutines-skill-official-release.md]
confidence: high
---

# Kotlin Coroutines

Kotlin 标准库提供的轻量级并发框架，基于**协程**（coroutine）概念——可以暂停和恢复的计算单元，比线程更轻量，比回调更直观。

## 核心特性

- **轻量**：成千上万个协程可以跑在少量线程上。
- **挂起/恢复**：通过 `suspend` 函数实现非阻塞的异步操作。
- **结构化并发**：通过 `CoroutineScope` 管理协程生命周期，避免任务飘浮。
- **Flow**：冷流式响应式流，处理数据序列。
- **Channel**：协程间通信的生产者-消费者模型。

## 常用 Scope

| Scope | 使用场景 | 是否推荐 |
|---|---|---|
| `GlobalScope` | 全局飘浮任务 | 禁止 |
| `lifecycleScope` | Android Activity/Fragment | 推荐 |
| `viewModelScope` | Android ViewModel | 推荐 |
| 自定义 Scope | 游戏引擎、后台任务 | 推荐（需注入） |

## 官方规范

JetBrains 与 Kotlin 团队发布了官方级的 Agent Skill（v2.0.0）来规范 AI 生成的协程代码，覆盖 32 条实践。见 [[kotlin-coroutines-skill]]。

## 参考

- 官方文档：https://kotlinlang.org/docs/coroutines-overview.html
- 微信文章：根治协程劣习！官方级协程Skill发布 ^[raw/articles/kotlin-coroutines-skill-official-release.md]
- 相关概念：[[structured-concurrency]], [[kotlin-coroutines-skill]]
