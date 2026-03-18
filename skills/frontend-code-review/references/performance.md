# 规则目录 — 性能

## React Flow 数据使用规范

IsUrgent: True
Category: Performance

### 说明

渲染 React Flow 时，UI 消费优先使用 `useNodes`/`useEdges`；在需要修改或读取 node/edge 状态的回调中使用 `useStoreApi`。避免在这些 hooks 之外手动拉取 Flow 数据。

## 复杂 props 必须做记忆化

IsUrgent: True
Category: Performance

### 说明

将复杂 props（对象、数组、Map 等）在传入子组件前用 `useMemo` 包裹，保证引用稳定并避免不必要的重渲染。

当新增、修改或删除性能规则时，请同步更新此文件，确保规则目录准确。

错误示例：

```tsx
<HeavyComp
    config={{
        provider: ...,
        detail: ...
    }}
/>
```

正确示例：

```tsx
const config = useMemo(() => ({
    provider: ...,
    detail: ...
}), [provider, detail]);

<HeavyComp
    config={config}
/>
```
