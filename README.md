# High-Fidelity Editable PPT

将 PDF / 图片重构为**高保真、关键元素可编辑**的 PowerPoint，而不是把整页图片塞进 PPT。

## 核心目标

- 视觉还原度：**90%+**
- 可编辑性：**80%+**
- 禁止“整页图片套 PPT”的伪编辑方案
- 所有页面必须通过 Quality Gate

## 重构原则

### Layer 1 — 原始环境背景
保留原稿的场景、光影、烟雾、纹理、暗角和整体氛围。禁止为了去字而整体重绘背景。

### Layer 2 — 内容承载层
标题、副标题、正文、按钮、图表、图标等尽可能使用 PowerPoint 原生对象重建；只对旧文字或旧图表区域做局部清理。

### Layer 3 — 前景装饰层
人物、徽章、装饰线、光效、烟雾前景等分层处理，保证边缘、环境光、阴影和色调自然融合，避免切块感与重影。

## 项目目录

```text
.
├── README.md
├── SKILL.md
├── CODEX.md
├── docs/
│   ├── HIGH_FIDELITY_STANDARD.md
│   └── QUALITY_GATE.md
├── config/
│   └── reconstruction.yaml
└── src/
    └── ppt_reconstructor/
        ├── __init__.py
        └── pipeline.py
```

## 推荐工作流

1. 输入 PDF / 页面图片
2. 分析版式、层级、字体、视觉氛围
3. 拆分背景 / 内容承载层 / 前景装饰层
4. 局部清理旧文字与图表区域
5. 使用 PPT 原生对象重建可编辑内容
6. 对人物、烟雾、光影和背景做融合
7. 逐页 Quality Gate 自检
8. 输出最终 `.pptx`

详细规则见 `docs/HIGH_FIDELITY_STANDARD.md` 和 `docs/QUALITY_GATE.md`。
