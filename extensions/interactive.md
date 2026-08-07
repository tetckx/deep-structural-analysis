---
name: deep-structural-analysis/interactive
description: Interactive analysis protocol — alternative to full one-shot delivery. Load when user says "先聊聊" / "探讨一下" / "一步步来" / "explore this with me" or topic is genuinely exploratory.
---

# Interactive Analysis Protocol（对话式分析 · 可选）

Alternative to full one-shot delivery. Activates when user says "先聊聊"/"探讨一下"/"不用太正式"/"一步步来" — or when the topic is exploratory.

## Phase 1: Direction Proposal
After decomposition but before research, present 3-4 possible lens selection directions with one-line rationales:
- e.g. "侧重经济学+制度分析的治理视角"
- "侧重人类学+情感政治的文化视角"
- "侧重系统论+时间性的转型视角"

Ask: "这几个方向中哪个最值得优先展开？"

> **信息基础说明**：交互式模式的 L1 和 L2 阶段基于预训练知识进行，不触发实时搜索。方向确认后（L3 或增量交付的第三个透镜起），启动搜索并事实绑定后续分析。

## Phase 2: Incremental Delivery
After each lens/tool is applied, pause and ask: "这个方向是否值得深入？还是切换到下一个透镜？" User controls depth allocation — can go deep on one, skip another.

## Phase 3: On-Demand Synthesis
After user signals completion (or pre-agreed number of lenses), deliver compact synthesis. **紧凑综合格式**: 核心发现（2-3句）+ 分层影响表。多镜共识、置信度说明、关键分歧、Meadows 杠杆如用户在对话中未触及可省略。完整执行摘要作为可选项——用户说"出完整摘要"即可获取。

## Constraint
Sacrifices analytical completeness for conversational depth. Appropriate for exploration, not for decision-support requiring full cross-validation. Does NOT replace standard protocol.

> **升级路径**：用户在交互式模式中随时可以说"出完整分析"或"按标准模式来"。此时不再逐透镜暂停，按照当前已确认的方向继续完成剩余透镜，最后输出标准执行摘要。

## Compatibility with Layered Protocol

If both Interactive Mode AND Layered Protocol trigger simultaneously (user says "先聊聊" while surface narrative is highly misleading):

- **Layered Protocol provides the internal structure** (L1→L2→L3 progression)
- **Interactive Mode provides the delivery rhythm** (pause after each layer for user input)

Round 1: Output L1 (surface impression). Ask "这是常见的看法——需要我用某个学科透镜挑战一下吗？"
Round 2: If yes, output L2 (single-lens challenge). Ask "这个方向值得深入吗？还是换个透镜？"
   - **若用户选择"换个透镜"**：回到 L2，用用户指定的另一个透镜再做一次单透镜挑战。连续两次"换个透镜"后，建议"是否直接用多透镜分析？"
Round 3: If yes, output L3 (full multi-lens). Offer full Executive Summary.

In Interactive+Layered mode, defer Phase 2 web search until user confirms direction after L2 — this avoids wasting search on a direction the user may reject. Bind facts after direction is confirmed.

