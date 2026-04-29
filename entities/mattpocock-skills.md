---
title: mattpocock/skills
created: 2026-04-29
updated: 2026-04-29
type: entity
tags: [tool, company, methodology]
sources: [raw/articles/mattpocock-skills-for-real-engineers.md]
confidence: high
---

# mattpocock/skills

Matt Pocock（Total TypeScript 作者）开源的一套面向 Claude Code、Codex 等 coding agent 的 skill 集合。仓库定位是 "Skills for Real Engineers"——与 vibe coding 相反，强调用小而精、可组合的 prompt 文件来约束 agent 行为，而非让 agent 接管整个流程。

## 关键数据

- GitHub: https://github.com/mattpocock/skills
- Stars: 38.2k（截至 2026-04-29）
- 安装方式：`npx skills@latest add mattpocock/skills`
- 协议：MIT

## 核心哲学

Matt 认为当前主流的 AI 开发框架（如 GSD、BMAD、Spec-Kit）的问题在于**为了帮你做事而夺走了你的控制权**，导致流程里的 bug 很难修复。他的解法是把软件工程基本功——《程序员修炼之道》、DDD、TDD、XP——编码成可复用的 agent 指令文件，开发者按需取用、自行 hack。

## 四个问题与解法

| 失败模式 | Skill |
|---|---|
| Agent 没理解需求 | `/grill-me`, `/grill-with-docs` |
| Agent 废话太多、术语混乱 | `CONTEXT.md` 共享语言（内建于 grill-with-docs） |
| 代码跑不通 | `/tdd`, `/diagnose` |
| 代码沦为泥球 | `/improve-codebase-architecture`, `/zoom-out` |

## 技能分类

**Engineering（日常使用）**
- `diagnose` — 结构化 debug 循环
- `grill-with-docs` — 带文档生成的 grilling session
- `triage` — issue 状态机分流
- `improve-codebase-architecture` — 架构改善
- `setup-matt-pocock-skills` — 仓库初始化
- `tdd` — 红绿重构 TDD
- `to-issues` / `to-prd` — 计划转 issue / PRD
- `zoom-out` — 全局视角

**Productivity**
- `caveman` — 超压缩通信，省约 75% token
- `grill-me` — 纯 grilling，无代码
- `write-a-skill` — 创建新 skill 的模板

**Misc**
- `git-guardrails-claude-code` — 危险 git 命令拦截
- `migrate-to-shoehorn` — 测试迁移
- `scaffold-exercises` — 练习目录生成
- `setup-pre-commit` — pre-commit 配置

## 与其他 skill 体系的关系

- [[neat-skill]] — 卡兹克的 skill 侧重**任务结束后的自动整理**（文档、约束、记忆）；Matt 的 skill 侧重**任务开始前的对齐**与**过程中的反馈循环**。两者互补。
- [[agent-knowledge-maintenance]] — 讨论的上下文腐败问题，Matt 用 `CONTEXT.md` 和 ADR 做了一种轻量级的缓解方案。
