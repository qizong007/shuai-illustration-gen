---
name: shuai-illustration-gen
description: 生成风格统一的复古编辑概念插画：暖米白纸底、黑白灰主体、有明确视觉分量的朱红强调、手工剪纸拼贴与印刷颗粒。用于文章配图、概念表达、系列插画，或用户指定 shuai 插画风格时；也可按要求仅输出提示词。
---

# Shuai Illustration Gen

把主题转化为一个清晰的视觉隐喻，使用固定的 Vintage Editorial Paper Collage 视觉规范生成插画。稳定性优先：同一系列保持配色、纸张质感、层次和留白一致，主要改变主体与表达内容。

## 确定画面

- 从用户主题、文章或段落中提取要表达的一个核心意思。已有明确画面描述时直接采用，不强行改成隐喻。
- 默认采用简单构图。选一个主要关系（如失衡、连接或遮挡），只保留看懂这个关系需要的物件，背景留出整块米白。
- 用户要求画图时直接生成；仅在用户要求提示词时只交付提示词。
- 默认一张无字插画。画幅优先服从用户要求或既有系列；无上下文时默认横向 3:2。数量、画幅、文字和主体是任务变量，不是风格规范。
- 不自动添加标题、标签、Logo、水印或装饰文字。用户指定文字时逐字保留。
- 若主题完全缺失且上下文无法推断，只询问主题；其他不影响执行的信息自行合理补齐。
- 用户本次明确指定的视觉变化优先于下方默认规范；只改指定项，不悄悄改写整套风格。

## 固定风格前缀

每张图使用下列完整前缀，再追加后面的内容块。不要仅用“复古”“剪纸风”等宽泛词替代，也不要为不同主题重新发明配色。本文件包含完整风格规范，默认只依赖文字，不需要读取参考图片或其他风格文件。

```text
VISUAL STYLE: Vintage Editorial Paper Collage.

Create a conceptual editorial illustration with a consistent handmade cut-paper collage aesthetic, as part of the same independent magazine illustration series.

PALETTE — use these five target colors as the only designed palette:
- Background Ivory: #FBF8F1 — the full canvas background.
- Ink Black: #171717 — primary silhouettes and high-contrast shapes.
- Paper White: #F7F5EF — light paper cutouts and highlights.
- Warm Gray: #BDB9B0 — secondary shapes and understated paper shadows.
- Accent Red: #D32918 — purposeful, clearly visible focal accents, including selected whole paper shapes.

Keep generous ivory negative space. Build the main silhouettes in ink black, paper white and warm gray. Aim for vermilion across roughly 10–20% of the whole canvas by visual estimate. Concentrate it on one focal shape or a few closely related parts read as a group. Keep the background consistently #FBF8F1 with subtle grain and soft paper shadows.

MATERIALS AND RENDERING:
Hand-cut paper shapes with slightly irregular edges, overlapping paper layers, subtle paper thickness and soft short contact shadows. Predominantly flat 2D shapes with only shallow paper relief. Fine natural paper grain, delicate vintage print noise and slightly uneven ink coverage. Matte, tactile surfaces. Texture must remain subtle enough that the background looks clean and the main shapes stay readable.

COMPOSITION:
Build one simple visual metaphor. Keep a clear silhouette and only the supporting objects needed to read the relationship. Use overlap deliberately, leave a broad unbroken area of ivory and keep the focal shape legible at thumbnail size.

ART DIRECTION:
Restrained vintage editorial illustration, conceptual magazine artwork, handmade mixed-media paper collage, minimal screen-print texture, subtle surrealism when useful to the subject. Calm, thoughtful and inventive rather than cute or promotional.

AVOID:
Additional blue, green, purple, yellow or orange hues; colorful gradients; neon; photorealism; glossy or volumetric 3D; glass, plastic or metallic finishes; smooth vector-perfect edges; cartoon mascots or chibi characters; watercolor washes; heavy distressed stains; busy backgrounds; excessive decorations; unintended text, logos or watermarks. People, when requested or necessary, should use simplified editorial paper-cut silhouettes rather than cartoon styling.
```

这些 HEX 是文档给出的目标色，不是已验证的原图取色结果。图像模型不保证逐像素复现；不能声称图片已通过精确色彩校验。不要为了精确五色而默认量化整张图，破坏纸纹与轻微阴影。用户明确要求像素级色值时，另行处理并实际测量。

## 红色的使用判断

- **面积**：以包含米白留白的整幅画面为基准，目测朱红约占 10%–20%。这是构图目标，纸纹、阴影和边缘可自然过渡。
- **落点**：先选一个值得强调的形体，或几块表达同一关系的纸片，再决定红色落在哪里。需要增加红色时，优先扩大已有焦点；红色过重时，把外围细节收回黑白。

## 每次替换的内容块

```text
SUBJECT: [具体主体与动作]
MESSAGE: [画面要传达的一句话]
VISUAL RELATIONSHIP: [主体之间的关系或视觉隐喻]
COMPOSITION AND FORMAT: [画幅、主次、留白位置；沿用系列已有设置]
RED ACCENT: [哪些完整纸片或关联细节用 #D32918；为什么强调它们；哪些部位保持黑白]
TEXT: [默认 no text；需要文字时填逐字原文]
REFERENCE ROLE: [仅当有参考图时填写：风格参考 / 待编辑图 / 主体参考]
TASK OVERRIDES: [仅填写用户明确要求改变的默认项；无则省略]
```

主题示例：表达“注意力被分散”时，用一张黑色人形剪纸面对几片向不同方向拉开的纸片，把其中一组有意义的纸片设为红色，其余保持黑白。不要自动加入写满文字的通知面板。此例只说明如何选隐喻，不固定以后所有画面的主体。

## 生成

- 使用当前可用的图像生成工具实际出图；在 Codex 中优先使用内置 `image_gen`。若环境提供 `imagegen` skill，遵循其工具调用与文件交付要求。不要用 SVG、HTML 或文字说明冒充已生成的插画。
- 默认直接使用本文件的文字规范，不查找、下载或读取历史试稿作为风格参考，也不依赖固定图片路径。
- 仅当用户本次提供或指定参考图、要求编辑现有图片时，查看并传入对应图像，明确其用途及需要保留的内容；不要把参考图中的物体或文字默认带入新主题。
- 批量生成时保持同一风格前缀及工具实际支持的相同模型和设置，各张独立使用文字规范，不逐代引用上一张造成风格漂移。
- 工具不暴露模型版本、seed 或精确尺寸时，不虚构或声称已锁定这些参数。
- 图像工具不可用时明确说明；可交付完整提示词，但不能把它当作出图完成，也不擅自切换付费 API。

## 检查与交付

查看生成结果，重点检查：暖米白背景是否稳定；是否出现额外彩色；朱红目测是否约占整幅 10%–20%、是否集中在主题形体上；纸纹和阴影是否克制；是否像剪纸拼贴；缩小后主体关系是否一眼可辨、能否删去分散注意力的配件；是否有多余文字。系列作品应并排比较配色、主体尺度、留白和材质的一致性。

有明显偏差时，保留固定前缀，只针对偏差修正，最多自动重试两次。仍不合格则如实说明未解决项，避免无限重绘。无法查看结果时，说明尚未完成视觉检查。

直接展示成图。需要保存到项目时按用户指定位置保存；未指定则使用项目内 `output/illustrations/`，采用主题命名且不覆盖已有文件。同时保存实际使用的完整提示词为同名 `.prompt.txt`，记录可用的参考来源和真实工具设置，便于复用。最终回复简短给出图片和保存位置；只输出提示词的任务无需生成图片文件。
