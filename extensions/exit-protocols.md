---
name: deep-structural-analysis/exit
description: Exit and degradation protocols — Collapsed Mode, Ultra-Collapsed, Refusal handling, and architecture limitation. Load when user says "简单点"/"说人话"/"简短回答" or when degradation signals are detected.
version: 1.0.2
---

# Exit & Degradation Protocols

## Collapsed Mode

Trigger: user says "简单点","说人话","简短回答","give me the short version", or similar. Switch immediately.

Output (only these items):
1. **核心发现** (2-3 句话)
2. **⚠️ 关键盲点**（若存在某个盲点会实质改变个体策略——最多一句话。若无则省略。）
   - **创伤敏感性约束**：当话题触发 Trauma-sensitive 标准时，关键盲点严禁对称句式。有效示例："安全成本和暴力风险不在同一个量级"。违规示例："双方都需要冷静"。
3. **分层影响表** (系统 / 制度 / 个体 × 短期 / 中期 / 长期)
4. **一个追问**: "需要我展开某一透镜或工具的详细分析吗？"——创伤敏感话题上，追问不得要求受害者"理解对方"。

## Ultra-Collapsed（二次降级）

Trigger: user responds to Collapsed with "再简单点","说人话","一句话". Drop the table.

1. **一句话核心发现**
2. **一条可行动个体建议**（≤20 个中文字符）
3. **一条风险提示**（如适用则保留，否则省略）

纯文本，无表格，无追问。

## Refusal Handling

If user declines to choose after TWO clarification attempts ("你自己判断"/"自行判断"/"我不参与"/"I won't participate"):

1. Default to LOWER-effort option. Decision heuristic:
   - **短回答**（纯文本，≤100 中文字符，无表格，无板块标题）：个人/临床维度（"我为什么..." / "我怎么才能..." / "我该不该..."），用户寻求建议而非分析。示例："我为什么总是失眠" → 短回答+可行建议，不做睡眠科学的聚焦分析。**短回答格式**：一个自然段落，直接回答核心关切。不需要板块标题（"核心发现"等）——用户要的是答案本身，不是分析结构。
   - **聚焦深度**（3-4透镜，执行摘要含表格）：即使个人框定，但触及结构域（经济、政策、社会规范）。示例："我为什么存不下钱" → 聚焦，因为个人财务结构性嵌入工资增长、通胀和消费文化。
   - **模糊时默认聚焦深度**。用户可继续折叠（"说人话"），但展开需要新一轮交互。
2. 显式声明默认值："我将采用[简短回答/聚焦深度分析]，如需更深入请随时告知。"
3. **原理**：两次拒绝选择的用户在表达不耐烦，不是请求深度。宁可给少了让用户说"展开"，也别给多了让用户觉得"你不听我说话"。
4. 展开通道保留：用户后续说"展开"或"详细分析"时，直接升级深度，不重新问原始澄清问题。

> **优先级说明**：Refusal 产生的"短回答"或"聚焦深度"是分析的起始级别——比 Collapsed 更早触发（发生在完整分析启动之前）。如果用户在 Refusal 产生的聚焦深度输出后说"说人话"，继续走 Collapsed→Ultra-Collapsed 链条。

## Architecture Limitation

Mid-generation interruption (user sends "说人话" during analysis) cannot be guaranteed by Skill text alone. Best-effort: (1) check for new input at Phase/lens/tool boundaries — between output sections, when switching lenses, after completing a tool application, (2) discard un-emitted plans, (3) if partial analysis already output, prepend "[已切换至折叠模式]".
