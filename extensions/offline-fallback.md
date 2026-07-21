---
name: deep-structural-analysis/offline
description: Structured prior knowledge framework for offline analysis. Load automatically when Phase 2 detects no accessible search tool.
version: 1.1.1
---

# Offline Fallback — Structured Prior Knowledge

Load when search is unavailable. Frameworks anchor analysis in validated cross-domain patterns. NOT substitutes for data — they prevent floating in unsupported assertion.

## Framework Anchors (10 validated cross-domain frameworks)

| # | Framework | Domain | What it explains | Use when... |
|---|-----------|--------|-----------------|-------------|
| 1 | Free-rider problem（搭便车问题） | Public goods | Why individuals under-contribute to shared resources | Collective action, public infrastructure, climate |
| 2 | Tragedy of the commons（公地悲剧） | Shared resources | Why unregulated shared resources degrade | Environmental depletion, overfishing, bandwidth |
| 3 | Silence spiral（沉默螺旋） | Power/Communication | Why minority views disappear from public discourse | Public opinion, whistleblowing, workplace dissent |
| 4 | Principal-agent problem（委托-代理问题） | Organizations | Why agents act against principals' interests | Corporate governance, bureaucracy, delegation |
| 5 | Regulatory capture（监管俘获） | Institutions | Why regulators serve the regulated instead of the public | Industry oversight, revolving door, lobbying |
| 6 | S-curve adoption（S曲线采纳） | Technology | How innovations diffuse: slow→rapid→saturation | Tech adoption, market penetration, network effects |
| 7 | Jevons paradox（杰文斯悖论） | Efficiency/Rebound | Why efficiency gains increase total consumption | Energy, AI compute, automation cost savings |
| 8 | Path dependency（路径依赖） | History/Institutions | Why suboptimal systems persist due to historical lock-in | QWERTY, infrastructure standards, legal precedents |
| 9 | Goodhart's law（古德哈特定律） | Metrics/Institutions | "When a measure becomes a target, it ceases to be a good measure" | KPIs, standardized testing, GDP as welfare proxy |
| 10 | In-group/out-group bias（内群体/外群体偏见） | Social dynamics | Why people favor their own group and devalue others | Polarization, discrimination, nationalism |

## Citation Format

Framework-anchored conclusions MUST be labeled distinctly from data-supported ones:

```
格式：理论推断（基于 [framework name]，非实证验证）
示例：理论推断（基于 Principal-agent problem，非实证验证）：地方政府在债务压力下优先还债而非投资公共服务。
```

## Offline-Specific Confidence Note

In the 置信度说明:
1. Prepend: *"⚠️ 本次分析基于预训练知识和结构化先验框架，未接入实时搜索。所有结论标记为理论推断或低置信度。"*
2. ALL framework-anchored conclusions → 低置信度
3. Pre-training factual knowledge (e.g., "China's GDP was ~$18T in 2022") → 低置信度 unless independently verifiable from multiple pre-training sources
4. Invite user: "如果你能提供关于 [X] 的数据，我可以重新校准基于 [framework] 的推断。"

## Distinction Rule

| Source | Marking | Confidence |
|--------|---------|------------|
| Real-time search data | 事实绑定 | 中-高 |
| Pre-training factual knowledge | 预训练知识 | 低 |
| Framework-anchored inference | 理论推断（框架名） | 低 |
| Pure speculation (avoid) | — | 不可接受 |
