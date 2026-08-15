# Deep Structural Analysis

**Read this in other languages:** [:cn: 简体中文](README.md)

[![Version](https://img.shields.io/badge/version-1.9.5-green.svg)](SKILL.md) [![License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)

> Multi-perspective structural analysis skill for complex social, economic, philosophical, and systemic questions. **Chinese primary** — developed and stress-tested with Chinese corpora; Chinese output quality exceeds English.

---

## What It Does

Most AI analysis gives you a confident single-perspective answer. This skill does the opposite: it forces the analysis through **16 disciplinary lenses**, **10 structural tools**, and an **attack loop** that exposes the analyst's own priors and subjects every conclusion to adversarial review before delivery.

The result is stratified, fact-bound, confidence-calibrated analysis — with blind spots explicitly listed and uncertain claims explicitly marked, instead of hidden.

**Use it when** the question is complex, multi-sided, or systemic:
- "Why does labor-law enforcement fail so consistently in practice?"
- "What's really driving the AI price war?"
- "Analyze this platform's ecosystem position from multiple angles"
- "用三向分析一下" / "深度分析一下当下的就业形势"

**Skip it for** factual questions, debugging, summaries, or anything a single source answers.

---

## What You Get (Example Output)

A real analysis of "Why do city metros keep losing money yet keep expanding?" (example · analyzed 2026-08-08) produces this shape:

```
Depth: Standard · Complexity domain: Complex

[PRIOR EXPOSED] Default stance: "Persistent metro losses = expansion should stop"
  (to be attacked)
[CORE FINDING] "Loss" is an accounting artifact (high depreciation + statutory
  public-service fares); expansion's hidden benefits (land value uplift, urban
  density, commute costs) never appear on the books
  → a mismatch between the loss narrative and full-cost accounting — not a
  "should we build" question at all
[CROSS-LENS CONSENSUS] Economics (accounting basis vs full-cost) / Institutional
  (statutory fare pricing) / Physical (ridership-density constraints)
[CONFIDENCE] Medium — "accounting basis" is fact (high), "hidden benefits drive
  decisions" is interpretation (medium)
[REVISION TRACE] Counter-evidence "local debt pressure should halt expansion"
  assessed: debt constraint is real but partly offset by land-sale revenue
  → "halt" downgraded to "slow the pace"
[LAYERED IMPACT] System (urban sprawl pattern) / Institutional (subsidy mechanism)
  / Individual (commuter costs)
[BLIND SPOTS] Local fiscal details invisible; shrinking-city cases not covered
```

Every analysis carries this shape: **priors exposed → facts gathered → multi-lens cross-validation → confidence calibrated → revisions from adversarial attack recorded** — so you can see *what was challenged* and *what survived*, not just the polished conclusion.

---

## How It Works

1. **Trigger Guard** — complexity check: is this a structural question or a simple fact?
2. **Attack Loop (every run)** — expose the analyst's default stance, list counter-evidence *before* gathering facts, then run an adversarial pass before delivery. Intensity is adjustable: "轻一点" (gentle) / "狠一点" (ruthless).
3. **Five Phases** — Decompose → Research (web search, mandatory for current events) → Multi-lens Analysis → Structural Tools → Synthesis.
4. **推演四查 (Four Deduction Checks)** — competing-hypothesis exclusion, second-order effects, physical anchoring, global-south variables, plus the coexistence check (default: things stay as they are; change needs explicit triggers).
5. **Quality Standards** — every claim fact-bound; confidence graded (high = 2+ independent sources with opposing stances); numbers carry source & scope; no false balance on power asymmetries.

## Key Features

- **16 lenses** across Foundation / Human / Structure / Material categories
- **10 structural tools** (三向, MLSD, Asymmetry Detection, Incentive Mapping, Strategic Interaction, Reflexivity, ...)
- **Attack-loop protocol** — the analyst's own priors are exposed and attacked before delivery (not a gimmick: it emerged from adversarial review of this very skill)
- **Trauma-sensitive standard** — for harm-related topics: no false balance, no "understand the other side" demands on victims
- **Gotchas** — 9 empirically-verified failure modes (comfort-zone lens selection, dropped history lens, over-fitted signal decoding, ...)
- **Behavior-verified** — the framework was pruned 590→216 lines based on real-usage trace evidence (now 351 lines after post-1.9.0 additions); the full decision chain is in `docs/behavioral-experiment.md`

## Quick Install

This skill uses the standard SKILL.md format (directory + SKILL.md + references/) and installs into any agent environment that loads skills by that convention:

- **OpenCode**: Windows `%USERPROFILE%\.config\opencode\skills\deep-structural-analysis\`; macOS/Linux `~/.config/opencode/skills/deep-structural-analysis/`
- **DeepSeek Harness (DSH)**: copy to the project `.agents/skills/deep-structural-analysis/` (or the user-level skills directory)
- **Claude Code / other SKILL.md-compatible environments**: copy to that environment's skills directory (e.g. `~/.claude/skills/`)
- **Any environment** that loads skills by the "directory + SKILL.md" convention works as-is.

Trigger by asking for depth: "深度分析…", "从多个角度…", "用三向…", or "泼冷水/挑刺/反驳我" (adversarial review mode).

## Configuration

No external config file — **output language follows the user's question language** (Chinese question → full Chinese output; English question → full English output; full switching, see "Output Language Rules" in SKILL.md). Depth defaults to Standard; user can specify.

## Files

- `SKILL.md` — core framework (execution, 379 lines)
- `docs/depth-reference.md` — full theory for 三向 & MLSD (reference)
- `docs/behavioral-experiment.md` — maintenance decision chain (validation boundaries)
- `docs/attack-survivors.md` — metacognitive reference (what survives attack)
- `docs/case-test-archive.md` — case & test archive (maintenance)

## Version

v1.9.5 — see `docs/UPDATELOG.md` for full history (authoritative).

## License

[MIT](LICENSE)
