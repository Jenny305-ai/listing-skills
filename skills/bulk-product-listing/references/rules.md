# Babelio 铺货 Listing 规则 v2.0.0

遵循内部《Babelio DTC｜新品上架 SEO 规则》，流程与 Petitwishes 批量草稿处理相似，但使用 Babelio 标题公式、E-E-A-T、三段式描述和品牌内链。铺货模式不做逐 SKU 深度竞品研究。

## 输入与选词

商品必须为 `DRAFT`，带 `listing:bulk`，不带 `listing:processed`，并具备可识别产品类型、图片和真实变体。读取原始标题、描述、图片、product type、option、variant 和现有标签。

- 只使用 Shopify/DSers 已有事实、第一方供应商规格和已审核关键词；供应商营销话术只是候选。
- 每品确定 1 个主品类关键词和最多 3 个支持词，优先相关性、购买意图和自然表达。
- 主词进入标题、首段、SEO title、Meta；正文完整主词最多 2 次。
- 不使用竞品品牌、角色/IP、无证据最高级或关键词串。

## Product Title

固定结构：`[Series/Product Name] [Model if known] | [Category Keyword] [Differentiating Feature]`

- 没有系列/型号时使用可验证的产品名，不得虚构型号。
- 必须包含一个主品类词和一个真实差异点，核心信息位于前 70 字符。
- 生成三个候选并按相关性、事实、差异化、英语可读性和站内重复评分。

## Product Description HTML

1. `<h2>Why Choose [Product Name] as Your [Category Keyword]?</h2>`：说明问题、真实差异点和用户价值。只有存在可靠来源时才加入奖项、认证或权威观点；铺货商品不因缺少背书而失败，直接省略背书句。
2. `<h2>Key Benefits of [Product Name]</h2>`：3–5 个利益点，每项遵循 Benefit → 功能支撑 → 场景/痛点 → 结果。
3. `<h2>Explore More from Babelio</h2>`：可选，只链接真实存在的 1–2 个同系列或互补商品；无有效链接则省略。

只允许安全语义 HTML。未知材质、洗护、尺寸、认证、奖项、年龄、兼容性和安全性必须省略，不使用竞品事实补全。

## SEO 与商品字段

- SEO title：50–65 字符，硬上限 70；主词 + 真实差异点 + `Babelio`。
- Meta description：140–160 字符；主词 + 一个可验证卖点 + 使用价值。
- Handle：小写 ASCII；仅从未发布草稿可改。
- 图片 ALT：只描述可见产品、颜色、场景和视角，不猜材质。
- Tags：只新增，成功后加 `listing:processed`，保留原标签。

## 硬性质量门

- 非 DRAFT、标签不合格、缺少图片/类型/变体。
- 标题不符合 Babelio 公式，或没有主关键词和真实差异点。
- 缺少两段必需描述结构、少于 3 个利益点。
- 虚构事实、使用竞品事实、危险 claim、敏感/IP 词或关键词堆砌。
- SEO title 超过 70、meta 不在 140–160、HTML 不安全、内容与图片/变体矛盾。

全部硬门通过且 QA ≥ 85 才能进入可写入状态。
