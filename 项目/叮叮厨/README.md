# 叮叮厨

菜谱内容平台 + AI 做菜助手。一端内容、三端界面、双后端服务，前后端共用一套类型契约。

| 目录 | 角色 | 技术栈 |
| --- | --- | --- |
| `apps/cooking-mini/` | 微信小程序 | Taro 4.2.1 + React 18 + webpack5 |
| `apps/cooking-app/` | 移动端 App | Expo SDK 57 + React Native + expo-router + NativeWind |
| `apps/admin-web/` | 管理后台 | Umi Max 4 + React 19 + Ant Design 6 + React Query 5 |
| `apps/brand/` | 项目/个人介绍站 | Astro 7 + Tailwind CSS 4（AstroWind 模板，静态站） |
| `services/api/` | 主后端 | Java 17 + Spring Boot 4.1.1 + MyBatis-Plus + MySQL + Redis |
| `services/chat/` | AI 聊天服务 | FastAPI + Uvicorn(5090) + LangChain/LangGraph |
| `packages/types/` | 跨端契约 `@po/types` | 字段变更先改这里，三端与后端再跟进 |

工程形态是 pnpm workspace monorepo（Node ≥ 22，pnpm ≥ 10），本地开发用根目录 `.env` + `docker compose` 起 MySQL/Redis。

## 笔记

- [架构与模块](架构与模块.md) — 模块划分、认证与登录 gating、聊天与 TTS 链路、持久层约定
- [云托管部署](云托管部署.md) — 镜像构建与推送到微信云托管、内网地址形态、小程序合法域名规则
- [小程序平台坑](小程序平台坑.md) — WXSS 不支持的语法、构建产物与审核项、环境变量注入规则

## 阅读顺序建议

先读「架构与模块」的登录 gating 和聊天链路两节——这两处决定了大部分跨端行为；要上线或排查线上问题再翻「云托管部署」；只在写小程序界面或提审前才需要「小程序平台坑」。

## 约定

密钥一律只存在各自的 `.env`（根目录那份只给 docker compose 用），文档与提交里不出现任何密钥值。云托管的域名、环境 ID、镜像仓库名这类平台常量必须从控制台逐字复制，不能凭记忆填写。
