# Deep Structural Analysis — 使用须知

> 跨学科深度结构分析技能。当前版本 **v1.9.0** · 渐进式架构 · 16透镜4类别 · 10核心工具 · 攻击循环协议 + 推演四查 + 行为实验精简（590→215 行）。

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

## 快速开始

放置整个目录到 OpenCode skills 文件夹：
- Windows: `%USERPROFILE%\.config\opencode\skills\deep-structural-analysis\`
- macOS/Linux: `~/.config/opencode/skills/deep-structural-analysis/`

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
├── SKILL.md                   核心框架（执行，215 行）
├── config.yaml                文档性配置（default: Standard, language: zh）
├── docs/
│   ├── depth-reference.md     三向+MLSD 完整理论（深度参考，非执行）
│   ├── behavioral-experiment.md  精简决策链（维护记录）
│   ├── attack-survivors.md    元认知参考（攻击幸存者记录）
│   ├── cases.md               维护案例库
│   ├── UPDATELOG.md           版本历史（唯一权威）
│   └── 极限测试全集.md        历史测试档案
└── extensions/                触发式扩展
    ├── exit-protocols.md      三级降级+拒绝处理
    ├── batch-analysis.md      批处理协议
    ├── trauma-sensitive.md    创伤敏感约束
    └── offline-fallback.md    离线框架锚点+理论推断标注
```

## 配置

`config.yaml` 为文档性配置——执行以 SKILL.md 为准（行为实验验证：配置项从未被执行路径读取）。

## 版本

v1.9.0——完整版本链见 `docs/UPDATELOG.md`（版本历史唯一权威）。
