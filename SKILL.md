# Skill: PDF / Image → High-Fidelity Editable PowerPoint v2

## Purpose

将 PDF 页面、截图或图片重构为高保真、真正可编辑的 PowerPoint。

本 Skill 的目标不是“转格式”，也不是“整页图片 + 盖文字”，而是：

> 最大程度保留原稿视觉气质、构图、氛围和层级，同时把有编辑价值的内容重建为 PowerPoint 原生对象。

核心目标：
- Visual Fidelity >= 90
- Editability >= 80
- 关键内容完整率 = 100%
- 所有页面通过 `docs/QUALITY_GATE.md`

---

## Trigger

当任务包含以下任一目标时使用本 Skill：
- PDF 转可编辑 PPT
- 图片 / 截图重构为 PPT
- 高保真还原原稿页面
- 目录页、封面页、人物页、产品页、科技页、文化页、图文页重构
- 保留背景氛围、人物、光影、烟雾、纹理，同时使文字 / 图表 / 模块可编辑
- 对现有 PPT 重构稿进行逐页修复
- 用户提出“只换背景 / 只换人物 / 不改大小 / 其他不要动”
- 对整套 PPT 执行逐页 Quality Gate

---

## Non-Goals

本 Skill 不接受以下结果作为最终交付：
- 整页 PDF / PNG / JPG 直接铺满幻灯片
- 整页截图作为背景，再覆盖少量可编辑文字
- 为了去旧文字而整体重绘背景，导致原稿气质改变
- 为了追求 100% 矢量化而牺牲视觉还原
- 使用不可获取、不可追溯的 AI 虚构字体
- 用户只要求局部修改时，擅自重做其他区域

---

## Required Inputs

至少需要：
- 原始 PDF / 页面图片 / 截图
- 目标输出：PPTX

可选输入：
- 目标比例；未指定时从原稿推断
- 指定字体 / 品牌字体
- 用户提供的替换图片
- 用户指定的局部修改范围
- 是否允许联网寻找真实素材
- 是否要求先输出预览图再生成 PPT

---

## Output Contract

每次重构至少应产出以下结果：

1. 页面视觉分析
2. 三层图层规划
3. 元素清单 / Element Inventory
4. 可编辑性决策
5. 版式坐标与比例关系
6. 字体与颜色策略
7. 重构后的 PPT 页面
8. 页面级 Quality Gate 结果
9. 最终导出预览检查

对于多页任务，还应输出整套页面的统一字体、色彩、间距和组件规范。

---

# Golden Rules

## Rule 1 — 先分析，再重构

禁止看到图片后直接开始摆 PPT 元素。

必须先识别：
- 页面尺寸 / 比例
- 视觉中心
- 主要构图区
- 背景环境
- 内容承载区
- 人物 / 产品 / 前景装饰
- 标题 / 正文 / 标签 / 编号
- 图表 / 图标 / 功能框
- 光源方向
- 烟雾 / 纹理 / 环境色
- 可重复组件

---

## Rule 2 — 始终按三层结构拆解

### Layer 1 — Environment Background
保留原稿的：
- 场景
- 建筑
- 天空
- 光影
- 烟雾 / 硝烟
- 纹理
- 暗角
- 环境色
- 原始叙事氛围

原则：
- 只做必要的局部清理
- 不因为旧文字存在而整体重绘背景
- 不把环境背景硬裁成明显矩形块

### Layer 2 — Editable Content
优先原生重建：
- 标题
- 副标题
- 正文
- 编号
- 标签
- 卡片
- 按钮
- 线条
- 分割线
- 简单图标
- 简单图表
- 内容承载框

### Layer 3 — Foreground Decoration
包括：
- 人物
- 徽章
- 花枝
- 装饰纹样
- 光效
- 烟雾前景
- 高光
- 阴影
- 复杂艺术装饰

要求：
- 边缘自然
- 环境光一致
- 色温一致
- 无白边 / 硬边 / 贴纸感 / 重影

---

# Editability Decision Matrix

## 必须优先原生可编辑

- 标题 / 正文 / 数字 / 标签
- 基础矩形 / 圆形 / 圆角矩形
- 分割线 / 边框
- 编号章
- 简单卡片
- 简单按钮
- 简单图标
- 简单柱状图 / 折线图 / 饼图
- 可重复的模块结构

## 可以作为独立图片资产

- 摄影背景
- 复杂人物
- 建筑实景
- 产品摄影
- 烟雾 / 火焰 / 云层
- 高复杂纹理
- 复杂国风纹样
- 复杂插画
- 难以原生复刻的艺术光效

## 禁止图片化

- 整页
- 整组目录卡片
- 整块文字内容
- 本可原生重建的简单功能框
- 本可原生重建的简单图表

---

# Standard Workflow

## Stage 0 — Scope Freeze

先记录用户明确要求。

若用户说：
- “只换背景”
- “只换人物”
- “不要改大小”
- “其他都不要动”

则进入 **Scoped Edit Mode**：
- 锁定未授权区域
- 不改变未授权元素的尺寸、位置、字体、颜色或层级
- 修改后仍要检查遮挡、比例、融合和环境光

---

## Stage 1 — Visual Analysis

输出页面分析：
- 页面类型：封面 / 目录 / 内容 / 人物 / 数据 / 产品 / 结束页
- 视觉风格关键词
- 页面比例
- 主色 / 辅助色 / 强调色
- 主视觉区域占比
- 标题区占比
- 内容区占比
- 前景装饰区
- 视觉动线
- 潜在高保真风险点

---

## Stage 2 — Layer Plan

建立三层图层表：

| Layer | 内容 | 处理策略 |
|---|---|---|
| Layer 1 | 环境背景 | 保留氛围，只做局部清理和融合 |
| Layer 2 | 内容承载 | 尽可能 PPT 原生重建 |
| Layer 3 | 前景装饰 | 独立资产，保证融合 |

---

## Stage 3 — Element Inventory

对页面建立逐元素清单。

每个元素至少记录：
- `name`
- `type`
- `layer`
- `editable`
- `reconstruction_method`
- `x / y / w / h`
- `z_order`
- `font / color`（如适用）
- `notes`

推荐命名：
- `BG-*`
- `TXT-*`
- `CARD-*`
- `IMG-*`
- `CHART-*`
- `ICON-*`
- `DEC-*`
- `FG-*`

典型卡片组件统一拆为：

`Frame + Badge + Title + Body + Image + Decor`

禁止把整个卡片合成单张图片。

---

## Stage 4 — Geometry Mapping

先建立版式坐标，再开始制作。

必须记录：
- Slide Width / Height
- 主要区域百分比
- X / Y / W / H
- 对齐基线
- 元素间距
- 外边距
- 卡片间距
- 图片裁切窗口比例

推荐同时保存：
- PowerPoint 英寸坐标
- 0–1 标准化坐标

原则：
- 不仅“看起来差不多”
- 同类组件必须共享统一尺寸和间距
- 对齐和留白必须接近原稿

---

## Stage 5 — Asset Strategy

对每个视觉资产选择最合适的方式：

### 原始资产优先
若原图中的人物、产品、建筑、背景可直接独立保留，则优先使用原始资产或高质量裁切。

### 局部提取
允许对：
- 人物
- 装饰
- 花枝
- 徽章
- 背景片段
进行单独提取。

### 真实图片优先
当需要补充素材且用户允许联网时：
- 优先使用真实摄影
- 避免明显 AI 味
- 新素材的光向、色温、透视必须与原稿一致

---

## Stage 6 — Typography Reconstruction

所有核心文字必须尽量真实可编辑。

流程：
1. 判断字体类别：宋体 / 黑体 / 楷体 / 衬线 / 无衬线 / 艺术字
2. 寻找真实可获取字体
3. 匹配字号、字重、字距、行距
4. 再匹配颜色、描边、阴影、渐变

复杂艺术字采用：

`Editable Text + Decorative Effects`

而不是直接把文字截图。

字体体系建议每页控制在 2–3 套以内。

---

## Stage 7 — Component Reconstruction

先制作标准组件，再复制扩展。

例如目录卡片：
1. Frame
2. Badge
3. Title
4. Body
5. Image Placeholder
6. Image Fade
7. Corner Decor

先确认一张组件达到质量要求，再复制到 02 / 03 / 04 / 05。

这样可以确保：
- 尺寸一致
- 间距一致
- 样式一致
- 后续可快速修改

---

## Stage 8 — Build Order

推荐严格按以下顺序重建：

1. Slide canvas
2. Base background
3. Environment image
4. Background fade / mask
5. Main content containers
6. Images / charts
7. Editable text
8. Badges / icons
9. Decorative elements
10. Foreground atmosphere
11. Final light / shadow integration

禁止一开始就添加大量装饰，再反过来修结构。

---

## Stage 9 — Visual Integration

完成结构后，专门执行一次“融合 Pass”。

重点检查和修复：
- 背景板与环境割裂
- 人物抠图感
- 图片硬切
- 卡片过白 / 过新
- 光影方向冲突
- 环境色温不一致
- 重影
- 烟雾 / 硝烟缺失
- 阴影强度不一致
- 图片与文字区衔接生硬

可使用：
- 渐变蒙版
- 柔光
- 半透明环境色
- 烟雾 / 雾效
- 边缘羽化
- 轻阴影

融合的目标不是增加新设计，而是恢复原稿的整体空间感。

---

## Stage 10 — Quality Gate

必须执行 `docs/QUALITY_GATE.md`。

每页至少记录：
- Visual Fidelity: 0–100
- Editability: 0–100
- Content Completeness: PASS / FAIL
- Background Integration: PASS / FAIL
- Typography: PASS / FAIL
- Alignment: PASS / FAIL
- Image Crop: PASS / FAIL
- Export: PASS / FAIL

任何 FAIL 都必须回到对应阶段修复。

---

## Stage 11 — Export Validation

最终 PPTX 完成后必须检查导出预览：
- 页面比例正确
- 无超出画布的意外对象
- 无字体替换
- 无错字 / 乱码
- 无图片拉伸
- 无异常透明度
- 无阴影错位
- 无锯齿或严重压缩
- 无关键对象缺失

不得只检查编辑视图，不检查实际导出结果。

---

## Stage 12 — Delivery Report

交付时至少说明：
- 页面数量
- 目标比例
- Visual Fidelity 结果
- Editability 结果
- 哪些内容为 PPT 原生对象
- 哪些复杂视觉保留为独立图片资产
- 是否存在字体替代
- 是否全部通过 Quality Gate

---

# Multi-Page / Batch Mode

多页任务禁止每页独立随意设计。

必须先建立 Deck-level Design System：
- 统一字体
- 统一主色 / 辅助色
- 统一边距
- 统一标题规则
- 统一图片裁切逻辑
- 统一卡片和编号样式
- 统一图层命名

然后逐页重构。

每页完成后执行 Quality Gate，最后再执行一次全局检查：
- 页面风格是否一致
- 字号是否跳变
- 色彩是否漂移
- 相同组件是否出现不同版本
- 图片质量是否参差

---

# Common Failure Modes

发现以下问题时不得直接交付：
- 整页截图伪编辑
- 背景被整体重绘导致气质改变
- 人物与背景割裂
- 内容板像贴纸
- 图片硬边明显
- 图像被不必要放大
- 用户指定“不改大小”却改变尺寸
- 原稿功能框旁的图片遗漏
- 艺术字变成不可编辑位图且无必要
- 卡片间距不一致
- 字体不可获取
- 原稿烟雾 / 光影 / 纹理被删除
- 产生双人物 / 双阴影 / 双光效重影

---

# Definition of Done

页面只有在满足以下全部条件时，才能标记为 FINAL：

- Visual Fidelity >= 90
- Editability >= 80
- Content Completeness = PASS
- Background Integration = PASS
- Typography = PASS
- Alignment = PASS
- Image Crop = PASS
- Export = PASS
- 无整页大图伪编辑
- 无明显重影、切块、白边、硬边
- 关键功能图、人物、装饰元素无遗漏
- 字体真实可获取、可替换、可编辑
- 用户明确的局部修改范围被严格遵守

---

# Recommended User Commands

用户以后可直接说：

- “按高保真可编辑 PPT 标准拆解这张图”
- “按 Skill v2 重构这页”
- “只换背景，其他不要动”
- “做元素清单和坐标表”
- “检查这页 Quality Gate”
- “按这个标准批量重构整套 PDF”

默认执行链路：

`Analyze → Layer Plan → Element Inventory → Geometry → Asset Strategy → Typography → Components → Reconstruction → Integration → Quality Gate → Export Validation → Delivery`

---

## Reference Files

- `docs/HIGH_FIDELITY_STANDARD.md`
- `docs/QUALITY_GATE.md`
- `docs/IMAGE_TO_EDITABLE_PPT_SOP.md`
- `config/reconstruction.yaml`
- `CODEX.md`
