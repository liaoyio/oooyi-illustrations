# oooyi-illustrations

`oooyi-illustrations` 是一个为中文文章、帖子、博客、Notion 文档、工作流和方法论内容生成正文配图的 Codex Skill。它先理解文章里的认知锚点，再把一个判断、流程、结构、状态或隐喻，变成一张有记忆点的 16:9 手绘解释图，让小星把关键的认知动作做出来。

它适合写中文文章、做知识型内容和 AI 工作流内容的人，也适合想把抽象判断画成具体隐喻、围绕固定 IP 建立视觉识别的人。配图比 PPT 信息图更轻、更甜，方便在 Codex 内容生产中复用同一套视觉语言。

这套风格不适合暗黑、极简线稿或恐怖谷方向，也不用于传统 PPT 信息图、复杂架构图、正式流程图、商业插画、品牌 KV 和正式图表。它不是通用插画 prompt 或 PPT 模板，不适合把大段正文或完整课程塞进一张图，也不提供严格可编辑的矢量源文件。

[安装](#安装) · [画风与配色](#画风与配色) · [如何使用](#如何使用) · [图文案例](#图文案例) · [文件结构](#文件结构) · [来源与许可](#来源与许可)

## 安装

把下面这段直接发给 Codex：

```text
请用 $skill-installer 安装下面目录中的 Skill，名称为 oooyi-illustrations，供我在各项目中使用：
https://github.com/liaoyio/oooyi-illustrations/tree/main/oooyi-illustrations

安装后检查 SKILL.md、agents/、references/ 和 assets/ 是否完整。若已有同名 Skill，先比较差异，不覆盖本地修改。
```

真正安装的是仓库内的 `oooyi-illustrations/` 子目录，根目录文档和 `examples/` 用于分享与阅读。旧版用户重新安装后，改用 `$oooyi-illustrations` 调用；若未识别到新名称，重启 Codex 再试。出图需要宿主提供可用的图像生成工具。

## 画风与配色

默认是 16:9 横版、纯白背景和细黑手绘线稿，线条轻微抖动，不加纸纹、米色底、阴影或渐变。画面留白要多，主体（含小星与物件）约占 40%～60%；小星以远景全身的小小形象出现，高度不超过画面的 1/3。

小星（Xing）是浅金短碎发、带蓝灰挑染的小酷仔，戴星星发夹和星星耳坠，穿条纹衬衫、绿领巾和阔腿牛仔裤，脸上没什么表情，却在认真做着有点荒诞的事。人物全部用线稿勾形，淡绿只点缀领巾，淡蓝灰只点缀挑染；少量红、橙、蓝用于中文手写批注。换主题服装时，只换衣服，脸、短发与挑染、星星发夹、星星耳坠四项不动。

每张图只表达一个核心动作、结构、状态或隐喻，小星必须亲手执行核心动作，记忆点来自“小小的人与巨型物件”的体型反差。酷是他的样子，荒诞是他的处境；如果去掉小星后画面仍完全成立，说明人物太像装饰。

生图时原样复用 [CHARACTER LOCK（手绘版）](oooyi-illustrations/references/ip-character.md)，并在工具支持参考图时附上[全身基准图](oooyi-illustrations/references/character/front-fullbody.jpg)和[脸部验脸锚点](oooyi-illustrations/references/character/face-closeup.jpg)。基准图只取设计元素，小星仍须画成手绘小小形象，禁止 3D 或写实渲染。

中文越短越稳定，不要把一张图做成说明书。模型可能生成错字、幻觉标签、风格漂移或形象走样，出图后应先验脸，再验动作，最后验结构；角色走样时优先局部修正，修不好再重生成。

## 如何使用

规划时默认给一篇文章 4～8 张 shot list，写清每张图放在哪段后、主题、核心意思、结构类型、小星动作和中文标注建议。生成后交付最终 PNG，保存到 workspace 的 `assets/<article-slug>-illustrations/`，并说明每张图的用途和路径。

默认不输出 PPTX、PDF、Keynote、SVG、HTML 或 Canvas 可编辑图，也不做商业海报、封面 KV 或大段文字型信息图。

先做配图规划时，把正文粘在需求后：

```text
Use $oooyi-illustrations 先不要生图。
请分析下面这篇文章哪里值得配图，输出 5 张左右的 shot list。
每张图写清楚：放在哪段后、主题、核心意思、结构类型、小星在做什么、建议中文标注词。

<粘贴文章>
```

要直接生成一组正文配图，可以这样说：

```text
Use $oooyi-illustrations 把下面这篇文章生成 4 张小星正文配图。
要求：16:9 横版、纯白背景、黑色手绘线稿、少量红橙蓝中文手写批注。
每张图只讲一个核心结构，不要做 PPT 信息图。

<粘贴文章>
```

也可以围绕单个观点生成一张图：

```text
Use $oooyi-illustrations 为"信任不是喊出来的，而是一块证据一块证据铺过去"生成一张正文配图。
画面要酷但有反差感，小星必须亲手执行核心动作。
中文标注最多 5 个，短一点。
```

如果形象走样，明确指出要修正的位置：

```text
Use $oooyi-illustrations 这张图里小星的星星发夹画错了，
请对照基准图局部修正，其他内容保持不变。
```

更多需求示例见 [examples/prompts.md](examples/prompts.md)。

接到需求后，Skill 会读取正文、链接、Notion 内容、Markdown 或截图，提炼核心观点、认知转折、流程结构和适合视觉化的段落，再列出 shot list、选择结构类型，为每个认知锚点重新发明一个怪诞但成立的物理隐喻，让小星亲手执行动作。生图时每张单独调用图像模型，附上两张基准图作设计参考并复用 CHARACTER LOCK 原文；检查时先验脸、再验动作、最后验结构，保存最终 PNG 并报告用途和路径。

## 图文案例

下面四张是风格校准样例，用于理解线条、留白、颜色克制和小星气质。换文章时需要重新发明隐喻，不能照抄旧图的物件、构图或标注。

### 补上断点

![补上断点](examples/images/01-patched-breakpoints.png)

### 一鱼多吃

![一鱼多吃](examples/images/02-one-fish-many-uses.png)

### 信任桥

![信任桥](examples/images/03-trust-bridge.png)

### 内容发酵

![内容发酵](examples/images/04-content-fermentation.png)

## 文件结构

```text
.
├── README.md                       # 安装、画风、用法与案例
├── LICENSE                         # MIT 许可
├── NOTICE.md                       # 来源与原作者署名
├── CHANGELOG.md                    # 版本变更记录
├── examples/
│   ├── images/                     # 小星风格校准样例
│   ├── archive-xiaohei/            # 旧小黑示例归档，仅供历史参考
│   └── prompts.md                  # 可复制的需求示例
└── oooyi-illustrations/            # 安装到 Codex 的 Skill 子目录
    ├── SKILL.md                     # 入口、触发条件与生成流程
    ├── agents/
    │   └── openai.yaml              # 展示信息与默认调用
    ├── assets/
    │   ├── examples/                # Skill 内的小星校准样例
    │   └── archive-xiaohei/          # 旧小黑示例归档
    └── references/
        ├── ip-character.md          # 小星角色圣经与 CHARACTER LOCK
        ├── character/               # 全身基准图与脸部验脸锚点
        ├── style-dna.md             # 画风、配色、文字与禁忌
        ├── composition-patterns.md  # 构图、隐喻与体型反差
        ├── prompt-template.md       # 单张生图提示词模板
        └── qa-checklist.md          # 出图检查与迭代规则
```

## 来源与许可

本仓库 fork 自 [helloianneo/ian-xiaohei-illustrations](https://github.com/helloianneo/ian-xiaohei-illustrations)（MIT License），原作者 Ian。Fork 后角色、风格、提示词与示例已全部替换为原创 IP 小星（Xing）与手绘白底视觉体系。根据原 NOTICE 要求，在此保留对原作者的署名。

作者 **Yi** 是 AI Builder，用 AI 团队打造一人公司。GitHub：[liaoyio](https://github.com/liaoyio)。

本仓库使用 MIT License，见 [LICENSE](LICENSE)；署名与来源说明见 [NOTICE.md](NOTICE.md)。
