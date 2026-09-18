---
name: frontend-console-errors
description: 排查浏览器控制台报错与前端页面异常（请求失败、白屏、JS 运行时错误、框架报错等）。当用户提到"控制台报错"、"页面白屏"、"请求失败"、"前端报错"时使用。
---

# 前端控制台报错排查

适用范围：前端（浏览器端 Web 应用）。先走通用排查六步法（见 [error-troubleshooting](../error-troubleshooting/SKILL.md)），本 Skill 提供前端场景的分流定位。

## 第一步：按报错类型分流

```text
控制台输出
├── 红色网络错误（Failed to load / 4xx / 5xx / CORS policy）
│   → 走「网络请求类」
├── Uncaught TypeError / ReferenceError 等运行时错误
│   → 走「运行时错误类」
├── 框架专属报错（React hooks / hydration / Vue warn）
│   → 走「框架错误类」
└── 页面无输出，白屏 / 不渲染
    → 走「白屏类」
```

## 网络请求类

1. 在 Network 面板确认状态码与响应体：4xx 是请求侧问题；5xx 是服务端问题
2. 5xx 时携带 traceId / 时间点 / 路由转后端排查（见 [backend-api-troubleshooting](../backend-api-troubleshooting/SKILL.md)），不要在前端反复重试
3. CORS 报错经常掩盖真实失败：先看 Network 面板里该请求的真实状态码，再判断是跨域配置问题还是接口本身报错

## 运行时错误类

1. 点击堆栈定位到源码行（dev 环境需开启 sourcemap）
2. TypeError 常见根因：异步数据未返回就渲染、可选链缺失、事件回调里 this 指向丢失
3. 复现路径固定时，在出错行上方打印相关变量，确认空值/undefined 的来源

## 框架错误类

- React "Cannot update a component while rendering"：渲染期间触发了父组件的 setState
- hydration mismatch：服务端与客户端输出不一致，排查 Date.now() / Math.random() / localStorage 的使用
- key 警告虽不阻塞，但常伴随列表渲染错乱：用稳定的业务 id 做 key，不要用数组下标

## 白屏类

1. 开发模式复现，先看是否存在构建错误（依赖缺失、循环 import）
2. 生产环境白屏多为未捕获的渲染异常：接入 ErrorBoundary / window.onerror 收集首错堆栈
3. 白屏伴随静态资源 404 时，检查发布产物路径与 CDN 配置

## 输出

排查结论沿用通用流程的汇报格式（根因 / 证据 / 修复 / 遗留风险）。
