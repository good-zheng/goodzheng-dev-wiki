# goodzheng

个人开发知识库。内容分两个区：**项目**（按项目归档的架构、链路与部署笔记）和**其他**（跨项目复用的 Skill 与排查经验）。

## 目录结构

```text
goodzheng/
├── README.md                    # 本站首页与导航
├── 项目/
│   └── 叮叮厨/                   # 菜谱内容平台 + AI 做菜助手
│       ├── README.md            # 项目索引
│       ├── 架构与模块.md
│       ├── 云托管部署.md
│       └── 小程序平台坑.md
└── 其他/
    └── skills/                  # 每个 Skill 一个独立目录
        ├── code-review-checklist/
        ├── error-troubleshooting/
        ├── frontend-console-errors/
        ├── backend-api-troubleshooting/
        └── git-commit-helper/
```

分区原则：只有属于某个具体项目的笔记进 `项目/<项目名>/`；能被任意项目复用的方法论进 `其他/`。同一篇文档不要两处放副本，需要交叉引用时用相对路径链接。

## 项目

| 项目 | 说明 | 索引 |
| ---- | ---- | ---- |
| 叮叮厨 | 菜谱内容平台 + AI 做菜助手；微信小程序、Expo App、管理后台三端，Spring Boot 与 FastAPI 双后端 | [项目/叮叮厨/README.md](项目/叮叮厨/README.md) |

## Skill 导航（渐进式查找）

不确定该用哪个 Skill？按两步定位：先判断「问题类型」分流，再按「技术栈」命中具体条目。

### 第一步：判断问题类型

```text
我要解决的是……
├── 一件事：要走完某个开发流程（提交、审查、构建、部署） → 工作流类
├── 一个错：报错、异常行为、性能劣化，要找根因        → 问题排查类
└── 一段代码：要编写、改进或检查代码                 → 编码辅助类
```

### 第二步：按技术栈命中

技术栈分三档：**通用**（前后端均适用）、**前端**、**后端**；后续可按需扩展数据库、运维等档位。

**工作流类**

| 技术栈 | Skill | 说明 |
| ------ | ----- | ---- |
| 通用 | [git-commit-helper](其他/skills/git-commit-helper/SKILL.md) | 分析 diff 生成 Conventional Commits 提交信息 |
| 前端 | （待添加） | |
| 后端 | （待添加） | |

**问题排查类**

| 技术栈 | Skill | 说明 |
| ------ | ----- | ---- |
| 通用 | [error-troubleshooting](其他/skills/error-troubleshooting/SKILL.md) | 通用排查六步法，建议作为所有排查的入口 |
| 前端 | [frontend-console-errors](其他/skills/frontend-console-errors/SKILL.md) | 控制台报错、白屏、请求失败的分流定位 |
| 后端 | [backend-api-troubleshooting](其他/skills/backend-api-troubleshooting/SKILL.md) | 接口 5xx、响应慢、数据错误的分流定位 |
| 其他 | （待添加：数据库、运维、网络……） | |

**编码辅助类**

| 技术栈 | Skill | 说明 |
| ------ | ----- | ---- |
| 通用 | [code-review-checklist](其他/skills/code-review-checklist/SKILL.md) | 按团队标准审查代码，输出分级反馈 |
| 前端 | （待添加） | |
| 后端 | （待添加） | |

> 排查类 Skill 存在「通用 → 技术栈」的递进关系：任何排查先走通用六步法，确认属于前端或后端场景后再进入特化分支，两者通过相对路径互相引用。

## 使用方式

Skill 以独立子目录存放在 `其他/skills/` 下，目录内的 `SKILL.md` 描述技能用途、触发时机与执行步骤；使用时把对应目录复制或引用到开发工具（如 Qoder）的 Skill 配置里。

## 维护说明

- 新增 Skill 时按三步归位：在 `其他/skills/` 下创建独立目录 → 判断问题类型（工作流 / 问题排查 / 编码辅助）→ 判断技术栈（通用 / 前端 / 后端 / 其他），挂到上方导航表
- Skill 内容应写清目标、适用场景与操作步骤；复杂流程优先写成「分流决策树 + 分支细则」的渐进式结构
- 新增项目时在 `项目/` 下建目录并补一份 `README.md` 索引，同时把这一行挂到上方「项目」表
- 通用 Skill 与技术栈特化 Skill 之间用相对路径互相引用，避免重复维护相同内容
