# Synthesis Reference（合成参考）

> 合成阶段参考文档 · 由 SKILL.md Phase 5 条件引用
> 版本归属：主版本链（随包同步，不设独立版本号）

## Supplementary Analysis Templates (L3 Layer)

Speed-reference — apply 1-2 per lens as sub-frameworks during lens analysis or Phase 5 synthesis. Models know these concepts from pre-training; this table maps them to lenses as a reminder.

| Template | Primary Lens | | Template | Primary Lens |
|----------|-------------|---|----------|-------------|
| Long Tail | 经济学 | | Principal-Agent | 经济学 |
| Base Rate | 心理学 | | Information Asymmetry | 经济学 |
| S-Curve / Diffusion | 技术 | | Externalities | 经济学 |
| Normal Accident Theory | 系统论 | | Tipping Point | 社会学 |
| Confirmation Bias | 心理学 | | Lock-in Mechanisms | 历史 |
| Framing Effect | 人类学 | | First Principles | 系统论 |
| Commons Governance | 政治学 | | Prisoner's Dilemma | 政治学 |
| Second-Order | 心理学 | | Zero-Sum vs Positive-Sum | 经济学 |
| Pre-mortem / Hubris | 系统论 | | Tradeoff Transparency | All (synthesis) |
| Materiality Check | All (blind-spot) | | MECE Principle | All (quality) |
| Inversion | All (strategy) | | | |

## 张力回填要求

Before synthesizing, complete the tension backfill: Review all lenses that marked tension as "待交叉验证." For each pair of lenses, determine whether a substantive conflict exists. If none found, annotate both as "与其他透镜视角无实质冲突，但提供了补充性视角。" Do NOT leave any "待交叉验证" marker unresolved before delivering output.

## Internal reference: Common lens tensions (guide, not output)

| Lens Pair | Typical Tension |
|-----------|----------------|
| 经济学 vs. 人类学 | Efficiency logic vs. meaning/gift/reciprocity logic |
| 系统论 vs. 心理学 | Structural determinism vs. individual agency |
| 政治学 vs. 技术研究 | Power concentration vs. tech-enabled diffusion; regulatory lag vs. tech acceleration |
| 制度分析 vs. 社会学 | Formal rules vs. informal norms; design intent vs. implementation culture |
| 历史 vs. 系统论 | Contingency/path dependency vs. systemic regularities |
| 时间性 vs. 制度分析 | Tech/social acceleration vs. institutional inertia |
| 时间性 vs. 经济学 | Social/ecological rhythm vs. discount-rate logic — economics discounts the future; temporality asks "who sets the discount rate, and for whom?" |
| 经济学 vs. 时间性 | Discount-rate optimization vs. intergenerational time sovereignty |

*Note: This is a prompt list, not a mandate. Do NOT fabricate tensions. If no conflict exists, say so.*

## Optional: Key Counterfactual check
Before finalizing synthesis, identify 1-2 critical branching points where a different historical choice could have produced a meaningfully different trajectory. Ask: *"If the opposite choice had been made at [point X], what would the system look like today?"* The purpose is NOT to speculate about alternative histories, but to expose which features of the current system are contingent (not inevitable) — these are potential high-leverage intervention points.

## Information-Missing Handling 模板（SKILL.md Phase 2 引用）

关键子问题搜索无果/低质时：
1. 显式标记缺口："⚠️ Could not verify [X]. The following conclusions are based on assumed preconditions and carry reduced confidence."
2. 依赖缺失数据的结论加"如果 (if)"前缀并声明假设
3. 盲点清单列出依赖缺失数据的结论
4. 邀请补充："如果你能提供关于 [X] 的数据或来源，我可以重新校准这部分分析。"
