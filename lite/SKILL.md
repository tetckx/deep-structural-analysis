<!-- Author: happy_chen -->

---
name: structural-analysis-lite
description: >-
  Lightweight structural analysis for Clear/Complicated complexity domains. Activated
  automatically by deep-structural-analysis when auto-degradation triggers, or directly
  when user asks for "绠€鍗曞垎鏋?/"蹇€熷垎鏋?/"澶ф鐪嬩竴涓?. Runs 2-3 lenses + 1 tool,
  outputs compact Executive Summary only, ~1/3 token budget. For Complex/Chaotic domains
  or user explicitly requests deep analysis, use the full deep-structural-analysis skill.
version: 2.0.1
---

# Structural Analysis 鈥?Lite

Progressive-depth companion to deep-structural-analysis. Activated when:
- Main skill's auto-degradation fires (Clear/Complicated domain, no explicit depth request)
- User says "绠€鍗曞垎鏋?/"蹇€熷垎鏋?/"澶ф鑱婅亰"/"绠€瑕佸垎鏋?/"quick analysis"
- User wants single-tool application on a structurally-framed question

For Complex/Chaotic domains or explicit "娣卞害鍒嗘瀽" requests: use the full skill.

---

## Core Workflow

**Phase 1 鈥?Decompose** (1 sentence each, internal):
1. Surface question
2. ONE misleading assumption in the common-sense answer 鈫?this becomes the core tension

**Phase 2 鈥?Research**: 1-2 fact searches. Goal: 2-3 concrete data points, not exhaustive coverage.
If search unavailable: use pre-training knowledge + mark all conclusions low-confidence.

**Phase 3 鈥?Analyze**: 2-3 lenses + 1 tool 鈫?compact output.

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
| Distribution/power concentration | 浜屽叚浜屽垎甯冩ā鍨?|
| Change over time | Adaptive Cycle or Path Dependency |
| Rules 鈮?reality | Asymmetry Detection |
| Who benefits vs. who pays | Incentive Mapping |
| Belief鈫抌ehavior鈫抮eality loop | Reflexivity Analysis |

---

## Lens Application (per lens, concise)

- **Core insight** (1 sentence 鈥?what does this lens reveal?)
- **Challenge to common sense** (1 sentence 鈥?what premise does it overturn?)
- **Fact anchor** (1 reference to research/pre-training data)
- **Blind spot** (what does this lens miss?)

---

## Output: Compact Executive Summary

No Part B. Output ONLY this:

```
> 鏈閲囩敤杞婚噺妯″紡锛?-3閫忛暅锛氶€愪竴鍒楀嚭閫忛暅鍚嶏紝濡?缁忔祹瀛?/ 绀句細瀛?锛涗粎鎵ц鎽樿锛屽厓璁ょ煡绠€鍖栵級銆傚闇€鏍囧噯娣卞害 (Standard: 5-7閫忛暅) 鎴栨洿鍏ㄩ潰 (Comprehensive: 7-9) 鐨勫垎鏋愶紝璇烽殢鏃跺憡鐭ャ€傗殸锔?鑻ユ湭鎺ュ叆瀹炴椂鎼滅储锛岃拷鍔犳爣娉?鍩轰簬棰勮缁冪煡璇?銆?
## [涓婚]

### 鏍稿績鍙戠幇
[2-3鍙?鈥?鏈€閲嶈鐨勪氦鍙夐獙璇佹礊瀵焆

### 鍏抽敭寮犲姏
[1鍙?鈥?甯歌瘑绛旀鐨勫摢涓粡楠屽墠鎻愯鎺ㄧ炕浜嗭紵]

### 缁撴瀯蹇収
[1涓伐鍏疯緭鍑?鈥?浜屽叚浜屽眰绾?/ 婵€鍔辨槧灏?/ 涓嶅绉板彂鐜癩

### 涓綋鍚彂
[1鍙ュ彲琛屽姩璁ょ煡 鈥?闈炵┖娉涘缓璁€傝嫢缁撴瀯闄愬埗涓嬫棤鍙鍔ㄧ瓥鐣ワ紝鎻愪緵璁ょ煡閿氱偣鑰岄潪缂栭€犲缓璁甝

### 鈿狅笍 鐩茬偣锛堝彲鐪佺暐锛?- [鏈垎鏋愭棤娉曡鐩栨垨楠岃瘉鐨勪竴涓叧閿洸鐐筣
```

鏃犲闀滃叡璇嗐€佹棤缃俊搴﹁鏄庛€佹棤鍏抽敭鍒嗘銆佹棤鍒嗗眰褰卞搷琛ㄣ€佹棤 Meadows 鏉犳潌銆傛暣浣撹緭鍑烘帶鍒跺湪涓€灞忎互鍐呫€?
---

## Quality Gates

| Gate | Test |
|------|------|
| **Anti-inertia** | Did I use at least one lens outside my comfort zone? |
| **Fact-bound** | Does every lens reference at least 1 concrete fact? |
| **Not labeling** | Did I apply lenses or just name them? |
| **Chinese output** | Primarily Chinese 鈥?section headers, table labels, prose |
| **Language-sensitive** | If I belong to the analyzed group, does this feel respectful? |
| **Trauma-aware** | If topic involves violence/discrimination: one sentence acknowledging real human pain, no false balance, no "understand both sides" |
| **Compact** | Fits one screen? If not, cut. |

---

## Anti-Patterns

| Violation | Fix |
|-----------|-----|
| Using 4+ lenses | Stick to 2-3 鈥?this is lite, not full |
| Outputting Part B with tables | Executive Summary only |
| "On one hand... on the other..." without weight | State which side has stronger evidence |
| Running full Phase 1-5 of the main skill | This is a separate skill |
| Uniform depth on multiple questions | Pick the 1-2 deepest, short-answer the rest |

---

## Exit / Degradation

- User says "鍐嶇畝鍗曠偣" 鈫?鏍稿績鍙戠幇 (1鍙? + 涓綋鍚彂 (1鍙?锛岀函鏂囨湰
- User wants full analysis 鈫?redirect to deep-structural-analysis
- Topic triggers trauma-sensitive concerns 鈫?load main skill's `extensions/trauma-sensitive.md`

---

## Relationship to Main Skill

```
Clear domain       鈫?short answer (no framework needed)
Complicated domain 鈫?structural-analysis-lite (this skill, auto-degrade target)
Complex domain     鈫?deep-structural-analysis core + extensions as needed
Chaotic domain     鈫?deep-structural-analysis core + all applicable extensions
```

This is the progressive-depth entry point. When in doubt between lite and full: use lite. The user can always say "灞曞紑" to upgrade.

---

*Companion to deep-structural-analysis v1.12.1+. For full framework documentation: see `../README.md`.*
