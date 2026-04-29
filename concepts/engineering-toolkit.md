---
title: 工程工具集
created: 2026-04-29
updated: 2026-04-29
type: concept
tags: [devops, tool, concept]
sources: [flomo personal notes]
confidence: medium
---

# 工程工具集

记录实践中遇到的各类工具与技术方案，作为工程实践的备忘录。

## 浏览器自动化

- **Browserless**：在 Docker 里面运行一个浏览器实例，然后 Puppeteer 连接实例。适合需要无头浏览器的场景。
- **Puppeteer**：用于自动化浏览器操作、爬虫、截图等。

## 前后端框架

- **Nitro**：用于统一包装前端 Vue3 和后端 Elysia，提供一致的开发体验。
- **ElysiaJS**：Bun 生态的高性能后端框架，支持自动化扫描目录添加 route。
- **npmx.dev**：查看 npm 包内容的代替品，避免 npmjs.com 直接打开大文件卡死。

## 远程串流

- **Sunshine**：显卡直通串流方案，适合远程游戏或工作场景。

## 服务管理

- **服务到期提醒**：需要一个面板能看到各种服务的到期时间，解决未知焦虑。

## 运营商短信限制

WhatsApp 无法接收验证码：部分运营商限制国际短信接收。可尝试发送以下指令开通：

- 移动号码：发送 `11111` 至 `10085`
- 联通号码：发送 `KTGJDX` 至 `10010`
- 电信号码：发送 `1031` 至 `10001`

## 待维护项目清单

`urp-parser` → `retrocam-studio` → `resume-filler` → `omini-craft-planner` → `focus-search` → `commit-gen` → `cliec-refine-v1` → `songzimind` → `sweep-tama`

## 前端技巧

### CSS filter 应用

参考：https://juejin.cn/post/7002829486806794276

### clsx vs classnames

`clsx` 是一个打包体积比 `classnames` 更小的替代工具，功能类似，可以用来组合类名字符串。总体来说：`clsx` 体积更小，`classnames` 逻辑考虑得更全一点。

### 动画状态机规则

状态转换的形式化描述：`state A -> state B* -> state B...`

## JS 语法备忘

### 逻辑空赋值运算符

`x ??= y` 仅在 `x` 是空值（`null` 或 `undefined`）时对其赋值。

### 注释格式转换

把只有一行内容的文档注释转换为单行：

- 匹配：`/\*\*\n\s+\*\s(.+)$\n\s+\*/`
- 替换：`/** $1 */`

## 系统工具

- **傲梅分区助手**：可以迁移安装到 C 盘的程序到其它盘，过程可逆。实测迁移后只有 Edge 会无法运行，所以迁移时不要移动 Edge 即可。

## 代码生成

### Mustache 模板实体字段

创建文件：`template/entity-field(ef).mustache`

编写注释：`// ef{name:'username',nullable:false}`

填充 template 的对象：`{name,nullable,_小驼峰:{name,nullable},_下划线:{name,nullable}}`

## AI 观察

### GPT 幻觉机制

GPT 幻觉是由于两个语义相近但实际相差比较大的对象，在检索的时候同时检索到这两个对象，导致输出的时候误把两个对象的内容合并为一个对象输出了。

## 技术阅读

- **Query 理解与优化教程**：https://mp.weixin.qq.com/s/I-PEO_mgH5OO-qzvLSQC1A