# goodzheng-dev-wiki

个人开发知识库，用于存储和沉淀自己在日常开发过程中编写的 Skill（技能）。

## 仓库用途

本仓库收录开发实践中总结出的可复用技能，包括但不限于：

- **编码辅助类**：代码规范检查、重构、生成模板等 Skill
- **工作流类**：构建、部署、提交等流程的自动化 Skill
- **问题排查类**：常见 Bug 定位、日志分析等经验沉淀

## 目录结构

```text
goodzheng-dev-wiki/
├── README.md                         # 仓库说明与 Skill 导航
└── skills/                           # 每个 Skill 一个独立目录
    ├── code-review-checklist/        # 编码辅助类（通用）
    ├── error-troubleshooting/        # 问题排查类（通用）
    ├── frontend-console-errors/      # 问题排查类（前端）
    ├── backend-api-troubleshooting/  # 问题排查类（后端）
    └── git-commit-helper/            # 工作流类（通用）
```

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
| 通用 | [git-commit-helper](skills/git-commit-helper/SKILL.md) | 分析 diff 生成 Conventional Commits 提交信息 |
| 前端 | （待添加） | |
| 后端 | （待添加） | |

**问题排查类**

| 技术栈 | Skill | 说明 |
| ------ | ----- | ---- |
| 通用 | [error-troubleshooting](skills/error-troubleshooting/SKILL.md) | 通用排查六步法，建议作为所有排查的入口 |
| 前端 | [frontend-console-errors](skills/frontend-console-errors/SKILL.md) | 控制台报错、白屏、请求失败的分流定位 |
| 后端 | [backend-api-troubleshooting](skills/backend-api-troubleshooting/SKILL.md) | 接口 5xx、响应慢、数据错误的分流定位 |
| 其他 | （待添加：数据库、运维、网络……） | |

**编码辅助类**

| 技术栈 | Skill | 说明 |
| ------ | ----- | ---- |
| 通用 | [code-review-checklist](skills/code-review-checklist/SKILL.md) | 按团队标准审查代码，输出分级反馈 |
| 前端 | （待添加） | |
| 后端 | （待添加） | |

> 排查类 Skill 存在「通用 → 技术栈」的递进关系：任何排查先走通用六步法，确认属于前端或后端场景后再进入特化分支，两者通过相对路径互相引用。

## 使用方式

每个 Skill 以独立子目录存放在 `skills/` 下，目录内包含 `SKILL.md` 描述技能的用途、触发时机与执行步骤。使用时将对应目录复制或引用至开发工具（如 Qoder）的 Skill 配置中即可。

## 维护说明

- 新增 Skill 时按三步归位：在 `skills/` 下创建独立目录 → 判断问题类型（工作流 / 问题排查 / 编码辅助）→ 判断技术栈（通用 / 前端 / 后端 / 其他），挂到导航表对应位置
- Skill 内容应描述清楚目标、适用场景与操作步骤；复杂流程优先写成「分流决策树 + 分支细则」的渐进式结构
- 通用 Skill 与技术栈特化 Skill 之间用相对路径互相引用，避免重复维护相同内容
