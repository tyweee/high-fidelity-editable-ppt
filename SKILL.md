# Skill: PDF / Image → High-Fidelity Editable PowerPoint

## Purpose

将 PDF 页面或图片重构为高保真、可编辑 PowerPoint。核心不是“转格式”，而是重建视觉结构与可编辑语义。

## Trigger

当任务包含以下目标时使用本 Skill：
- PDF 转可编辑 PPT
- 图片重构为 PPT
- 高保真还原原稿页面
- 保留背景氛围、人物、光影、烟雾，同时使文字/图表可编辑
- 对现有重构稿进行逐页修复和 Quality Gate 检查

## Required Inputs

至少需要：
- 原始 PDF / 页面图片
- 目标比例（未指定时从原稿推断）
- 用户指定的局部替换要求（如有）

## Workflow

### Stage 1 — Analyze
识别：
- 页面尺寸和比例
- 背景环境
- 内容承载区
- 人物 / 前景装饰
- 字体和艺术字
- 图表 / 图标 / 功能框
- 光源、烟雾、纹理、环境色

### Stage 2 — Layer Plan
严格按三层拆解：
1. Layer 1：原始环境背景
2. Layer 2：内容承载层
3. Layer 3：前景装饰层

### Stage 3 — Reconstruction
- 局部清理旧文字和图表区域
- 原生重建文本、形状、简单图标、简单图表
- 复杂摄影、人物、烟雾和纹理作为独立视觉资产处理
- 保持原稿的比例、位置、留白和视觉节奏

### Stage 4 — Integration
重点修复：
- 人物与背景割裂
- 背景板切块感
- 重影
- 光影方向不一致
- 烟雾 / 硝烟缺失
- 环境色不一致

### Stage 5 — Quality Gate
执行 `docs/QUALITY_GATE.md`，任何失败项必须回到对应阶段修复。

## Definition of Done

- Visual Fidelity >= 90
- Editability >= 80
- 无整页大图伪编辑
- 无明显重影、切块、白边
- 关键功能图、人物、装饰元素无遗漏
- 字体可获取、可替换、可编辑
- 导出预览正常
