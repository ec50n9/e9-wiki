---
source_url: https://mp.weixin.qq.com/s/Tj3oenAjaa2MpVCeYs_h-g
ingested: 2026-04-28
sha256: dd20560e4fca6dc25cf14b81e8792766f9d52893006d067cc494721ea58873fa
---

# 使用 Zustand 时你必须遵循的 5 个强大最佳实践

学习 Zustand 的 TOP 5 最佳实践，并配合简单示例快速上手。

Zustand 为 React 提供了简单且强大的 state 管理。它足够快、足够易用，但如果使用方式不对，你依然会踩坑。

下面是 5 个清晰习惯，能让你的 store 保持干净且可扩展。每一条都包含“不该怎么做”和“正确做法”。

1. 只导出 custom hooks

不要把整个 store 暴露给每个 component。使用 custom hooks，只返回你真正需要的值。

❌ 不要导出整个 store

export const useTodoStore = create((set) => ({  todos: [],  addTodo: (t) => set((s) => ({ todos: [...s.todos, t] })),}));

✅ 使用带 selector 的 custom hooks 导出

export const useTodoStore = create((set) => ({  todos: [],  addTodo: (t) => set((s) => ({ todos: [...s.todos, t] })),}));
export const useTodos = () => useTodoStore((s) => s.todos);export const useAddTodo = () => useTodoStore((s) => s.addTodo);

收益：你的 components 会更轻量，并且只在必要时 re-render。

2. 使用 atomic 且 stable 的 selectors

不要在 selector 里返回对象。每次新建对象都会强制触发一次 re-render。

❌ 不要返回新对象

const { todos, isSubscribed } = useStore((state) => ({  todos: state.todos,  isSubscribed: state.isSubscribed,}));

✅ 使用拆分后的 atomic selectors

const todos = useStore((s) => s.todos);const isSubscribed = useStore((s) => s.isSubscribed);

收益：你的 UI 会保持流畅，并避免无意义的 re-render。

3. 将 actions 与 state 分离

把所有 actions 放进一个稳定对象。这样可以让你的 store 更干净、更稳定。

❌ 不要把 actions 与原始 state 字段混在一起

// ❌ 难以追踪，变更会导致很多 components 重新渲染export const useStore = create((set) => ({  todos: [],  addTodo: (t) => set((s) => ({ todos: [...s.todos, t] })),  removeTodo: (id) => set((s) => ({ todos: s.todos.filter((t) => t.id !== id) })),}));

✅ 使用稳定的 actions 对象

export const useStore = create((set) => {  const actions = {    addTodo: (t) => set((s) => ({ todos: [...s.todos, t] })),    removeTodo: (id) =>      set((s) => ({ todos: s.todos.filter((t) => t.id !== id) })),  };
  return {    todos: [],    actions,  };});

收益：当别处的 state 变化时，actions 不会触发额外 re-render。

4. 把 actions 建模为 events

不要使用简单 setter。使用能够描述事件语义的 actions。

❌ 不要写基础 setters

setTodo: (todo) => set({ todo });

✅ 编写事件语义 actions

addTodo: (text) =>  set((s) => ({ todos: [...s.todos, { id: Date.now(), text }] })),
removeTodo: (id) =>  set((s) => ({ todos: s.todos.filter((t) => t.id !== id) })),

收益：你的 components 会更干净，业务逻辑也会更集中在 store 中。

5. 让 store 保持小而专注

不要让一个 store 无限膨胀。拆分成多个小 store，结构会更清晰。

❌ 不要创建一个巨大的 store

export const useStore = create((set) => ({  user: null,  todos: [],  theme: "light",  cart: [],  notifications: [],}));

✅ 将逻辑拆分到多个小 stores

export const useUserStore = create((set) => ({  user: null,  setUser: (u) => set({ user: u }),}));
export const useTodoStore = create((set) => ({  todos: [],  addTodo: (t) => set((s) => ({ todos: [...s.todos, t] })),}));

收益：你的代码会更易测试，store 也会更加稳定。
