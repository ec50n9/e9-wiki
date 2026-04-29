---
title: Agent Grilling
created: 2026-04-29
updated: 2026-04-29
type: concept
tags: [methodology, concept]
sources: [raw/articles/mattpocock-skills-for-real-engineers.md]
confidence: medium
---

# Agent Grilling

一种在让 coding agent 动手写代码之前，**先让 agent 反过来面试你、追问细节**的对齐技术。名称来自 Matt Pocock 的 `/grill-me` 与 `/grill-with-docs` skill。

## 核心洞察

> "No-one knows exactly what they want" —— David Thomas & Andrew Hunt,《程序员修炼之道》

软件开发最常见的失败模式不是技术错误，而是**需求错位**。你以为 agent 懂了，等它写完才发现完全不是那回事。Grilling 的本质是：在投入编码成本之前，花少量 token 让 agent 把决策树的所有分支都问清楚。

## 运作方式

用户提出需求后，agent 不直接执行，而是进入"拷问模式"：
1. 追问目标与约束的边界条件
2. 确认术语定义（不同人对同一个词理解不同）
3. 暴露隐含假设（"你确定要改这个文件吗？它会影响 X 和 Y"）
4. 要求用户在所有分支上给出明确选择

直到决策树被完全展开，agent 才开始编码。

## 两个变体

- **`/grill-me`** — 通用版，不限于代码。适用于任何计划、设计、文档场景。
- **`/grill-with-docs`** — 工程版，在 grilling 过程中同步更新 `CONTEXT.md`（共享语言文档）和 `docs/adr/`（架构决策记录）。

## 与常规 prompt 的区别

| 常规 prompt | Grilling |
|---|---|
| 用户一次性描述需求 | 需求是渐进式、交互式澄清的 |
| agent 被动接受 | agent 主动质疑 |
| 术语由 agent 自行推断 | 术语在 `CONTEXT.md` 中预定义 |
| 返工成本高 | 前置对齐成本低 |

## 适用边界

- **适合**：需求模糊、涉及多个模块、术语复杂的任务
- **不适合**：单行修复、明确到不能再明确的 bugfix（此时 grilling 反而浪费时间）

## 相关

- [[mattpocock-skills]] — 该概念的来源仓库
- [[agent-shared-language]] — grilling-with-docs 的配套机制
- [[agent-knowledge-maintenance]] — 从另一个角度处理 agent 协作中的信息衰减
