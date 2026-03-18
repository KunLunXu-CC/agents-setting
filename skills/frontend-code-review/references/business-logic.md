# 规则目录 — 业务逻辑

## Node 组件中不能使用 workflowStore

IsUrgent: True

### 说明

Node 组件路径模式：`web/app/components/workflow/nodes/[nodeName]/node.tsx`

Node 组件在基于模板创建 RAG Pipe 时也会被复用，但该场景下不存在 workflowStore Provider，会导致页面白屏。[这个 Issue](https://github.com/langgenius/dify/issues/29168) 正是由此引发。

### 建议修复

使用 `import { useNodes } from 'reactflow'`，不要使用 `import useNodes from '@/app/components/workflow/store/workflow/use-nodes'`。
