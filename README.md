# Deep Structural Analysis

> 跨学科深度结构分析技能 · Multi-Perspective Structural Analysis for Complex Questions  
> **v1.12.1+** · Progressive Architecture · 608-core + 250-extensions

[![License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)
[![Version](https://img.shields.io/badge/version-1.12.1-green.svg)](SKILL.md)

A disciplined, cross-disciplinary analytical framework for complex social, economic, and systemic questions. Uses web search for factual grounding, applies multiple disciplinary lenses with mandatory cross-validation, and delivers stratified output with explicit confidence calibration.

**Not a chatbot. Not a prompt template. An analytical operating system.**

---

## Quick Install

Place the entire directory in your OpenCode skills folder:

```
~/.config/opencode/skills/deep-structural-analysis/
```

Or load the skill explicitly in your session. All extensions are loaded on-demand based on trigger conditions — no manual configuration needed for defaults.

---

## What It Does

| Step | Action |
|------|--------|
| Phase 1 | Decompose the question — surface → structural → micro → temporal |
| Phase 2 | Web search for factual grounding (mandatory) |
| Phase 3 | Apply 3-12 disciplinary lenses across Foundation / Human / Structure categories |
| Phase 4 | Apply 2-3 structural tools (二六二, Asymmetry Detection, Reflexivity, etc.) |
| Phase 5 | Synthesize with cross-validation, divergence mapping, blind spot audit, Meadows leverage |

**Output**: Executive Summary → Detailed Analysis (on demand) → Collapsed/Ultra-Collapsed (degradable)

---

## Architecture

```
deep-structural-analysis/
├── SKILL.md                         Core framework (608 lines)
├── config.yaml                      Module config (all enabled by default)
├── lite/SKILL.md                    Auto-degrade target (Clear/Complicated)
├── extensions/                      On-demand modules (6 files, 250 lines)
│   ├── trauma-sensitive.md          Trauma-aware analysis + over-abstraction check
│   ├── exit-protocols.md            Degradation + refusal handling
│   ├── batch-analysis.md            Batch processing + multi-question triage
│   ├── offline-fallback.md          Structured prior knowledge (10 frameworks)
│   ├── interactive.md               Conversational analysis mode
│   └── layered-protocol.md          L1→L2→L3 cognitive progression
├── docs/
│   ├── SKILL构建全记录.md             Complete build history
│   ├── UPDATELOG.md                 Changelog
│   └── 极限测试全集.md               10 extreme test cases + retrospective
└── config.yaml                      Toggle modules on/off
```

**Progressive Depth**: Core loads always. Extensions load on trigger. Clear/Complicated domains auto-degrade to Lite. Complex/Chaotic domains load core + extensions as needed.

---

## Key Features

### 13 Disciplinary Lenses (3 categories)
- **Foundation** (1-2): Epistemology, Systems Theory, History, Temporality
- **Human** (1-2): Psychology, Sociology, Anthropology, Affect/Emotional Politics
- **Structure** (1-3): Economics, Political Science, Institutional Analysis, Technology Studies, Geography

### 8 Structural Tools
二六二 Distribution · 80/20 Principle · Adaptive Cycle · Path Dependency · Asymmetry Detection · Incentive Mapping · Capital Type Matrix · Reflexivity Analysis

### 7 Metacognitive Checks
Adversarial test · Data-dependence audit · Blind-spot verification · Temporal bias check · Dimension coverage · Normative stance · Over-abstraction check

### Quality Standards
- **Anti-inertia**: Forces at least one Human lens on economic/policy topics
- **History mandatory**: Current events/policy/trends → History lens required
- **Trauma-sensitive**: 5 constraints + anti-dilution for systemic violence topics
- **Language**: Chinese output, English only for proper nouns without standard translations
- **Confidence calibration**: Every conclusion tagged with data source and confidence level

### Degradation Protocol
Full Analysis → Collapsed (4 items) → Ultra-Collapsed (3 sentences) → Short answer (≤100 chars)

---

## Tested Limits

This skill has been stress-tested through **10 extreme test cases** (see docs/极限测试全集.md):

| # | Test | Upper Limit Tested |
|---|------|-------------------|
| 1 | Self-referential analysis (analyzer = analyzed) | Reflexivity, positionality |
| 2 | Trauma analysis with protection layer off | Ethical judgment precision |
| 3 | Concept resisting its own analysis (Love) | Cross-lens incommensurability |
| 4 | Information vacuum with pseudo-precision | Honesty under data insufficiency |
| 5 | Metacognition analyzing itself | Self-reference paradox |
| 6 | Conflicting protocol requirements (Silence) | Protocol conflict resolution |
| 7 | Real-time feedback loop (Public opinion trial) | Reflexivity acceleration |
| 8 | Self-negation (When NOT to use) | Harm scenario identification |
| 9 | Value incommensurability (Justice) | Forced choice under conflict |
| 10 | Simulation hypothesis (Knowledge) | Epistemological ultimate limit |

**Core finding**: The skill's ceiling is not its rule system — rules provide the skeleton. The model's judgment, reflexivity, and honesty fill in the flesh at the boundary where rules end.

---

## Configuration

Edit `config.yaml` to toggle modules:

```yaml
depth:
  default: Standard          # Focused | Standard | Comprehensive
  auto_degrade_to_lite: true # Clear/Complicated → Lite

extensions:
  batch_analysis:    true
  exit_protocols:    true
  layered_protocol:  true
  trauma_sensitive:  true
  interactive:       true
  offline_fallback:  true
```

---

## Version History

From v1.0.0 (initial framework, 397 lines) to v1.12.1 (progressive architecture, 608-core + 250-extensions). 15 major iterations. See docs/UPDATELOG.md for full changelog.

---

## License

MIT — use, modify, distribute freely. Attribution appreciated.

---

*Built through 15 versions, 10 extreme test cases, 8 mechanism test cases, 5 self-tests, and 20+ Zhihu real-world validations. The framework is complete; the model is the analyst.*
