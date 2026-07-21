**Read this in other languages:** [:cn: 简体中文](README.md)

# Deep Structural Analysis

> Multi-Perspective Structural Analysis for Complex Questions
> **v1.12.1+** - Progressive Architecture - 608-core + 250-extensions

[![License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)
[![Version](https://img.shields.io/badge/version-1.12.1-green.svg)](SKILL.md)

> **Note**: This skill was developed and stress-tested exclusively with Chinese training corpora. English output may not match the quality of Chinese output. For best results, use Chinese as the output language (`language: zh` in config.yaml).

A disciplined, cross-disciplinary analytical framework for complex social, economic, and systemic questions. Uses web search for factual grounding, applies multiple disciplinary lenses with mandatory cross-validation, and delivers stratified output with explicit confidence calibration.

**Not a chatbot. Not a prompt template. An analytical operating system.**

---

## Quick Install

Place the entire directory in your OpenCode skills folder:

```
~/.config/opencode/skills/deep-structural-analysis/
```

All extensions load on-demand based on trigger conditions - no manual configuration needed for defaults.

---

## What It Does

| Phase | Action |
|-------|--------|
| 1 | Decompose the question (surface, structural, micro, temporal) |
| 2 | Web search for factual grounding (mandatory) |
| 3 | Apply 3-12 disciplinary lenses across Foundation / Human / Structure |
| 4 | Apply 2-3 structural tools (Asymmetry Detection, Reflexivity, etc.) |
| 5 | Synthesize with cross-validation, divergence mapping, blind spot audit |

**Output**: Executive Summary -> Detailed Analysis (on demand) -> Collapsed (degradable)

---

## Architecture

```
deep-structural-analysis/
├── SKILL.md                    Core framework (608 lines)
├── config.yaml                 Module config
├── lite/SKILL.md              Auto-degrade target
├── extensions/                 On-demand modules (6 files)
│   ├── trauma-sensitive.md     Trauma-aware + over-abstraction
│   ├── exit-protocols.md       Degradation + refusal handling
│   ├── batch-analysis.md       Batch + multi-question triage
│   ├── offline-fallback.md     Prior knowledge (10 frameworks)
│   ├── interactive.md          Conversational mode
│   └── layered-protocol.md     L1->L2->L3 progression
└── docs/                       Build history + changelog + test cases
```

**Progressive Depth**: Core always. Extensions on trigger. Clear/Complicated -> Lite. Complex/Chaotic -> core + extensions.

---

## Key Features

### 13 Disciplinary Lenses (3 categories)
- **Foundation**: Epistemology, Systems Theory, History, Temporality
- **Human**: Psychology, Sociology, Anthropology, Affect
- **Structure**: Economics, Political Science, Institutional Analysis, Technology, Geography

### 8 Structural Tools
262 Distribution - 80/20 - Adaptive Cycle - Path Dependency - Asymmetry Detection - Incentive Mapping - Capital Type Matrix - Reflexivity Analysis

### 7 Metacognitive Checks
Adversarial test - Data-dependence audit - Blind-spot verification - Temporal bias - Dimension coverage - Normative stance - Over-abstraction

### Quality Standards
- **Anti-inertia**: Forces at least one Human lens on economic/policy topics
- **History mandatory**: Current events/policy/trends -> History lens required
- **Trauma-sensitive**: 5 constraints + anti-dilution + precision exception
- **Confidence calibration**: Every conclusion tagged with source and confidence

### Degradation
Full Analysis -> Collapsed (4 items) -> Ultra-Collapsed (3 sentences) -> Short answer (100 chars)

---

## Output Language

Default: **Chinese**. Switch to English by editing `config.yaml`:

```yaml
language: en
```

---

## Tested Limits

10 extreme test cases (see `docs/极限测试全集.md`): self-reference, protocol conflict, incommensurability, information vacuum, metacognitive self-reference, real-time feedback loops, self-negation, value conflict, epistemological collapse.

---

## Configuration

```yaml
depth:
  default: Standard          # Focused | Standard | Comprehensive
  auto_degrade_to_lite: true

language: zh                 # zh = Chinese, en = English

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

v1.0.0 (397 lines) to v1.12.1+ (608-core + 250-extensions). 15 major iterations. See `docs/UPDATELOG.md`.

---

## License

MIT - use, modify, distribute freely. Attribution appreciated.

---

*Built through 15 versions, 10 extreme test cases, and 20+ real-world validations. The framework is complete; the model is the analyst.*
