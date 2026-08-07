**Read this in other languages:** [:us: English](README.en.md)

# Deep Structural Analysis — 使用须知

![Version](https://img.shields.io/badge/version-1.9.0-green.svg) ![License](https://img.shields.io/badge/license-MIT-green.svg)

> 跨学科深度结构分析技能。当前版本 v1.9.0 · 渐进式架构 · 核心框架 + 8 扩展（裁剪配置）+ lite · 16透镜4类别 · 10核心工具 · 元规则层 + 机制执行分层协议 + 案例库分离

---

## 这是什么

一个 AI 分析框架。当面对复杂社会/经济/制度问题时：

1. **搜索事实** — 不是凭空推测（时事/数据类问题强制）
2. **多透镜交叉验证** — 强制至少一个非舒适区透镜，防止经济-政治单轴论证
3. **应用结构工具** — 三向、不对称检测、激励映射、多层信号解码 (MLSD)、策略互动矩阵 等 10 个工具
4. **元认知自检** — 敌对测试、数据审计、盲点验证、规范性立场检查、人的因素检查 等（思考链内执行，不输出过程）
5. **合成推演** — 交叉验证 + 竞争性假说排除 + 二阶效应推演 + 物理锚定检查
6. **分层交付** — 系统-制度-个体 × 三个时间维度
7. **质量保障** — 置信度分级判定（高/中/低）、验证强度分级（公开验证 ≠ 公告声明）、数量口径透明；伦理敏感性：创伤议题内置保护约束

输出格式：执行摘要（必出）→ 详细分析（按需）→ 可降级到折叠/超折叠模式。

---

## 何时使用

| 用 | 不用 |
|----|------|
| 复杂社会/经济/制度问题 | 简单事实查询 |
| 涉及多利益群体、系统性矛盾 | 单一领域、可一句话回答 |
| 需要跨学科视角 | 纯技术/代码/数学问题 |
| "深度分析"、"多角度"、"结构性" | "总结一下"、"翻译"、"天气" |

- **Complicated 域**自动降级到 Lite（2-3透镜，仅执行摘要）
- **Clear 域**：简短回答 + 询问是否需要展开（不做 Lite）
- **Complex/Chaotic 域**才展开完整框架
- **标准单轮分析只用核心**；扩展与 `docs/` 在显式场景读取（单工具模式 / 交互模式 / 用户追问展开）

---

## 快速开始

```
用户：深度分析一下为什么中国劳动法执行这么难

→ 触发守卫：识别为 Governance/Compliance
→ 复杂度：Complex
→ 搜索事实 → 选 6-7 透镜（含反惯性强制人文透镜）
→ 应用 2-3 工具（不对称检测+激励映射+路径依赖）
→ 元认知自检 → 输出执行摘要
```

---

## 输出语言

默认：**中文**。所有章节标题、表格标签、正文均为中文。仅保留无标准翻译的专有名词（Cynefin, Meadows, Bourdieu）与深度声明（Focused/Standard/Comprehensive）。

切换为全英文输出，编辑 `config.yaml`：

```yaml
language: en
```

---

## 透镜速查

| 类别 | 透镜 | 定量 |
|------|------|------|
| 基础 | 认识论、系统论、历史、时间性 | 1-2 |
| 人文 | 心理学、社会学、人类学、情感 | 1-2（反惯性强制） |
| 结构 | 经济学、政治学、制度分析、技术研究、地理 | 1-3 |
| **物质** | **生态/环境、基础设施/物质流、生命科学/身体** | **0-1（领域触发式必选）** |

强制规则：经济/政策话题不得跳过人文透镜。当前事件必须包含历史透镜。输出使用透镜中文名（英文名仅供内部参考）。

---

## 测试极限

11 道极限测试（见 `docs/极限测试全集.md`）：自指、协议冲突、不可通约性、信息真空、元认知自指、实时反馈环、自我否定、价值冲突、认识论崩溃、全工具池自指分析等。

---

## 配置

```yaml
depth:
  default: Standard          # Focused | Standard | Comprehensive
  auto_degrade_to_lite: true

language: zh                 # zh = 中文 | en = 英文

extensions:
  batch_analysis:
    enabled: true
  exit_protocols:
    enabled: true
  layered_protocol:
    enabled: true
  trauma_sensitive:
    enabled: true
  interactive:
    enabled: true
  offline_fallback:
    enabled: true
  ai_epistemology:
    enabled: true
  lens_application:
    enabled: true
```

---

## 目录

```
deep-structural-analysis/
├── SKILL.md                   核心框架（~580行）
├── config.yaml                模块配置
├── README.md                  简体中文
├── README.en.md               English
├── lite/SKILL.md              轻量模式入口（Clear/Complicated 域自动降级）
├── extensions/                8个扩展（裁剪配置）
│   ├── trauma-sensitive.md    创伤敏感
│   ├── exit-protocols.md      降级协议 + 协议冲突解决
│   ├── batch-analysis.md      批处理
│   ├── offline-fallback.md    离线框架
│   ├── interactive.md         对话式
│   ├── layered-protocol.md    认知递进
│   ├── ai-epistemology.md     AI认知论
│   └── lens-application.md    透镜应用细节
├── docs/                      文档
│   ├── tools/                 工具完整文档（8个）
│   ├── 三向理论.md            三向透镜完整文档
│   ├── 多层信号解码.md        MLSD 完整文档
│   ├── synthesis-reference.md 合成参考（模板/张力表）
│   ├── cases.md               案例库（机制入库审查用）
│   ├── 极限测试全集.md        11道极限测试
│   └── UPDATELOG.md           更新日志 + 构建全记录（版本历史唯一权威）
```

---

## 版本链

当前版本 **v1.9.0**（新编号体系 1.0.0 → 1.9.0）。版本号体系说明：全包统一版本号，**仅 SKILL.md frontmatter 保留 version 字段**（主版本声明），config/lite/extensions 不设 version 字段；版本历史唯一权威来源为 `docs/UPDATELOG.md`（含新旧编号映射表、版本矩阵、构建全记录附录与维护规范）。

---

## 许可证

MIT License — 自由使用、修改、分发，署名致谢。详见 [LICENSE](LICENSE)。
