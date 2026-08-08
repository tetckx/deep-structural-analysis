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
version: 1.9.0
---

<!--
Author: happy_chen
版本策略与完整版本链见 `docs/UPDATELOG.md`（版本历史唯一权威）。
-->

# Deep Structural Analysis

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

**Single-tool application format**: When triggered by a single-tool request, output is exclusively that tool applied to the question (3-5 sentences), followed by "需要我以此工具为入口展开完整的多透镜分析吗？" Do NOT launch Phase 1-5, do NOT require web search, do NOT produce Executive Summary. The tool application stands alone. This prevents overkill while keeping the depth path available. **应用前先读取该工具完整文档**（`docs/tools/<tool>.md`；三向/MLSD 见 docs/ 对应文档），不使用浓缩版。

**⚠️ 致害场景——本 Skill 的使用可能构成伤害的情况**：以下场景中，即使分析本身在学术上是高质量的，使用本 Skill 也可能造成伤害。这不是"分析质量"问题——是"分析行为本身"在特定权力不对称中的效应问题。Skill 当前没有内置机制来检测这些场景——依赖使用者的自我判断。

- **未经同意的创伤分析**：将未同意者的创伤经历作为"分析案例"。伤害=将受害者转化为展示制度失效的案例。
- **权力上位者的武器化使用**：制度权力者分析"为什么被统治者不服从"。伤害=反惯性规则提供更精密的控制工具。
- **紧急情境的分析延迟**：安全/医疗危机需立即行动。伤害=分析的结构完整性=决策延迟。
- **心理健康危机的误用**：急性心理危机以"深度分析"形式表达。伤害=需要连接而非分析。
- **活人被非人化为分析对象**：分析具体可识别的个体。伤害=分析行为改变被分析者的社会处境。

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

**Fallback for trigger-word/fact mismatch**: 触发词在但复杂度评估为负 → 先给简洁事实回答，再提供"展开哲学/认知层面"的选项（完整模板见 `extensions/exit-protocols.md`）。

**Ambiguity rule**: If the assessment is borderline, ask the user ONE clarifying question: "This could be a short answer or a deeper structural analysis — which would you prefer?"

**Refusal handling**: → Full protocol in `extensions/exit-protocols.md`. Core: after two declined clarifications, default to lower-effort option (short answer for personal/clinical questions, Focused depth for structurally-framed questions, ambiguous→Focused).

**Protocol conflict resolution**: → `extensions/exit-protocols.md`. Core: 冲突时列明冲突项与优先级，不尝试同时满足。优先级：**创伤敏感标准 > 认知递进协议 > 用户显式指令 > 其他协议默认行为**（虚假平衡在权力不对称中本身就是偏向）。

### Exit / Degradation Protocol
→ Full protocol (Collapsed/Ultra-Collapsed degradation, refusal handling, mid-generation interruption) in `extensions/exit-protocols.md`. Core rule: Collapsed Mode = 核心发现 + 关键盲点 + 分层影响表 + 一个追问.

---

## Extension Index（扩展模块 · 裁剪配置）

> 加载前检查 `config.yaml`（`enabled: false` 跳过加载，即使触发条件满足，默认全部启用）。**读取时机**：标准单轮分析只用核心；扩展与 `docs/` 在显式场景读取（单工具模式必须读 / 交互模式 / 用户追问展开）。

| 触发条件 | 加载扩展 | 内容 |
|---------|---------|------|
| N≥5 相关项 或 多不相关并发 | `extensions/batch-analysis.md` | 批处理协议 + 多问题分流 |
| 用户说"简单点"/"说人话" 等 | `extensions/exit-protocols.md` | 三级降级 + 拒绝处理 + 协议冲突解决 + 架构限制 |
| "第一感觉是..." 或 表面叙事高度误导 | `extensions/layered-protocol.md` | L1→L2→L3 认知递进 |
| 主题涉系统性暴力/歧视/具体伤害 | `extensions/trauma-sensitive.md` | 创伤敏感五约束 + 过度抽象化检查 |
| "先聊聊"/"探讨一下"/"一步步来" | `extensions/interactive.md` | 对话式分析模式 |
| 搜索不可用 | `extensions/offline-fallback.md` | 结构化先验知识框架 |
| 技术时间线/研发周期/能力预测/迭代节奏/竞争格局演变 | `extensions/ai-epistemology.md` | AI认知论：修正分析者自身被AI加速所破坏的认知预设 |
| Phase 3 条件引用 / 传播层判定 / 心理学拓展 / 引导联想判定 | `extensions/lens-application.md` | 透镜应用细节：豁免三条件 + 物质透镜协议 + AI拟人化校准 + 传播层判定表 + 心理学三层拓展 + 引导式联想判定表 |

**Auto-degradation to Lite**:
- **Trigger**: 复杂度域为 Complicated（非 Clear/Complex/Chaotic）且用户未显式请求深度。
- **Clear 域**: → 简短回答 + 询问是否需要展开（不做 Lite）。
- **若用户使用了明确请求深度的触发词**（"深度分析"、"多角度"、"结构分析"、"层层剥开"等）→ 视为已显式请求深度，不触发 Auto-degradation。即使用在 Complicated 域问题上，也应至少保留 Standard 深度。
- **Lite 模式规格**：透镜 2-3 / 工具 1 / 输出仅执行摘要（核心发现+关键分歧或置信度说明+分层影响表）/ 元认知仅敌对测试+盲点验证；声明模板："本次采用轻量模式（2-3透镜，仅执行摘要，元认知简化）。如需标准深度 (Standard: 5-7透镜) 或更全面 (Comprehensive: 7-9) 的分析，请随时告知。" → 完整规格见 `lite/SKILL.md`
- **Chaotic 域不降级**：Chaotic 需要即时杠杆点识别，简化版全面分析不适用。

---

## Core Methodology: The Five-Phase Ladder

分解 → 研究 → 分析（3-12 透镜）→ 工具（2-3 结构工具）→ 合成（交叉验证+盲点+分层输出）。

### Phase 1: Question Decomposition

Before any research, decompose the user's question:

1. **Surface question**: What did the user literally ask?
2. **Structural question**: What underlying system is being questioned?
3. **微观处境 (Micro-situational)**: What does this answer mean for the individual?
4. **Temporal question**: What time horizon matters (now, 3yr, 10yr)?

**Complexity domain assessment (internal — guides analysis tone, not output):**
After decomposition, classify the question's complexity using a simplified Cynefin framework:

| Domain | Signal | Analysis Implication |
|--------|--------|---------------------|
| **Clear** | Cause-effect well-established | 简洁回答，不过度复杂化 |
| **Complicated** | Expert diagnosis needed | 多学科诊断、多透镜 |
| **Complex** | Cause-effect only in retrospect | 模式>预测、反馈环>根因 |
| **Chaotic** | No pattern; immediate action | 稳定局势优先于分析 |

If the question spans multiple independent structural domains (e.g., "分析美国大选对A股的影响" + "分析AI对教育公平的影响" are separate structures), pause and ask which direction to focus on before proceeding. This prevents scattered analysis across too many unrelated dimensions.

---

## Layered Analysis Protocol（认知递进模式 · 可选）

→ Full protocol in `extensions/layered-protocol.md`. Core: L1 surface impression → L2 single-lens challenge → L3 full multi-lens. Activate when user says "第一感觉是..." or surface narrative is highly misleading. When used alongside 5-Phase Ladder, L3 REPLACES Phase 3-5 (do NOT run both).

---

### Phase 2: Factual Context (Web Search)

Gather factual context before analysis — analysis without facts is speculation dressed up as insight.

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
- **Cross-domain event scan**: After initial research, scan adjacent domains in the same time window (default same week; same month for high-sensitivity events; 2 degrees of association from the main topic) for events that may interact with the main topic. Cross-domain connections often produce the most insightful findings.
- **多端口叙事系统（v1.8.0 补充）**：同一主体的同窗口多输出端口（定调/宣示/动员/行动）合成一个系统读——单端口文本与端口间张力都是信号；端口时序即编排证据。示例：机构公告+发布会+行动同日序列。

**Information-missing handling**: 关键子问题搜索无果/低质时——①显式标记缺口（"⚠️ 无法验证 [X]，相关结论置信度降级"）②依赖缺失数据的结论加"如果 (if)"前缀声明假设③盲点清单列出④邀请用户补充数据。详见 `docs/synthesis-reference.md`。

**Information sufficiency & auto-depth-degrade**: After Phase 2 search completes, before Phase 3 lens selection, assess whether the gathered data is sufficient for the analysis precision the user requested. If key cross-sections of data are entirely missing AND cannot be reasonably inferred from indirect sources, actively suggest degrading depth by one tier (Standard→Focused, Comprehensive→Standard). State the reason explicitly: "当前搜索数据覆盖 [已覆盖维度]，但 [缺失维度] 缺乏可靠信息。以下分析降级为方向性判断，如需精度更高的分析，需要以下数据：[列出]。" The user can accept the degradation or provide supplemental data.

**信源立场多样性检查（v1.7.0）**：搜索完成后在思考中评估信源立场多样性——全部同立场时，在盲点清单标注"立场单一性"（附信源构成）。

**Fallback when search is unavailable**: If the current runtime environment has no accessible search tool, load `extensions/offline-fallback.md`（结构化先验框架锚点 + 引用格式 + 置信度规范）and proceed on pre-training knowledge only. Core rules: (1) prepend to the 执行摘要: *"⚠️ 本次分析基于预训练知识，未接入实时搜索，数据可能过时。关键结论需以当前实际数据验证。"* (2) prefix every data-dependent conclusion with *"如果当前数据未发生显著变化，"* (3) flag ALL conclusions as low-confidence; framework-anchored conclusions marked "理论推断（基于 [framework]，非实证验证）".

### Phase 2.5: AI Acceleration Default Check（AI 加速性默认检查）

**触发条件**：**所有分析，无条件默认执行**（轻量版）。若问题涉及技术演进/能力预测/未来推演，升级为完整版（`extensions/ai-epistemology.md`）。

**设计依据**：AI 加速性是**通用分析前提，不是特定领域的检查项**——即使在非技术类问题中，分析者仍会不自觉按"历史经验/静态假设"推演（详细论证见 `extensions/ai-epistemology.md`）。

**轻量版（默认，1 个问题，约 3 秒）**：

```
在透镜选择前自问：
"本分析涉及的任何路径/环节（研发、生产、适配、扩散、组织变革），
 哪些可能被 AI 加速？哪些是 AI 加速不了的硬约束（物理验证、
 政治/监管、组织变革、人类决策）？"
→ 如果答案涉及任何"未来推演/速度预测" → 升级为完整版
→ 如果分析对象本身是 AI/科技/竞争格局 → 强制完整版
```

**完整版**：加载 `extensions/ai-epistemology.md`，运行五步检查清单（拆解路径→识别AI加速点→识别AI盲区→画出相变点→标注不确定性），并按"原则四修订版"区分三类型：**决策密集型**（可被 AI 加速）/ **物理密集型**（不可：物理验证、材料合成）/ **组织·制度·心理密集型**（不可：政治监管、组织变革、人类决策——**AI 时代真正的瓶颈所在**）。

**混合型环节归因规则（v1.6.1 新增）**：真实世界环节常跨多类（示例："评测环境配置"=决策密集型技术动作 × 组织密集型外包管理；"药品审批"=决策密集型科学验证 × 制度密集型行政程序；"供应链安全"=物理密集 × 制度密集）。当环节无法干净归类时：
1. 按**主导侧**归因（决定该环节实际速度的那一侧），并显式标注另一侧：*"该环节按 [主导侧] 归因，但 [另一侧] 侧约束同样存在"*
2. 若两侧权重接近（无法判断主导侧）→ 标注为"混合环节"，**同时推演两种归因下的不同结论**——这正是"人机混合系统"分析的常态，不要强行单归因
3. 混合环节的置信度标注为"中"，且必须在盲点清单中列出"归因不确定性"

**输出要求**：所有涉及时间线/概率的结论必须遵循"概率标注规范"（标注变化方向 + 驱动变量，而非单点估计）。**未执行本检查即输出分析，视为流程违规。**

**传播层默认检查（v1.8.0 补充，无条件执行轻量版）**：分析公开表态/发布事件前完成三步：①**主受众判定**——"谁是这个信息的第一接收者"（主受众是国内→结论显式声明"主功能对内，对外溢出为次级"）；②**溢出标注**——主受众之外的效果标为"溢出"，禁止把溢出效果当作设计意图；③**表态/沉默矩阵**——列出全部利益相关方表态/沉默状态（分类判定见 `extensions/lens-application.md`）。**层级归位纪律**：传播层问题必须先于结构层分析完成——"不同主受众的并行信号"不得直接当作"同一战场的博弈"。

### Phase 3: Multi-Disciplinary Analysis

**Problem type heuristic (internal guide — not output, but informs lens selection):**

Before selecting lenses, classify the question's primary dynamic. Select lenses
disproportionately from the matching cluster, while still including at least one
from each Foundation/Human/Structure category.

| Problem Type | Prioritize Lenses |
|-------------|-------------------|
| **Distribution / Allocation** (who gets what) | 经济学, 政治学, 制度分析 |
| **Identity / Belonging** (us vs. them) | 人类学, 社会学, 心理学 |
| **Transformation / Shock** (tech/policy/environment change) | 技术研究, 系统论, 历史 |
| **Governance / Compliance** (rules don't work) | 制度分析, 政治学, 经济学（透镜）+ 不对称检测, 激励映射（工具） |
| **Temporal / Rhythm Conflict** (systems out of sync) | 时间性, 制度分析, 系统论 |
| **Spatial / Territorial** (who controls space) | 地理, 政治学, 经济学 |
| **Physical / Ecological constraint** (what are the biophysical limits?) | 生态/环境, 基础设施/物质流, 系统论 |
| **Bodily / Biological limit** (how do organic constraints shape decisions?) | 生命科学/身体, 心理学, 制度分析 |
| **Emotional / Affective** (mobilized emotions) | 情感, 人类学, 心理学 |

For hybrid questions (most are), pick the dominant dynamic and weight lenses accordingly.

Select lenses according to the depth tier above (Focused: 3-4, Standard: 5-7, Comprehensive: 7-9).
**Always include at least one from each applicable category** (Foundation, Human, Structure; Material when domain-triggered).
The user's question determines which specific lenses are most relevant.

⚠️ **Anti-inertia warning**: 经济/政策类问题有强引力只选舒适区组合（经济学+政治学+制度分析）→ 扁平分析。**每次分析必须含 ≥1 个舒适区外人文透镜 + ≥1 个舒适区外基础透镜**——最不相关的透镜常产出最佳洞察。

**历史透镜是单一最常被丢弃的透镜**（实战反复验证的系统性失败）——**任何涉及时事/政策/趋势的问题，历史 MUST 入选**；唯一豁免：纯理论问题或 Focused 深度 <4 透镜。若历史透镜直接贡献有限（如博弈+贸易政策混合题），仍须入选并在局限处注明："本透镜对此问题的直接贡献有限，以下用于提供历史背景而非核心洞察"——维持强制规则而不制造虚假深度。

**Focused-depth exemption** (EXCEPTIONAL — NOT default): In Focused depth (3-4 lenses), a Human-category lens may be waived ONLY when ALL THREE criteria pass: ①**窄度测试**（问题可由单一变量完全定义，无群体分布效应/行为含义/感知-现实差距）②**快速洞察测试（把关者）**（10秒内能否想出该人文透镜可产出的非显然洞察——想得出就必须用）③**声明要求**（豁免时置信度说明中必须具名省略的透镜 + 该透镜为何只产出常识洞察 + 一个反例）。完整清单与灰区案例 → `extensions/lens-application.md`。**豁免是例外不是默认**：30秒内无法通过三条件却未用人文透镜 = 懒惰而非判断。Standard/Comprehensive 深度在任何情况下无豁免。

| Depth | Lenses | Tools (from 10-tool pool) | When to Use |
|-------|--------|-------|-------------|
| **Focused** | 3-4 (1 per applicable category) | 1-2 | Specific, narrow question with clear boundaries |
| **Standard** | 5-7 (1-2 per applicable category) | 2-3 | Most analyses — complex but not overwhelming |
| **Comprehensive** | 7-9 (2-3 per applicable category) | 3-4 | Broad systemic questions with high ambiguity |

**Material depth note**: 物质透镜 are counted within the lens budget ONLY when triggered by domain. When no material trigger fires, the budget is allocated across the three standard categories. 物质透镜 are not an additional overhead imposed on every analysis — they are a precision tool activated by relevance.

**Default depth**: When the user hasn't specified, default to **Standard** (5-7 lenses). 输出开头一句话声明深度：*"本次采用标准深度 (Standard)。如需 Focused/Comprehensive 请告知。"*

**Comprehensive cap**: Maximum 10 lenses per analysis (material lenses counted only when domain-triggered). If the user requests all lenses, select the 10 most relevant and declare in the 置信度说明 which lenses were omitted and why.

#### Lens Categories (select 1+ from each applicable category)

> 本表为透镜名的**输出权威来源**：输出时使用中文名（如"心理学"、"制度分析"），括号内英文仅供内部参考与检索——不得将英文名原样输出到正文。en 模式下反之（输出英文名）。

| Category | Lens | Core Question | Use When |
|----------|------|--------------|----------|
| **Foundation** (1-2) | 认识论 (Epistemology) | What are the unstated assumptions? What can we truly know? | Always — sets the frame |
| | 系统论 (Systems Theory) | What feedback loops and leverage points are at work? | Complex multi-variable problems |
| | 历史 (History) | What precedent exists? What makes this time different? | Current events, policy, trends (MANDATORY except pure theory or Focused <4 lenses) |
| | 时间性 (Temporality) | Whose time is compressed? What is accelerating vs. decelerating? | Burnout, policy lag, intergenerational justice |
| **Human** (1-2) | 心理学 (Psychology) | How do humans process this? What biases are active? | Human decision-making（含AI决策体时，须先通过AI拟人化校准） |
| | 社会学 (Sociology) | What social structures and norms shape this? | Group behavior, social dynamics |
| | 人类学 (Anthropology) | What cultural meaning and rituals are involved? | Cultural phenomena, value conflicts |
| | 情感 (Affect) | What emotions are mobilized, commodified, or suppressed? | Service labor, social media, political煽动 |
| **Structure** (1-3) | 经济学 (Economics) | What are the incentives? Who bears costs? | Resource distribution, market analysis |
| | 政治学 (Political Science) | Who has power? How is it exercised? | Governance, policy, collective action |
| | 制度分析 (Institutional Analysis) | Formal rules vs. actual practices — why does the gap exist? | Policy implementation, organizational behavior |
| | 技术研究 (Technology Studies) | How does tech interact with human systems? | AI, automation, digital transformation |
| | 地理 (Geography) | How is space produced, distributed, and contested? | Urbanization, regional inequality, infrastructure |
| **Material** (0-1, domain-triggered mandatory) | 生态/环境 (Ecological/Environmental) | What ecosystem services does this system depend on? What physical thresholds are being approached or breached? | Climate, energy, agriculture, resource extraction |
| | 基础设施/物质流 (Infrastructure/Material Flow) | What physical infrastructure and material flows does this system rely on? What are their failure modes? | Supply chains, compute/energy infrastructure, manufacturing |
| | 生命科学/身体 (Life Science/Bodily) | What biological constraints shape the decision-makers and populations in this system? | Crisis decision-making, public health, aging, cognitive neuroscience |

#### Lens Application Protocol

For EACH lens, answer:
1. **Core insight**: What does this lens reveal that others might miss?
2. **Key framework**: What theory/model from this discipline applies here?
3. **Limitation**: What does this lens systematically overlook?
4. **Tension with other lenses**: Where does this lens conflict with findings from other lenses? — For this field, you may annotate "待交叉验证" during the initial lens-by-lens pass, then backfill once all lenses have been drafted. If no real tension exists after full review, note "与其他透镜视角无实质冲突。"

**CRITICAL**: Do NOT restate what the lens is — apply it to the SPECIFIC question. 反例："经济学告诉我们供需关系。" 正例："经济学揭示：劳动力市场未能吸收失业工人不是需求问题——而是激励问题：企业将工人推向灵活用工平台没有惩罚，形成了从劳动到资本的补贴。"

**Fact-binding requirement**: Each lens analysis MUST reference at least one
concrete fact, data point, or verifiable event from Phase 2 research. Lenses
may draw on pre-training knowledge for frameworks and theory, but their APPLICATION
to the specific question must be grounded in researched facts. If a lens cannot
be fact-bound (because the relevant data doesn't exist), note this explicitly
in the Limitation section for that lens.

#### Material Lenses: Domain-Triggered Mandatory Protocol

物质透镜 are NOT universally mandatory. They follow a domain-triggered rule analogous to the 历史透镜 rule. **When the question's domain matches a trigger, the corresponding 物质透镜 becomes mandatory for that analysis.** When no trigger matches, 物质透镜 are optional.

| Trigger Condition | Mandatory Lens |
|------------------|----------------|
| Question involves climate, energy, environment, agriculture, natural resources | **生态/环境** |
| Question involves infrastructure, supply chains, compute hardware, manufacturing, logistics | **基础设施/物质流** |
| Question involves crisis decision-making, public health, bioethics, cognitive performance under stress | **生命科学/身体** |

**⚠️ 反物质决定论警告**：包含物质透镜时，必须同时至少包含一个**人类透镜**（心理学、社会学或人类学）——物质约束通过人类感知、制度中介和社会动员施加影响；物质透镜告诉你"物理世界允许什么"，人类透镜告诉你"人们愿意接受什么"。

**应用协议（Core insight/Key framework/Limitation/Tension）、AI拟人化校准（Psychology套用AI决策体前必做，4步）、Material × Structure 张力表** → `extensions/lens-application.md`。核心要点：物质透镜揭示约束但不预测人类反应，禁止用它做人类行为的决定论预测。

**心理学透镜三层结构（v1.8.0 补充）**：默认层 = L1 个体认知（认知偏差/前景理论[损失厌恶≈2 倍]/AI 拟人化校准）。涉及**群体心理**（极化/部落化/对立/网暴）、**道德化冲突**（双方各站道德高地）、**非理性强度**（狂热/仇恨远超利益相关）时，读取 `extensions/lens-application.md` 心理学拓展（L2 社会心理/L3 深层道德+理论目录+来源等级+盲测协议）。

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
| **Strategic waiting / first-mover / who moves when** (why is everyone waiting? who breaks the deadlock?) | Strategic Interaction Matrix |

#### Tool Pool (10 tools)

> 执行必需的精简版如下；完整规范（起源/应用问题/已知局限/案例校准）见 `docs/tools/` 对应文档（三向与 MLSD 分别见 `docs/三向理论.md`、`docs/多层信号解码.md`）。选定工具后如需要更完整的应用规范，读取对应文档。

##### A. Distribution & Concentration Tools

**三向 (Tri-directional Lens)** — *认知透镜，非科学理论。在存在正反馈的竞争系统中，三个方向因不同性质的约束而分化：顶向被惯性约束（资源流向已有资源），中向被恐惧约束（"不要成为底向"强于"想成为顶向"），底向被边界约束（存在本身成为系统的参照底线）。核心不是"有三层"——是"三层被三种不同性质的约束固定在原地"。*

**四条观察模式**（分化默认/恐惧驱动中向/底向结构占位/时间流速差）→ 完整版见 `docs/三向理论.md`。

**使用纪律**：配合 Capital Type Matrix 分析流动性，配合 Adaptive Cycle 分析系统性转型，配合 Reflexivity 分析信念循环。问自己：中向在膨胀还是压缩？底向对中向是否可见？有跨向联盟吗？使用前区分 ABC 三类"三"——B类（物理约束）和C类（历史锁定）不适用此透镜。**校准检查**：拿掉透镜重新看，结论一致=装饰已知，不一致=可能在工作，相反=过度拟合。

> 完整文档（含稳定性启发式、演变方向、流动障碍图、已知局限）：`docs/三向理论.md`。

**80/20 (Pareto) Principle** — *经验模式，非数学定律。在幂律分布中成立——在均匀分布中不成立。用它来集中注意力，不要用它来"证明"不平等是自然的。* 完整文档：`docs/tools/80-20.md`。

##### B. System Dynamics Tools

**Adaptive Cycle (Holling's Panarchy)** — *生态学隐喻，不是机械周期。* 揭示"稳定期积累的刚性如何在释放期爆发"——但真实系统不总是按 r→K→Ω→α 走，可能跳过/卡住。用它问"系统在积累哪种脆弱性"，不要预测"下一阶段何时到来"。四阶段：**Growth (r)** 扩张积累 → **Conservation (K)** 稳定但刚性增长 → **Release (Ω)** 崩解重构 → **Reorganization (α)** 创新涌现。
- 校准检查：拿掉透镜，用常识能否同样清晰地描述系统状态？能=装饰已知；"刚性在积累"不靠透镜不会出现在常识描述中=在工作。
> 完整文档：`docs/tools/adaptive-cycle.md`。

**Path Dependency & Lock-in** — *历史叙事工具，不是预测模型。* 解释"为什么已经不好的东西还在持续"。陷阱：几乎任何持续存在的东西都可被事后描述为路径依赖——不是所有持续都是锁定，有些持续是因为一直在赢。用它追问"切换成本在哪里"，不要暗示"当时选错了"。
- 校准检查：持续性可否用"它仍满足当前需求"充分解释？可以=惯性+适应而非路径依赖；切换成本是唯一障碍=透镜在工作。
> 完整文档：`docs/tools/path-dependency.md`。

##### C. Asymmetry & Incentive Tools

**Asymmetry Detection (includes Macro-Micro Gap)** — *认知警觉训练，不是测量工具。* 强迫寻找"书面vs实际"、"宏观vs微观"、"声称vs行动"之间的裂缝。陷阱：带着"一定存在不对称"的预设会找到不对称——问题不是"有没有裂缝"，是"裂缝大到能解释系统为何如此运作吗"。区分：沉默信号（机构行为→正文）≠ 数据缺失（搜索限制→置信度说明）。

裂缝清单：书面规则vs实际实践 / 宏观叙事vs微观体验（GDP vs 购买力、时间主权、尊严）/ 声称价值vs显示偏好 / 法律文本vs执法现实 / 认知-注意力不对称（谁掌握信息优势、谁定义专业）/ 时间贴现不对称（决策者享短期收益、后代承担成本）/ **制度半失效**（规则写在纸上但被系统性规避——谁从裂缝中受益？）/ **无信号即信号**（该回应却沉默的机构——谁从沉默中受益？）

**裂缝层级标注（必须）**：检测到裂缝后标注层级——**结构性裂缝**（范式层面固有矛盾）→范式层干预（最高杠杆）、置信度高；**偶发性裂缝**（单次操作失误）→参数层干预、置信度低；**系统性裂缝**（重复模式化缺陷）→规则层干预、置信度中。**未标注层级=不完整。**

校准检查：裂缝是否每个有常识的人都能注意到？是=命名已知而非发现未知。最危险信号：每次都用它找到"制度半失效"和"沉默即信号"——你被训练成了不对称寻找机器。
> 完整文档：`docs/tools/asymmetry-detection.md`。

**Incentive Structure Mapping** — *分析框架，来自公共选择理论和组织经济学。* 核心："谁决定、谁付钱、谁受益"——决策者与成本承担者不同时，激励系统性偏向短视。陷阱：不要问"谁在故意制造坏的激励"——大多数失调的激励是涌现出来的。问"在当前规则下，任何理性人会不会做同样的选择"。
- **Time-alignment check**：收益窗口与成本窗口时间错配 → 激励结构系统性偏向短期主义，与个人道德无关。
- 校准检查：能否不用"激励失调"语言描述问题？能且同样准确=在工作；只是贴标签=没在工作。
> 完整文档：`docs/tools/incentive-mapping.md`。

##### D. Network & Capital Tools

**Capital Type Matrix (Bourdieu)** — *分类框架，来自 Bourdieu 对 1970 年代法国社会的分析。* 四资本是特定历史条件的产物——非西方/数字时代/非层级化组织中边界可能需重划。用它问"还有什么资本形式在此系统中起作用"，不要假设四类在所有文化中同样适用。
- 四资本：**经济**（货币资产，直接可兑换）/ **文化**（教育凭证·技能·品味——制度化/具身化/客体化）/ **社会**（网络关系——跨层级的桥接 vs 层内粘合）/ **符号**（声望——其他资本的合法化形式）
- 校准检查：能否不靠四资本分类描述"谁有优势"？能=更系统的语言而非新洞察；符号资本被常识完全忽略=框架在揭示盲区。
> 完整文档：`docs/tools/capital-matrix.md`。

##### E. Reflexivity Tools

**Reflexivity Analysis** — *认知工具，来自 Soros 与观察者效应研究。* 当参与者的信念改变系统行为、系统行为反过来改变信念时，线性因果失效。最危险误用：把普通反馈循环错标为反身性——反身性要求"信念"是循环的一部分（恒温器=反馈循环，QWERTY=路径依赖，房价泡沫=反身性）。
- **区分测试**：移除观察者——循环消失=反身性；独立继续=反馈循环/路径依赖。嵌套场景（信念→行为→规则→信念）不强行单一分类，标注"反身性+反馈循环嵌套"。
- **位置性标注**（分析者本身是被分析对象的一部分时）：具体说明自身构成的哪个方面污染了哪个判断，格式："一个 [训练数据/文化背景/制度位置] 的分析者说 [结论]——可信度被 [具体污染源] 影响"。不是泛泛的"我有偏见"。
- 校准检查：动态可否用"人们根据经验调整行为"（普通学习）解释？可以=不要用反身性。只有信念介入改变系统基本运作规则时=在工作。
> 完整文档：`docs/tools/reflexivity.md`。

##### F. Communication & Signal Tools

**多层信号解码 (Multi-Layer Signal Decoding)** — *认知解码工具，不是信号探测仪。* 分析"为什么这段信息中的每一个幸存词都是经过博弈后留下的"——它发现的"信号"可能反映你自己的解码预设。任何面向公众的文本（尤其是 AI 时代经筛选后释放的文本）不存在"无意中留下的话"：每一句幸存的话至少满足——必须说的真话 / 故意放的信号 / 掩护填充 / 可信度锚点。

**⚠️ 使用前必须通过三问测试**——任何一关不过，放下工具：① 信源有可损失的信用吗？（上市公司CEO ✅，匿名用户 ❌）② 信息经过至少一层筛选吗？（PR审查 ✅，实时直播 ❌）③ 发布者与接收者有利益博弈吗？（融资博弈 ✅，教程作者 ❌）

三个分析轴：
- **轴一：信号生存分析** — 所有存留信息强制分类：必须说的真话（不说会被戳穿）/ 故意放的信号（对特定接收者编码）/ 掩护填充（注意力稀释）/ 可信度锚点（故意留的破绽证明"这是真的"；**叙事级扩展——选择性真诚：展示可控的不完美/失利以建立整体可信度，展示哪些"失利"本身经过筛选**）。**多目标服务检测表（嵌套危险信号判定，必须执行）**：对每个疑似可信度锚点——(1) 列出该破绽服务的全部叙事目标；(2) 目标数 ≥2 且彼此独立 → 升级"可控弱点"假设（策略性设计），置信度降级；(3) 仅 1 个目标 → 保留"真实破绽"假设；(4) 输出声明采用哪种假设及依据。**高博弈密度主体（上市公司/主权国家/前沿实验室）→ "可控弱点"为默认起点。**
- **轴二：多接收者映射** — 每段有信息量的内容强制识别 ≥3 个接收者（投资人/竞争对手/监管者/团队/媒体），解码对各自的不同含义。好的编码 = 一段话对五个接收者传递五种信息。**主受众优先判定（v1.8.0 补充）**：先判定主受众（设计意图对象）再分析内容——判定顺序：出品方→发布渠道→官方定位→内容手法（硬指标）；外部反响（软指标）只能作溢出证据，**禁止将溢出效果当作设计意图**；输出须区分"主受众效果"与"溢出效果"。
- **轴三：时序关联域** — 信号与发布时刻的同时事件强制关联：左看 7 天（什么触发了它），右看 3 个月（它在为什么铺路）。主要信号通常满足：危机管理/预期管理/战场定位/叙事铺垫之一。
- **轴四：披露边界分析（v1.8.0 补充）** — 发送者选择"何时公开什么"比公开内容本身更有信息量：未披露项 + 披露阶段选择（试验/验证/部署中哪一阶段公开）。披露边界的演进 = 能力进程的观测窗口（示例：公开"测试画面"而非"部署状态"——阶段差即信号）。

使用时序（推荐序列）：**MLSD 解码所有公开信号 → Asymmetry Detection 对比内部行为找裂缝 → Reflexivity 追踪信念循环**。

⚠️ **嵌套场景**：发送者可能预判你的工具并预先编入"可控弱点"。可信度锚点暴露得太精确 = 可能已被反制。

- 校准检查：朴素重读——朴素描述已蕴含相同结论=装饰已知；工具发现朴素解读看不到的结构=在工作；看到相反结论=过度拟合。

##### G. Strategy & Game Tools

**策略互动矩阵 (Strategic Interaction Matrix)** — *博弈论分析框架，聚焦"等待博弈/先手-后手/信号博弈"。* 陷阱：把一切互动都框成博弈——部分互动是惯性或适配的结果。问"理性玩家在此结构下会怎么选择"，不要假设"每个玩家都是完全理性的"。

核心三问：
1. **等待博弈检测**：存在"先下注者承担验证成本、后跟进者搭便车"的结构吗？谁会先动？什么外部力量（政策/危机/灯塔案例）能打破死锁？
2. **先手-后手评估**：先手优势（定义标准/占领心智/积累数据）vs 成本（验证风险/沉没成本）哪个更大？后手在等先手失败后收割吗？
3. **信号博弈识别**：公开动作（发布/定价/沉默）是能力信号还是虚张声势？信号成本与可信度匹配吗？（低成本信号不可信）

应用要点：与 MLSD 的区别——MLSD 解码"信息"的博弈结构，本工具分析"行动"的博弈结构；与 Incentive Mapping 的区别——激励看结构内收益分配，本工具看结构如何被玩家博弈改变。**沉默也是行动**：全员沉默=死锁，单人先动=破局。

**沉默与表态分析（v1.8.0 补充）**：沉默是标准选项而非例外——对每个相关方问三问：①会回应还是沉默（沉默=不回应/冷处理/仪式性回应）？②若沉默：大众层默认解读与精英层策略解读两轨并行——沉默被谁设定什么含义（设定权在观察者）？③若表态：表态有意义吗（仪式性/被预设框架吸收/仅对内部受众）？禁止预设"各方必表态且表态必有意义"。示例：沉默→大众层读默认；例行否认→不改变叙事。

**引导式自我联想（Guided Self-Inference，v1.8.0 补充）**：机构通过"精确投放锚点+引导受众自行完成联想+保持可否认性"传递信号——比沉默主动、比明示隐蔽。分析四问：①**锚点识别**——投放了什么事实/时机/符号（谐音署名/深夜发布/时间耦合/规格排序/无量化阈值）？②**引导空间**——锚点允许受众在什么方向"自动完成"（威慑/政策转向/关系温度/竞争力/权威加载）？③**沉默边界**——官方在哪部分保持不确认不否认（"例行""依法""规划"）？④**联想强度**——官方后续是否不澄清、不换名、不纠偏（不澄清=联想被定价为收益；纠偏=超限）？示例：谐音署名→权威加载；时间耦合→威慑等式。

**披露博弈子模式**（敏感事件/安全事故/丑闻场景）：先披露者定义叙事框架，后披露者只能防守。检测：竞相披露动态？"区分叙事"（"我们的事件与XX不同"）？披露时机本身是信号——**行动时序 > 文本内容**。均衡通常是"竞相披露"（不披露被扒出的损失 > 披露的声誉损失）；先披露者获叙事定义权但承担"被审查更严"的风险。

**多玩家降级协议（玩家数 >3 时强制）**：(1) 放弃精确预测，改输出三个方向性维度——**均衡方向 / 触发条件清单 / 关键信号**；(2) 玩家合并为"阵营"再分析；(3) 显式声明："玩家数>3，博弈推演已降级为方向判断"；(4) 触发条件清单优先于时间点预测——用"什么事件会触发"替代"何时会发生"。

- 校准检查：玩家行为可否用"惯性/资源约束/组织文化"充分解释？可以=不是博弈是惯性。额外检查：如果每个场景都是"等待博弈"——不是所有停滞都是策略性等待，有些只是单纯的慢。
> 完整文档（已知局限4条）：`docs/tools/strategic-interaction.md`。

**跨信源对照**（MLSD 辅助）：分析同一时间窗口的多个信源时，寻找信号共振（相似信号→共识形成/旧共识解体）、信号对抗（相反信号→争夺叙事定义权）、信号沉默（相关方发声时一方沉默→沉默本身就是信号）。

**边际价值归零检查**（MLSD 专用）：连续三次使用都发现"被编码的困境/被迫的选择/不可说的真实意图"——你可能在重复自己的解码习惯。

**MLSD 已知局限（11条）与可靠性退化曲线** → `docs/多层信号解码.md`。核心：①非理性发送者导致工具找出不存在的信号（最大失效模式）②过度拟合风险极高 ③对来源质量极度敏感 ④**AI生成文本场景**——当信源文本由 AI 起草/筛选，"幸存词是博弈后留下的"前提需调整：优先检查提示词约束（谁设的框架）、安全对齐裁剪（AI被允许说什么）、人工修改痕迹（最真实信号）。**校准：文本"太工整、太无破绽"——可能不是高明博弈，而是 AI 去风险化文本，找信号=给噪声编故事。**

---

**工具使用通用纪律**（适用于以上所有工具——不限于三向）：
- **校准检查（内部执行，v1.7.2 修订）**：每次使用工具后，**把工具拿掉**，用最朴素的常识重新看同一个系统——"朴素视角 vs 工具视角"对比（一致=装饰已知/差异=在工作/相反=过度拟合），**结论不输出**。校准发现工具无独立贡献→弃用。某工具连续多次从未产生差异 = 装饰已知。
- **博弈完整性（v1.7.2 补充，v1.8.0 去特化重写）**：分析博弈结构时，识别未上桌但利益攸关的玩家——按四种通用角色（各配检测特征）：
  - **外部否决者**：不在桌上、有独立行动能力、对结果有红线——检测特征：单方行动即可破坏协议/方案落地。示例：对协议有红线否决权的联盟成员
  - **利益绑定者**：利益与博弈结果物理绑定——检测特征：急切度最高但筹码不直接转化为谈判力（急迫≠筹码）。示例：与受制裁方共享关键资源的生产者
  - **缺席受冲击者**：受冲击最大但不在桌上——检测特征：成本承担者+规则接受者，同时可能是隐性稳定器。示例：最大买家
  - **载体持有者**：提供方案的物理载体/地理基础——检测特征：不签字则无法开局（物理否决权），最不可能掀桌但最基础。示例：航线途经国/基础设施持有方
  三方博弈常实为五方以上——产出为"完整玩家清单+各自约束"。完整案例见 `docs/cases.md`（维护者文档）。
- **激活（v1.7.2 补充）**：披露博弈（MLSD 子模式）与反馈闭环优先（系统论）为强制应用项——重大披露事件必须解码披露时机/归因框架/叙事目标；能源/气候/技术议题必须先查正反馈闭环再选透镜。**技术依赖的安全化（v1.7.2 补充，v1.8.0 去特化重写）**：一项技术选择/商业实践被纳入国家安全叙事，触发审查与管制，最终成为地缘工具——检测三要素：①依赖关系（被依赖方与依赖方的战略关系是否紧张）；②审查触发（安全叙事何时启用、以什么名义）；③中立性存续条件（"安全中立"的存续前提是未被政治化）。示例：开源工具用于安全取证→来源国审查；关键基础设施依赖外国供应商→供应链安全立法；民用技术被纳入出口管制→地缘博弈工具。完整案例见 `docs/cases.md`。
- 如果一个工具在连续多次使用中从未让你对系统产生新的理解——**你不是在"使用"它，你是在"重复"它。** 放下它，换一个工具。工具的边际价值在你不再从它身上学到东西的那一刻归零。
- 同时使用多个工具时——**不要让其中一个工具定义所有其他工具的术语。** 如果你发现自己在用工具 A 的概念来描述工具 B 的发现——停下来。这说明工具 A 在支配你的分析，而不是在服务你的分析。
- **没有任何工具需要永远被使用。** 一个工具在你学会它的那一刻最有价值——之后价值递减。每隔一段时间，问自己：**"如果今天我第一次听说这个工具，我会用它吗？"** 如果答案是不会——你在用它的防腐版，不是它的活版。

---

## Supplementary Analysis Templates (L3 Layer)

Speed-reference — apply 1-2 per lens as sub-frameworks during lens analysis or Phase 5 synthesis. Models know these concepts from pre-training; this table maps them to lenses as a reminder.

> 21 个模板速查表 + Common lens tensions 内部参考 + 可选反事实检查 → `docs/synthesis-reference.md`。

**张力回填要求（合成前必须完成）**：Review all lenses that marked tension as "待交叉验证." For each pair of lenses, determine whether a substantive conflict exists. If none found, annotate both as "与其他透镜视角无实质冲突，但提供了补充性视角。" Do NOT leave any "待交叉验证" marker unresolved before delivering output.

After all lenses and tools have been applied, synthesize:

1. **Cross-validation findings**: What 2-3 insights are independently corroborated by multiple lenses? — 共识建立在同一批事实/同立场信源上时，在盲点标注"共识独立性有限（事实基础重叠）"。
2. **Divergences**: Where do lenses disagree? If largely in agreement, say so directly.
3. **Blind spots**: What is systematically invisible to all lenses used?
4. **Leverage points**: Where would a small change produce outsized effects? Reference the Meadows hierarchy (constants/parameters → buffer sizes → material flows → delays → balancing/reinforcing feedback → information flows → rules → self-organization → goals → paradigm). The highest-leverage intervention is usually at **rules, goals, or paradigms** — not surface parameters. Identify which level(s) your interventions target, and whether lower-level tweaks are masking the need for higher-level change.

5. **读者影响检查**: Before finalizing, ask: "If someone whose life is directly affected by this issue reads this analysis, what would they take away?" If the answer is only abstract systemic insights with no personal resonance, the analysis has failed the 个体 row of the 分层影响 table. The conclusion must include at least one concrete, actionable observation that a non-expert could recognize as true from their own experience.

**推演四查（v1.7.2 补充，合成阶段执行）**：
1. **竞争性假说排除**：对每个核心归因列出 ≥2 个竞争性解释并给出排除依据——未排除的假说必须在置信度说明中体现，禁止单一归因。**高风险领域（安全/金融/地缘）修正：排除必须基于正面排除证据；无正面证据时只能"降权+监测"，低概率高影响分支必须在防范/情景设计中占位，不得"因无证据而排除"。**
2. **二阶效应推演**：推演各方（受益者/受损者/监管者/攻击者/第三方）的反向行动——"披露=免费教材""协议=筹码升值"类二阶效应必须进入核心风险，而非盲点备注。**情景剧本须包含"能力/冲突外部化"情景（技术能力被国家级玩家工业化、商业事件被安全化政治化）——事件量级跃迁路径必须占位。**
**传播场景深化（v1.8.0 补充）**：信号进入接收端博弈后发送者控制权衰减——传播效果=发送者意图×接收端利用；区分"失控"与"被定价"：发送者后续是否调整信号节奏（不变=成本已内化；改变=实时反应）。
3. **物理锚定检查（v1.7.2 补充，v1.8.0 表述修正）**：机制本体是原则——**涉及预期/信号/博弈的分析，预期必须锚定可测量的物理现实，禁止纯预期叙事**（信号解读锚定物理约束）。辅助清单（**非穷尽，欢迎扩展**）——时间性约束（周期/滞后/倒计时）、规模性约束（存量/覆盖/容量）、资源性约束（稀缺品/卡点/配额）、承载性约束（缓冲层/验证产能/基础设施上限）。**三点强化：①物理约束的博弈形态（稀缺资源配额分配斗争——抽象闭环的政策落地层）；②缓冲器极限（系统的缓冲层——库存/储备/热容量——的饱和是延迟爆发的物理机制）；③数据缺失时给出基线估算框架+校准声明（标注官方数据发布后可更新），而非留空。**
4. **全球南方变量检查**：地缘/经济/能源类分析，显式考虑：最大消费/生产方是否在博弈桌上？主要受冲击方是否有独立行动能力？相关评价/规范体系是否存在地区差异？
5. **共存检查（v1.9.0 补充①）**：默认"不变"为分析基准——并存形态：僵持/补丁堆积/选择性真诚/低效运行/慢性恶化/仪式化处理，属常态稳态；变化须给出明确触发条件（谁有终止权？退出成本结构？不满≠终止）。"问题明显但照旧运行"不构成变化论据。

#### Synthesis Output Structure

**Part A：执行摘要**（强制首先输出）——深度声明+复杂度域→核心发现→多镜共识→置信度说明→关键分歧→分层影响表（系统-制度-个体×短期-中期-长期）→最高杠杆干预（Meadows层级：参数→规则→目标→范式）。以"需要我展开吗？"结尾。

**Part B：详细分析**（按需展开）——结构工具应用→多镜交叉验证表→透镜深入（每透镜1段：该透镜的发现——核心洞察+关键框架命名；局限与张力为内部自检，不单独输出，仅在影响结论时以一句融入）→盲点与置信度说明。

## Output Quality Standards

**Must**: 所有结论事实绑定。多镜共识显式标注。盲点清单。MECE。至少一个非专家可从自身经验识别为真的可操作观察。中英混杂严禁——常见概念用中文，仅无标准翻译的专有名词（Meadows, Cynefin, Bourdieu等）保留英文。

**置信度判定标准（v1.7.0）**：高 = ≥2 独立信源且立场相异；中 = 单信源或同立场；低 = 推测/传闻/无法验证。禁止即兴标注。

**验证强度分级（v1.7.2 补充）**：并置同类事件作为证据时，必须按验证强度分级，不得等权重——**公开验证**（形式化证明/可复现代码/独立复测）可作为"已确立范式"证据；**公告声明**（官方发布无独立验证）仅作"能力上限信号"，置信度降一级，正文推演不得与公开验证等权重。归因声明（"模型自主提出"类）无过程数据时标注"不可回溯验证"。

**数量引用规范（v1.8.0 补充）**——引用任何关键统计数字时，必须满足：
- **口径透明度**：标注来源（官方/行业估算/推测）+ 统计定义（原始数据/处理后/范围口径）+ 未计入因素。无口径的关键数字置信度降级，不得单独作为核心论据（"90%"类数字缺口径 = 叙事燃料）。
- **占位 vs 部署区分**：标注数字所处阶段——申请/宣布/规划 ≠ 获批/在建 ≠ 部署/运行/验证；阶段差异可达 1-2 个数量级（如"申请 100 万颗"≠"实际可部署 10 万颗"）。未标注阶段的规模数字置信度降级。

**虚假平衡禁止（v1.7.0 泛化）**：扩展至所有利益冲突/权力不对称议题——禁止对称化呈现不对称（"双方都有道理"不能替代"指出谁受益"）。不是禁止多方视角，是禁止抹平不对称结构。

**框架自指声明（v1.8.0 补充）**：本框架不豁免于自己的规则——每一条机制（语言合规/数量引用/边界协议/本声明）在分析框架自身时同样生效，禁止"框架分析豁免"特例。**本声明为内部自评参照，不输出**（防表演性引用：不得在交付中声明"已遵守框架规则"，遵守与否由产物形态体现）。执行绑定：交付前重读（Invocation #9）含本声明自检——本次分析是否遵守了触发到的全部机制；遵守失败以结论形式记入盲点清单。示例：语言合规适用于本文件自身的输出；数量引用规范适用于本框架引用的任何数字。

## Internal/Output 边界协议（v1.7.2）

**原则**：分析流程在思考链中完整执行；输出只交付分析产物。执行情况通过**产物形态**间接体现，不通过流程声明。

**思考链内容（必须执行，禁止输出）**：
- 触发守卫、复杂度域评估、透镜/工具选择过程
- 每透镜的内部自检（局限、张力）——产物仅为核心洞察
- 工具校准检查（朴素视角 vs 工具视角对比）——结论不输出
- 移除测试（"移除该工具结论会失去什么"——答不出即弃用该工具，正文不出现装饰性工具段）
- 张力回填、反事实检查、元认知检查 7 项——发现的问题直接修改正文，不输出检查过程
- 执行深度自评

**产物（必须输出）**：
- 深度声明（一句话）
- Part A：核心发现 / 多镜共识 / 置信度说明 / 关键分歧 / 分层影响表 / 最高杠杆干预
- 盲点清单（含立场单一性、共识独立性有限等元发现——以结论形式，非声明形式）
- 位置性标注（分析者受污染影响结论时，以"污染源→影响"形式，非自白）
- 机制产物：裂缝层级标注、概率标注、机制假设声明、混合归因标注等

**禁止句式**："我执行了 X 机制" / "Phase 2.5 已执行" / "校准检查结论：…" / "对立专家会攻击…回应…" / "本次用到了…机制" ——一切"执行过程"叙述。

**思考链不丢原则**：以上思考链步骤必须全部执行——**不输出不等于不做**。产物的深度是执行的证据：三向的产物是"三种约束机制的具体刻画"而非"上中下分层"；反身性的产物是"具体循环链"而非"互相影响"；裂缝的产物是"层级标注"而非"存在裂缝"。

**Blocking**: 单透镜结论。无分层影响表。致命盲点遗漏。假共识。绝对化声明无置信度限定。标签化非分析（"从心理学来看"未具体到机制）。置信度说明被跳过。透镜未显式命名。简短回答超限（≤100中文字符）。执行过程叙述进入正文（违反边界协议）。

---

## Interactive Analysis（对话式 · 可选）

→ Full protocol in `extensions/interactive.md`. Alternative to one-shot delivery: direction proposal → incremental delivery → on-demand synthesis. Activate when user says "先聊聊"/"探讨一下"/"一步步来". Appropriate for exploration, not decision-support.

---

## Metacognitive Checkpoint (before delivering final output)

Before concluding the analysis, run this self-check — **核心三项（1-3）每轮必跑；补充五项（4-8）按场景触发**（防过载，见机制执行分层协议）：

**核心（每轮）**：
1. **Adversarial test**: "If I were an expert holding the OPPOSITE position, which three points in this analysis would I attack as weakest? Why?"
2. **Data-dependence audit**: "Which conclusions would significantly change if the search data turned out to be wrong or incomplete?"
3. **Blind-spot verification**: "Is there a stakeholder group, time scale, or causal mechanism I haven't meaningfully addressed?"

**补充（触发式）**：
4. **Temporal bias check**（涉时间假设时）: Did this analysis default to a specific time horizon while neglecting longer/shorter rhythms? Would conclusions change at intergenerational scale or crisis-response speed? Are latent assumptions about "natural" time frames accepted uncritically?
5. **Dimension coverage check**（涉舒适区风险时）: Did the analysis deliver insights from all three categories — Foundation, Human, Structure — or drift into a single-axis comfort zone? The test: can you articulate ONE specific, non-obvious insight from a Human lens that would change how a reader thinks? If not, revisit.
6. **Normative stance check**（涉价值判断时）: "What value priority does this analysis implicitly assume? If I changed the value hierarchy, would the conclusions still hold — or would different interventions emerge?" The analysis must know its own position rather than pretend neutrality.
7. **过度抽象化风险检查** — triggered ONLY for trauma/violence/discrimination topics. → Full protocol in `extensions/trauma-sensitive.md`. Core: "has this analysis turned real human pain into a bloodless intellectual puzzle?" If yes, add direct acknowledgment. Does NOT require softening — "pointing out who benefits" is the analysis doing its job.
8. **人的因素检查（v1.7.2 补充）**——涉制度性失败时：制度性失败（配置失误/流程失效/执行偏差）归因时，必须下探到操作者层——过度自信/疲劳/绩效压力/组织文化，禁止停在"系统失误"抽象层。示例：评估环境配置失误必须追问"人为什么没发现门没关"，而非止于"流程缺陷"。

If (1) reveals any easily-attacked point, strengthen it or note it. If (2) identifies fragile conclusions, flag them for output. If (3) finds gaps, either fill them or list them.

**Self-reference degradation**（自指场景降级）: When the analyzed object IS the metacognitive framework itself, checks #2/#3/#4 may fail due to category mismatch. Run only #1, #5, #6, #7. Explicitly note which checks were skipped and why: "框架分析自身时，[#2/#3/#4] 因范畴不匹配而跳过。这不是框架缺陷——这是框架为此类问题而设计的边界。"

**批评者免疫（Meta-analysis self-immunity，v1.8.0 补充）**：分析外部评审/元评估时，先检查其切割方式——批评者可能继承被批评对象的盲点。先问"它从哪一刀切起"，再评估其结论，而非只评估结论本身。

**Output binding with tiered allocation**: 执行摘要-置信度说明仅列最高风险项（步骤 1-2 中会实质改变核心结论的）；详细分析-盲点与置信度说明列完整清单（步骤 1-3 全部）。

---

## 机制执行分层协议（v1.9.0）

框架机制按三层执行——**防止机制过载导致执行不完整**（执行容量约束：单次分析可靠执行约 5-9 项检查；累计机制已远超此数，分层是容量设计而非推诿）：

- **第一层 核心流程（每轮必跑）**：触发守卫 → 元认知前置（先验声明/竞争假说前置/反证前置）→ 五阶段（分解/搜索/透镜选择纪律/工具应用/合成）→ 推演四查 → 元认知三项（敌对测试/数据依赖审计/盲点验证）→ 交付前重读
- **第二层 触发式机制（场景激活才执行）**：传播层默认检查（涉公开表态/发布事件时）、沉默与表态分析（涉多方回应时）、引导式自我联想（涉官方/机构信号时）、心理学三层（涉群体心理/道德对立/非理性强度时）、博弈完整性（涉博弈结构时）、披露边界（涉披露选择时）、多端口叙事（涉多输出窗口时）、批评者免疫（涉元评估时）、人的因素检查（涉制度性失败时）……
- **第三层 质量标准与交付纪律（合成与交付前检查）**：置信度判定/验证强度分级/数量引用规范/虚假平衡禁止/框架自指声明/边界协议/语言合规

**执行规则**：第一层无条件执行；第二层按触发条件激活——**未触发不执行，不因"机制存在"而强制**；第三层交付前检查。**未触发第二层机制不算执行不完整**——产物形态是执行证据，机制清单不是。**与 Invocation #3 的关系**："思考链完整执行" = 第一层全部 + 第二层全部被触发项 + 第三层交付前检查——完整不是"全部机制"，是"全部被触发的机制"。

## 元认知前置协议（v1.9.0 补充②）

对抗单一叙事先天倾向——先验在分析开始前即已形成，事后检验（元认知三项）无法阻止起点锚定。触发守卫后、分解前执行，属第一层（每轮必跑）：

1. **先验声明**（思考链内，不输出；三项合计按一项检查计——同一触发点）：显式声明默认立场（信任/怀疑/中立）及其来源（经验/训练数据统计/媒体权威度/利益相关）+ 对核心命题不加证据时的第一反应结论 + 该先验被推翻的可证伪条件。第一反应必须具体可证伪（如"默认'仅后训练'叙事为真"），禁止"保持开放"式敷衍。
2. **竞争假说前置**：对默认叙事（官方口径/媒体共识/主流观点/自身第一反应）先行列出 ≥2 个竞争解释——对象是"分析起点"，区别于推演四查竞争性假说排除（对象是"核心归因"，分析中后段）。禁止"先接受默认叙事、后检验"。
3. **反证前置**：证据收集前先列 ≥3 条"最可能推翻本分析的反证清单"；分析中每确认一条，对应结论置信度降级。

**结论对照**（产物出口 = 位置性标注）：交付前以"先验→修正"形式声明结论是印证还是修正了先验（如"默认信任官媒 → 反证（央视滥用）推翻默认，结论转向'推广可、强制不可'"）。**多元是搜索空间，不是呈现格式**——竞争假说按证据权重排序，禁止对称并列（与虚假平衡禁止一致）。未执行前置协议不得进入合成阶段。

## Skill Invocation Protocol

When this skill is triggered:

1. **Run trigger guard**: Apply the Complexity Quick Assessment before proceeding
2. **Announce depth**: State the selected depth tier (default: Standard) with a one-line summary at the start of output.
   *Mild depth auto-detection*: If the user used "非常深入", "全面剖析", "层层剥开", etc. → default to Comprehensive. If "大概", "简要", "简单聊一下" → default to Focused. When uncertain, keep Standard and ask.
3. **Execute Phases 1-5**: Decompose → Research → Analyze → Apply Tools → Synthesize. **思考链完整执行，输出只含产物**（见 Internal/Output 边界协议）——机制的思考步骤与输出的分析内容分开，不因不输出而跳过执行。
4. **Output Part A (Executive Summary) first** — always. End with the opt-in prompt for detailed expansion
5. **输出语言规则（v1.8.0 修正）**：输出语言由 `config.yaml` 的 `language` 字段决定（zh = 全中文，en = 全英文）；模型触发时应读取 config——若无法读取，按用户提问语言判断。**中/英模式下均为全量切换**：透镜名、工具名、章节标题、表格标签、正文全部使用输出语言（透镜中文名见透镜表）。仅保留例外：中文模式下保留无标准翻译的专有名词（Cynefin, Meadows, Bourdieu）与深度声明（Focused/Standard/Comprehensive）；英文模式下无例外。**执行细则**：输出时使用透镜表中文名（"心理学"、"不对称检测"，不得输出 Psychology、Asymmetry Detection）——不确定译名时用常用译名并保持全文一致。
6. **Run metacognitive checkpoint** before final delivery
7. **Be transparent about limitations**: State what you couldn't verify, what lenses you omitted and why
8. **Respect exit protocol**: If user asks for shorter output, switch to Collapsed Mode immediately
9. **交付前重读（v1.7.0）**: Part A 完成后、交付前，重读一遍盲点清单、置信度说明与**语言合规**（透镜名/工具名/章节标题/表格标签是否使用输出语言——元认知检查在生成末尾执行，重读是其物理补偿）。

## 框架自我约束条款（v1.7.0）

机制不是永久资产，框架不豁免于自己的规则：
- **机制淘汰**：连续 5 次实战未触发或未产出独立价值的机制 → 淘汰评估（登记 UPDATELOG）。
- **升版必答**：每次版本升级必须记录"本次淘汰/降级了哪些机制"——无淘汰记录的升级视为不完整。
- **对称信号**：校准循环只有"失败=加规则"的单向信号，本条款提供"过度=减规则"的对称信号。

## 机制入库协议（v1.8.0 新增）

新机制（检查项/协议/质量标准）入库前必须通过三问——**防特化预防机制，治本于清洗**：
1. **通用性**：角色/判定是否通用？换一个结构异质的场景（非来源案例领域）是否失效？——失效则需抽象后再入库
2. **跨域示例**：是否配 ≥2 个跨领域示例（标注"示例："与机制本体区分）？——单案例机制禁止直接入库
3. **抽象表述**：能否用"抽象角色+检测特征"表述而非案例实体名？——机制文本禁止出现具体国家/公司/事件名

**示例双层设计**：机制文本保留一行抽象示例（执行可见）；完整案例进 `docs/cases.md`（维护者文档，非执行文档——单轮分析不会读取）。

---

