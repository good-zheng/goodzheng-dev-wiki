# 审查反馈示例

以一个"订单查询接口"的变更为例，展示反馈格式。

## 变更摘要

新增 `GET /api/orders`，按用户 ID 查询订单列表，含分页。

## 反馈输出示例

**Critical**

- `orderService.ts:42` — SQL 使用字符串拼接用户输入的 `status` 参数，存在 SQL 注入风险。触发条件：`status` 传入 `'; DROP TABLE orders; --`。应改用参数化查询。

**Suggestion**

- `orderService.ts:57` — 分页参数 `pageSize` 未设上限，传 `pageSize=100000` 会拖垮数据库。建议上限 100。
- `orderController.ts:18` — `getUserOrders` 与既有 `getUserProfile` 的鉴权逻辑重复，可复用 `requireAuth` 中间件。

**Nice to have**

- `orderService.ts:30` — `page * pageSize + 1` 可提取为 `offset` 常量，提升可读性。

## 反例

不要输出这样的反馈：

- "代码写得不好" —— 没有定位、没有原因、没有改进方向
- "建议使用更好的架构" —— 空泛，不具可操作性
- 把 Nice to have 混入 Critical —— 虚高严重级别会稀释真正的风险
