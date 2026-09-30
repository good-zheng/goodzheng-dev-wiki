# 团队编码规范（审查依据）

## 命名

- 变量、函数用 camelCase；类、类型用 PascalCase；常量用 UPPER_SNAKE_CASE
- 布尔值以 is/has/should 开头，如 `isLoading`、`hasPermission`
- 禁止无意义缩写：`u`、`data2`、`tmp1`

## 函数

- 单函数不超过 80 行；参数不超过 4 个，超出时收拢为对象
- 优先纯函数；副作用集中在入口层（controller、handler）

## 错误处理

- 禁止空 catch；至少记录日志或向上抛出
- 对外错误信息不暴露内部实现细节（堆栈、SQL、路径）

## 依赖与导入

- 未使用的导入与依赖必须移除
- 禁止循环依赖；跨层引用只能自上而下（如 api -> service -> dao）

## 注释

- 只解释"为什么"，不复述"是什么"
- 遗留 TODO 必须附带负责人与背景：`// TODO(goodzheng): 等待支付网关 v2 上线后移除`
