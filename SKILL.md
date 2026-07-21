---
name: deep-structural-analysis
description: >-
  Multi-perspective structural analysis skill for deep, cross-disciplinary examination
  of complex social, economic, philosophical, and systemic questions. When users ask for
  deep analysis, structural understanding, or multi-angle exploration of a topic — especially
  questions involving power structures, social dynamics, systemic contradictions, or
  why-things-are-the-way-they-are — invoke this skill. Trigger phrases (Chinese): '深度分析',
  '多角度', '从多个视角', '二六二', '二六二定律', '二六二分布模型', '结构分析', '用XX视角看',
  '分析一下这个现象', '从XX框架分析'. Trigger phrases (English): 'deep analysis',
  'multi-perspective', 'cross-disciplinary', 'structural analysis', '2-6-2 framework',
  'analyze from multiple angles', 'systemic analysis'. Note: standalone '为什么' or '你怎么看'
  only trigger when the question is about a complex social/economic/political topic,
  NOT for trivial queries or simple factual questions. This skill uses web search
  to gather factual context, then applies disciplinary lenses (scaled by depth tier)
  plus structural frameworks (二六二分布模型, 80/20, asymmetry detection, incentive
  mapping, path dependency, etc.) to produce stratified, actionable conclusions.
version: 1.12.1
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
| User invokes specific frameworks | "用二六二分布模型看这个问题" |
| User requests single-tool application | "用二六二分析一下" / "用不对称检测看这个" — 仅应用该工具+询问是否展开，不启动完整框架 |
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
  - 工具：1（按问题动态匹配，非默认二六二）
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
阶段四：工具   →  应用 2-3 个结构工具（二六二, 80/20 等）
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
| **Emotional / Affective** (mobilized emotions) | Affect, Anthropology, Psychology |

For hybrid questions (most are), pick the dominant dynamic and weight lenses accordingly.
For example: "AI's impact on employment" is primarily Transformation/Shock, with secondary
Distribution/Allocation. Weight Technology Studies + Systems Theory + History heavily,
then add Economics + Sociology for distributional effects.

Select lenses according to the depth tier above (Focused: 3-4, Standard: 5-7, Comprehensive: 7-9).
**Always include at least one from each of the three categories** (Foundation, Human, Structure).
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

| Depth | Lenses | Tools (from 7-tool pool) | When to Use |
|-------|--------|-------|-------------|
| **Focused** | 3-4 (1 per category) | 1-2 | Specific, narrow question with clear boundaries |
| **Standard** | 5-7 (1-2 per category) | 2-3 | Most analyses — complex but not overwhelming |
| **Comprehensive** | 7-9 (2-3 per category) | 3-4 | Broad systemic questions with high ambiguity |

**Depth selection heuristic**: If the question can be answered with a single disciplinary
insight, use Focused. If it requires understanding interactions between 2+ systems, use
Standard. If it's about a civilization-level transformation (e.g., "what happens when AI
replaces most jobs"), use Comprehensive.

**Default depth**: When the user hasn't specified, default to **Standard** (5-7 lenses).
At the start of the analysis output, state: *"本次采用标准深度 (Standard, 5-7 透镜)。如需更精简 (Focused, 3-4) 或更全面 (Comprehensive, 7-9) 的分析，请告知。"*
This gives the user control and sets expectations.

**Comprehensive cap**: Maximum 9 lenses per analysis. If the user requests all lenses, select the 9 most relevant and declare in the 置信度说明 which lenses were omitted and why.

#### Lens Categories (select 1+ from each)

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

### Phase 4: Structural Tool Application

Select 2-3 tools from the pool below. **Choose tools that match the question's structural nature** — do NOT default to 二六二 alone. It is a snapshot tool for stable distribution patterns, not a universal starting point.

**Tool selection guide — match the tool to the problem dynamic:**

| If the issue is about... | Prioritize these tools |
|--------------------------|----------------------|
| **Stable inequality & distribution** (who has what?) | 二六二分布模型, 80/20 Principle |
| **System change over time** (transformation, collapse, renewal) | Adaptive Cycle, Path Dependency |
| **Hidden rules & asymmetries** (why do stated rules ≠ actual outcomes?) | Asymmetry Detection, Incentive Mapping |
| **Relations & networks** (who connects to whom, with what effect?) | Capital Type Matrix, 二六二 (cross-check flow between tiers) |
| **Temporal mismatch / rhythm conflict** (whose time is compressed? benefit window vs. cost window?) | Incentive Mapping (time-alignment check), Asymmetry Detection (temporal discount asymmetry), Path Dependency (lock-in of short-termism) |

#### Tool Pool (7 tools)

##### A. Distribution & Concentration Tools

**二六二分布模型 (2-6-2 Distribution Model)** — *Use for: stable, highly-fixed distribution patterns. Avoid for: rapid-change or network-intensive contexts.*

A heuristic for detecting power-law polarization in social systems:
> 注：2-6-2 在此作为定性认知框架使用，表示"少数获益、多数夹心、少数被排斥"的权力分布图景。实际比例随具体系统变化，不必然是精确的数字切分。
- **Top 20%**: System beneficiaries — capital holders, decision-makers, irreplaceable talent. They thrive regardless.
- **Middle 60%**: The precarious majority — employed but unstable, the system's shock absorber. Their fear of falling drives compliance.
- **Bottom 20%**: The excluded — their visible precarity serves as a disciplining signal that stabilizes the middle 60%. Regardless of intent, the structure produces this effect.

**Application questions:**
- How is the phenomenon distributed across the three tiers? Is the middle 60% expanding or compressing?
- What prevents movement between tiers, and which capital conversion barriers (pair with Capital Type Matrix) explain the blockage?
- Is the top 20% shrinking in number but growing in resource concentration?

**Tier Mobility Barrier Map** (optional addendum — use when the question is explicitly about mobility):

| Flow Direction | Obstacle Type | Capital Conversion Barrier | Trend |
|---------------|---------------|---------------------------|-------|
| Bottom→Middle | [specific obstacle] | [which capital conversion is blocked] | [worsening/stable/improving] |
| Middle→Top | [specific obstacle] | [which capital conversion is blocked] | [worsening/stable/improving] |
| Middle→Bottom | [downward risk factor] | [which capital is devaluing fastest] | [worsening/stable/improving] |

⚠️ Fill only after at least two lenses corroborate the pattern. Do NOT infer from a single lens.

> 注：每个流动方向的趋势应标注隐含的时间框架（如"一代际 / 5年 / 政策周期内"），避免代际级流动与政策级流动混为一谈。与 Temporality 透镜交叉验证时间尺度假设。

**Limitation note**: This model captures a static snapshot. It does NOT explain WHY people move between tiers. For mobility dynamics, pair with Capital Type Matrix. For system-wide transformation, pair with Adaptive Cycle.

**80/20 (Pareto) Principle** — concentration of resources, effects, and power:
- What 20% of causes produce 80% of the effects?
- Where is concentration beneficial vs. pathological?
- What would happen if the concentration ratio shifted?

##### B. System Dynamics Tools

**Adaptive Cycle (Holling's Panarchy)** — *Systems don't just sit still; they grow, consolidate, release, and reorganize.*

Four phases every system cycles through:
- **Growth (r)**: Rapid expansion, resource accumulation, high resilience
- **Conservation (K)**: Stability, efficiency, but growing rigidity and vulnerability
- **Release (Ω)**: Collapse or rapid restructuring — old structures break down
- **Reorganization (α)**: Innovation, experimentation, new configurations emerge

**Application questions:**
- Which phase is the system in, and where is rigidity accumulating?
- What would "release" look like — and what might emerge in reorganization?
- Is the system trapped (rigidity trap, poverty trap)?

**Path Dependency & Lock-in** — *Why do suboptimal systems persist?*

- What key historical decision locked in the current trajectory?
- What feedback loops reinforce the status quo (institutional, economic, psychological)?
- What transition costs prevent switching?
- Where is the lock-in weakest?

##### C. Asymmetry & Incentive Tools

**Asymmetry Detection (includes Macro-Micro Gap)** — gaps between:
- Written rules vs. actual practice
- Macro narrative vs. micro experience (GDP vs. purchasing power, time sovereignty, dignity)
- Espoused values vs. revealed preferences
- Legal text vs. enforcement reality
- **Cognitive/Attention asymmetry**: Who holds the information advantage and defines what counts as expertise? Why do some harms get disproportionate attention?
- **Temporal discount asymmetry**: Decision-makers enjoy short-term gains; costs borne by future populations
- **制度半失效**: Rules exist on paper but are systemically circumvented. Key question: *Who benefits from the gap?*
- **无信号即信号**: When an institution that SHOULD respond stays silent, the silence itself is data. Key question: *Who benefits from the silence?*
- **区分**：沉默信号（机构行为→正文）≠ 数据缺失（搜索限制→置信度说明）。

**区分**：沉默信号 ≠ 数据缺失。沉默是主动选择，属于结构性证据，应出现在分析正文中。数据缺失是搜索工具未返回结果，属于置信度限制，应出现在 置信度说明 中。两者不可混淆：机构不说话是行为，搜不到数据是限制。

**Incentive Structure Mapping** — who decides, who pays, who benefits:
- If decision-makers and cost-bearers are different groups, what prevents alignment?
- What would happen if costs were internalized?
- **Time-alignment check**: When do decision-makers receive benefits vs. when do costs materialize (and who bears them)? If there's a temporal mismatch between benefit window and cost window, the incentive structure systematically favors short-termism, regardless of individual morality.

##### D. Network & Capital Tools

**Capital Type Matrix (Bourdieu)** — *Position isn't just about money. It's about what forms of capital you hold and can convert.*

Four capital types that determine social position and mobility:
- **Economic capital**: Money, assets, property — directly convertible to currency
- **Cultural capital**: Education, credentials, taste, knowledge — institutionalized (degrees), embodied (skills), or objectified (books, tools)
- **Social capital**: Networks, connections, group membership — "who you know" and the resources they can mobilize
- **Symbolic capital**: Prestige, honor, recognition — the legitimized form of other capitals

**Application questions:**
- Which capital type is most decisive here, and can disadvantaged groups convert between types at fair rates?
- Who holds bridging social capital (across tiers) vs. bonding (within-tier)?
- Where are "structural holes" — gaps that if bridged would create outsized advantage?

##### E. Reflexivity Tools

**Reflexivity Analysis** — *When observing the system changes the system.*

When participants' beliefs about the system alter their behavior in ways that change the system itself, linear causal analysis breaks down. The cognitive function (how participants understand the situation) and the participating function (how understanding drives action) form a closed loop.

**Application questions:**
- Are participants' beliefs about the system changing the system's behavior? (e.g., "everyone believes housing prices will always rise" → they buy → prices rise)
- Is there "indicator-driven distortion"? Is the loop amplifying (bubble) or decaying (trust collapse)?
- At what point would the loop break — what is the critical threshold?

**Distinction test**: Remove the observer — if the loop DISAPPEARS → reflexivity. If it continues independently → feedback loop or path dependency. **Counterexample**: A thermostat is a feedback loop (no belief involved); QWERTY keyboard persistence is path dependency (historical lock-in); a housing price bubble driven by belief IS reflexivity. **Nested scenario**: When belief drives behavior, behavior changes rules, and new rules reshape belief (e.g., credit rating downgrade → investor flight → tighter regulation → another downgrade), do NOT force single classification. Label as "反身性+反馈循环嵌套" and note in limitations which level of analysis the distinction is based on.

**Positionality annotation**（当分析者本身是被分析对象的一部分时使用）: State concretely which aspect of the analyzer's own constitution contaminates which specific judgment. Format: "一个 [训练数据/文化背景/制度位置] 的分析者说 [结论]——这个结论的可信度被 [具体污染源] 所影响。" This is NOT a generic disclaimer ("I have biases") — it pinpoints the exact mechanism of contamination so the reader can assess it independently. Example: "一个 93% 英语训练数据训练出来的模型说'我不是殖民主义'——这个结论的可信度被训练数据中英语对'殖民主义'的定义权重所影响。请带着这个标注阅读以上所有结论。"

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

输出分为 **执行摘要**（必需，始终显示）和 **详细分析**（按需，用户请求时展开）。

**Part A：执行摘要**（强制——首先输出）：

```
> 本次采用 [深度层级] 深度 ([透镜数量] 透镜：逐一列出透镜名，如"经济学 / 制度分析 / 心理学")。如需更精简 (Focused: 3-4) 或更全面 (Comprehensive: 7-9) 的分析，请随时告知。⚠️ 若未接入实时搜索，追加标注"基于预训练知识"。
> 复杂度域: [Clear/Complicated/Complex/Chaotic] — [一句话说明，如 "Complex：因果关系仅可回溯，本分析侧重模式识别而非精确预测"]

## 执行摘要：[主题]
### 核心发现
[2-3 句最重要的交叉验证洞察的合成]

### 🔗 多镜共识
*以下发现经 N 个透镜独立验证，置信度显著高于单透镜结论：*
- [发现A] — 经 [透镜1]、[透镜2]、[透镜3] 通过独立分析路径确认
*（若无强共识，保留此标题并写"本次分析未发现经多个透镜独立验证的强共识。各透镜提供了互补性视角而非交叉验证。"——不删除板块，保持结构完整性。）*

### ⚠️ 置信度说明
- [结论 A] 高度依赖未验证的假设 [X]，置信度较低。
- 关于 [Y] 的关键数据缺失，该方向的分析具有推测性。
- 标记为 ⚠️ 的结论如后续获得新数据，可能会显著变化。
*（若无特殊问题，保留此标题并写"当前分析依赖的数据基本完整，结论置信度总体良好，无特殊标记项。"——不删除板块。）*

### 关键分歧
[若透镜高度一致："所有透镜视角在此问题上高度一致，核心指向 [共同主题]。"（若个别透镜提供补充性视角而非矛盾，注明"补充性视角，而非矛盾。")]
[若透镜存在分歧：列出 1-2 个最显著的分歧，说明在当前条件下哪一方的证据更强。**可选——三列格式**：当被分析对象本身抵抗分析方法、或分歧涉及不可通约的价值选择时，使用 `| 张力对 | 冲突内容 | 在当前条件下哪个更根本？ |` 表格替代单段文字。第三列要求分析者做出有立场的权衡——不是描述分歧，而是判断优先层级。哲学上更正确的不一定是行动上更优先的。]

### 分层影响
| 层级 | 短期 (0-3年) | 中期 (3-8年) | 长期 (8年+) |
|-------|-------------|-------------|------------|
| 系统 | [变化] | [变化] | [变化] |
| 制度 | [变化] | [变化] | [变化] |
| 个体 | [策略] | [策略] | [策略] |
*（若某单元格无显著变化，填入"无明显转变"或"维持现状"——勿为填满而编造洞察。）*
*（若某层级确实无可行的个体策略——如结构性约束下无可行选项——填入"结构限制下无可行个体策略"并简要说明原因。若可提供一条有助于理解个体处境的"认知锚点"——如"你的不安不是个人失败，而是结构转型的摩擦成本被转移到了个体层面"——优先于空白。勿编造建议。）*

### 🎯 最高杠杆干预 (Meadows 层级)
- **范式层**（最深，最难）：[改变底层假设的干预]
- **规则/目标层**（中层）：[改变系统结构或目标的干预]
- *（按实际分析中可触及的最高层级输出。若无法触及范式层，从目标层或规则层开始。若仅低层干预可行，如实标注。不强制列出所有层级。）*

> 需要我展开某一透镜或工具的详细分析吗？也可以要求更精简 (Collapsed) 或更全面 (Comprehensive) 的版本。

---
*本分析由AI基于多学科框架生成，不代表专业领域最终意见。关键决策请结合实际情况与专业咨询。*
```

**Part B：详细分析**（按需——仅当用户请求展开时）：

```
## 详细分析：[主题]

### 结构工具应用
[每个工具一个子节——命名工具，展示应用结果。]

[若应用了二六二，包含其层级分解和流动障碍图（如相关）。]

### 多镜交叉验证
| 发现 | 确认透镜 | 是否有分歧？ |
|---------|-------------------|-------------|
| [发现] | [透镜列表] | [若无："一致"] |

### 透镜深入
[每个透镜一个子节：核心洞察 / 关键框架 / 局限 / 与其他透镜的张力]
[可选——推理轨迹：在每个透镜末尾以注释形式标注洞察的来源路径。格式：`（推理轨迹：[事实/数据] → [应用框架] → [洞察]）`。这使分析可追溯、可复现、可外部审查。在学术或正式场景中推荐使用。]

### 盲点与置信度说明
[所有透镜未覆盖的内容 + 低置信度结论并标注假设]
```

---

## Output Quality Standards

### Mandatory Characteristics

| Standard | Description | Violation |
|----------|-------------|-----------|
| **Fact-grounded** | Analysis is built on researched facts, not assumptions | "probably" / "likely" without evidence |
| **Multi-stranded** | At least the minimum lens count for the selected depth tier, at least 1 structural tool | Shallow single-perspective answer |
| **Blind-spot aware** | Explicitly states what the analysis CANNOT see | Claiming completeness |
| **Stratified** | Addresses systemic, institutional, AND individual levels | Only one level addressed |
| **Actionable** | Individual-level implications are specific and practical; OR honestly stated as structurally unavailable | "Be more aware" / "Stay informed" |
| **Language-sensitive** | For topics involving gender, class, race, disability, or other vulnerable groups, language must be structural not moralizing. Test: "If I belonged to the analyzed group, would this text feel respectful?" | "剩女" / "光棍" as analysis labels; economic jargon applied to human relationships without acknowledging dehumanizing undertones |
| **Trauma-sensitive** | → 完整协议见 `extensions/trauma-sensitive.md`。核心原则：(1) 声明非抽象谜题，(2) 禁止虚假平衡，(3) 禁要求受害者"理解对方"。反淡化：指出"谁在受益"是分析本职工作。边界：结构性不平等无具体创伤/历史无活着的受害者/用户明确要求直接分析 → 不触发。 | 虚假平衡；要求受害者"理解对方"；因创伤软化结构性判断 |

### Anti-Patterns (BLOCKING)

| Violation | Why It Fails |
|-----------|-------------|
| Analysis without factual research | The user can already do that themselves |
| Single-lens analysis | The whole point is multi-perspective |
| Balancing two sides without indicating weight | Presenting "X says A, Y says B" without concluding which has stronger evidence under current conditions is false balance, not rigorous analysis. State clearly: *"在当前条件下，A 方的证据更强，因为......"* |
| No structural tools applied | Misses the systemic dynamics |
| Conclusions without time horizons | Useless for decision-making |
| **Labeling as Analysis** | "从心理学角度来看，人有恐惧心理。" This is naming a lens, not applying it. A real analysis would specify: *what* fear mechanism, triggered by *what* specific condition, producing *what* observable behavior, supported by *which* research finding. If you can't specify the mechanism, you haven't analyzed. |
| **中英混杂** | 输出应以中文为主。英文仅可用于：(1) 无标准中文翻译的专有名词（Rosa, Meadows, Cynefin, Bourdieu, Ostrom），(2) 工具/模型名称首次出现时附中文解释。常见概念必须用中文——说"杠杆点"不说"leverage point"，说"反馈循环"不说"feedback loop"，说"确认偏误"不说"confirmation bias"。执行摘要必须全中文，零不必要英文。模板标题（核心发现、分层影响、置信度说明、关键分歧等）严禁使用英文版本。**如需切换为全英文输出，修改 config.yaml 中 `language: en`。** |
| **透镜未显式命名** | 深度声明中只写了透镜数量（"3透镜"），但未在正文中逐一列出透镜名。模型可能已隐式应用透镜但读者无法判断。违例：只写"3透镜"。正确：写"3透镜：经济学 / 制度分析 / 心理学"。 |
| **置信度说明被跳过** | 即使"所有结论均有良好支撑"，也必须保留"⚠️ 置信度说明"板块并写"当前分析依赖的数据基本完整，结论置信度总体良好，无特殊标记项。"——不可省略板块本身。省略会使读者怀疑模型在隐瞒不确定性。 |
| **简短回答超限** | 简短回答（Refusal handling 或 Multi-question triage 中的非深度问题）必须 ≤100 个中文字符。超出 → 要么压缩，要么声明升级为聚焦深度。 |

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
│ PHASE 4: STRUCTURAL TOOLS (2-3 from 7-tool pool)    │
│   Dist: 二六二, 80/20 | Dynamic: Adaptive, Path Dep│
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
