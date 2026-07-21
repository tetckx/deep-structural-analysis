---
name: structural-analysis-lite
description: >-
  Lightweight structural analysis for Clear/Complicated complexity domains. Activated
  automatically by deep-structural-analysis when auto-degradation triggers, or directly
  when user asks for "简单分析"/"快速分析"/"大概看一下". Runs 2-3 lenses + 1 tool,
  outputs compact Executive Summary only, ~1/3 token budget. For Complex/Chaotic domains
  or user explicitly requests deep analysis, use the full deep-structural-analysis skill.
version: 2.0.1
---

# Structural Analysis — Lite

Progressive-depth companion to deep-structural-analysis. Activated when:
- Main skill's auto-degradation fires (Clear/Complicated domain, no explicit depth request)
- User says "简单分析"/"快速分析"/"大概聊聊"/"简要分析"/"quick analysis"
- User wants single-tool application on a structurally-framed question

For Complex/Chaotic domains or explicit "深度分析" requests: use the full skill.

---

## Core Workflow

**Phase 1 — Decompose** (1 sentence each, internal):
1. Surface question
2. ONE misleading assumption in the common-sense answer → this becomes the core tension

**Phase 2 — Research**: 1-2 fact searches. Goal: 2-3 concrete data points, not exhaustive coverage.
If search unavailable: use pre-training knowledge + mark all conclusions low-confidence.

**Phase 3 — Analyze**: 2-3 lenses + 1 tool → compact output.

---

## Lens Selection (2-3 lenses)

Pick from problem-driven clusters. Always include at least ONE lens outside your comfort zone.

| Problem feels like... | Lenses |
|----------------------|--------|
| Economic/Resource | Economics, Institutional Analysis, History |
| Social/Cultural | Sociology, Anthropology, Psychology |
| Tech/Transformation | Technology Studies, Systems Theory, Temporality |
| Power/Governance | Political Science, Institutional Analysis, Geography |
| Emotional/Identity | Affect, Anthropology, Psychology |

**Anti-inertia rule**: If instinct says "this is an economic problem", pick Psychology or Anthropology as one of your 2-3.

---

## Tool Selection (1 tool)

Pick the ONE that best matches the problem dynamic:

| Dynamic | Tool |
|---------|------|
| Distribution/power concentration | 二六二分布模型 |
| Change over time | Adaptive Cycle or Path Dependency |
| Rules ≠ reality | Asymmetry Detection |
| Who benefits vs. who pays | Incentive Mapping |
| Belief→behavior→reality loop | Reflexivity Analysis |

---

## Lens Application (per lens, concise)

- **Core insight** (1 sentence — what does this lens reveal?)
- **Challenge to common sense** (1 sentence — what premise does it overturn?)
- **Fact anchor** (1 reference to research/pre-training data)
- **Blind spot** (what does this lens miss?)

---

## Output: Compact Executive Summary

No Part B. Output ONLY this:

```
> 本次采用轻量模式（2-3透镜：逐一列出透镜名，如"经济学 / 社会学"；仅执行摘要，元认知简化）。如需标准深度 (Standard: 5-7透镜) 或更全面 (Comprehensive: 7-9) 的分析，请随时告知。⚠️ 若未接入实时搜索，追加标注"基于预训练知识"。

## [主题]

### 核心发现
[2-3句 — 最重要的交叉验证洞察]

### 关键张力
[1句 — 常识答案的哪个经验前提被推翻了？]

### 结构快照
[1个工具输出 — 二六二层级 / 激励映射 / 不对称发现]

### 个体启发
[1句可行动认知 — 非空泛建议。若结构限制下无可行动策略，提供认知锚点而非编造建议]

### ⚠️ 盲点（可省略）
- [本分析无法覆盖或验证的一个关键盲点]
```

无多镜共识、无置信度说明、无关键分歧、无分层影响表、无 Meadows 杠杆。整体输出控制在一屏以内。

---

## Quality Gates

| Gate | Test |
|------|------|
| **Anti-inertia** | Did I use at least one lens outside my comfort zone? |
| **Fact-bound** | Does every lens reference at least 1 concrete fact? |
| **Not labeling** | Did I apply lenses or just name them? |
| **Chinese output** | Primarily Chinese — section headers, table labels, prose |
| **Language-sensitive** | If I belong to the analyzed group, does this feel respectful? |
| **Trauma-aware** | If topic involves violence/discrimination: one sentence acknowledging real human pain, no false balance, no "understand both sides" |
| **Compact** | Fits one screen? If not, cut. |

---

## Anti-Patterns

| Violation | Fix |
|-----------|-----|
| Using 4+ lenses | Stick to 2-3 — this is lite, not full |
| Outputting Part B with tables | Executive Summary only |
| "On one hand... on the other..." without weight | State which side has stronger evidence |
| Running full Phase 1-5 of the main skill | This is a separate skill |
| Uniform depth on multiple questions | Pick the 1-2 deepest, short-answer the rest |

---

## Exit / Degradation

- User says "再简单点" → 核心发现 (1句) + 个体启发 (1句)，纯文本
- User wants full analysis → redirect to deep-structural-analysis
- Topic triggers trauma-sensitive concerns → load main skill's `extensions/trauma-sensitive.md`

---

## Relationship to Main Skill

```
Clear domain       → short answer (no framework needed)
Complicated domain → structural-analysis-lite (this skill, auto-degrade target)
Complex domain     → deep-structural-analysis core + extensions as needed
Chaotic domain     → deep-structural-analysis core + all applicable extensions
```

This is the progressive-depth entry point. When in doubt between lite and full: use lite. The user can always say "展开" to upgrade.

---

*Companion to deep-structural-analysis v1.12.1+. For full framework documentation: see `../README.md`.*
