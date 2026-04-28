---
title: Zustand
created: 2026-04-28
updated: 2026-04-28
type: entity
tags: [technology, tool]
sources: [raw/articles/zustand-top-5-best-practices.md]
confidence: high
---

# Zustand

一个轻量级的 React 状态管理库，以简洁的 API 和无需 Context Provider 的设计著称。名字来自德语"zustand"（状态）。

## 核心特性

- **无 Provider**：不需要在组件树外层包裹 Context Provider。
- **选择器驱动**：通过 selector 函数精确控制订阅，避免不必要的 re-render。
- **中间件支持**：devTools、persist、immer 等插件可以组合使用。
- **TypeScript 友好**：类型推导自然，无需额外配置。

## 基本用法

```typescript
import { create } from 'zustand';

const useStore = create((set) => ({
  count: 0,
  increment: () => set((state) => ({ count: state.count + 1 })),
}));

// 在组件中使用
const count = useStore((s) => s.count);
```

## 与 Redux / MobX 的区别

| 特性 | Zustand | Redux | MobX |
|---|---|---|---|
| 代码量 | 少 | 多 | 中 |
| 需要 Provider | 否 | 是 | 是 |
| 响应式 | selector 驱动 | 全局 dispatch | 自动追踪 |
| 中间件 | 插件系统 | 丰富生态 | 有限 |

## 官方规范

文章总结了 5 条最佳实践，包括 selector 优化、actions 分离、store 拆分等。见 [[zustand-best-practices]]。

## 参考

- 官方文档：https://docs.pmnd.rs/zustand
- 微信文章：使用 Zustand 时你必须遵循的 5 个强大最佳实践 ^[raw/articles/zustand-top-5-best-practices.md]
- 相关概念：[[zustand-best-practices]]
