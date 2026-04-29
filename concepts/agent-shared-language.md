---
title: Agent Shared Language
created: 2026-04-29
updated: 2026-04-29
type: concept
tags: [methodology, concept, framework]
sources: [raw/articles/mattpocock-skills-for-real-engineers.md]
confidence: medium
---

# Agent Shared Language

一种通过维护 `CONTEXT.md` 文档来为 coding agent 建立**项目专属术语表**的技术。来源于 Matt Pocock 的 `/grill-with-docs` skill，借鉴了 Eric Evans 的《领域驱动设计》中的"统一语言"（Ubiquitous Language）概念。

## 问题

Agent 被丢进项目后，需要边读代码边猜术语含义。结果：
- 用 20 个词描述一个可用 1 个词表达的概念
- 变量、函数命名不一致
- 每次会话都重复解释同一术语

## 解法：CONTEXT.md

在仓库根目录维护一个 `CONTEXT.md`，记录项目特有的术语、缩写、领域概念。例如 Matt 的 `course-video-manager` 项目中：

- **BEFORE**: "There's a problem when a lesson inside a section of a course is made 'real' (i.e. given a spot in the file system)"
- **AFTER**: "There's a problem with the materialization cascade"

"materialization cascade" 一旦被写入 `CONTEXT.md`，agent 后续就能用这个词精确定位问题，无需每次都展开解释。

## 附带收益

1. **变量与函数命名一致性** — 所有人（包括 agent）用同一套词汇
2. **代码导航更容易** — 搜索关键词与领域术语对齐
3. **减少思考 token** — agent 不需要在脑子里做术语映射

## 与 ADR 的配合

在 `/grill-with-docs` 中，`CONTEXT.md` 不是孤立的。Grilling 过程中发现的**难以解释的设计决策**会被同步记录到 `docs/adr/`（Architecture Decision Records）。这样 agent 不仅知道"这个词什么意思"，还知道"当初为什么选这个词"。

## 实践要点

- `CONTEXT.md` 不是 API 文档，而是**词汇表**
- 术语定义要简洁，一行能说完就别用两行
- 每次 grilling session 后回顾：有没有新术语需要加入？有没有旧术语已经过时？

## 相关

- [[mattpocock-skills]] — 来源仓库
- [[agent-grilling]] — 生成和更新 `CONTEXT.md` 的主要场景
- [[agent-knowledge-maintenance]] — 从更宏观的视角讨论 agent 协作中的知识沉淀
