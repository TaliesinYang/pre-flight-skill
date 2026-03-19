# pre-flight

[English](README.md) | [中文](README.zh-CN.md)

A Claude Code skill that assesses your readiness before starting new features.
Complements [Superpowers](https://github.com/obra/superpowers) — runs **before** brainstorming to ensure the right tools are in place.

## What it does

When you're about to start a new feature or non-trivial task, `pre-flight` answers three questions:

1. **Do I already have the skills/tools for this?** — Scans your installed skills, plugins, and MCP servers
2. **Has the community built something I can use?** — Searches skill marketplaces and GitHub
3. **Is it safe to use?** — Evaluates every community resource with security-first criteria (stars, maintenance, author reputation)

## The gap it fills

```
         ❌ Gap (before)              ✅ Superpowers (already great)
┌────────────────────────┐    ┌─────────────────────────────────────┐
│ Can I do this?         │ →  │ brainstorming → plan → implement →  │
│ What already exists?   │    │ TDD → code review → branch finish   │
│ Is it safe to install? │    └─────────────────────────────────────┘
└────────────────────────┘
```

## Install

```bash
# Personal skill (all projects)
git clone https://github.com/TaliesinYang/pre-flight-skill ~/.claude/skills/pre-flight

# Or project-scoped
git clone https://github.com/TaliesinYang/pre-flight-skill .claude/skills/pre-flight
```

## Usage

```bash
/pre-flight implement OAuth2 authentication
/pre-flight add PDF export feature
/pre-flight build a real-time notification system
```

Or just describe what you want to build — Claude will auto-trigger it when relevant.

## Output

A structured Pre-Flight Report:

- **Environment Readiness** — which skills/tools/code you already have
- **Community Resources** — skills, plugins, repos found, each with a trust rating
- **Recommended Path** — ready to go, install something first, or build from scratch
- **Gaps & Risks** — what's missing and any security concerns

Then hands off to `superpowers:brainstorming` (or whatever workflow you prefer).

## Security-First Evaluation

Every community resource is rated on a 4-tier trust system:

| Tier | Label | Meaning |
|------|-------|---------|
| T1 | 🟢 Trusted | Official Anthropic or 1k+ stars + known org |
| T2 | 🟡 Verified | 100+ stars + identifiable author |
| T3 | 🟠 Community | <100 stars but readable, clean code |
| T4 | 🔴 Unverified | Anonymous, no stars, or security concern |

Hard reject signals: obfuscated code, credential harvesting, overly broad permissions, prompt injection patterns.

See [references/evaluation-criteria.md](references/evaluation-criteria.md) for the full rubric.

## Enhanced search (optional)

Works offline with a bundled skill registry. For richer results, install any web search MCP:

- Perplexity MCP
- WebSearch (built-in with Claude Max)
- Any MCP providing web search

## Design principles

- **Complementary** — never replaces Superpowers or any other skill
- **Tool-agnostic** — uses whatever search tools you have, works offline too
- **Read-only** — never installs or executes community code; decisions are yours
- **Security-first** — when in doubt, flags it 🔴

## Structure

```
pre-flight/
├── SKILL.md                          # Core instructions (~120 lines)
└── references/
    ├── evaluation-criteria.md        # Security evaluation rubric
    └── skill-registry.md             # Offline fallback index
```

## License

MIT
