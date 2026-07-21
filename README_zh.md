# Deep Structural Analysis — 使用须知

> 跨学科深度结构分析技能。将研讨会方法论编码为可复用指令集。
> 当前核心 v1.12.1+ · 渐进式架构 · 默认全家桶加载 · 核心 608 行 + 扩展 250 行
> 六扩展版本: trauma v1.0.1 / exit v1.0.1 / batch v1.0.1 / offline v1.1.1 / interactive v1.0.1 / layered v1.0.1
> Lite 版本: v2.0.0（渐进式深度入口）

---

## 这是什么

一个 AI 分析框架。当面对复杂社会/经济/制度问题时，它强制性地：

1. **搜索事实** → 不是凭空推测
2. **多透镜交叉验证** → 强制至少一个非舒适区透镜，防止经济-政治单轴论证
3. **应用结构工具** → 二六二分布、不对称检测、激励映射等 8 个工具
4. **元认知自检** → 7 项硬约束：敌对测试、数据审计、盲点验证、价值透明化等
5. **分层交付** → 系统-制度-个体 × 三个时间维度
6. **伦理敏感性** → 创伤议题内置五项保护约束，反淡化机制防止分析失去锐度

输出格式：执行摘要（必出）→ 详细分析（按需）→ 可降级到折叠/超折叠模式。支持单工具快速触发、对话式交互模式、离线先验知识回退。

---

## 何时使用

| 用 | 不用 |
|----|------|
| 复杂社会/经济/制度问题 | 简单事实查询（"为什么天是蓝的"） |
| 涉及多利益群体、系统性矛盾 | 单一领域、可一句话回答的问题 |
| 需要跨学科视角的问题 | 纯技术/代码/数学问题 |
| "深度分析"、"多角度"、"结构性" | "总结一下"、"翻译"、"今天天气" |

**复杂度自判**：Clear/Complicated 域会自动降级到 lite 模式（2-3透镜，仅执行摘要）。Complex/Chaotic 域才展开完整框架。

---

## 快速开始

```
用户：深度分析一下为什么中国劳动法执行这么难

→ 触发守卫：识别为 Governance/Compliance 问题
→ 复杂度：Complex
→ 搜索事实 → 选 6-7 透镜（含反惯性强制人文透镜）
→ 应用 2-3 工具（不对称检测+激励映射+路径依赖）
→ 元认知自检 → 输出执行摘要
```

---

## 配置

编辑 `config.yaml` 控制模块加载：

```yaml
depth:
  default: Standard          # Focused | Standard | Comprehensive
  auto_degrade_to_lite: true # Clear/Complicated 自动降级

extensions:
  batch_analysis:    true    # 批处理+多问题分流
  exit_protocols:    true    # 降级协议（"说人话"→折叠模式）
  layered_protocol:  true    # L1→L2→L3 认知递进
  trauma_sensitive:  true    # 创伤话题特殊处理
  interactive:       true    # 对话式分析模式
  offline_fallback:  true    # 无搜索时的先验知识框架
```

**预设方案**（取消注释即可激活）：

- **轻量**：关 batch/layered/trauma/interactive，仅保留核心+退出+离线
- **速查**：全关，仅核心框架

---

## 渐进式架构

```
Clear/Complicated 域 → lite 模式（2-3透镜，自动降级）
Complex 域          → 核心 + 按需扩展（5-9透镜）
Chaotic 域          → 核心 + 全部扩展
```

核心文件 `SKILL.md`（607行）始终加载。6 个扩展按触发条件按需加载。默认全家桶全部启用。

---

## 输出格式

**执行摘要**（必出）：
```
## 执行摘要：[主题]
### 核心发现
### 🔗 多镜共识
### ⚠️ 置信度说明
### 关键分歧
### 分层影响（系统/制度/个体 × 短期/中期/长期）
### 🎯 最高杠杆干预
```

**降级路径**：
```
完整分析 → 说人话 → 折叠模式（4项）→ 再简单点 → 超折叠（3句话）
```

---

## 透镜速查

| 类别 | 透镜 | 何时用 |
|------|------|--------|
| 基础 | 认识论、系统论、历史、时间性 | 必选 1-2 |
| 人文 | 心理学、社会学、人类学、情感 | 必选 1-2（反惯性强制） |
| 结构 | 经济学、政治学、制度分析、技术研究、地理 | 必选 1-3 |

**强制规则**：经济/政策话题不得跳过人文透镜。当前事件必须包含历史透镜。

---

## 目录

```
deep-structural-analysis/
├── SKILL.md              核心框架（608行）
├── config.yaml           模块配置（默认全家桶）
├── README.md             使用须知
├── lite/SKILL.md         v2.0.0  精简版（渐进式深度入口）
├── extensions/           按需扩展（6个, 250行）
│   ├── trauma-sensitive.md     v1.0.3  创伤敏感五约束+过度抽象化
│   ├── exit-protocols.md       v1.0.1  三级降级+拒绝处理+架构限制
│   ├── batch-analysis.md       v1.0.1  批处理协议+多问题分流
│   ├── offline-fallback.md     v1.1.1  离线先验知识框架(10框架)
│   ├── interactive.md          v1.0.1  对话式分析模式
│   └── layered-protocol.md     v1.0.1  L1→L2→L3认知递进
├── docs/                 文档
│   ├── SKILL构建全记录.md
│   ├── UPDATELOG.md
│   └── 极限测试全集.md（10道压力测试）
└── backups/              备份
    ├── SKILL.v1.12.0.backup.md
    └── SKILL.v1.12.1.latest.backup.md
```

---

## 回滚

```powershell
# 恢复当前最新备份
Copy-Item backups\SKILL.v1.12.1.latest.backup.md SKILL.md

# 恢复 v1.12.0（精简前完整版, 847行）
Copy-Item backups\SKILL.v1.12.0.backup.md SKILL.md
```
