# 提交信息示例

## 示例 1：缺陷修复

变更内容：修复报表页时区转换导致的日期显示错误

```text
fix(reports): correct date formatting in timezone conversion

Use UTC timestamps consistently across report generation.
```

## 示例 2：重构

变更内容：将重复的参数校验逻辑抽取为独立函数

```text
refactor(api): extract shared param validation into helper

Move duplicated validation blocks from controllers into a
single helper to reduce maintenance cost.
```

## 示例 3：杂项

变更内容：升级 ESLint 至 v9 并适配新配置格式

```text
chore: upgrade ESLint to v9 with flat config

Migrate .eslintrc to eslint.config.js and update plugin deps.
```

## 反例

不要生成这样的提交信息：

```text
更新了一些文件          # 无类型、无具体内容
fix: 修复 bug           # 没说明修复了什么
feat: add feature       # 空洞，缺少 scope 与细节
```
