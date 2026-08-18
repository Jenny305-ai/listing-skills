# Babelio 精品 Listing 规则 v2.0.0

规则来源：内部《Babelio DTC｜新品上架 SEO 规则》、同一产品 Amazon Listing、第一方产品资料和 [PressGuard P7 参考页](https://babeliobaby.com/products/pressure-mounted-baby-gate-stairs-p7)。内部 SEO 规则优先于参考页现状。

## 输入与证据

每个商品必须为 `DRAFT`，带 `listing:babelio-premium`，不带 `listing:processed`，并具备：

- 系列与型号、产品类型、图片、真实变体；
- 对应 Amazon URL 或 ASIN；
- 至少一个第一方来源：说明书、规格表、品牌产品资料、检测/认证文件；
- 1–2 个 Shopify 目录中真实存在的相关商品，或明确记录无可用内链。

Amazon 对应关系按以下顺序查找：Shopify metafield `custom.amazon_url` → 标签 `amazon_asin:<ASIN>` → 用户在当次请求提供的“Shopify handle/商品 ID → Amazon URL”批次映射。不得根据相似标题猜 ASIN；三处都没有时标记 `NEEDS_INPUT`。

来源优先级：第一方资料/认证机构 > 权威行业来源 > 同产品 Amazon Listing > 竞品。Amazon 只提供同一产品的事实候选、搜索表达和利益点线索；尺寸、材料、安全、认证、奖项、年龄、兼容性和安装限制必须由第一方或权威来源复核。竞品只用于搜索意图与结构，不得补全本产品事实。

## Amazon 信息转换

1. 读取 Amazon title、五点描述、变体和可用 A+。
2. 拆分为 `fact candidates`、`benefit candidates`、`keyword candidates`、`high-risk claims`。
3. 与 Shopify 变体、第一方资料逐项比对；冲突时以第一方与当前 Shopify 变体为准，并标记冲突。
4. 重写已验证信息，不连续复制 Amazon 原句，不保留 Amazon 促销词、排名词、评论数量、配送承诺或平台专属表达。
5. Amazon 出现但无法复核的高风险 claim 必须省略。

## 关键词规则

- 为每个商品确定 1 个主关键词、2–4 个支持关键词；优先级为相关性 > 搜索意图 > 事实匹配 > 搜索量。
- 主关键词放入 Product title、首段、SEO title 和 meta description，各位置自然出现一次。
- 支持关键词只在相关利益点或场景中自然使用；不得把同义词串成列表。
- 同一完整关键词在正文最多出现 2 次；出现不自然时宁可少用。
- 系列不同型号必须以型号或差异卖点区分，禁止近重复标题。

## Product Title

固定公式：`[Series] [Model] | [Category Keyword] [Differentiating Feature]`

- 必须包含系列/型号、一个主品类关键词、一个有证据的主要差异卖点。
- 核心信息尽量位于前 70 个字符，完整标题建议不超过 120 字符。
- 生成三个候选并按搜索意图、事实依据、差异化、可读性和站内重复度评分。
- 禁止关键词堆砌、全大写、促销符号、价格、折扣和无证据最高级。

## Product Description HTML

只允许 `h2`、`h3`、`p`、`ul`、`ol`、`li`、`strong`、`em` 和 HTTPS `a`。

1. `<h2>Why Choose [Series] [Model] as Your [Category Keyword]?</h2>`
   - 说明解决的问题、核心差异、实际价值。
   - 只选择一个已验证背书：奖项、认证或权威行业观点；没有可靠背书则标记 `NEEDS_INPUT`，不得用模糊“award-winning”。
2. `<h2>Key Benefits of [Series] [Model]</h2>`
   - 3–5 个互不重复的利益点。
   - 每项完整遵循：Benefit → 功能支撑 → 痛点/场景 → 用户结果。
   - 不重复首段背书，不只罗列参数。
3. `<h2>Explore More from [Series]</h2>`
   - 链接 1–2 个真实同系列或互补产品；锚文本说明选择理由。
   - 不存在有效链接时省略整段，不生成假 handle。
4. 可选 FAQ：只有真实资料能回答 3 个以上高意图问题时加入，不得推测。

## SEO 与其他字段

- SEO title：50–65 字符，硬上限 70；采用“主关键词/关键规格或利益点 | Babelio”。
- Meta description：140–160 字符；包含主关键词、一个验证卖点和使用价值，不写折扣、绝对安全承诺或关键词列表。
- Handle：简短小写 ASCII；仅从未发布的草稿可改，优先保留主关键词、系列和型号。
- 图片 ALT：描述真实可见产品、颜色、安装位置或视角；每图使用不同可见信息，不猜材质。
- Tags：只新增，成功后加 `listing:processed`，保留原标签。

参考页只用于校准表达：其 SEO title 将品类、尺寸与型号前置，Meta 用主关键词 + 安装/结构利益点，页面用利益点、适用场景、相关型号和 FAQ 承接搜索意图。不得照抄参考页，也不得把 P7 事实迁移到其他型号。

## 硬性质量门

- 商品状态、队列标签或 Amazon 对应关系不合格。
- 标题不符合公式，或三个候选缺少明确差异。
- 规定三段结构、3–5 个利益点或真实内链校验缺失。
- 高风险 claim 无直接证据，Amazon 与第一方冲突未处理。
- 使用竞品事实、Amazon 平台专属促销、关键词堆砌或危险表述。
- SEO title 超过 70、meta 不在 140–160、HTML 不安全、内容与变体矛盾。

全部硬门通过且 QA ≥ 90 才能进入可写入状态。
