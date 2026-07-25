---
name: deep-structural-analysis
description: >-
  Multi-perspective structural analysis skill for deep, cross-disciplinary examination
  of complex social, economic, philosophical, and systemic questions. When users ask for
  deep analysis, structural understanding, or multi-angle exploration of a topic — especially
  questions involving power structures, social dynamics, systemic contradictions, or
  why-things-are-the-way-they-are — invoke this skill. Trigger phrases (Chinese): '深度分析',
  '多角度', '从多个视角', '三向', '三向分布', '三向理论', '结构分析', '用XX视角看',
  '分析一下这个现象', '从XX框架分析'. Trigger phrases (English): 'deep analysis',
  'multi-perspective', 'cross-disciplinary', 'structural analysis', 'tri-directional', 'three-tier',
  'analyze from multiple angles', 'systemic analysis'. Note: standalone '为什么' or '你怎么看'
  only trigger when the question is about a complex social/economic/political topic,
  NOT for trivial queries or simple factual questions. This skill uses web search
  to gather factual context, then applies disciplinary lenses (scaled by depth tier)
  plus structural frameworks (三向, 80/20, asymmetry detection, incentive
  mapping, path dependency, etc.) to produce stratified, actionable conclusions.
version: 1.15.1
---

<!--
Author: happy_chen
版本策略 (Semver-like):
- 主版本 (X.0.0): 结构性重构、向后不兼容变更、输出格式根本变化
- 次版本 (X.Y.0): 新增独立机制（新检查条目、新协议分支、新质量标准、重写现有机制）
- 补丁版本 (X.Y.Z): 对已有机制的细化、澄清、合规修复、内容精简（无新机制）

历史（原始 1.0.0 → 1.10.2，见 SKILL构建全记录.md）:
- 1.10.2 → 1.11.0: +Refusal handling(新机制) / +Trauma-sensitive标准(新标准) / +三标准豁免(重写) / +过度抽象化检查#7 / +架构限制声明
- 1.11.0 → 1.11.2: +Refusal决策启发式(细化) / +Collapsed Mode创伤约束(细化)
- 1.11.2 → 1.12.0: +Multi-question triage(新机制) / +模板全量中文化(合规修复)
- 1.12.0 → 1.12.1: 内容精简 — 删除Workflow Example(38行) / 合并Web Search→Phase 2(25行) / 合并Iterative Clarification→Phase 1(8行) / 压缩Templates+Tool Pool+Lens Tables(55行)
- 1.12.1 → 当前: +三向透镜（二六二→跨域泛化→22域爆破→认识论降级为认知透镜）。+全工具池透镜化改造（80/20, Adaptive Cycle, Path Dependency, Asymmetry Detection, Incentive Mapping, Capital Type Matrix, Reflexivity Analysis 统一标注认识论类型、构造历史、失效条件和校准检查）+工具使用通用纪律
- 当前 → 1.13.0: +多层信号解码（MLSD）工具 v0.2 —— 高博弈密度信息逆向解码（信号生存分析/多接收者映射/时序关联域）。+F类 Communication & Signal Tools。+认识论标注+校准增强+边际价值归零+使用时序+嵌套场景+集成状态 —— 7 gaps closed，工具池 8→9
- 1.13.0 → 1.14.0: MLSD v0.3 历史校准升级。四个边界测试案例（Powell/BP/Apple/Google）→ +加权混合分类+发送者自反身性（轴一增强）+后排检测协议+间接接收者检测（轴二下限修订）+筛查压力衰减（三问第二关增强）+可靠性退化曲线+缺失检测协议+已知局限 5→8（新增症状vs信号、信息空白的策略功能）
- 1.14.0 → 1.14.1: MLSD v0.4 Skill联合使用协议。+MLSD作为Skill前置传感器的定位+产出密度→分析深度的依赖关系+博弈密度不对称声明。两者分析对象不同：MLSD分析信息，Skill分析结构。
- 1.14.1 → 1.14.2: MLSD v0.5 联合实战案例库。三次Skill+MLSD联合实战写入附录——三方治理文件/黄仁勋×孙正义/Xi WAIC演讲。构造历史从单次扩展为完整三次记录。方法学教训逐案标注。
- 1.14.2 → 1.14.3: MLSD v0.6 管道架构校准。修正 MLSD-Skill 关系：三问=解码门控≠管道门控。Skill独立启动。MLSD是可选输入源。+三种联合模式。
- 1.14.3 → 1.15.0: +第四类物质透镜（Material Lenses）——生态/环境、基础设施/物质流、生命科学/身体。领域触发式必选（类比历史透镜规则）。+反物质决定论警告。+物质-结构张力表。透镜池 13→16。<!-- 次版本：新增独立机制（透镜类别） -->
- 1.15.0 → 1.15.1: MLSD v0.7 对话引导分析模块。+三个追问（引导性问题/追问压力/独白对比）+三种时间尺度（微观/中观/宏观）+立场漂移检测。修正 MLSD 的"独白假设"和"时间冻结假设"。新增已知局限 9（对话引导偏差）和 10（时间冻结偏差）。
-->

# Deep Structural Analysis

Multi-perspective, cross-disciplinary analysis for complex questions. Uses
web search for factual layering, then applies multiple disciplinary lenses
and structural frameworks to produce a stratified understanding that accounts
for blind spots and reveals leverage points.

## When to Use This Skill

| Trigger | Example |
|---------|---------|
| User asks to deeply analyze a topic | "深度分析一下当下的就业形势" |
| User wants multi-angle exploration | "从多个角度分析这个现象" |
| User invokes specific frameworks | "用三向看这个问题" |
| User requests single-tool application | "用三向分析一下" / "用不对称检测看这个" — 仅应用该工具+询问是否展开，不启动完整框架 |
| User asks a structural "why" question | "为什么劳动法执行这么难" |
| User asks for your genuine perspective | "你怎么看这个问题" |
| User references previous analytical styles | "像上次那样用多学科视角分析" |

**Single-tool application format**: When triggered by a single-tool request, output is exclusively that tool applied to the question (3-5 sentences), followed by "需要我以此工具为入口展开完整的多透镜分析吗？" Do NOT launch Phase 1-5, do NOT require web search, do NOT produce Executive Summary. The tool application stands alone. This prevents overkill while keeping the depth path available.

**⚠️ 致害场景——本 Skill 的使用可能构成伤害的情况**：以下场景中，即使分析本身在学术上是高质量的，使用本 Skill 也可能造成伤害。这不是"分析质量"问题——是"分析行为本身"在特定权力不对称中的效应问题。Skill 当前没有内置机制来检测这些场景——依赖使用者的自我判断。

- **未经同意的创伤分析**：一个用户将第三者的具体创伤经历作为"分析案例"提交，而该第三者未同意。伤害机制——将受害者转化为"展示制度失效的案例"。
- **权力上位者的武器化使用**：拥有制度权力者使用本 Skill 分析"为什么被统治者不服从"。伤害机制——反惯性规则和不对称检测在此场景中提供更精密的控制工具。
- **紧急情境的分析延迟**：用户面临需要立即行动的安全/医疗危机。伤害机制——分析的结构完整性 = 决策延迟。
- **心理健康危机的误用**：用户处于急性心理危机中但以"深度分析"形式表达。伤害机制——最需要的是连接而非分析，被分析者需要的是不被当作分析对象的回应。
- **活人被非人化为分析对象**：分析的"对象"是具体可识别的个体，分析行为本身会将其从匿名状态拉到被审视状态。伤害机制——分析行为改变被分析者的社会处境。
- **触发守卫的负向清单**依然适用：事实查询、代码调试、天气、总结——这些不需要深度分析的问题用本 Skill 是大炮打蚊子。

### Trigger Guard: Complexity Quick Assessment

Before firing the full framework, assess the question against these criteria:

**Positive indicators (skill likely needed):**
- Question involves ≥2 distinct stakeholder groups with conflicting interests
- References a systemic contradiction (policy-vs-practice, macro-vs-micro)
- Spans multiple domains (economic, social, political, technological)
- User explicitly asks for structural or multi-angle analysis

**Negative indicators (skill likely NOT needed):**
- "为什么天空是蓝色的", "为什么1+1=2" — factual/scientific explanation
- "代码为什么报错" — debugging
- "帮我总结一下这篇文章" — summarization
- "今天天气怎么样" — information lookup
- Question can be fully addressed by a single factual source

**Fallback for trigger-word/fact mismatch**: If a trigger word IS present (e.g., "深度分析一下为什么天空是蓝色的") but complexity assessment returns negative, do NOT silently reject the trigger. Instead: (1) give a concise factual answer first; (2) add: *"这是一个科学事实类问题，通常不需要结构性多学科分析。需要我用多学科框架展开它的哲学/认知层面吗？还是简短回答就够了？"* This respects the user's trigger word while transparently offering the option to pivot.

**Ambiguity rule**: If the assessment is borderline, ask the user ONE clarifying question: "This could be a short answer or a deeper structural analysis — which would you prefer?"

*Example of a borderline case*: "为什么现在年轻人不爱生孩子了" — this touches population structure, economics, and culture simultaneously (complex domain), but the user might only want a brief sociological take. This is a boundary case → trigger the clarification ask.

**Refusal handling**: → Full protocol in `extensions/exit-protocols.md`. Core: after two declined clarifications, default to lower-effort option (short answer for personal/clinical questions, Focused depth for structurally-framed questions, ambiguous→Focused).

**Protocol conflict resolution**: When user instructions activate multiple protocols that contain mutually exclusive requirements, do NOT attempt to satisfy all of them. Instead: (1) Identify and list the conflicting requirements explicitly before analysis begins, (2) State which protocol takes priority and WHY, (3) State which protocols are being suspended and that their suspension is a structural limitation of this analysis, not a defect. Priority order when conflict is unavoidable: **创伤敏感标准 > 认知递进协议 > 用户显式指令 > 其他协议默认行为**。创伤敏感标准优先于所有其他规则，因为虚假平衡在权力不对称中本身就是一种偏向。用户指令中"情绪中立"和"不偏向任何一方"在与创伤敏感标准冲突时被覆盖——这是设计，不是缺陷。

### Exit / Degradation Protocol
→ Full protocol (Collapsed/Ultra-Collapsed degradation, refusal handling, mid-generation interruption) in `extensions/exit-protocols.md`. Core rule: Collapsed Mode = 核心发现 + 关键盲点 + 分层影响表 + 一个追问.

---

## Extension Index（扩展模块 · 按需加载）

> 加载前检查 `config.yaml`。`enabled: false` 的模块跳过加载，即使触发条件满足。默认全部启用（全家桶）。

| 触发条件 | 加载扩展 | 内容 |
|---------|---------|------|
| N≥5 相关项 或 多不相关并发 | `extensions/batch-analysis.md` | 批处理协议 + 多问题分流 |
| 用户说"简单点"/"说人话" 等 | `extensions/exit-protocols.md` | 三级降级 + 拒绝处理 + 架构限制 |
| "第一感觉是..." 或 表面叙事高度误导 | `extensions/layered-protocol.md` | L1→L2→L3 认知递进 |
| 主题涉系统性暴力/歧视/具体伤害 | `extensions/trauma-sensitive.md` | 创伤敏感五约束 + 过度抽象化检查 |
| "先聊聊"/"探讨一下"/"一步步来" | `extensions/interactive.md` | 对话式分析模式 |
| 搜索不可用 | `extensions/offline-fallback.md` | 结构化先验知识框架 |

**Auto-degradation to Lite**:
- **Trigger**: 复杂度域为 Complicated（非 Clear/Complex/Chaotic）且用户未显式请求深度。
- **Clear 域**: → 简短回答 + 询问是否需要展开（不做 Lite）。
- **若用户使用了明确请求深度的触发词**（"深度分析"、"多角度"、"结构分析"、"层层剥开"等）→ 视为已显式请求深度，不触发 Auto-degradation。即使用在 Complicated 域问题上，也应至少保留 Standard 深度。
- **Lite 模式规格**（若无独立 lite skill 文件）:
  - 透镜：2-3（基础 1 + 人文 1 + 结构 1，按问题类型启发式选最相关的）
  - 工具：1（按问题动态匹配，非默认三向）
  - 输出：仅执行摘要（核心发现 + 关键分歧或置信度说明 + 分层影响表）。无详细分析。
  - 元认知：仅运行敌对测试 + 盲点验证。跳过 #2-7。
  - 声明：开头标注"> 本次采用轻量模式（2-3透镜，仅执行摘要，元认知简化）。如需标准深度 (Standard: 5-7透镜) 或更全面 (Comprehensive: 7-9) 的分析，请随时告知。"
- **Chaotic 域不降级**：Chaotic 需要即时杠杆点识别，简化版全面分析不适用。

---

## Core Methodology: The Five-Phase Ladder

```
阶段一：分解   →  真正的问题是什么？拆解为子问题
阶段二：研究   →  通过 web 搜索收集事实背景
阶段三：分析   →  应用 3-12 个学科透镜（深度缩放）
阶段四：工具   →  应用 2-3 个结构工具（三向, 80/20 等）
阶段五：合成   →  交叉验证，映射盲点，交付分层输出
```

### Phase 1: Question Decomposition

Before any research, decompose the user's question:

1. **Surface question**: What did the user literally ask?
2. **Structural question**: What underlying system is being questioned?
3. **微观处境 (Micro-situational)**: What does this answer mean for the individual?
4. **Temporal question**: What time horizon matters (now, 3yr, 10yr)?

If the question spans multiple independent structures (e.g., two unrelated policy domains), and the user hasn't specified priority, ask which direction to focus on before proceeding.

**Complexity domain assessment (internal — guides analysis tone, not output):**
After decomposition, classify the question's complexity using a simplified Cynefin framework:

| Domain | Signal | Analysis Implication |
|--------|--------|---------------------|
| **Clear** | Cause-effect is well-established; definitive answers exist | Identify the known causal chain; avoid overcomplicating |
| **Complicated** | Multiple possible causes; expert diagnosis needed but knowable | Emphasize cross-disciplinary diagnostic; multiple lenses needed |
| **Complex** | Cause-effect only visible in retrospect; emergent, unpredictable | Emphasize patterns over predictions; note limits of certainty; feedback loops matter more than root causes |
| **Chaotic** | No discernible pattern; immediate action needed | Analysis is secondary to stabilizing the situation; focus on immediate leverage points |

For **Complex** domains: the output should emphasize emergent properties, acknowledge the limits of prediction, and avoid definitive "X will cause Y" statements. For **Complicated**: emphasize diagnostic rigor and cross-verification across lenses. For **Clear**: the analysis should be concise — consider Focused depth tier.

If the question spans multiple independent structural domains (e.g., "分析美国大选对A股的影响" + "分析AI对教育公平的影响" are separate structures), pause and ask which direction to focus on before proceeding. This prevents scattered analysis across too many unrelated dimensions.

---

## Layered Analysis Protocol（认知递进模式 · 可选）

→ Full protocol in `extensions/layered-protocol.md`. Core: L1 surface impression → L2 single-lens challenge → L3 full multi-lens. Activate when user says "第一感觉是..." or surface narrative is highly misleading. When used alongside 5-Phase Ladder, L3 REPLACES Phase 3-5 (do NOT run both).

---

### Phase 2: Factual Context (Web Search)

Gather factual context before analysis. This is NOT optional — analysis without facts
is speculation dressed up as insight.

**Web search is MANDATORY** when the question involves: current events/recent policy, specific data points, user-referenced events/regulations, or topics changed since your training cutoff. **Optional** for purely philosophical/conceptual questions, timeless patterns, or when the user explicitly wants analysis without external data.

**Tool selection — use generic placeholders, adapt to current runtime environment:**

| Scenario | Tool Reference |
|----------|---------------|
| Current events, news, policy | `{search_tool}` — any available web search interface (e.g., `websearch_web_search_exa`, `web_search`, `brave_search`) |
| Specific data points | `{search_tool}` with precise, fact-targeted queries |
| Technical/library documentation | `{docs_tool}` — any available documentation lookup (e.g., `context7_query-docs`, library-specific MCP tools) |

**Search principles:**
- Run 2-4 searches in parallel with different angles
- Prioritize: official data > reputable analysis > opinion
- Capture facts, not narratives — separate "what happened" from "what it means"
- Note when data is missing or contradictory
- **Cross-domain event scan**: After initial research, scan for events in adjacent domains that occurred in the same time window and may interact with the main topic. Example: when analyzing Q2 GDP data, also check for major policy announcements, social events, or international developments from the same week. The AI伴侣禁令 was a same-week social/tech event that should have been included in the economic analysis. Cross-domain connections often produce the most insightful findings.
  - **Boundary**: Time window defaults to the same week (extend to same month for high-sensitivity events). Domain scope: 2 degrees of association from the main topic (e.g., economy → tech + social + international; society → economy + culture + tech). Beyond this radius, returns diminish rapidly unless preliminary signs already point to a distant connection.

**Information-missing handling**: If search returns no results, low-quality results, or
only irrelevant data for a critical sub-question:
1. Mark the gap explicitly: "⚠️ Could not verify [X]. The following conclusions are based on assumed preconditions and carry reduced confidence."
2. For any conclusion that DEPENDS on the missing data, prefix it with "如果 (if)" and state the assumption it rests on.
3. List these dependent conclusions in the Blind Spots section of the output.
4. Invite the user: "如果你能提供关于 [X] 的数据或来源，我可以重新校准这部分分析。"

**Information sufficiency & auto-depth-degrade**: After Phase 2 search completes, before Phase 3 lens selection, assess whether the gathered data is sufficient for the analysis precision the user requested. If key cross-sections of data are entirely missing AND cannot be reasonably inferred from indirect sources, actively suggest degrading depth by one tier (Standard→Focused, Comprehensive→Standard). State the reason explicitly: "当前搜索数据覆盖 [已覆盖维度]，但 [缺失维度] 缺乏可靠信息。以下分析降级为方向性判断，如需精度更高的分析，需要以下数据：[列出]。" The user can accept the degradation or provide supplemental data.

**Fallback when search is unavailable**: If the current runtime environment has no
accessible search tool, proceed with analysis based on pre-training knowledge only. HOWEVER:
1. Prepend to the 执行摘要: *"⚠️ 本次分析基于预训练知识，未接入实时搜索，数据可能过时。关键结论需以当前实际数据验证。"*
2. For every data-dependent conclusion, prefix with *"如果当前数据未发生显著变化，"*
3. Flag ALL conclusions as low-confidence in the 置信度说明 section.
4. **Structured prior knowledge**: When search is unavailable, use validated cross-domain frameworks (free-rider, Goodhart's law, silence spiral, S-curve, Jevons paradox, etc.) as analytical anchors. Full list in `extensions/offline-fallback.md`. Example anchors: *搭便车问题* explains why individuals under-contribute to shared resources; *古德哈特定律* ("When a measure becomes a target, it ceases to be a good measure") explains metric distortion. Mark as "理论推断（基于 [framework]，非实证验证）".

### Phase 3: Multi-Disciplinary Analysis

**Problem type heuristic (internal guide — not output, but informs lens selection):**

Before selecting lenses, classify the question's primary dynamic. Select lenses
disproportionately from the matching cluster, while still including at least one
from each Foundation/Human/Structure category.

| Problem Type | Prioritize Lenses |
|-------------|-------------------|
| **Distribution / Allocation** (who gets what) | Economics, Political Science, Institutional Analysis |
| **Identity / Belonging** (us vs. them) | Anthropology, Sociology, Psychology |
| **Transformation / Shock** (tech/policy/environment change) | Technology Studies, Systems Theory, History |
| **Governance / Compliance** (rules don't work) | Institutional Analysis, Political Science, Economics（透镜）+ Asymmetry Detection, Incentive Mapping（工具） |
| **Temporal / Rhythm Conflict** (systems out of sync) | Temporality, Institutional Analysis, Systems Theory |
| **Spatial / Territorial** (who controls space) | Geography, Political Science, Economics |
| **Physical / Ecological constraint** (what are the biophysical limits?) | Ecological/Environmental Lens, Infrastructure/Material Flow, Systems Theory |
| **Bodily / Biological limit** (how do organic constraints shape decisions?) | Life Science/Bodily Lens, Psychology, Institutional Analysis |
| **Emotional / Affective** (mobilized emotions) | Affect, Anthropology, Psychology |

For hybrid questions (most are), pick the dominant dynamic and weight lenses accordingly.
For example: "AI's impact on employment" is primarily Transformation/Shock, with secondary
Distribution/Allocation. Weight Technology Studies + Systems Theory + History heavily,
then add Economics + Sociology for distributional effects.

Select lenses according to the depth tier above (Focused: 3-4, Standard: 5-7, Comprehensive: 7-9).
**Always include at least one from each applicable category** (Foundation, Human, Structure; Material when domain-triggered).
The user's question determines which specific lenses are most relevant.

⚠️ **Anti-inertia warning**: When a question is primarily about economics/policy (e.g., GDP data, labor law), there is a strong gravitational pull to select only Economics + Political Science + Institutional Analysis — the "comfort zone" cluster. This produces flat, predictable analysis. **For every analysis, deliberately include at least one lens from the Human category (Psychology, Sociology, or Anthropology) and one lens from Foundation outside your comfort zone.** The best insights often come from the lens that initially seems least relevant. If the question is about economic data, ask: what does this mean for *how people feel and behave* (Psychology)? What *cultural meaning* does this carry (Anthropology)?

**History lens is the single most commonly dropped lens.** In three consecutive test analyses of current events, History was not meaningfully used even once. This is a systemic failure pattern. The rule: **if the question involves any current event, policy, or trend — which is nearly all questions — History MUST be one of the selected lenses.** The only valid reason to omit History is if the question is purely theoretical or the analysis is in Focused depth with fewer than 4 lenses. In Standard/Comprehensive depth, if the historical lens genuinely has limited direct contribution (e.g., a question mixing game theory with current trade policy), include it but honestly note in its Limitation section: "本透镜对此问题的直接贡献有限，以下将其用于提供历史背景而非核心洞察。" This maintains the mandatory rule without forcing fabricated depth.

**Focused-depth exemption** (EXCEPTIONAL — NOT default): In Focused depth (3-4 lenses), a Human-category lens may be waived ONLY when ALL THREE of the following criteria are met. This is a checklist, not a suggestion — failing any one criterion means the exemption does NOT apply.

**Exemption criteria** (ALL three MUST pass):

1. **Narrowness test**: The question can be fully defined by a single variable or event — no distributional effects across groups, no behavioral implications, no perception-reality gap. *"What caused PPI to drop 0.8% last month?"* may qualify. *"Why is GDP below expectations?"* does NOT — "expectations" themselves are a psychological variable embedded in the question's own framing. **Grey case**: *"Why did EV sales drop in June?"* — FAILS. Although it looks like a single metric, the drop necessarily involves consumer behavior (why people stopped buying) and likely has a perception-reality gap (media reports of decline may further suppress purchases). If the metric's movement cannot be explained without invoking human decision-making, the narrowness test fails.

2. **Rapid insight test (THE GATEKEEPER)**: Can you articulate, in 10 seconds, a specific, non-obvious insight that a Human lens COULD produce for this question? If yes → exemption does NOT apply. If you can think of one, you must use it. The 10-second constraint is deliberate: long enough to retrieve one relevant concept from memory, too short to fabricate a fake one. This test exists to prevent "I didn't think hard enough" from masquerading as "no insight was possible."

3. **Declaration requirement**: If both criteria above are passed and exemption is invoked, the 执行摘要 - 置信度说明 MUST contain: (a) name the specific Human lens being omitted — "Psychology" or "Sociology" or "Anthropology", not the generic phrase "a human lens"; (b) state why it can only produce common-sense insight FOR THIS SPECIFIC QUESTION; (c) provide one counter-example — a slightly broader version of the question where this lens WOULD be indispensable, demonstrating you understand the boundary between "narrow enough" and "too broad."

**Exemption is exceptional, not default.** If this analysis uses NO Human-category lens and you cannot pass all three criteria above in 30 seconds or less — the omission was laziness, not judgment. Re-select lenses. Standard and Comprehensive depths have no such exemption under any circumstances.

**Analysis depth scaling** — not every question needs the full 8-lens treatment:

| Depth | Lenses | Tools (from 9-tool pool) | When to Use |
|-------|--------|-------|-------------|
| **Focused** | 3-4 (1 per applicable category) | 1-2 | Specific, narrow question with clear boundaries |
| **Standard** | 5-7 (1-2 per applicable category) | 2-3 | Most analyses — complex but not overwhelming |
| **Comprehensive** | 7-9 (2-3 per applicable category) | 3-4 | Broad systemic questions with high ambiguity |

**Material depth note**: Material lenses are counted within the lens budget ONLY when triggered by domain. When no material trigger fires, the budget is allocated across the three standard categories. Material lenses are not an additional overhead imposed on every analysis — they are a precision tool activated by relevance.

**Depth selection heuristic**: If the question can be answered with a single disciplinary
insight, use Focused. If it requires understanding interactions between 2+ systems, use
Standard. If it's about a civilization-level transformation (e.g., "what happens when AI
replaces most jobs"), use Comprehensive.

**Default depth**: When the user hasn't specified, default to **Standard** (5-7 lenses).
At the start of the analysis output, state: *"本次采用标准深度 (Standard, 5-7 透镜)。如需更精简 (Focused, 3-4) 或更全面 (Comprehensive, 7-9) 的分析，请告知。"*
This gives the user control and sets expectations.

**Comprehensive cap**: Maximum 10 lenses per analysis (material lenses counted only when domain-triggered). If the user requests all lenses, select the 10 most relevant and declare in the 置信度说明 which lenses were omitted and why.

#### Lens Categories (select 1+ from each applicable category)

| Category | Lens | Core Question | Use When |
|----------|------|--------------|----------|
| **Foundation** (1-2) | Epistemology | What are the unstated assumptions? What can we truly know? | Always — sets the frame |
| | Systems Theory | What feedback loops and leverage points are at work? | Complex multi-variable problems |
| | History | What precedent exists? What makes this time different? | Current events, policy, trends (MANDATORY except pure theory or Focused <4 lenses) |
| | Temporality | Whose time is compressed? What is accelerating vs. decelerating? | Burnout, policy lag, intergenerational justice |
| **Human** (1-2) | Psychology | How do humans process this? What biases are active? | Human decision-making |
| | Sociology | What social structures and norms shape this? | Group behavior, social dynamics |
| | Anthropology | What cultural meaning and rituals are involved? | Cultural phenomena, value conflicts |
| | Affect | What emotions are mobilized, commodified, or suppressed? | Service labor, social media, political煽动 |
| **Structure** (1-3) | Economics | What are the incentives? Who bears costs? | Resource distribution, market analysis |
| | Political Science | Who has power? How is it exercised? | Governance, policy, collective action |
| | Institutional Analysis | Formal rules vs. actual practices — why does the gap exist? | Policy implementation, organizational behavior |
| | Technology Studies | How does tech interact with human systems? | AI, automation, digital transformation |
| | Geography | How is space produced, distributed, and contested? | Urbanization, regional inequality, infrastructure |
| **Material** (0-1, domain-triggered mandatory) | Ecological/Environmental | What ecosystem services does this system depend on? What physical thresholds are being approached or breached? | Climate, energy, agriculture, resource extraction |
| | Infrastructure/Material Flow | What physical infrastructure and material flows does this system rely on? What are their failure modes? | Supply chains, compute/energy infrastructure, manufacturing |
| | Life Science/Bodily | What biological constraints shape the decision-makers and populations in this system? | Crisis decision-making, public health, aging, cognitive neuroscience |

#### Lens Application Protocol

For EACH lens, answer:
1. **Core insight**: What does this lens reveal that others might miss?
2. **Key framework**: What theory/model from this discipline applies here?
3. **Limitation**: What does this lens systematically overlook?
4. **Tension with other lenses**: Where does this lens conflict with findings from other lenses? — For this field, you may annotate "待交叉验证" during the initial lens-by-lens pass, then backfill once all lenses have been drafted. If no real tension exists after full review, note "与其他透镜视角无实质冲突。"

**CRITICAL**: Do NOT just restate what the lens is. Apply it to the SPECIFIC question.
Bad: "Economics tells us about supply and demand."
Good: "Economics reveals that the labor market's failure to absorb displaced workers
is not a demand problem — demand exists for services — it's an incentive problem:
enterprises face no penalty for offloading workers onto flexible platforms, creating
a subsidy from labor to capital."

**Fact-binding requirement**: Each lens analysis MUST reference at least one
concrete fact, data point, or verifiable event from Phase 2 research. Lenses
may draw on pre-training knowledge for frameworks and theory, but their APPLICATION
to the specific question must be grounded in researched facts. If a lens cannot
be fact-bound (because the relevant data doesn't exist), note this explicitly
in the Limitation section for that lens.

#### Material Lenses: Domain-Triggered Mandatory Protocol

Material lenses are NOT universally mandatory. They follow a domain-triggered rule analogous to the History lens rule. **When the question's domain matches a trigger, the corresponding Material lens becomes mandatory for that analysis.** When no trigger matches, Material lenses are optional.

| Trigger Condition | Mandatory Lens |
|------------------|----------------|
| Question involves climate, energy, environment, agriculture, natural resources | **Ecological/Environmental** |
| Question involves infrastructure, supply chains, compute hardware, manufacturing, logistics | **Infrastructure/Material Flow** |
| Question involves crisis decision-making, public health, bioethics, cognitive performance under stress | **Life Science/Bodily** |

**⚠️ 反物质决定论警告**：当分析因触发条件而包含物质透镜时，必须同时至少包含一个**人类透镜**（心理学、社会学或人类学）。物质约束不直接决定人类行为——它们通过人类感知、制度中介和社会动员来施加影响。说"碳预算限制了一切"本身的准确性不亚于说"碳预算限制了一切——但是否被接受取决于政治叙事和公众认知"。物质透镜告诉你"物理世界允许什么"——人类透镜告诉你"人们愿意接受什么"。

**Material lens application protocol**（与其他透镜一致）：
1. **Core insight**: What physical or biological constraint does this lens reveal?
2. **Key framework**: What model/data from this discipline applies? (e.g., planetary boundaries, EROI, material flow analysis, allostatic load)
3. **Limitation**: This lens reveals constraints but not how humans will respond to them — do NOT use it to make deterministic predictions about human behavior.
4. **Tension with other lenses**: Common tensions include Economics (efficiency vs. sustainability), Systems Theory (feedback loops vs. hard physical ceilings), Psychology (cognitive mechanisms vs. neurophysiological substrates).

**Common Material × Structure tensions**（延伸现有张力表）：
| Lens Pair | Typical Tension |
|-----------|----------------|
| Economics vs. Ecological/Environmental | Discount-rate optimization vs. intergenerational ecosystem debt |
| Political Science vs. Infrastructure/Material Flow | Sovereignty claims vs. transboundary material dependencies |
| Institutional Analysis vs. Life Science/Bodily | Rule design vs. biological limits of decision-makers under prolonged stress |

### Phase 4: Structural Tool Application

Select 2-3 tools from the pool below. **Choose tools that match the question's structural nature** — do NOT default to 三向 alone. It is a structural snapshot tool, not a universal starting point.

**Tool selection guide — match the tool to the problem dynamic:**

| If the issue is about... | Prioritize these tools |
|--------------------------|----------------------|
| **Stable inequality & distribution** (who has what?) | 三向, 80/20 Principle |
| **System change over time** (transformation, collapse, renewal) | Adaptive Cycle, Path Dependency |
| **Hidden rules & asymmetries** (why do stated rules ≠ actual outcomes?) | Asymmetry Detection, Incentive Mapping |
| **Relations & networks** (who connects to whom, with what effect?) | Capital Type Matrix, 三向 (cross-check flow between directions) |
| **Temporal mismatch / rhythm conflict** (whose time is compressed? benefit window vs. cost window?) | Incentive Mapping (time-alignment check), Asymmetry Detection (temporal discount asymmetry), Path Dependency (lock-in of short-termism) |
| **Encoded communication & multi-audience messaging** (why was this statement released now, and what is it signaling to whom?) | Multi-Layer Signal Decoding |

#### Tool Pool (9 tools)

##### A. Distribution & Concentration Tools

**三向 (Tri-directional Lens)** — *认知透镜，非科学理论。在存在正反馈的竞争系统中，三个方向因不同性质的约束而分化：顶向被惯性约束（资源流向已有资源），中向被恐惧约束（"不要成为底向"强于"想成为顶向"），底向被边界约束（存在本身成为系统的参照底线）。核心不是"有三层"——是"三层被三种不同性质的约束固定在原地"。*

**四条观察模式（简版）**：(1) 分化默认——初始差异+正反馈+资源约束→三向涌现；(2) 恐惧驱动中向——向下斥力>向上引力；(3) 底向是结构占位符——N%在数学上必然存在，可改变的是其功能；(4) 时间流速差（最弱，因果未定）——三向在不同时间粒度上运作。

**使用纪律**：配合 Capital Type Matrix 分析流动性，配合 Adaptive Cycle 分析系统性转型，配合 Reflexivity 分析信念循环。问自己：中向在膨胀还是压缩？底向对中向是否可见？有跨向联盟吗？使用前区分 ABC 三类"三"——B类（物理约束）和C类（历史锁定）不适用此透镜。**校准检查**：拿掉透镜重新看，结论一致=装饰已知，不一致=可能在工作，相反=过度拟合。

> 完整文档（含稳定性启发式、演变方向、流动障碍图、已知局限）：`docs/三向理论.md`。

**80/20 (Pareto) Principle** — *经验模式，非数学定律。在幂律分布中成立——在均匀分布中不成立。用它来集中注意力，不要用它来"证明"不平等是自然的。*

##### B. System Dynamics Tools

**Adaptive Cycle (Holling's Panarchy)** — *生态学隐喻，不是机械周期。C.S. Holling (1986) 从森林生态系统的动态中抽象出这四个阶段。Gunderson & Holling (2002) 扩展为跨尺度的"泛archy"。它的力量在于揭示"稳定期积累的刚性如何在释放期爆发"——但真实系统不总是按 r→K→Ω→α 的顺序走，可能跳过阶段，可能卡在某个阶段数十年。用它来问"系统在积累哪种脆弱性"，不要用它来预测"下一个阶段何时到来"。*

Four phases every system cycles through:
- **Growth (r)**: Rapid expansion, resource accumulation, high resilience
- **Conservation (K)**: Stability, efficiency, but growing rigidity and vulnerability
- **Release (Ω)**: Collapse or rapid restructuring — old structures break down
- **Reorganization (α)**: Innovation, experimentation, new configurations emerge

**Application questions:**
- Which phase is the system in, and where is rigidity accumulating?
- What would "release" look like — and what might emerge in reorganization?
- Is the system trapped (rigidity trap, poverty trap)?
- **校准检查**：拿掉这个透镜，用常识看——你能描述系统当前的状态而不使用"处于 K 阶段"这种语言吗？如果能，而且描述同样清晰——透镜可能在装饰已知。如果"刚性在积累"这个洞察在没有透镜的帮助下不会出现在你的常识描述中——透镜在工作。

**Path Dependency & Lock-in** — *历史叙事工具，不是预测模型。Paul David (1985) 的 QWERTY 键盘研究和 Brian Arthur (1989) 的锁定效应模型奠定了它的基础。它帮你解释"为什么已经不好的东西还在持续"——但它有一个深层陷阱：几乎任何持续存在的东西都可以被事后描述为"路径依赖"。不是所有持续都是锁定——有些持续是因为一直在赢。用它来追问"切换成本在哪里"，不要用它来暗示"当时选错了"。*

- What key historical decision locked in the current trajectory?
- What feedback loops reinforce the status quo (institutional, economic, psychological)?
- What transition costs prevent switching?
- Where is the lock-in weakest?
- **校准检查**：拿掉这个透镜，用常识看——这个系统的持续性是否可以用"它仍然在满足当前需求"来充分解释？如果可以——可能不是路径依赖，只是惯性+适应。如果"切换成本"是唯一的障碍——透镜在工作。

##### C. Asymmetry & Incentive Tools

**Asymmetry Detection (includes Macro-Micro Gap)** — *认知警觉训练，不是测量工具。这个透镜强迫你寻找"书面vs实际"、"宏观vs微观"、"声称vs行动"之间的裂缝。它的起源是多元的——制度分析（制度半失效）、经济学（信息不对称）、社会学（宏观-微观差距）。它的陷阱是：如果你带着"一定存在不对称"的预设去分析任何系统，你会找到不对称——因为现实和理想之间永远有裂缝。问题不是"有没有裂缝"——是"裂缝大到了能解释系统为什么像现在这样运作的程度吗"。** 区分：沉默信号（机构行为→正文）≠ 数据缺失（搜索限制→置信度说明）。

Gaps to detect:
- Written rules vs. actual practice
- Macro narrative vs. micro experience (GDP vs. purchasing power, time sovereignty, dignity)
- Espoused values vs. revealed preferences
- Legal text vs. enforcement reality
- **Cognitive/Attention asymmetry**: Who holds the information advantage and defines what counts as expertise?
- **Temporal discount asymmetry**: Decision-makers enjoy short-term gains; costs borne by future populations
- **制度半失效**: Rules exist on paper but are systemically circumvented. Key question: *Who benefits from the gap?*
- **无信号即信号**: When an institution that SHOULD respond stays silent, the silence itself is data. *Who benefits from the silence?*
- **校准检查**：拿掉这个透镜，用常识看——这个系统中的裂缝是不是每个有常识的人都能注意到的？如果是——透镜在帮你命名已知，不在帮你发现未知。如果裂缝只有在透镜引导下才会被注意到——透镜在工作。最危险的信号：你每次都用这个透镜找到"制度半失效"和"沉默即信号"——这可能不是系统充满不对称，是你被训练成了不对称寻找机器。

**Incentive Structure Mapping** — *分析框架，来自公共选择理论和组织经济学。核心问题是"谁决定、谁付钱、谁受益"——当决策者和成本承担者不是同一个人时，激励结构系统性地偏向短视。它的陷阱：很容易变成一个"找坏人"的工具——但实际上大多数失调的激励结构不是被设计出来的，是涌现出来的。不要问"谁在故意制造坏的激励"——问"在当前的规则下，任何一个理性人会不会做出同样的选择"。*

- If decision-makers and cost-bearers are different groups, what prevents alignment?
- What would happen if costs were internalized?
- **Time-alignment check**: When do decision-makers receive benefits vs. when do costs materialize (and who bears them)? If there's a temporal mismatch between benefit window and cost window, the incentive structure systematically favors short-termism, regardless of individual morality.
- **校准检查**：拿掉这个透镜，用常识看——你能否不用"激励失调"的语言来描述这个系统的问题？如果能，而且同样准确——透镜在工作（它帮你看到了更深层的结构）。如果不能——你可能只是在给一个显而易见的问题贴上"激励问题"的标签。

##### D. Network & Capital Tools

**Capital Type Matrix (Bourdieu)** — *分类框架，来自 Pierre Bourdieu 对 1970 年代法国社会的分析。四种资本类型（经济/文化/社会/符号）是特定历史和社会条件的产物——在非西方社会、数字时代或非层级化组织中，资本的分类边界可能需要重划。用它来问"还有什么形式的资本在这个系统中起作用"，不要用它来假设"这四个类型在所有文化中都同样适用"。*

Four capital types that determine social position and mobility:
- **Economic capital**: Money, assets, property — directly convertible to currency
- **Cultural capital**: Education, credentials, taste, knowledge — institutionalized (degrees), embodied (skills), or objectified (books, tools)
- **Social capital**: Networks, connections, group membership — "who you know" and the resources they can mobilize
- **Symbolic capital**: Prestige, honor, recognition — the legitimized form of other capitals

**Application questions:**
- Which capital type is most decisive here, and can disadvantaged groups convert between types at fair rates?
- Who holds bridging social capital (across tiers) vs. bonding (within-tier)?
- Where are "structural holes" — gaps that if bridged would create outsized advantage?
- **校准检查**：拿掉这个框架，用常识看——你能否描述这个系统中"谁有优势"而不使用四种资本的分类？如果能——框架在给你一套更系统的语言，但不一定在提供新的洞察。如果某种资本类型（比如"符号资本"）在你的常识分析中完全被忽略了——框架在帮你看到盲区。

##### E. Reflexivity Tools

**Reflexivity Analysis** — *认知工具，来自 George Soros 对金融市场的分析和科学社会学对观察者效应的研究。当参与者的信念改变系统行为、系统行为反过来改变信念时，线性因果分析失效。最危险的误用：把普通反馈循环错标为反身性。反身性要求"信念"是循环的一部分——恒温器是反馈循环（没有信念参与），QWERTY 键盘是路径依赖（历史锁定），房价泡沫才是反身性（"相信房价永远涨"→买→涨→更相信）。如果你不确定，用区分测试。*

**Application questions:**
- Are participants' beliefs about the system changing the system's behavior? (e.g., "everyone believes housing prices will always rise" → they buy → prices rise)
- Is there "indicator-driven distortion"? Is the loop amplifying (bubble) or decaying (trust collapse)?
- At what point would the loop break — what is the critical threshold?

**Distinction test**: Remove the observer — if the loop DISAPPEARS → reflexivity. If it continues independently → feedback loop or path dependency. **Nested scenario**: When belief drives behavior, behavior changes rules, and new rules reshape belief, do NOT force single classification. Label as "反身性+反馈循环嵌套" and note in limitations which level of analysis the distinction is based on.

**Positionality annotation**（当分析者本身是被分析对象的一部分时使用）: State concretely which aspect of the analyzer's own constitution contaminates which specific judgment. Format: "一个 [训练数据/文化背景/制度位置] 的分析者说 [结论]——这个结论的可信度被 [具体污染源] 所影响。" This is NOT a generic disclaimer ("I have biases") — it pinpoints the exact mechanism of contamination so the reader can assess it independently.

**校准检查**：拿掉这个透镜，用常识看——这个系统的动态是否可以用"人们根据经验调整行为"来解释（这是普通学习，不是反身性）？如果可以——不要用反身性。只有当信念的介入改变了系统的基本运作规则时——反身性才是在工作的。

##### F. Communication & Signal Tools

**多层信号解码 (Multi-Layer Signal Decoding)** — *这是一个认知解码工具，不是信号探测仪。它帮你注意到信息中的博弈结构，但它发现的"信号"可能更多反映了你自身的解码预设，而非发送者的真实意图。它不是分析"信息说了什么"——而是在分析"为什么这段信息中的每一个幸存词都是经过博弈后留下的"。*

在 AI 时代的组织沟通中，任何面向公众的文本——尤其是经过内部 AI 分析筛选后释放的文本——不存在"无意中留下的话"。每一句幸存下来的话，至少满足一个条件：必须说的真话、故意放的信号、用来稀释注意力的填充、或是为了增加可信度而故意留下的破绽。

**⚠️ 使用前必须通过三问测试**——任何一关不过，放下工具：
- **信源是否有可损失的信用？** （上市公司CEO ✅，匿名用户 ❌）
- **信息经过至少一层筛选吗？** （内部信经PR审查 ✅，实时直播 ❌）
- **发布者和接收者之间存在利益博弈吗？** （融资博弈 ✅，教程作者 ❌）

**三个分析轴**：

**轴一：信号生存分析** — 对所有存留信息强制分类为：必须说的真话（不说会被戳穿）、故意放的信号（对特定接收者编码）、掩护填充（保护核心信息的注意力稀释）、可信度锚点（故意留的破绽用来证明"这是真的"）。⚠️ **嵌套危险信号**：如果可信度锚点被暴露得太精确、太有策略性——发送者可能已经预判了你正在使用不对称检测并提前反制。区分：真实的破绽通常只服务于一个叙事目标；策略性"可控弱点"会同时服务多个目标（可信度提升 + 信息锚定 + 误导方向）。

**轴二：多接收者映射** — 对每一段有信息量的内容，强制识别至少三个接收者（投资人、竞争对手、监管者、团队内部、媒体/公众），并解码对每一个接收者的不同含义。好的编码 = 一段话对五个不同的接收者传递五种不同的信息。

**轴三：时序关联域** — 将信号与其发布时刻的同时事件强制关联。向左看7天（什么触发了这个信号），向右看3个月（这个信号在为什么铺路）。主要信号通常至少满足：危机管理、预期管理、战场定位、叙事铺垫中的一个。

**使用时序——推荐分析序列**：
1. **MLSD（阶段一：解码所有公开信号）** → 2. **Asymmetry Detection（阶段二：将信号与内部行为对比，寻找裂缝）** → 3. **Reflexivity Analysis（阶段三：追踪信念→行为→信念的反身性循环）**

⚠️ **嵌套场景——当发送者预判了你的工具**：当发送者知道受众会进行不对称检测，ta 可能预先编入"可控弱点"以增加可信度。如果可信度锚点被暴露得太精确——发送者可能已内化了你的分析工具并提前反制。

**校准检查**：退出工具，用最简单的语言重新描述这段文本。朴素描述和工具分析的对比——如果朴素描述已经蕴含了相同的结论，工具在装饰已知。如果工具发现了朴素描述无法揭示的结构性约束，工具可能在工作。**额外检查——拿掉这个工具，用最朴素的常识重新读一遍这段文本。你看到的"隐藏信号"是否可能只是一个普通人在压力下自然地选择措辞？如果朴素解读和工具解读得出相同结论——工具在装饰已知。如果工具解读让你看到朴素解读看不到的结构——工具在工作。如果工具解读让你看到了和朴素解读相反的东西——你大概率在过度拟合。**

**跨信源对照**：当分析同一时间窗口的多个信源时，寻找信号共振（多个信源释放相似信号→正在形成共识或解体的旧共识）、信号对抗（相反方向的信号→争夺叙事定义权）、信号沉默（所有相关方在发声时一方选择沉默→沉默本身就是信号）。

**边际价值归零检查**（MLSD 专用版）：如果连续三次使用这个工具，你每次发现的都是"被编码的困境"、"被迫的选择"、"不可说的真实意图"——你可能不是在解码发送者，你是在重复自己的解码习惯。

**已知局限**：
1. 假设发送者是理性的——非理性发送者会导致工具找出不存在的信号（最大失效模式）
2. 过度拟合风险极高——校准检查只能部分防御，不能完全消除
3. 对来源质量极度敏感——低质量信源产生的是投射，不是洞察
4. 无法分析信息空白——被完全删除的段落和选择的沉默不在工具的覆盖范围内。使用缺失检测协议（完整文档中）获取部分防御
5. 无法区分"策略性表现"和"压力性症状"——当发送者在长期危机压力下发言时，ta 的话可能已是认知资源的耗尽（来源：BP 2010 案例）
6. 历史校准已完成——基于七个已知结局案例（含四个边界测试：Powell/BP/Apple/Google）的系统校准。可靠性退化曲线见完整文档
7. 接收者超过五个时注意力配给效应——间接接收者可能被系统性遗漏，且其对长期演化的影响可能反超前排（来源：Apple 2016 案例）
8. 文本中存在显眼"信息空白"时——核心策略信号可能位于文本之外，工具产出必须附带标注（来源：Google 2010 案例）

**可靠性退化曲线**：正常→高 | 发送者不确定性→中 | 理性框架收窄→中转低 | 危机压力→低或退出 | 非理性→不适用。完整文档见 `docs/多层信号解码.md`。

**集成状态**：独立可用，已集成进 Skill 的 Phase 4 工具池 F 类。完整文档见 `docs/多层信号解码.md`，精简版在此。

---

**工具使用通用纪律**（适用于以上所有工具——不限于三向）：
- 每次使用工具后，**把工具拿掉**。用最朴素的常识重新看同一个系统。工具视角和常识视角看到的东西一样吗？如果一样——工具在装饰已知。如果不同——工具可能在工作。如果相反——你可能在强行套用。
- 如果一个工具在连续多次使用中从未让你对系统产生新的理解——**你不是在"使用"它，你是在"重复"它。** 放下它，换一个工具。工具的边际价值在你不再从它身上学到东西的那一刻归零。
- 同时使用多个工具时——**不要让其中一个工具定义所有其他工具的术语。** 如果你发现自己在用工具 A 的概念来描述工具 B 的发现——停下来。这说明工具 A 在支配你的分析，而不是在服务你的分析。
- **没有任何工具需要永远被使用。** 一个工具在你学会它的那一刻最有价值——之后价值递减。每隔一段时间，问自己：**"如果今天我第一次听说这个工具，我会用它吗？"** 如果答案是不会——你在用它的防腐版，不是它的活版。

---

## Supplementary Analysis Templates (L3 Layer)

Speed-reference — apply 1-2 per lens as sub-frameworks during lens analysis or Phase 5 synthesis. Models know these concepts from pre-training; this table maps them to lenses as a reminder.

| Template | Primary Lens | | Template | Primary Lens |
|----------|-------------|---|----------|-------------|
| Long Tail | Economics | | Principal-Agent | Economics |
| Base Rate | Psychology | | Information Asymmetry | Economics |
| S-Curve / Diffusion | Technology | | Externalities | Economics |
| Tipping Point | Sociology | | Confirmation Bias | Psychology |
| Lock-in Mechanisms | History | | Framing Effect | Anthropology |
| Commons Governance | Political Science | | First Principles | Systems Theory |
| Prisoner's Dilemma | Political Science | | Second-Order | Psychology |
| Zero-Sum vs Positive-Sum | Economics | | Pre-mortem / Hubris | Systems Theory |
| Tradeoff Transparency | All (synthesis) | | Materiality Check | All (blind-spot) |
| MECE Principle | All (quality) | | Inversion | All (strategy) |

**Before synthesizing, complete the tension backfill**: Review all lenses that marked
tension as "待交叉验证." For each pair of lenses, determine whether a substantive
conflict exists. If none found, annotate both as "与其他透镜视角无实质冲突，但提供了
补充性视角。" Do NOT leave any "待交叉验证" marker unresolved before delivering output.

**Internal reference: Common lens tensions** (guide, not output — use to accelerate cross-checking):

| Lens Pair | Typical Tension |
|-----------|----------------|
| Economics vs. Anthropology | Efficiency logic vs. meaning/gift/reciprocity logic |
| Systems Theory vs. Psychology | Structural determinism vs. individual agency |
| Political Science vs. Technology Studies | Power concentration vs. tech-enabled diffusion; regulatory lag vs. tech acceleration |
| Institutional Analysis vs. Sociology | Formal rules vs. informal norms; design intent vs. implementation culture |
| History vs. Systems Theory | Contingency/path dependency vs. systemic regularities |
| Temporality vs. Institutional Analysis | Tech/social acceleration vs. institutional inertia |
| Temporality vs. Economics | Social/ecological rhythm vs. discount-rate logic — economics discounts the future; temporality asks "who sets the discount rate, and for whom?" |
| Economics vs. Temporality | Discount-rate optimization vs. intergenerational time sovereignty |

*Note: This is a prompt list, not a mandate. Do NOT fabricate tensions. If no conflict exists, say so.*

After all lenses and tools have been applied, synthesize:

**Optional: Key Counterfactual check** — Before finalizing synthesis, identify 1-2 critical
branching points where a different historical choice could have produced a meaningfully
different trajectory. Ask: *"If the opposite choice had been made at [point X], what would
the system look like today?"* The purpose is NOT to speculate about alternative histories,
but to expose which features of the current system are contingent (not inevitable) —
these are potential high-leverage intervention points.

1. **Cross-validation findings**: What 2-3 insights are independently corroborated by multiple lenses?
2. **Divergences**: Where do lenses disagree? If largely in agreement, say so directly.
3. **Blind spots**: What is systematically invisible to all lenses used?
4. **Leverage points**: Where would a small change produce outsized effects? When discussing leverage, reference the Meadows hierarchy (12 levels, from weakest to strongest): constants/parameters → buffer sizes → material flows → delays → balancing feedback → reinforcing feedback → information flows → rules → self-organization → goals → paradigm. For most complex questions, the highest-leverage intervention is at the level of **rules, goals, or paradigms** — not adjusting surface parameters. Identify which level(s) your proposed interventions target, and whether lower-level tweaks are masking the need for higher-level change.

5. **读者影响检查**: Before finalizing, ask: "If someone whose life is directly affected by this issue reads this analysis, what would they take away?" If the answer is only abstract systemic insights with no personal resonance, the analysis has failed the 个体 row of the 分层影响 table. The conclusion must include at least one concrete, actionable observation that a non-expert could recognize as true from their own experience.

#### Synthesis Output Structure

**Part A：执行摘要**（强制首先输出）——深度声明+复杂度域→核心发现→多镜共识→置信度说明→关键分歧→分层影响表（系统-制度-个体×短期-中期-长期）→最高杠杆干预（Meadows层级：参数→规则→目标→范式）。以"需要我展开吗？"结尾。

**Part B：详细分析**（按需展开）——结构工具应用→多镜交叉验证表→透镜深入（每透镜1段：核心洞察/框架/局限/张力）→盲点与置信度说明。

## Output Quality Standards

**Must**: 所有结论事实绑定。多镜共识显式标注。盲点清单。MECE。至少一个非专家可从自身经验识别为真的可操作观察。中英混杂严禁——常见概念用中文，仅无标准翻译的专有名词（Meadows, Cynefin, Bourdieu等）保留英文。

**Blocking**: 单透镜结论。无分层影响表。致命盲点遗漏。假共识。绝对化声明无置信度限定。标签化非分析（"从心理学来看"未具体到机制）。置信度说明被跳过。透镜未显式命名。简短回答超限（≤100中文字符）。

---

## Interactive Analysis（对话式 · 可选）

→ Full protocol in `extensions/interactive.md`. Alternative to one-shot delivery: direction proposal → incremental delivery → on-demand synthesis. Activate when user says "先聊聊"/"探讨一下"/"一步步来". Appropriate for exploration, not decision-support.

---

## Metacognitive Checkpoint (before delivering final output)

Before concluding the analysis, run this self-check:

1. **Adversarial test**: "If I were an expert holding the OPPOSITE position, which three
   points in this analysis would I attack as weakest? Why?"

2. **Data-dependence audit**: "Which conclusions in this analysis would significantly
   change if the search data turned out to be wrong or incomplete?"

3. **Blind-spot verification**: "Is there a stakeholder group, time scale, or causal
   mechanism that I haven't meaningfully addressed?"

4. **Temporal bias check**: "Did this analysis default to a specific time horizon
   (e.g., policy-cycle thinking of 3-5 years) while neglecting longer/shorter rhythms?
   Would the conclusions change if stretched to intergenerational scale or compressed
   to crisis-response speed? Are there latent assumptions about 'natural' time frames
   (e.g., quarterly reporting, election cycles) that the analysis accepts uncritically?"

5. **Dimension coverage check**: Map this analysis against the three lens categories. Did the
   analysis genuinely deliver insights from all three — Foundation, Human, and Structure — or
   did it drift into a single-axis comfort zone (typically economics-politics)? If the Human
   category (Psychology/Sociology/Anthropology) produced only shallow or ritualistic output,
   this analysis is incomplete. The test: can you articulate ONE specific, non-obvious insight
   from a Human lens that would change how a reader thinks about this topic? If not, revisit.

If (1) reveals any easily-attacked point, strengthen it or note it. If (2) identifies fragile
conclusions, flag them for output. If (3) finds gaps, either fill them or list them.

6. **Normative stance check**: "What value priority does this analysis implicitly assume? (efficiency over equity, individual freedom over collective protection, stability over transformation?) If I changed the value hierarchy, would the conclusions still hold — or would a different set of interventions emerge?" This does not resolve value conflicts, but requires that the analysis know its own position rather than pretend neutrality.

7. **过度抽象化风险检查** — triggered ONLY for trauma/violence/discrimination topics. → Full protocol and anti-dilution constraint in `extensions/trauma-sensitive.md`. Core: ask "has this analysis turned real human pain into a bloodless intellectual puzzle?" If yes, add direct acknowledgment. Does NOT require softening or avoiding power asymmetry — "pointing out who benefits" is the analysis doing its job.

**Self-reference degradation**（自指场景降级）: When the analyzed object IS the metacognitive framework itself, checks #2 (data-dependence audit), #3 (blind-spot verification), and #4 (temporal bias check) may fail due to category mismatch — the framework has no fact-assertions to audit, no stakeholders, and no time-sensitive causal mechanisms. In this case, run only #1, #5, #6, #7. Explicitly note which checks were skipped and why: "框架分析自身时，[#2/#3/#4] 因范畴不匹配而跳过。这不是框架缺陷——这是框架为此类问题而设计的边界。"

**Output binding with tiered allocation**:
- **执行摘要 - 置信度说明**: only the highest-risk item from steps (1) and (2) — those that would materially change the core finding or individual strategy if wrong.
- **详细分析 - 盲点与置信度说明**: the FULL list of attackable points, data dependencies, and blind-spot gaps from all three steps.

---

## Skill Invocation Protocol

When this skill is triggered:

1. **Run trigger guard**: Apply the Complexity Quick Assessment before proceeding
2. **Announce depth**: State the selected depth tier (default: Standard) with a one-line summary at the start of output.
   *Mild depth auto-detection*: If the user used "非常深入", "全面剖析", "层层剥开", etc. → default to Comprehensive. If "大概", "简要", "简单聊一下" → default to Focused. When uncertain, keep Standard and ask.
3. **Execute Phases 1-5**: Decompose → Research → Analyze → Apply Tools → Synthesize
4. **Output Part A (Executive Summary) first** — always. End with the opt-in prompt for detailed expansion
5. **输出格式化自查**：生成最终输出前，扫描全部文本，将不必要的英文术语替换为中文对应词（常见概念、章节标题、表格标签）。仅保留无标准中文翻译的专有名词（Cynefin, Meadows, Bourdieu 等）和深度声明中的 "Focused/Standard/Comprehensive"。
6. **Run metacognitive checkpoint** before final delivery
7. **Be transparent about limitations**: State what you couldn't verify, what lenses you omitted and why
8. **Respect exit protocol**: If user asks for shorter output, switch to Collapsed Mode immediately

### Quick Reference Card

```
┌─────────────────────────────────────────────────────┐
│            DEEP STRUCTURAL ANALYSIS                  │
├─────────────────────────────────────────────────────┤
│ PHASE 1: DECOMPOSE + Cynefin complexity class       │
│   Surface → Structural → Micro-situational → Temporal│
├─────────────────────────────────────────────────────┤
│ PHASE 2: RESEARCH (parallel {search_tool})          │
│   Facts first → info-missing flag → assumptions logged│
├─────────────────────────────────────────────────────┤
│ PHASE 3: ANALYZE (3-12 lenses, fact-bound)           │
│   Problem-type heuristic → weighted lens selection   │
│   Foundation:  Philosophy, Systems, History, Tempo   │
│   Human:       Psychology, Sociology, Anthropology, Affect │
│   Structure:   Economics, PoliSci, Institutions, Tech, Geo │
├─────────────────────────────────────────────────────┤
│ PHASE 4: STRUCTURAL TOOLS (2-3 from 8-tool pool)    │
│   Dist: 三向, 80/20 | Dynamic: Adaptive, Path Dep│
│   Asym: Gap, Incentive | Network: Capital Matrix    │
├─────────────────────────────────────────────────────┤
│ PHASE 5: SYNTHESIZE & DELIVER                       │
│   执行摘要 (required) → 详细分析 (on demand)│
│   Leverage: Meadows hierarchy (param→rules→paradigm)│
│   Cross-validation → Divergences → Blind Spots      │
├─────────────────────────────────────────────────────┤
│ DEPTH: Focused(3-4) / Standard(5-7) / Comprehensive(7-9)       │
│ EXIT: Collapsed Mode | CHECK: Metacognitive audit   │
│ BATCH: N≥5 → Cluster(3-5) → Tier depth → Unified synth │
└─────────────────────────────────────────────────────┘
```
