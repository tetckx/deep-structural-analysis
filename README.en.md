**Read this in other languages:** [:cn: 简体中文](README.md)

# Deep Structural Analysis

![Version](https://img.shields.io/badge/version-1.9.0-green.svg) ![License](https://img.shields.io/badge/license-MIT-green.svg)

> Multi-Perspective Structural Analysis for Complex Questions
> **v1.9.0** - Progressive Architecture - core + 8 config-trimmed extensions + lite · 16 lenses (4 categories) · 10 core tools · Meta-Rule Layer + mechanism execution layering + case library separation

> **Note**: This skill was developed and stress-tested exclusively with Chinese training corpora. English output may not match the quality of Chinese output. For best results, use Chinese as the output language (`language: zh` in config.yaml).

A disciplined, cross-disciplinary analytical framework for complex social, economic, and systemic questions. Uses web search for factual grounding (mandatory for current-events/data questions), applies multiple disciplinary lenses with mandatory cross-validation, and delivers stratified output with explicit confidence calibration (confidence tiers, verification-strength grading, quantity-source transparency).

**Not a chatbot. Not a prompt template. An analytical operating system.**

---

## Quick Install

Place the entire directory in your OpenCode skills folder:

```
~/.config/opencode/skills/deep-structural-analysis/
```

All extensions are pre-wired in config.yaml as trim switches - standard single-turn analysis uses only the core; extensions/docs are read in explicit scenarios (single-tool mode / interactive mode / user follow-up).

---

## What It Does

| Phase | Action |
|-------|--------|
| 1 | Decompose the question (surface, structural, micro, temporal) |
| 2 | Web search for factual grounding (mandatory for current events / specific data; optional for purely conceptual questions) |
| 3 | Apply 3-12 disciplinary lenses across Foundation / Human / Structure / Material |
| 4 | Apply 2-3 structural tools (Asymmetry Detection, Reflexivity, MLSD, etc.) |
| 5 | Synthesize with cross-validation, divergence mapping, blind spot audit |

**Output**: Executive Summary -> Detailed Analysis (on demand) -> Collapsed (degradable)

---

## When to Use

| Use | Don't Use |
|-----|-----------|
| Complex social/economic/institutional questions | Simple factual queries |
| Multiple stakeholder groups, systemic contradictions | Single-domain, one-sentence answers |
| Cross-disciplinary perspectives needed | Pure technical/code/math questions |
| "deep analysis", "multi-angle", "structural" | "summarize", "translate", "weather" |

- **Complicated** domain -> auto-degrade to Lite (2-3 lenses, executive summary only)
- **Clear** domain -> short answer + offer to expand (NO Lite)
- **Complex/Chaotic** domains -> full framework
- **Standard single-turn analysis uses only the core**; extensions/docs are read in explicit scenarios

---

## Architecture

```
deep-structural-analysis/
├── SKILL.md                    Core framework (~580 lines)
├── config.yaml                 Module config
├── README.md                   简体中文
├── README.en.md               English
├── lite/SKILL.md              Lite mode entry (Clear/Complicated auto-degrade)
├── extensions/                 Config-trimmed modules (8 files)
│   ├── trauma-sensitive.md     Trauma-aware + over-abstraction
│   ├── exit-protocols.md       Degradation + refusal + conflict resolution
│   ├── batch-analysis.md       Batch + multi-question triage
│   ├── offline-fallback.md     Prior knowledge (10 frameworks)
│   ├── interactive.md          Conversational mode
│   ├── layered-protocol.md     L1->L2->L3 progression
│   ├── ai-epistemology.md      AI epistemology (timeline analysis)
│   └── lens-application.md     Lens detail rules (exemption/material/AI calibration)
├── docs/                       Theory docs + tool docs + changelog
│   ├── tools/                  Tool full docs (8 files)
│   ├── 三向理论.md            Tri-directional Lens full doc
│   ├── 多层信号解码.md        Multi-Layer Signal Decoding full doc
│   ├── synthesis-reference.md  Synthesis reference (templates/tensions)
│   ├── cases.md                Case library (mechanism review)
│   ├── 极限测试全集.md        11 limit test cases
│   └── UPDATELOG.md           Update log + build history (single source of truth)
```

---

## Key Features

### 16 Disciplinary Lenses (4 categories)
- **Foundation**: Epistemology, Systems Theory, History, Temporality
- **Human**: Psychology, Sociology, Anthropology, Affect
- **Structure**: Economics, Political Science, Institutional Analysis, Technology, Geography
- **Material**: Ecological/Environmental, Infrastructure/Material Flow, Life Science/Bodily (domain-triggered)

### 10 Structural Tools
Tri-directional (三向) - 80/20 - Adaptive Cycle - Path Dependency - Asymmetry Detection - Incentive Mapping - Capital Type Matrix - Reflexivity Analysis - Multi-Layer Signal Decoding (MLSD) - Strategic Interaction Matrix

### 8 Metacognitive Checks
Adversarial test - Data-dependence audit - Blind-spot verification - Temporal bias - Dimension coverage - Normative stance - Over-abstraction (trauma topics only) - Human-factor check (institutional failures)

### Quality Standards
- **Anti-inertia**: Forces at least one Human lens on economic/policy topics
- **History mandatory**: Current events/policy/trends -> History lens required
- **Trauma-sensitive**: 5 constraints + anti-dilution + precision exception
- **Confidence calibration**: confidence tiers (high/medium/low criteria), verification-strength grading (publicly-verified != announced), quantity-source transparency (scope + stage)

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

11 extreme test cases (see `docs/极限测试全集.md`): self-reference, protocol conflict, incommensurability, information vacuum, metacognitive self-reference, real-time feedback loops, self-negation, value conflict, epistemological collapse, full tool-pool self-referential analysis.

---

## Configuration

```yaml
depth:
  default: Standard          # Focused | Standard | Comprehensive
  auto_degrade_to_lite: true

language: zh                 # zh = Chinese, en = English

extensions:
  batch_analysis:
    enabled: true
  exit_protocols:
    enabled: true
  layered_protocol:
    enabled: true
  trauma_sensitive:
    enabled: true
  interactive:
    enabled: true
  offline_fallback:
    enabled: true
  ai_epistemology:
    enabled: true
  lens_application:
    enabled: true
```

---

## Version History

Current version **v1.9.0** (new numbering chain 1.0.0 -> 1.9.0). Unified version scheme: only `SKILL.md` frontmatter carries the version field (main version declaration); config/lite/extensions carry none. `docs/UPDATELOG.md` is the single source of truth for version history (old-to-new mapping table, version matrix, build history appendix, and maintenance rules).

---

## License

MIT License - use, modify, distribute freely. Attribution appreciated. See [LICENSE](LICENSE).

---

*Built through iterative version milestones, 11 extreme test cases, and validated in real-world analyses. The framework is complete; the model is the analyst.*
