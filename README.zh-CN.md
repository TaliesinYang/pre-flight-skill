# pre-flight

[English](README.md) | [中文](README.zh-CN.md)

一个 Claude Code 技能，在开始新功能前评估你的准备状态。
与 [Superpowers](https://github.com/obra/superpowers) 互补 — 在头脑风暴**之前**运行，确保工具就位。

## 它做什么

当你准备开始新功能或非简单任务时，`pre-flight` 回答三个问题：

1. **我已有的技能/工具够不够？** — 扫描已安装的 skills、plugins 和 MCP servers
2. **社区有没有现成的？** — 搜索技能市场和 GitHub
3. **安全吗？** — 用安全优先标准评估每个社区资源（stars、维护状态、作者声誉）

## 它填补的空白

```
         ❌ 缺失（之前）               ✅ Superpowers（已经很棒）
┌────────────────────────┐    ┌─────────────────────────────────────┐
│ 我能做这个吗？          │ →  │ 头脑风暴 → 计划 → 实现 →            │
│ 有现成的吗？            │    │ TDD → 代码审查 → 分支完成            │
│ 安装它安全吗？          │    └─────────────────────────────────────┘
└────────────────────────┘
```

## 安装

```bash
# 个人技能（所有项目可用）
git clone https://github.com/TaliesinYang/pre-flight-skill ~/.claude/skills/pre-flight

# 或项目级别
git clone https://github.com/TaliesinYang/pre-flight-skill .claude/skills/pre-flight
```

## 使用

```bash
/pre-flight 实现 OAuth2 认证
/pre-flight 添加 PDF 导出功能
/pre-flight 构建实时通知系统
```

也可以直接描述你要做什么 — Claude 会在相关时自动触发。

## 输出

结构化的 Pre-Flight 报告：

- **环境准备度** — 你已有哪些 skills/工具/代码
- **社区资源** — 找到的 skills、plugins、仓库，每个都有信任评级
- **推荐路径** — 直接开始、先安装某些东西、还是从零构建
- **缺口与风险** — 缺什么以及安全顾虑

然后交接给 `superpowers:brainstorming`（或你偏好的工作流）。

## 安全优先评估

每个社区资源按 4 级信任体系评级：

| 等级 | 标签 | 含义 |
|------|------|------|
| T1 | 🟢 可信 | 官方 Anthropic 或 1k+ stars + 知名组织 |
| T2 | 🟡 已验证 | 100+ stars + 可识别作者 |
| T3 | 🟠 社区 | <100 stars 但代码可读、干净 |
| T4 | 🔴 未验证 | 匿名、无 stars 或存在安全疑虑 |

硬性拒绝信号：混淆代码、凭证收集、过宽权限、提示注入模式。

完整评估标准见 [references/evaluation-criteria.md](references/evaluation-criteria.md)。

## 增强搜索（可选）

自带离线技能索引，无需网络即可工作。安装任意搜索 MCP 可获得更丰富结果：

- Perplexity MCP
- WebSearch（Claude Max 内置）
- 任何提供网络搜索的 MCP

## 设计原则

- **互补** — 不替代 Superpowers 或任何其他技能
- **工具无关** — 使用你有的任何搜索工具，也支持离线
- **只读** — 不安装不执行社区代码，决定权在你
- **安全优先** — 有疑虑就标 🔴

## 结构

```
pre-flight/
├── SKILL.md                          # 核心指令 (~120 行)
└── references/
    ├── evaluation-criteria.md        # 安全评估标准
    └── skill-registry.md             # 离线备用索引
```

## 许可证

MIT
