---
name: petitwishes-apparel-listing
description: 为一批 Petitwishes 服装 Shopify 草稿商品创建并质检准确的英文 Listing；自动读取 DSers 草稿内容，按指定 Google Sheet 关键词表选词并拦截敏感词与第三方 IP，批量生成或在当次明确授权后写回 DRAFT。覆盖强点击标题、HTML、SEO、尺码、内链和图片 ALT。
---

# Petitwishes 服装 Listing

每次处理 Shopify 商品列表中一个边界明确的 Petitwishes DRAFT 批次。默认仅生成整批预览，不得改动 Shopify。

## 操作流程

1. 完整读取 [references/rules.md](references/rules.md)。
2. 读取 Shopify 商品列表，将同时满足以下条件的商品作为唯一批次：状态为 `DRAFT`、包含 `listing:petitwishes-apparel`、不包含 `listing:processed`。任何条件无法确认时不纳入。默认每批最多 20 个商品，超过时只处理列表顺序最前的 20 个并报告剩余数量。
3. 逐个打开商品并建立批次清单，记录商品 ID、原始标题、状态和读取时间。跳过非 `DRAFT` 商品，不因单个失败终止整批。
4. 对每个商品读取原始标题、描述、图片、产品类型、选项和变体；不完整时标记 `NEEDS_INPUT`。只从这些输入提取可见款式属性，省略未知事实。
5. 读取规则指定的 Google Sheet 关键词表，按词根、相关性、意图、流量和 KD 选择关键词。先剔除 `是否是敏感词=是`、品牌词和第三方角色/IP，再生成文案。
6. 每个商品生成三个英文标题候选、规定 HTML、SEO、add-only 标签、安全 handle 和图片 ALT，并输出实际使用关键词清单。
7. 逐品执行硬性质量门。分数低于 85、出现敏感词、关键词与商品不匹配或任一硬门失败时，不得写入该商品。
8. 检查当前请求是否逐字包含 `允许写入 Shopify`：
   - 不包含：展示整批预览、逐品 QA 和统计后结束，不点击保存。
   - 包含：按清单逐个写入；每个商品保存前再次读取最新状态，只有仍为 `DRAFT` 且不存在未保存的人工修改时才保存。
9. 每个商品保存后只新增 `listing:processed`，重新读取并确认仍为 `DRAFT`。最后输出 `总数/已写入/NEEDS_INPUT/QA_FAILED/CONFLICT/SKIPPED` 汇总及逐品结果；无法验证时禁止声称成功。

## Shopify 写入边界

- 只允许更新标题、英文描述、SEO title、meta description、从未发布草稿的 handle、add-only 标签、高置信度 product type/category 和准确图片 ALT。成功后新增 `listing:processed`，保留所有原标签。
- 禁止修改状态、发布设置、销售渠道、价格、对比价、成本、库存、SKU、变体、图片文件或顺序。
- 禁止点击 `Publish`、`Set as active`、`Archive` 或同类控件。
- 最新状态不是 `DRAFT`、状态不可见、页面属于其他商品或发生人工编辑冲突时立即停止。
- 浏览器或 Shopify 控制能力不可用时，只输出可复制的 Listing，不尝试绕过限制。

优先提供清晰购买信息，避免空泛的时尚修辞。
