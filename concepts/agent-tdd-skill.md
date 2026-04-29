---
title: Agent TDD Skill
created: 2026-04-29
updated: 2026-04-29
type: concept
tags: [methodology, tool, concept]
sources: [raw/articles/mattpocock-skills-for-real-engineers.md]
confidence: medium
---

# Agent TDD Skill

Matt Pocock 为 coding agent 设计的 TDD（测试驱动开发）skill，核心是**让 agent 在红绿重构循环中获得稳定的反馈**，而不是一次性写完大量代码后再去调试。

## 设计动机

Agent 生成代码的速度极快，但没有运行反馈时它等于在盲飞。传统的"写完全部再测试"模式对 agent 尤其致命，因为：
- 错误会在大量代码中扩散
- agent 难以定位错误源头
- 修复时可能引入新的回归问题

## 红绿重构循环

`/tdd` skill 要求 agent 严格按以下步骤工作：

1. **Red** — 先写一个会失败的测试（明确表达期望行为）
2. **Green** — 写最小实现让测试通过
3. **Refactor** — 在测试通过的前提下清理代码
4. 重复，每次只处理一个**垂直切片**（vertical slice）

## 垂直切片

区别于按层开发（先写模型、再写服务、再写控制器），垂直切片要求每个循环都交付一个**端到端可用的小功能**。这样即使中途停止，代码也是可运行、可测试的。

## 配套：/diagnose

当测试失败但原因不明时，使用 `/diagnose` skill：
1. Reproduce — 稳定复现
2. Minimise — 缩小范围
3. Hypothesise — 提出假设
4. Instrument — 添加日志/断点验证
5. Fix — 修复
6. Regression-test — 确保不引入新问题

## 对 agent 开发的特殊价值

对人类开发者来说，TDD 是一种纪律。对 agent 来说，TDD 是一种**必要的约束机制**——它把 agent 的"发散式生成"限制在"有验证的增量"之内，大幅降低返工率。

## 相关

- [[mattpocock-skills]] — 来源仓库
- [[agent-grilling]] — 在动手之前先对齐需求，与 TDD 形成"前后夹击"
