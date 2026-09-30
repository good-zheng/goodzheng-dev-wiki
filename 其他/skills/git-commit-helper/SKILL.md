---
name: git-commit-helper
description: 分析 git diff 并生成符合 Conventional Commits 规范的提交信息。当用户请求编写 commit message、提交代码，或提到"提交"、"commit"、"写提交信息"时使用。
---

# Git 提交信息助手

适用范围：通用（不区分技术栈）。

## 工作流程

1. 运行 `git status` 与 `git diff --staged` 查看变更；若暂存区为空，改用 `git diff` 并提醒用户先暂存
2. 归纳变更内容，判断提交类型
3. 按下方模板生成提交信息，供用户确认后再执行 `git commit`

## 提交类型

| 类型 | 说明 |
| ---- | ---- |
| feat | 新功能 |
| fix | 缺陷修复 |
| docs | 文档变更 |
| style | 代码格式（不影响逻辑） |
| refactor | 重构（非新增功能、非修复） |
| perf | 性能优化 |
| test | 测试相关 |
| chore | 构建、依赖、工具链等杂项 |

## 提交信息模板

```text
<type>(<scope>): <一句话概括，50 字符以内，不加句号>

<正文：说明改了什么、为什么改，每行 72 字符以内>
```

## 约束

- 标题使用祈使句（如 add、fix），不写"添加了"、"修复了"
- 一次提交只做一件事；发现混杂变更时建议用户拆分提交
- 不使用 `--no-verify` 跳过钩子

## 中文标题 + commitlint 的坑

配置了 `@commitlint/config-conventional` 的仓库（锚点：`.commitlintrc.cjs` 的 `extends`、`.husky/commit-msg`），`subject-case` 规则会校验标题首词的字母大小写形态。中文标题里以大写拉丁词开头会被拒：

- `feat: Taro 微信小程序端与用户审批契约` → ✖ subject must not be sentence-case
- `feat: 新增 Taro 微信小程序端与用户审批契约` → ✔
- `feat: App 封面上传接线` → ✖，改成 `feat: 移动端封面上传接线` → ✔

原因是规则把开头的大写拉丁词判成 sentence-case，与后面接的是不是中文无关。生成中文标题时让首字为汉字，把英文技术名放到句中或加动词前缀。

钩子失败时提交并没有发生，因此修好标题后重跑 `git commit`，不要用 `--amend`（那会改到上一条已存在的提交）。

## 示例

输入：新增了基于 JWT 的登录接口

```text
feat(auth): add JWT-based login endpoint

Add login route and token validation middleware.
```

更多示例见 [examples.md](examples.md)。
