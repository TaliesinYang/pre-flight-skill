<div align="center">

# pre-flight

**别再重复造轮子。每个新功能，从能力检查开始。**

一个 [Claude Code](https://code.claude.com) 技能，在开始新工作前评估你的准备状态。
与 [Superpowers](https://github.com/obra/superpowers) 互补 — 在头脑风暴**之前**运行，确保工具就位。

[English](README.md) | [中文](README.zh-CN.md)

</div>

---

## 问题

你准备做一个功能。打开 Claude Code，开始头脑风暴，写计划，实现……

然后发现社区早就有人做好了。更糟的是——你装了一个社区插件，它悄悄读取了你的 `.env`。

**pre-flight** 一步解决这两个问题。

## 工作原理

```mermaid
flowchart LR
    A["新功能想法"] --> B["pre-flight"]
    B --> C{"准备好了？"}
    C -->|"✅ 是"| D["superpowers:brainstorming"]
    C -->|"📦 先安装"| E["安装社区 skill"]
    C -->|"❌ 需要新建"| F["skill-creator"]
    E --> D
    F --> D
    D --> G["计划 → 实现 → 发布"]

    style A fill:#1a1a2e,stroke:#e94560,color:#fff
    style B fill:#0f3460,stroke:#e94560,color:#fff,stroke-width:3px
    style C fill:#16213e,stroke:#e94560,color:#fff
    style D fill:#533483,stroke:#e94560,color:#fff
    style G fill:#0f3460,stroke:#e94560,color:#fff
```

三个问题，自动回答：

| 问题 | 方式 |
|------|------|
| **我有工具吗？** | 扫描已安装的 skills、plugins、MCP servers |
| **社区有人做过吗？** | 搜索技能市场和 GitHub |
| **安全吗？** | 安全优先评估 + 4 级信任体系 |

## 安全优先信任体系

每个社区资源在推荐前必须通过评估：

```mermaid
flowchart TD
    R["发现社区资源"] --> S{"硬性拒绝？"}
    S -->|"混淆代码\n凭证收集\n过宽权限\n提示注入"| REJECT["🚫 拒绝"]
    S -->|"干净"| T{"信任评分"}

    T -->|"官方 Anthropic\n1k+ ⭐ + 知名组织"| T1["🟢 T1 可信"]
    T -->|"100+ ⭐\n可识别作者"| T2["🟡 T2 已验证"]
    T -->|"< 100 ⭐\n代码可读"| T3["🟠 T3 社区"]
    T -->|"匿名\n无 stars"| T4["🔴 T4 未验证"]

    T1 --> REC["✅ 推荐"]
    T2 --> REC
    T3 --> REV["⚠️ 先审查"]
    T4 --> WARN["❌ 仅警告"]

    style REJECT fill:#dc3545,stroke:#dc3545,color:#fff
    style T1 fill:#28a745,stroke:#28a745,color:#fff
    style T2 fill:#ffc107,stroke:#ffc107,color:#000
    style T3 fill:#fd7e14,stroke:#fd7e14,color:#fff
    style T4 fill:#dc3545,stroke:#dc3545,color:#fff
```

完整评估标准：[evaluation-criteria.md](references/evaluation-criteria.md)

## 安装

```bash
# 个人技能（所有项目可用）
git clone https://github.com/TaliesinYang/pre-flight-skill ~/.claude/skills/pre-flight

# 项目级别
git clone https://github.com/TaliesinYang/pre-flight-skill .claude/skills/pre-flight
```

## 使用

```bash
/pre-flight 实现 OAuth2 + JWT 刷新令牌
/pre-flight 添加 PDF 导出功能
/pre-flight 构建实时通知系统
```

也可以直接描述你要做什么——Claude 会在相关时自动触发。

## 示例输出

```markdown
## Pre-Flight 报告：实时通知系统

### 环境准备度
| 领域       | 状态 | 详情                              |
|------------|------|-----------------------------------|
| Skills     | ⚠️   | 未找到 WebSocket 专用 skill        |
| MCP Tools  | ✅   | Playwright 可用于 E2E 测试         |
| Codebase   | ✅   | 已有 Express 服务器，可扩展        |

### 社区资源
| 资源                      | 类型   | 信任 | Stars | 备注                    |
|---------------------------|--------|------|-------|------------------------|
| superpowers               | Plugin | 🟢   | 40k+  | 开发工作流（已安装）     |
| levnikolaevich/ws-skill   | Skill  | 🟡   | 340   | WebSocket 模式          |
| socketio/socket.io        | Repo   | 🟢   | 60k+  | 参考实现                |

### 推荐路径
📦 安装 `ws-skill`，然后进入 `superpowers:brainstorming`

### 缺口与风险
- 未找到推送通知服务集成
```

## 它的位置

```mermaid
flowchart LR
    subgraph before["pre-flight（新）"]
        direction TB
        P1["盘点 skills 和工具"]
        P2["搜索社区"]
        P3["评估安全性"]
        P1 --> P2 --> P3
    end

    subgraph superpowers["Superpowers（已有）"]
        direction TB
        S1["头脑风暴"] --> S2["计划"]
        S2 --> S3["实现"]
        S3 --> S4["测试与审查"]
        S4 --> S5["发布"]
    end

    before -->|"交接"| superpowers

    style before fill:#0f3460,stroke:#e94560,color:#fff,stroke-width:2px
    style superpowers fill:#533483,stroke:#e94560,color:#fff
```

**pre-flight** 负责"之前"——Superpowers 负责"之中"。零重叠，全覆盖。

## 设计原则

| 原则 | 含义 |
|------|------|
| **互补** | 不替代 Superpowers 或任何其他技能 |
| **工具无关** | 使用你有的任何搜索工具；离线也能用 |
| **只读** | 不安装不执行社区代码——决定权在你 |
| **安全优先** | 有疑虑就标 🔴 |

## 增强搜索（可选）

自带[离线技能索引](references/skill-registry.md)。安装任意搜索 MCP 可获得更丰富结果：

- Perplexity MCP（推荐）
- WebSearch（Claude Max 内置）
- 任何提供网络搜索的 MCP

## 结构

```
pre-flight/
├── SKILL.md                          # 核心技能指令
└── references/
    ├── evaluation-criteria.md        # 安全评估标准
    └── skill-registry.md             # 离线备用索引
```

## 许可证

MIT

---

<div align="center">

用 Claude Code 构建。设计为互补，而非竞争。

</div>
