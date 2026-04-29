# Wiki Schema

## Domain
AI 辅助开发、工程实践、认知工具与产品设计。涵盖 coding agent 使用模式与 skill 设计、编程语言与框架、工程方法论、认知科学与笔记法、产品与系统设计。中文为主，术语保留英文原貌。

## Conventions
- 文件名：小写，连字符，无空格（如 `agent-grilling.md`）
- 每页开头必须有 YAML frontmatter
- 使用 `[[wikilinks]]` 链接页面（每页至少 2 个出站链接）
- 更新页面时，必须更新 `updated` 日期
- 新页面必须加入 `index.md` 正确分类
- 每次操作必须追加到 `log.md`
- **来源追溯**：合成 3+ 来源的页面，在段落末尾附加 `^[raw/articles/source.md]` 标记

## Frontmatter
```yaml
---
title: 页面标题
created: YYYY-MM-DD
updated: YYYY-MM-DD
type: entity | concept | comparison | query | summary
tags: [来自下方标签体系]
sources: [raw/articles/source-name.md]
# 可选质量信号：confidence: high | medium | low
---
```

### raw/ Frontmatter
```yaml
---
source_url: https://example.com/article
ingested: YYYY-MM-DD
sha256: <正文内容的 hex digest>
---
```

## Tag Taxonomy
- **核心领域**: ai-agent, programming, frontend, backend, devops
- **类型**: concept, methodology, framework, tool, skill, pattern
- **人物/组织**: person, company, lab, open-source
- **来源**: article, paper, video, course
- **元信息**: comparison, timeline, prediction

规则：每页标签必须在此 taxonomy 内。需要新标签时，先在此添加，再使用。

## Page Thresholds
- **创建页面**：概念在 2+ 来源中出现，或是某来源的核心主题
- **添加到已有页面**：来源提及已有内容
- **不创建页面**：仅一笔带过、脚注提及、域外内容
- **拆分页面**：超过 200 行时拆分子主题，互相链接
- **归档页面**：内容被完全替代或超出领域范围时，移入 `_archive/`，从 index 移除

## Entity Pages
一个实体一页。包含：
- 概述 / 是什么
- 关键事实与时间
- 与其他实体的关系（[[wikilinks]]）
- 来源引用

## Concept Pages
一个概念一页。包含：
- 定义 / 解释
- 当前认知状态
- 开放问题或争议
- 相关概念（[[wikilinks]]）

## Comparison Pages
并排分析。包含：
- 比较对象与原因
- 比较维度（表格优先）
- 结论或综合
- 来源

## Update Policy
新信息与旧内容冲突时：
1. 检查日期——新来源通常优先
2. 若真实矛盾，记录两种立场并标注日期与来源
3. 在 frontmatter 标记 `contradictions: [page-name]`
4. 在 lint 报告中标记待审
