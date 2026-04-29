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
