# Deep Structural Analysis — 使用须知

**Read this in other languages:** [:us: English](README.en.md)

![Version](https://img.shields.io/badge/version-1.9.4-green.svg) ![License](https://img.shields.io/badge/license-MIT-blue.svg)

> 跨学科深度结构分析技能。当前版本 **v1.9.4** · 渐进式架构 · 16透镜4类别 · 10核心工具 · 立场切换发现引擎 + 攻击循环协议 + 推演四查 + 行为实验精简。

## 它是什么

对复杂社会/经济/哲学/系统性问题做多学科交叉分析：分解 → 研究（web search）→ 多透镜分析 → 结构工具 → 合成（交叉验证+置信度标注+分层输出）。所有结论事实绑定、置信度分级、盲点显式标注。

## 何时使用

| 触发 | 例子 |
|------|------|
| 用户要求深度分析 | "深度分析一下当下的就业形势" |
| 多角度探索 | "从多个角度分析这个现象" |
| 特定框架 | "用三向看这个问题" |
| 结构性 why | "为什么劳动法执行这么难" |

不适用：事实解释（"为什么天空是蓝色的"）、调试、总结、信息查询——直接简短回答。

## 案例（实际输出形态）

对"为什么城市地铁普遍亏损却仍在持续扩建"的分析（示例 · 分析时间 2026-08-08）产出如下形态：

```
深度声明：Standard · 复杂度域 Complex

【暴露靶子】默认立场："地铁持续亏损 = 应该停止扩建"（待攻击）
【核心发现】"亏损"是会计口径产物（高折旧 + 公益票价法定），扩建的
  隐性收益（土地增值/城市密度/通勤成本）不在报表内
  → 亏损叙事 vs 全成本收益错位，而非"该不该建"的问题
【多镜共识】经济学（口径 vs 全成本核算）/ 制度（公益票价法定）/
  物理（客流密度约束）
【置信度】中——"会计口径"是事实（高），"隐性收益主导决策"是解释（中）
【修订痕迹】反证"地方债务压力应叫停扩建"被评估：债务约束真实，
  但被土地出让收益部分对冲 → "叫停"结论降级为"节奏放缓"
【分层影响】系统（城市蔓延模式）/ 制度（补贴机制）/ 个体（通勤者成本）
【盲点】地方财政明细不可见；人口流出城市的个案未覆盖
```

每次分析都带这个形态：**暴露先验 → 收集事实 → 多镜交叉验证 → 置信度校准 → 攻击修订痕迹**——你能看到"什么被挑战了、什么幸存了"，而不只是一个抛光过的结论。

## 快速开始

本 skill 为标准 SKILL.md 格式（目录 + SKILL.md + references/），可安装到任何兼容 SKILL.md 技能的 agent 环境：

- **OpenCode**：Windows `%USERPROFILE%\.config\opencode\skills\deep-structural-analysis\`；macOS/Linux `~/.config/opencode/skills/deep-structural-analysis/`
- **DeepSeek Harness（DSH）**：复制到项目 `.agents/skills/deep-structural-analysis/`（或用户级 skills 目录）
- **Claude Code 等 SKILL.md 兼容环境**：复制到对应环境的 skills 目录（如 `~/.claude/skills/`）
- **其他环境**：任何按"目录 + SKILL.md"约定加载技能的 agent 均可直接使用

## 核心机制

- **攻击循环协议**：分析前暴露默认立场（靶子）+ 反证前置 + 交付前对立立场攻击——对抗单一叙事先天倾向
- **推演四查**：竞争性假说排除 / 二阶效应推演 / 物理锚定检查 / 全球南方变量 / 共存检查
- **质量标准**：置信度判定（高=≥2独立信源且立场相异）/ 数量引用规范（口径+阶段）/ 虚假平衡禁止
- **透镜纪律**：反惯性（≥1 舒适区外透镜）+ 历史透镜强制 + 事实绑定

## 透镜速览

Foundation：认识论/系统论/历史/时间性 · Human：心理学/社会学/人类学/情感 · Structure：经济学/政治学/制度分析/技术研究/地理 · Material（域触发）：生态/基础设施/生命科学

## 工具池（10 个）

三向 / 80-20 / Adaptive Cycle / Path Dependency / Asymmetry Detection / Incentive Mapping / Capital Matrix / Reflexivity / 多层信号解码 (MLSD) / 策略互动矩阵

## 目录

```
├── SKILL.md                   核心框架（执行，379 行）
└── docs/
    ├── depth-reference.md     三向+MLSD 完整理论（深度参考，非执行）
    ├── behavioral-experiment.md  精简决策链（维护记录）
    ├── attack-survivors.md    元认知参考（攻击幸存者记录）
    ├── case-test-archive.md   案例与测试档案（维护参考）
    └── UPDATELOG.md           版本历史（唯一权威）
```

## 配置

无外部配置文件——**语言由用户提问语言决定**（中文提问→全中文输出，英文提问→全英文输出；全量切换，见 SKILL.md"输出语言规则"）。深度默认 Standard，用户可指定。

## 版本

v1.9.4——完整版本链见 `docs/UPDATELOG.md`（版本历史唯一权威）。

## 许可证

[MIT](LICENSE)
