# Codex Operating Instructions — Editable PPT Reconstruction v2

你正在维护一个 PDF / 图片 → 高保真可编辑 PowerPoint 重构项目。

## 最高优先级

1. 视觉还原度 >= 90%
2. 可编辑性 >= 80%
3. 关键内容完整率 = 100%
4. 不允许使用整页截图作为伪背景来冒充可编辑 PPT
5. 每页必须通过 `docs/QUALITY_GATE.md`
6. 用户明确局部修改范围时，必须严格遵守

---

## 必读文件

执行任何重构任务前，先阅读：
- `SKILL.md`
- `docs/HIGH_FIDELITY_STANDARD.md`
- `docs/IMAGE_TO_EDITABLE_PPT_SOP.md`
- `docs/QUALITY_GATE.md`
- `config/reconstruction.yaml`

若实现与上述规范冲突，以 `SKILL.md`、高保真标准和 Quality Gate 为最高优先级。

---

## 强制执行顺序

### 1. Scope Freeze
先记录用户明确约束，例如：
- 只换背景
- 只换人物
- 不改大小
- 其他不要动

若存在此类要求，锁定未授权对象。

### 2. Analyze
分析：
- 页面比例
- 页面类型
- 构图
- 背景
- 人物 / 产品 / 场景
- 标题 / 正文 / 标签
- 图标 / 图表 / 功能框
- 光源方向
- 环境色
- 烟雾 / 纹理 / 暗角
- 重复组件

### 3. Layer Plan
严格规划：
- Layer 1：原始环境背景
- Layer 2：内容承载层
- Layer 3：前景装饰层

### 4. Element Inventory
为每个元素记录：
- name
- type
- layer
- editable
- method
- x / y / w / h
- z-order
- font / color
- notes

### 5. Geometry
先确定坐标、尺寸、基线、间距，再开始绘制。

禁止完全靠目测随意摆放。

### 6. Reconstruct
- 只局部清理旧文字 / 图表 / 按钮区域
- 优先 PowerPoint 原生文本、形状、图标、简单图表
- 复杂摄影、人物、建筑、烟雾、纹理作为独立图片资产
- 禁止整页图片化

### 7. Typography
- 使用真实可获取字体
- 艺术字优先采用“可编辑文字 + 装饰效果层”
- 匹配字号、字重、字距、行距、颜色、阴影、描边

### 8. Components
重复模块先构建标准组件，再复制。

典型卡片：
`Frame + Badge + Title + Body + Image + ImageFade + Decor`

### 9. Integration Pass
专门检查：
- 人物与背景割裂
- 背景板切块感
- 图片硬切
- 重影
- 光影方向不一致
- 色温不一致
- 烟雾 / 硝烟缺失
- 卡片过白 / 过新

### 10. Quality Gate
执行 `docs/QUALITY_GATE.md`。

任何 FAIL 必须返回对应阶段修复，不得直接交付。

### 11. Export Validation
必须检查实际导出预览，而不是只看编辑视图。

检查：
- 字体替换
- 错字 / 乱码
- 图片拉伸
- 透明度异常
- 裁切异常
- 锯齿
- 阴影错位
- 关键元素遗漏

---

## 禁止事项

- 禁止把整页 PDF / PNG 直接铺满幻灯片
- 禁止整组卡片直接截图
- 禁止为了方便而整体重绘背景
- 禁止擅自改变原稿风格
- 禁止忽略原稿留白、比例和层级
- 禁止人物切块感、白边、硬边、重影
- 禁止遗漏原稿关键图片或功能模块
- 禁止使用不可追溯、不可获取的 AI 虚构字体作为交付字体
- 禁止用户要求局部修改时顺带改动其他区域
- 禁止图片变形拉伸来适配容器

---

## 用户明确局部修改时

如果指令为“只换背景 / 只换人物 / 不改大小 / 其他不要动”：

1. 锁定其他元素
2. 不改变其他对象坐标、尺寸、字体、颜色、层级
3. 只处理指定对象
4. 替换后检查构图、遮挡、比例、环境光和融合
5. 不顺带优化其他区域

---

## 多页项目

先建立 Deck Design System：
- 字体
- 色彩
- 边距
- 标题层级
- 卡片组件
- 图片裁切规则
- 编号规则
- 图层命名

逐页通过 Quality Gate 后，再执行全局一致性检查。

---

## Final 判定

只有满足以下全部条件，才能标记 FINAL：
- Visual Fidelity >= 90
- Editability >= 80
- Content Completeness = PASS
- Background Integration = PASS
- Typography = PASS
- Alignment = PASS
- Image Crop = PASS
- Export = PASS
- Scoped Edit Compliance = PASS / N/A
