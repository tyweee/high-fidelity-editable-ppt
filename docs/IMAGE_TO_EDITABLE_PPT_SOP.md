# 图片 / PDF → 高保真可编辑 PPT 通用 SOP

本 SOP 用于任何单页或多页图片 / PDF 的可编辑 PowerPoint 重构。

## 目标

- 视觉还原度：90%+
- 有效可编辑性：80%+
- 关键内容完整率：100%
- 禁止整页截图伪编辑
- 每页通过 Quality Gate

---

## Phase 1 — 原图分析

先判断：
- 页面比例
- 页面类型
- 主题风格
- 视觉中心
- 主色 / 辅助色
- 标题区 / 内容区 / 图片区
- 背景环境
- 人物 / 产品 / 场景
- 光线方向
- 纹理 / 烟雾 / 氛围
- 重复组件

输出：页面分析结论 + 高保真风险点。

---

## Phase 2 — 三层拆解

### Layer 1：环境背景
场景、建筑、天空、光影、烟雾、纹理、暗角、环境色。

### Layer 2：内容承载
标题、副标题、正文、编号、卡片、按钮、图标、图表、分割线、功能框。

### Layer 3：前景装饰
人物、徽章、花枝、纹样、光效、烟雾前景、局部高光、阴影。

输出：三层图层规划。

---

## Phase 3 — 元素清单

每个元素记录：

| 字段 | 含义 |
|---|---|
| name | 元素命名 |
| type | text / shape / image / chart / decor |
| layer | 1 / 2 / 3 |
| editable | yes / replaceable / no |
| method | native / crop / transparent image / vector |
| x,y,w,h | 页面坐标 |
| z | 图层顺序 |
| font | 字体，如适用 |
| color | 颜色，如适用 |
| notes | 裁切、透明度、融合等备注 |

推荐命名：`BG-* / TXT-* / CARD-* / IMG-* / CHART-* / ICON-* / DEC-* / FG-*`。

---

## Phase 4 — 可编辑性决策

### 原生重建
- 文字
- 编号
- 基础形状
- 卡片
- 线条
- 简单图标
- 简单图表
- 重复模块

### 独立图片资产
- 摄影背景
- 人物
- 建筑实景
- 产品摄影
- 烟雾、火焰、复杂纹理
- 复杂装饰
- 高复杂插画和艺术光效

### 禁止整体图片化
- 整页
- 整组卡片
- 整块正文
- 可原生重建的功能框 / 图表

---

## Phase 5 — 坐标化

先建立页面几何参数：
- Slide W / H
- 主视觉区占比
- 内容区占比
- 标题区占比
- 外边距
- 卡片间距
- 对齐基线
- 图片裁切窗口

建议同时记录：
- PowerPoint 英寸坐标
- 0–1 标准化坐标

同类组件必须共享一致尺寸、间距和基线。

---

## Phase 6 — 背景重构

- 原环境优先保留
- 仅局部清理旧字 / 旧图表
- 不整体重绘
- 左右区域或前后景有断裂时，用渐变、柔光、雾效、环境色过渡
- 检查矩形硬切、白边、重影、贴图感

---

## Phase 7 — 字体重构

1. 判断原字形类别
2. 寻找真实可获取字体
3. 匹配字号、字重、字距、行距
4. 匹配颜色、描边、阴影、渐变
5. 艺术字采用“可编辑文字 + 装饰效果层”

尽量控制在 2–3 套字体体系。

---

## Phase 8 — 组件化重建

典型卡片拆为：

`Frame + Badge + Title + Body + Image + ImageFade + Decor`

先完成 1 个标准组件，再复制到其他同类模块。

这样保证：
- 对齐一致
- 间距一致
- 样式一致
- 后续容易批量修改

---

## Phase 9 — 建议制作顺序

1. Canvas
2. Base Background
3. Environment Image
4. Fade / Mask
5. Content Containers
6. Images / Charts
7. Editable Text
8. Badge / Icon
9. Decorative Elements
10. Foreground Atmosphere
11. Integration Pass

---

## Phase 10 — 融合 Pass

专门检查：
- 人物与背景割裂
- 卡片与背景割裂
- 图片硬切
- 卡片过白 / 过新
- 环境光不一致
- 色温不一致
- 重影
- 雾效 / 烟雾缺失
- 图片与文字衔接生硬

允许使用：渐变蒙版、柔光、半透明环境色、轻阴影、雾效、局部羽化。

---

## Phase 11 — Quality Gate

每页必须记录：
- Visual Fidelity
- Editability
- Content Completeness
- Background Integration
- Typography
- Alignment
- Image Crop
- Export

不通过则返回对应阶段修复。

---

## Phase 12 — 导出与交付

检查：
- 页面比例
- 字体替换
- 乱码 / 错字
- 图片拉伸
- 图片裁切
- 透明度异常
- 阴影错位
- 超出画布对象
- 锯齿 / 压缩
- 关键元素遗漏

交付说明：
- 页面数量
- 原生可编辑内容
- 图片资产内容
- 字体替代情况
- Quality Gate 结果

---

# Scoped Edit Mode — 局部修改模式

如果用户说“只换背景 / 只换人物 / 不改大小 / 其他不要动”：

1. 锁定未授权元素
2. 不改变其他元素坐标、尺寸、字体、颜色、层级
3. 只修改指定对象
4. 修改后检查遮挡、构图、比例、环境光和融合
5. 不顺带优化其他区域

---

# Batch Mode — 多页模式

先建立整套 Deck Design System：
- 字体
- 色彩
- 边距
- 标题规则
- 卡片样式
- 图片裁切规则
- 编号规则
- 图层命名

逐页完成后再做全局检查，避免：
- 字号跳变
- 色彩漂移
- 相同组件出现多个版本
- 图片质量不一致
- 页面节奏不统一

---

# 快捷调用语句

以后可以直接使用：

> 按高保真可编辑 PPT Skill v2 拆解并重构这张图。

或：

> 按 Skill v2 输出元素清单、坐标、可编辑性判断，并执行 Quality Gate。

默认链路：

`Analyze → 3 Layers → Element Inventory → Geometry → Asset Strategy → Typography → Components → Build → Integration → Quality Gate → Export`
