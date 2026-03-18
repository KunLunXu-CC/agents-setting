# 规则目录 — 代码质量

## 条件 className 必须使用工具函数

IsUrgent: True
Category: Code Quality

### 说明

条件 CSS 必须通过统一的 `classNames` 处理，不要用自定义三元表达式、字符串拼接或模板字符串。集中管理类名逻辑可以提升组件一致性并降低维护成本。

### 建议修复

```ts
import { cn } from '@/utils/classnames'
const classNames = cn(isActive ? 'text-primary-600' : 'text-gray-500')
```

## 优先使用 Tailwind 进行样式编写

IsUrgent: True
Category: Code Quality

### 说明

- 如项目中已配置 Tailwind 则优先使用 Tailwind
- 除非 Tailwind 组合无法实现目标样式, 否则不要新增任何样式文件。
- 将样式集中在 Tailwind 中可提升一致性并减少维护负担。

当新增、修改或删除代码质量规则时，请同步更新此文件，确保规则目录准确。

## className 排序应便于覆盖

### 说明

编写组件时，始终把传入的 `className` 放在组件自身类名之后，便于下游调用方覆盖或扩展样式。这样既保留默认样式，也允许外部修改或移除特定样式。

示例：

```tsx
import { cn } from '@/utils/classnames'

const Button = ({ className }) => {
  return <div className={cn('bg-primary-600', className)}></div>
}
```
