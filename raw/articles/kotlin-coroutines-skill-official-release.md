---
source_url: https://mp.weixin.qq.com/s/ARmRTIXll30n0AySP3qCBA
ingested: 2026-04-28
sha256: bf3cf25f59452915f1e5b359cce9a373d3724c219adb0cf2d1a62b2be80fd04d
---

# 根治协程陋习！官方级协程Skill发布

自Android Skill发布之后，Kotlin协程也发布了相关Skill。

是什么

Kotlin Coroutines Skill 是一份开源的 Agent Skill（v2.0.0），隶属于 Structured Coroutines 项目。

你可以把它理解成一本"AI 专用的协程操作手册"：

• SKILL.md：入口文件，包含 Agent 行为契约（身份、严格规则、语气、输出格式）和完整的分诊表（topic/error → 对应参考文件）

• references/：32 个 Markdown 文件，每个对应一条实践，结构统一：Bad / Recommended / Why / Quick fix

当 Agent 接收到协程相关的提问或代码 Review 请求时，它会沿着分诊表找到对应的参考文件，按"分析 → 问题代码 → 优化代码 → 技术解释"的固定格式输出。

为什么需要它

AI 写协程代码最常犯的错误，往往不是"不会写"，而是"用了一种看起来能跑但长期有害的写法"。
这些错误你可能见过很多次：

这些写法为什么反复出现？因为互联网上大量教程、StackOverflow 回答、甚至官方早期示例里就是这么写的。
模型的训练数据里充满了这些"能跑但不推荐"的模式，如果没有一份明确的规范来覆盖它，AI 只会继续复读。

Kotlin Coroutines Skill 的解法是：把正确做法编码成可检索、可触发的结构化文件，让模型在需要时"查手册"而不是"凭印象"。

它覆盖了哪些场景

v2.0.0 包含 32 条实践和 34 条分诊规则，按 9 个主题组织：

展开来看几个"最容易中招"的：

Scope 与结构化并发

• 1.1 GlobalScope：直接禁止，改用 viewModelScope / lifecycleScope / 注入的自定义 scope

• 1.2 async 没有 await：异常会被静默丢弃，直到 Deferred 被 GC 才可能暴露

• 1.4 awaitAll：并发任务应当用 coroutineScope { } + awaitAll() 而不是逐个 await

取消与异常

• 4.2 吞掉 CancellationException：你的 catch(Exception) 可能在默默破坏取消链

• 4.6–4.7 withTimeout：不处理 TimeoutCancellationException 会让 scope 被取消——这在嵌套场景下特别隐蔽

测试

• 6.1 用 runTest + 虚拟时间替换 runBlocking + 真实 delay()，否则 CI 会慢且不稳定

• 6.3Dispatchers.setMain / resetMain：Android 单元测试里绑定与清理的标准写法

Flow 与 Android 生命周期

• 8.2 在 lifecycleScope.launch 里收集 Flow 但没有 repeatOnLifecycle：后台继续收集，白耗资源

• 9.1–9.4 Flow 的冷/热选型、flowOn 的用法、stateIn 的初始值策略

每条参考文件都是同一个格式：问题代码 → 推荐做法 → 为什么 → 一步修复。

规则清单速览

如果你暂时不想装，也可以先把这份 Quick Checklist 当作团队协程 Review 的最小共识：

写在最后

Agent Skill 这个概念正在从"锦上添花"变成"基础设施"——当你的 AI 工具有了领域专用的规范文件，它的输出质量会显著稳定。

你在用 AI 写 Kotlin 代码时踩过哪些协程的坑？你更希望 Skill 覆盖哪些新场景（Compose、Ktor、KMP）？

#Kotlin #协程 #AI编程 #Agent #Android开发
