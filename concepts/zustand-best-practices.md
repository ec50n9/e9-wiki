---
title: Zustand 最佳实践
created: 2026-04-28
updated: 2026-04-28
type: concept
tags: [technology, methodology]
sources: [raw/articles/zustand-top-5-best-practices.md]
confidence: high
---

# Zustand 最佳实践

Zustand 的 API 极简，但极简不等于无规范。以下 5 条实践来自官方推荐，目标是让 store 保持干净、组件保持轻量、渲染保持精准。

## 1. 只导出 custom hooks

不要把整个 store 暴露给每个组件。使用带 selector 的 custom hooks，只返回真正需要的值。

```typescript
// ❌ 不要这么做
const store = useTodoStore(); // 整个 store 都会引起 re-render

// ✅ 正确做法
export const useTodos = () => useTodoStore((s) => s.todos);
export const useAddTodo = () => useTodoStore((s) => s.addTodo);
```

## 2. 使用 atomic 且 stable 的 selectors

Selector 里返回新对象会强制触发 re-render。

```typescript
// ❌ 每次都新建对象
const { todos, isSubscribed } = useStore((state) => ({
  todos: state.todos,
  isSubscribed: state.isSubscribed,
}));

// ✅ 拆分成原子 selector
const todos = useStore((s) => s.todos);
const isSubscribed = useStore((s) => s.isSubscribed);
```

## 3. 将 actions 与 state 分离

把所有 actions 放进一个稳定对象。这样当其他 state 变化时，组件不会因为引用了 actions 而被重新渲染。

```typescript
const useStore = create((set) => {
  const actions = {
    addTodo: (t) => set((s) => ({ todos: [...s.todos, t] })),
  };
  return { todos: [], actions };
});
```

## 4. 把 actions 建模为 events

不要写简单的 setter，而是用事件语义来命名 actions。

```typescript
// ❌ 基础 setter
setTodo: (todo) => set({ todo });

// ✅ 事件语义
addTodo: (text) => set((s) => ({
  todos: [...s.todos, { id: Date.now(), text }],
})),
```

## 5. 让 store 保持小而专注

不要让一个 store 无限膨胀。按领域拆分成多个小 store。

```typescript
// ❌ 巨大的单一 store
export const useStore = create((set) => ({
  user: null, todos: [], theme: "light", cart: [], notifications: [],
}));

// ✅ 拆分
export const useUserStore = create((set) => ({ user: null, setUser: (u) => set({ user: u }) }));
export const useTodoStore = create((set) => ({ todos: [], addTodo: (t) => set((s) => ({ todos: [...s.todos, t] })) }));
```

## 参考

- 微信文章：使用 Zustand 时你必须遵循的 5 个强大最佳实践 ^[raw/articles/zustand-top-5-best-practices.md]
- 相关实体：[[zustand]]
