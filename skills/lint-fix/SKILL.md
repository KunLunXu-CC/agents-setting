---
name: lint-fix
description: 当出现 lint 报错、格式问题，或在提交代码前需要确保通过 CI 时使用。
---

# 修复 Lint 与格式问题

## 操作步骤

1. 检测项目是否配置 `prettier`, 如果有则运行 `npx prettier` 修复格式问题
2. 检测项目是否配置 `lint-staged`, 如果有则运行 `npx lint-staged` 修复 `lint` 问题
3. 报告仍需手动处理的修复项
