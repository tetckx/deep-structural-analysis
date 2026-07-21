---
name: deep-structural-analysis/layered
description: Layered Analysis Protocol 鈥?L1 surface impression 鈫?L2 single-lens challenge 鈫?L3 full multi-lens structural analysis. Load when user says "绗竴鎰熻鏄?.." / "鐩磋涓?.." / "涔嶄竴鐪?.." or when surface narrative is highly misleading.
version: 1.0.1
---

# Layered Analysis Protocol锛堣鐭ラ€掕繘妯″紡锛?
Optional protocol. Especially useful when the surface narrative is highly misleading.

## Three Layers

| Layer | Core Question | Output |
|-------|--------------|--------|
| L1: 鍒濆嵃璞?| What does common sense say? | 1-2 sentences |
| L2: 鍒濇鍒嗘瀽 | What does ONE disciplinary lens reveal that contradicts L1? | 1 paragraph, name the lens |
| L3: 娣卞害鎬濊€?| What emerges from multi-lens cross-validation? | Full Phase 3-5 output |

## Transition Protocol

```
L1鈫扡2: "[L1鍙戠幇] 鐪嬩技鍚堢悊锛屼絾 [鍏蜂綋浜嬪疄鎴栭€忛暅娲炲療] 瀵规鎻愬嚭浜嗘寫鎴橈紝鍥犱负..."

L2鈫扡3: "[L2鍒嗘瀽] 鎻ず浜嗕竴涓淮搴︼紝浣嗗畠鏃犳硶瑙ｉ噴 [浜や簰鐜拌薄]銆傝繖闇€瑕佸閫忛暅鍒嗘瀽銆?
```

杩囨浮鍙ヤ綅浜?L2 娈佃惤鏈熬鎴?L2 涓?L3 涔嬮棿锛屼綔涓虹嫭绔嬬煭娈佃惤銆備笉宓屽叆 L2 姝ｆ枃锛屼篃涓嶄綔涓?L3 寮€澶淬€?
## L1鈫扡2 Self-Check
Before writing L2, ask: "Which ONE factual premise of L1 is most likely false or misleading?" Target that premise specifically.

## Anti-Patterns
| Violation | Fix |
|-----------|-----|
| L2 just refines L1 slightly | L2 must produce a genuinely different answer |
| L3 restates L2 with more detail | L3 must synthesize across multiple lenses |
| Skipping L1 | L1 is the baseline 鈥?without it, the distance traveled is invisible |

## L2鈫扡3 Anti-Patterns
| Anti-pattern | Fix |
|-------------|------|
| Vague transition ("this is only one perspective") | Name the SPECIFIC thing L2 cannot explain |
| 3+ complementary lenses at once | Pick the SINGLE most critical missing lens |

## Duplication Guard
When activated alongside 5-Phase Ladder: L3 REPLACES Phase 3-5 鈥?do NOT run both. If user says "灞曞紑鏌愰€忛暅" after L3, output Part B 璇︾粏鍒嗘瀽 format directly 鈥?do NOT re-enter the L1鈫扡2鈫扡3 cycle.
