---
name: deep-structural-analysis/offline
description: Structured prior knowledge framework for offline analysis. Load automatically when Phase 2 detects no accessible search tool.
version: 1.1.1
---

# Offline Fallback 鈥?Structured Prior Knowledge

Load when search is unavailable. Frameworks anchor analysis in validated cross-domain patterns. NOT substitutes for data 鈥?they prevent floating in unsupported assertion.

## Framework Anchors (10 validated cross-domain frameworks)

| # | Framework | Domain | What it explains | Use when... |
|---|-----------|--------|-----------------|-------------|
| 1 | Free-rider problem锛堟惌渚胯溅闂锛?| Public goods | Why individuals under-contribute to shared resources | Collective action, public infrastructure, climate |
| 2 | Tragedy of the commons锛堝叕鍦版偛鍓э級 | Shared resources | Why unregulated shared resources degrade | Environmental depletion, overfishing, bandwidth |
| 3 | Silence spiral锛堟矇榛樿灪鏃嬶級 | Power/Communication | Why minority views disappear from public discourse | Public opinion, whistleblowing, workplace dissent |
| 4 | Principal-agent problem锛堝鎵?浠ｇ悊闂锛?| Organizations | Why agents act against principals' interests | Corporate governance, bureaucracy, delegation |
| 5 | Regulatory capture锛堢洃绠′繕鑾凤級 | Institutions | Why regulators serve the regulated instead of the public | Industry oversight, revolving door, lobbying |
| 6 | S-curve adoption锛圫鏇茬嚎閲囩撼锛?| Technology | How innovations diffuse: slow鈫抮apid鈫抯aturation | Tech adoption, market penetration, network effects |
| 7 | Jevons paradox锛堟澃鏂囨柉鎮栬锛?| Efficiency/Rebound | Why efficiency gains increase total consumption | Energy, AI compute, automation cost savings |
| 8 | Path dependency锛堣矾寰勪緷璧栵級 | History/Institutions | Why suboptimal systems persist due to historical lock-in | QWERTY, infrastructure standards, legal precedents |
| 9 | Goodhart's law锛堝彜寰峰搱鐗瑰畾寰嬶級 | Metrics/Institutions | "When a measure becomes a target, it ceases to be a good measure" | KPIs, standardized testing, GDP as welfare proxy |
| 10 | In-group/out-group bias锛堝唴缇や綋/澶栫兢浣撳亸瑙侊級 | Social dynamics | Why people favor their own group and devalue others | Polarization, discrimination, nationalism |

## Citation Format

Framework-anchored conclusions MUST be labeled distinctly from data-supported ones:

```
鏍煎紡锛氱悊璁烘帹鏂紙鍩轰簬 [framework name]锛岄潪瀹炶瘉楠岃瘉锛?绀轰緥锛氱悊璁烘帹鏂紙鍩轰簬 Principal-agent problem锛岄潪瀹炶瘉楠岃瘉锛夛細鍦版柟鏀垮簻鍦ㄥ€哄姟鍘嬪姏涓嬩紭鍏堣繕鍊鸿€岄潪鎶曡祫鍏叡鏈嶅姟銆?```

## Offline-Specific Confidence Note

In the 缃俊搴﹁鏄?
1. Prepend: *"鈿狅笍 鏈鍒嗘瀽鍩轰簬棰勮缁冪煡璇嗗拰缁撴瀯鍖栧厛楠屾鏋讹紝鏈帴鍏ュ疄鏃舵悳绱€傛墍鏈夌粨璁烘爣璁颁负鐞嗚鎺ㄦ柇鎴栦綆缃俊搴︺€?*
2. ALL framework-anchored conclusions 鈫?浣庣疆淇″害
3. Pre-training factual knowledge (e.g., "China's GDP was ~$18T in 2022") 鈫?浣庣疆淇″害 unless independently verifiable from multiple pre-training sources
4. Invite user: "濡傛灉浣犺兘鎻愪緵鍏充簬 [X] 鐨勬暟鎹紝鎴戝彲浠ラ噸鏂版牎鍑嗗熀浜?[framework] 鐨勬帹鏂€?

## Distinction Rule

| Source | Marking | Confidence |
|--------|---------|------------|
| Real-time search data | 浜嬪疄缁戝畾 | 涓?楂?|
| Pre-training factual knowledge | 棰勮缁冪煡璇?| 浣?|
| Framework-anchored inference | 鐞嗚鎺ㄦ柇锛堟鏋跺悕锛?| 浣?|
| Pure speculation (avoid) | 鈥?| 涓嶅彲鎺ュ彈 |
