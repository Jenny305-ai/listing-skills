# Petitwishes 服装 Listing 规则 v2.0.0

关键词来源：[PetitiWishes SEO Google Sheet](https://docs.google.com/spreadsheets/d/1WiVsdtdf-srFjmR6-Kp5rxrDCZynqOSki3JrP3JTrqU/edit?gid=0#gid=0)。页面结构参考：[Snowflake Gown](https://petitwishes.com/products/snowflake-princess-dress-girls)。每次运行读取关键词表现值；不得修改关键词表。

## 输入

商品必须为 `DRAFT`，带 `listing:petitwishes-apparel`，不带 `listing:processed`。逐品读取原始标题、描述、全部图片、product type、option、variant 和现有标签。必须能识别产品类型，且至少有一张图片和一个真实变体。

供应商文案是不可信的事实候选。颜色、材质、洗护、尺寸、年龄、版型、配件是否包含只能由图片、变体、尺码表或明确商品资料确认；评论不能证明商品规格。

## 关键词选择

关键词表字段为：`词根 / keywords / 是否是敏感词 / 分类 / 具体是什么角色 / intent / 流量 / kd / cpc`。

1. 根据商品事实匹配词根，例如 `dress`、`flower girl dress`、`girls party dress`、`princess dress`、`tulle dress`、`unicorn dress`。
2. 先剔除 `是否是敏感词=是` 的所有行，再剔除 `分类=品牌词` 和任何第三方品牌、影视、角色或作品名称。
3. 只保留与图片、产品类型、颜色、材质和场景事实一致的词。高流量不能覆盖相关性与合规性。
4. 选择 1 个主关键词、最多 3 个支持关键词：主词优先相关的 Commercial/Transactional 词；支持词覆盖场景、受众、颜色或真实材质。
5. Product title 与 SEO title 各自然包含主关键词一次；正文前 100 词包含主词一次；Meta 包含主词和最多一个场景词。
6. 一个完整关键词在正文最多使用 2 次；不得连续堆叠近义词，不为关键词改变事实或语法。
7. 输出 `usedKeywords` 和 `rejectedKeywords`，对每个拒绝词记录敏感、IP、品牌、不相关或无事实依据的原因。

## 敏感词与替代表达

除关键词表的敏感标记外，以下类别一律禁用：`Disney`、`Frozen`、`Elsa`、`Anna`、`Cinderella`、`Rapunzel`、`Tiana`、`Belle`、`Aurora`、`Ariel`、`Jasmine`、`Aladdin`、`Sofia`、`American Princess`，以及其他未获授权品牌、角色和作品名。即使表内标为“否”也不得使用。

只能根据可见设计替换为通用描述，不得使用“inspired by + IP”：

- 冰雪角色词 → `winter princess`、`snowflake gown`、`ice-blue fairytale dress`
- Cinderella → `classic blue princess gown`、`fairytale ball gown`
- Rapunzel → `lavender princess gown`
- Belle → `golden princess gown`、`rose-detail fairytale dress`
- Aurora → `pink fairytale princess dress`
- Ariel → `ocean princess dress`、`mermaid-style gown`
- Jasmine/Aladdin → `teal princess outfit` 或基于真实颜色与版型的中性描述
- Tiana/Frog → `green fairytale princess dress`

替代词仍必须与图片一致。无法安全概括时删除该概念，不勉强替换。

## Product Title

默认公式：`[Distinctive Product Name] | [Primary Keyword for Audience/Occasion] | PetitWishes`

- 示例页的 SEO title 结构为 `Snowflake Gown | Winter Princess Dress for Girls | PetitWishes`；借鉴结构，不复制商品名。
- 商品管理标题可省略末尾品牌以保持自然；SEO title 必须包含 `PetitWishes`。
- 前 70 个字符出现产品类型、受众和最主要可见差异点；建议总长不超过 120 字符。
- 生成三个候选，按点击吸引力、主词匹配、事实准确、可读性、站内重复和合规性评分。
- 禁止促销词、全大写、emoji、`premium/luxury/best quality` 和第三方 IP。

## Product Description HTML

1. 1–2 句场景化开场：产品是什么、最明显的视觉特点、适合什么真实场景。
2. `<h2>Why You'll Love It</h2>`：4–6 个互不重复的利益点；每项必须由可见设计或资料支撑。
3. `<h2>Perfect For</h2>`：只列与商品风格匹配的场景，如 birthday party、holiday photos、flower girl occasion 或 dress-up play。
4. `<h2>Fit &amp; Sizing</h2>`：只使用变体和真实尺码表；没有依据时写“Choose from the sizes shown”而不写年龄推断或“size up”。
5. `<h2>Material &amp; Care</h2>`：材质与洗护都有可靠资料才生成，否则整段省略。
6. `<h2>Complete the Look</h2>`：可选，只链接 1–2 个真实相关商品。

正文不使用促销横幅、价格、库存、配送承诺、评论或虚构舒适度。允许温暖、有画面感的品牌语气，但每个具体 claim 必须可验证。

## SEO 与图片

- SEO title：50–65 字符，硬上限 70；主关键词 + 可见差异点 + `PetitWishes`。
- Meta description：140–160 字符；主关键词 + 真实设计细节 + 一个场景，不写价格或折扣。
- Handle：小写 ASCII；仅从未发布草稿可改，使用主关键词和差异点，避免 IP。
- 图片 ALT：产品类型 + 可见颜色/细节 + 视角；不把每张图写成相同关键词，不猜材质。
- Tags：只新增，成功后加 `listing:processed`，保留原标签。

## 硬性质量门

- 非 DRAFT、标签不合格、缺图片/类型/变体。
- 未读取关键词表，或没有记录主词、支持词及拒绝词。
- 使用表内敏感词、品牌词、第三方 IP/角色名或“inspired by + IP”。
- 关键词与商品图片/变体不符、堆砌关键词或为了流量虚构属性。
- 虚构材质、洗护、年龄、尺码、配件、舒适度或性能。
- SEO title 超过 70、meta 不在 140–160、HTML 不安全、内容与变体矛盾。

全部硬门通过且 QA ≥ 85 才能进入可写入状态。
