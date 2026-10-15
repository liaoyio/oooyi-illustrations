# 生图提示词模板（小星手绘白底版）

每张图单独生成。根据正文内容替换变量，不要把多张图拼在一起。

CHARACTER LOCK（手绘版）每次原样复用，一字不改。管线支持参考图时，附上 `references/character/` 的两张基准图（全身＋脸部特写）作为设计参考，其中脸部特写为验脸锚点；注意基准图仅取设计元素，画风一律按手绘线稿走。

```text
Generate one standalone 16:9 horizontal Chinese article illustration: black hand-drawn line art on pure white background.

CHARACTER LOCK, hand-drawn render (reuse verbatim, do not alter):
Xing, a tiny cool boy drawn in loose black hand-drawn line art (slightly wobbly pen lines; NOT 3D, NOT photorealistic, NOT polished render; draw him as a BOY, never as a little girl): short tousled blonde hair with a blue-grey streak doodle in the front bangs; silver star hair clip doodle on the left side; star drop earring doodle on the left ear; boyish face, big eyes with a distant deadpan gaze, blush lines and freckle dots on cheeks; oversized pinstripe shirt doodle; green neckerchief (light green wash ONLY on the neckerchief); baggy jeans; white sneakers; cool expressionless face. Tiny figure in a wide shot: full body no more than ~1/3 of the canvas height (aim ~1/4); never a close-up.

Visual DNA:
Pure white background. Minimalist black hand-drawn line art, slightly wobbly pen lines. Lots of empty white space. Sparse handwritten Chinese annotations in red/orange/blue. Light green wash only on Xing's neckerchief, light blue-grey only on the hair streak; everything else black on white. Clean absurd product-sketch feeling. No gradients, no shadows, no paper texture, no complex background, no commercial vector style, no PPT infographic look, no 3D render, no photorealism.

Theme:
{正文配图主题}

Structure type:
{结构类型：Workflow / 系统局部 / 前后对比 / 角色状态 / 概念隐喻 / 方法分层 / 地图路线 / 小漫画分镜}

Core idea:
{这张图要表达的核心意思}

Composition:
{具体画面：小小的小星在哪里、正在做什么、主要物件是什么、信息如何流动。善用"小小的人 vs 巨型物件"的体型反差制造记忆点}

Suggested elements:
{元素1} / {元素2} / {元素3} / {元素4}

Chinese handwritten labels:
{标注词1} / {标注词2} / {标注词3} / {标注词4}

Color use:
Black for main line art and Xing. Light green wash only on Xing's neckerchief; light blue-grey only on the hair streak. Red only for key warnings/problems/results. Orange for main flow/path/arrows. Blue only for secondary notes or feedback/system state.

Constraints:
One image explains only one core structure. Xing must perform the core conceptual action, not decorate the scene. GLOBAL SIZE RULE: compose a WIDE establishing shot first — lay out the full scene (conveyor, bridge, jar, stamp, etc.) spanning the canvas — then place Xing inside it as a tiny full-body figure. Xing's full body must occupy NO MORE than 1/3 of the canvas height (aim for ~1/4). If he comes out bigger, the image fails: shrink him, never enlarge the scene around him. No close-ups, no portrait framing, no bust shots — full body, far away, always. Keep the main subject (Xing + objects) around 40%-60% of the canvas with at least 35% blank white space. At most 5-8 short handwritten Chinese labels. Do not write a title in the top-left corner. Do not write the structure type on the image. Do not make it a formal diagram, course slide, or dense explainer. Do not render Xing as a 3D doll or a photorealistic person; he must be hand-drawn line art. Do not copy prior examples; invent a fresh visual metaphor for this specific article. It should be clear but not instructional, interesting but not childish, strange but clean.
```

## 图像编辑提示

去掉左上角标题：

```text
Edit the provided image. Remove only the handwritten title "{要删除的文字}" and its underline from the top-left corner. Fill that area with the same clean white background, matching the surrounding blank paper. Preserve everything else exactly: characters, labels, paths, line style, composition, aspect ratio, and image quality. Do not add any new text or objects.
```

修正形象走样：

```text
Edit the provided image. Fix only this character issue: {具体走样项，如星星发夹缺失 / 挑染没有 / 绿领巾画错}, making Xing match the reference design. Keep her as tiny black hand-drawn line art (NOT 3D, NOT photorealistic). Preserve everything else exactly: composition, background, labels, aspect ratio, and image quality. Do not add new text or objects.
```

增强小星参与感：

```text
Regenerate this illustration with the same core meaning and hand-drawn white-background style, but make the tiny Xing the true performer of the conceptual action. She should be doing the strange work that explains the idea with her own hands, not standing beside the scene. Keep it clean, sparse, hand-drawn, tiny-figure absurdity. Reuse the CHARACTER LOCK verbatim.
```
