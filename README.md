# Deep Structural Analysis — 使用须知

**Read this in other languages:** [:us: English](README.en.md)

![Version](https://img.shields.io/badge/version-1.9.0-green.svg) ![License](https://img.shields.io/badge/license-MIT-blue.svg)

> 跨学科深度结构分析技能。当前版本 **v1.9.0** · 渐进式架构 · 16透镜4类别 · 10核心工具 · 攻击循环协议 + 推演四查 + 行为实验精简。

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

对"为什么 DeepSeek 在需求暴涨时反而预告涨价"的分析产出如下形态：

```
深度声明：Standard · 复杂度域 Complex

【暴露靶子】默认立场："涨价 = 纯供需调节"（待攻击）
【核心发现】涨价预告未执行 + 公告后需求创新高（8.9T/日峰值）
  → 不是降压工具，而是"叙事动作 + 资源重配信号"
【多镜共识】博弈（预告=期权）/ 制度（口径=信号）/ 物理（97%缓存=算力紧）
【置信度】中——"预告不执行"是事实（高），"动机归因"是解释（中）
【修订痕迹】反证"8/4服务降级=危机反应"被评估：无法排除 → 动机归因降级
【分层影响】系统（价格体系重锚）/ 制度（开发者成本结构）/ 个体（囤积行为）
【盲点】内部训练数据不可见；竞争对手反应未覆盖
```

每次分析都带这个形态：**暴露先验 → 收集事实 → 多镜交叉验证 → 置信度校准 → 攻击修订痕迹**——你能看到"什么被挑战了、什么幸存了"，而不只是一个抛光过的结论。

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
├── SKILL.md                   核心框架（执行，219 行）
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

v1.9.0——完整版本链见 `docs/UPDATELOG.md`（版本历史唯一权威）。

## 许可证

[MIT](LICENSE)
