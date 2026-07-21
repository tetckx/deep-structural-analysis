---
name: deep-structural-analysis/layered
description: Layered Analysis Protocol — L1 surface impression → L2 single-lens challenge → L3 full multi-lens structural analysis. Load when user says "第一感觉是..." / "直觉上..." / "乍一看..." or when surface narrative is highly misleading.
version: 1.0.1
---

# Layered Analysis Protocol（认知递进模式）

Optional protocol. Especially useful when the surface narrative is highly misleading.

## Three Layers

| Layer | Core Question | Output |
|-------|--------------|--------|
| L1: 初印象 | What does common sense say? | 1-2 sentences |
| L2: 初步分析 | What does ONE disciplinary lens reveal that contradicts L1? | 1 paragraph, name the lens |
| L3: 深度思考 | What emerges from multi-lens cross-validation? | Full Phase 3-5 output |

## Transition Protocol

```
L1→L2: "[L1发现] 看似合理，但 [具体事实或透镜洞察] 对此提出了挑战，因为..."

L2→L3: "[L2分析] 揭示了一个维度，但它无法解释 [交互现象]。这需要多透镜分析。"
```

过渡句位于 L2 段落末尾或 L2 与 L3 之间，作为独立短段落。不嵌入 L2 正文，也不作为 L3 开头。

## L1→L2 Self-Check
Before writing L2, ask: "Which ONE factual premise of L1 is most likely false or misleading?" Target that premise specifically.

## Anti-Patterns
| Violation | Fix |
|-----------|-----|
| L2 just refines L1 slightly | L2 must produce a genuinely different answer |
| L3 restates L2 with more detail | L3 must synthesize across multiple lenses |
| Skipping L1 | L1 is the baseline — without it, the distance traveled is invisible |

## L2→L3 Anti-Patterns
| Anti-pattern | Fix |
|-------------|------|
| Vague transition ("this is only one perspective") | Name the SPECIFIC thing L2 cannot explain |
| 3+ complementary lenses at once | Pick the SINGLE most critical missing lens |

## Duplication Guard
When activated alongside 5-Phase Ladder: L3 REPLACES Phase 3-5 — do NOT run both. If user says "展开某透镜" after L3, output Part B 详细分析 format directly — do NOT re-enter the L1→L2→L3 cycle.
