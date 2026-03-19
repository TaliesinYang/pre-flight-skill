# Offline Skill & Resource Registry

Curated index of high-quality Claude Code skills and resources.
Use as fallback when no web search tool is available.

Last updated: 2026-03-19

## Skill Marketplaces & Registries (search here first)

| Registry | URL | Notes |
|----------|-----|-------|
| Anthropic Official | `anthropics/claude-plugins-official` | T1, built-in marketplace |
| Claude Code Plugins | `anthropics/claude-code` (plugins dir) | T1, official |
| Superpowers | `obra/superpowers-marketplace` | T2, 40k+ stars, dev workflow |
| SkillsMP | skillsmp.com | Community marketplace with AI search |
| SkillHub | skillhub.club | Community skill browser |
| ClaudeSkills | claudeskills.info | Community discovery platform |

## Curated Skill Collections (GitHub)

| Repo | Stars | Focus |
|------|-------|-------|
| travisvn/awesome-claude-skills | High | Curated list across categories |
| alirezarezvani/claude-skills | High | 192+ skills, engineering to marketing |
| levnikolaevich/claude-code-skills | High | 84 skills, full Agile lifecycle |
| abubakarsiddik31/claude-skills-collection | Medium | Mixed official + community |
| Jeffallan/claude-skills | Medium | 66 full-stack dev skills |

## Skills by Category

### Development Workflow
| Skill/Plugin | Source | Trust | Description |
|-------------|--------|-------|-------------|
| superpowers | obra/superpowers-marketplace | 🟢 T1 | Complete dev lifecycle: brainstorm → plan → implement → review |
| full-development-workflow | levnikolaevich/claude-code-skills | 🟡 T2 | 84 Agile skills with Linear integration |

### Security & Auditing
| Skill/Plugin | Source | Trust | Description |
|-------------|--------|-------|-------------|
| trail-of-bits/skills | GitHub | 🟢 T1 | Security research, vuln detection, audit workflows |
| claude-bug-bounty | shuvonsec/claude-bug-bounty | 🟠 T3 | Bug bounty hunting workflows |

### Frontend & Design
| Skill/Plugin | Source | Trust | Description |
|-------------|--------|-------|-------------|
| frontend-design | claude-plugins-official | 🟢 T1 | Production-grade UI generation |
| ui-ux-pro-max | nextlevelbuilder/ui-ux-pro-max-skill | 🟡 T2 | Advanced UI/UX design patterns |

### DevOps & Infrastructure
| Skill/Plugin | Source | Trust | Description |
|-------------|--------|-------|-------------|
| claude-code-docker-skill | wrsmith108 | 🟠 T3 | Container-based development |
| agent-sandbox-skill | community | 🟠 T3 | Isolated cloud sandboxes for testing |

### Documentation & Writing
| Skill/Plugin | Source | Trust | Description |
|-------------|--------|-------|-------------|
| elements-of-style | superpowers-marketplace | 🟡 T2 | Writing quality guidelines |

### Data & API
| Skill/Plugin | Source | Trust | Description |
|-------------|--------|-------|-------------|
| swift-lsp | claude-plugins-official | 🟢 T1 | Swift language server integration |

## How to Install from Marketplace

```bash
# Add a marketplace (one-time)
/plugin marketplace add owner/repo

# Install a plugin
/plugin install plugin-name@marketplace-name

# Update plugins
/plugin update plugin-name
```

## How to Install Standalone Skills

```bash
# Clone to personal skills (available everywhere)
git clone https://github.com/author/skill-repo ~/.claude/skills/skill-name

# Or clone to project skills (project-scoped)
git clone https://github.com/author/skill-repo .claude/skills/skill-name
```

## Contributing to This Registry

This file is manually curated. To update:
1. Verify the resource still exists and is maintained
2. Evaluate against criteria in `evaluation-criteria.md`
3. Assign appropriate trust tier
4. Add to the relevant category
