---
title: 结构化并发
created: 2026-04-28
updated: 2026-04-28
type: concept
tags: [technology, methodology]
sources: [raw/articles/kotlin-coroutines-skill-official-release.md]
confidence: high
---

# 结构化并发

Structured Concurrency 是一种协程管理范式，核心原则是：**任何并发任务都必须有明确的父级 scope，父级结束时子任务必须被取消或等待。**这与"任务飘浮"（fire-and-forget）相反。

## 核心原则

- **层级关系**：子任务的生命周期不能超过父任务。
- **错误传播**：任何子任务失败都会导致父 scope 失败，避免静默损失。
- **取消传播**：父 scope 被取消时，所有子任务递归取消。

## 常见反模式

| 反模式 | 后果 | 正确做法 |
|---|---|---|
| `GlobalScope.launch` | 任务飘浮，无法取消和跟踪 | `viewModelScope` / `lifecycleScope` / 注入的自定义 scope |
| `async` 后不 `await` | 异常静默丢失 | 每个 `async` 必须绑定 `await` 或 `awaitAll` |
| 吞掉 `CancellationException` | 打断取消链，父级无法正常结束 | `catch(Exception e) when (e !is CancellationException)` |

## 语言支持

- **Kotlin**：`coroutineScope { }` / `supervisorScope { }` 构建父子关系。
- **Swift**：`TaskGroup`。
- **Python**：`trio.Nursery`。
- **Java**：`StructuredTaskScope`（JDK 21）。

## 参考

- 微信文章：根治协程劣习！官方级协程Skill发布 ^[raw/articles/kotlin-coroutines-skill-official-release.md]
- 相关概念：[[kotlin-coroutines-skill]]
