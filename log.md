# Wiki Log

> 时序操作记录，仅附加。
> 格式：`## [YYYY-MM-DD] action | subject`
> action: ingest, update, query, lint, create, archive, delete
> 超过 500 条时旋转：改名为 log-YYYY.md，重新开始。

## [2026-04-28] create | Wiki 初始化
- 领域：个人阅读笔记与知识沉淀
- 位置：~/documents/e9-wiki
- 语言：中文为主
- 结构：SCHEMA.md, index.md, log.md 创建完成

## [2026-04-29] archive | pre-bedtime-ritual
- 原因：超出 wiki 领域范围（健康/效率），e9-wiki 收窄为 AI 辅助开发与工程实践
- 移至：_archive/concepts/pre-bedtime-ritual.md
- 更新：SCHEMA.md 标签体系、index.md 总页数 14 → 13

## [2026-04-29] ingest | 今天起，建议晚上提前洗漱
- 来源：微信公众号文章 ^[raw/articles/今天起建议晚上提前洗漱.md]
- 新建页面：concepts/pre-bedtime-ritual.md
- 更新：index.md (总页数 13 → 14)

## [2026-04-29] ingest | flomo 个人笔记批量聚合
- 来源：flomo 导出 (353 条 memos，筛除 62 条后保留 253 条)
- 分类：15 个主题聚类，合并为 8 个概念页
- 新建页面：concepts/ai-blueprint-driven-dev.md, concepts/ai-context-and-prompts.md, concepts/product-system-design.md, concepts/cognition-tools.md, concepts/learning-cognition.md, concepts/freelance-work-observations.md, concepts/game-design-notes.md, concepts/engineering-toolkit.md
- 更新：index.md (总页数 13 → 21)，SCHEMA.md 领域拓展为“AI 辅助开发、工程实践、认知工具与产品设计”

## [2026-04-29] update | flomo other 分类重新消化
- 来源：/tmp/flomo_topics/other.json 中 50 条未分类 memos + personal-growth 主题 6 条 + communication-style 2 条
- 筛除：生活碎事、隐私信息约 10 条
- 扩展已有页面：
  - cognition-tools.md: 增加情绪描述、期望管理、行动哲学、HALT 原则、得失随缘、消费冷静期、搜索即行动、创造与品味等
  - product-system-design.md: 增加路线对比工具、打包发送、日均成本计算器、记账优化、输入框交互等
  - engineering-toolkit.md: 增加运营商短信、待维护项目清单、CSS filter、clsx、JS 语法、幻觉机制、傲梅分区等
- 新建页面：concepts/communication-patterns.md (沟通表达模式)
- 更新：index.md (总页数 21 → 22)，log.md

## [2026-04-29] ingest | mattpocock/skills：Skills for Real Engineers
- 来源：GitHub 仓库 https://github.com/mattpocock/skills ^[raw/articles/mattpocock-skills-for-real-engineers.md]
- 新建页面：entities/mattpocock-skills.md, concepts/agent-grilling.md, concepts/agent-shared-language.md, concepts/agent-tdd-skill.md
- 更新：index.md (总页数 9 → 13)

## [2026-04-29] ingest | 开源「洁癖.skill」，让你的Agent越用越聪明
- 来源：微信文章 ^[raw/articles/neat-skill-open-source-agent-knowledge-maintenance.md]
- 新建页面：entities/neat-skill.md, concepts/agent-knowledge-maintenance.md
- 更新：index.md (总页数 7 → 9)

## [2026-04-28] ingest | 使用 Zustand 时你必须遵循的 5 个强大最佳实践
- 来源：微信文章 ^[raw/articles/zustand-top-5-best-practices.md]
- 新建页面：entities/zustand.md, concepts/zustand-best-practices.md
- 更新：index.md (总页数 5 → 7)

## [2026-04-28] ingest | 根治协程劣习！官方级协程Skill发布
- 来源：微信文章 ^[raw/articles/kotlin-coroutines-skill-official-release.md]
- 新建页面：entities/kotlin-coroutines.md, concepts/kotlin-coroutines-skill.md, concepts/structured-concurrency.md
- 更新：index.md (总页数 2 → 5)

## [2026-04-28] ingest | WSL2中的幽灵空间
- 来源：微信文章 ^[raw/articles/wsl2-ghost-space-why-deleted-files-dont-free-disk.md]
- 新建页面：entities/wsl2.md, concepts/wsl2-virtual-disk-cleanup.md
- 更新：index.md (总页数 0 → 2)
