# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

**AI Research Engineering Skills Library** — Open-source library of 83+ AI research skills across 20 categories, enabling AI agents to autonomously conduct AI research experiments. Each skill provides expert-level guidance (200-500 lines) with real code examples, troubleshooting guides, and production-ready workflows.

**Repository**: `Orchestra-Research/AI-Research-SKILLs` (case-sensitive — matters for OIDC/npm publishing)

## Architecture

Skills are organized into numbered categories (`01-model-architecture/` through `20-ml-paper-writing/`) representing the AI research lifecycle. Each skill directory follows this structure:

```
skill-name/
├── SKILL.md          # Main guidance (200-500 lines, YAML frontmatter required)
├── references/       # Deep documentation (300KB+ target)
│   ├── README.md     # Official docs
│   ├── api.md        # API reference
│   ├── tutorials.md  # Step-by-step guides
│   ├── issues.md     # Real GitHub issues & solutions
│   └── releases.md   # Version history
├── scripts/          # Helper scripts (optional)
├── templates/        # Code templates (optional)
└── examples/         # Example implementations (optional)
```

### npm Package (`packages/ai-research-skills/`)

Interactive CLI installer for deploying skills to coding agents. ESM module, Node.js 18+.

```
packages/ai-research-skills/
├── bin/cli.js        # Entry point
├── src/
│   ├── index.js      # Main flow (menu, install, update, uninstall)
│   ├── agents.js     # Agent detection (Claude Code, OpenCode, Cursor, Codex, Gemini CLI, Qwen Code)
│   ├── installer.js  # Installation logic (symlinks to ~/.orchestra/skills/)
│   ├── prompts.js    # Interactive prompts, skill/category definitions
│   └── ascii.js      # Terminal UI (welcome screen, spinners)
└── package.json      # v1.3.6, deps: chalk, inquirer, ora
```

### Key Files

- **CONTRIBUTING.md** — Contribution guidelines and quality standards
- **docs/SKILL_TEMPLATE.md** — Copy-paste scaffold for new skills
- **docs/ROADMAP.md** — Development roadmap
- **anthropic_official_docs/** — Anthropic's official best practices for skills
- **.claude-plugin/marketplace.json** — Claude Code marketplace configuration
- **dev_data/GITHUB_SKILLS_SYNC_SETUP.md** — Detailed Orchestra sync setup

## Development Commands

### npm Package

```bash
cd packages/ai-research-skills
npm install              # Install dependencies
npm start                # Run CLI locally (or: node bin/cli.js)
npm test                 # Run tests (node --test)
npm version patch        # Bump version (always use this, not manual edits)
```

### Skill Quality Validation

```bash
# Validate YAML frontmatter syntax
python -c "import yaml; yaml.safe_load(open('SKILL.md').read().split('---')[1])"

# Check SKILL.md line count (target 200-500)
wc -l category/skill-name/SKILL.md

# Check documentation size (target 300KB+)
du -sh category/skill-name/references/
```

## SKILL.md Requirements (CRITICAL)

### YAML Frontmatter

Every SKILL.md **must** start with this frontmatter:

```yaml
---
name: skill-name-here              # kebab-case, gerund form preferred (e.g., serving-llms)
description: Third-person description of what AND when to use this skill  # No quotes, max 1024 chars
version: 1.0.0                     # Semantic versioning
author: Orchestra Research         # Standard author
license: MIT
tags: [Tag One, Tag Two, GRPO]    # Title Case for words, UPPERCASE for acronyms
dependencies: [pkg>=1.0.0]         # Optional, with version constraints
---
```

**Rules**: No quotes around field values (except in arrays). `name` must be gerund form. `description` must be third person ("Provides guidance for..."). `tags` use Title Case except acronyms (GRPO, TRL, RLHF, DPO, PPO, FSDP, MoE).

### Content Standards

**Required**:
- 200-500 lines (under 500 is critical for performance)
- Progressive disclosure: overview in SKILL.md, details in `references/` (one level deep, no nesting)
- Workflows with copy-paste checklists
- "When to use vs alternatives" section
- Common issues section with solutions
- Code blocks must have language tags (```python, ```bash)

**Gold standard**: `06-post-training/grpo-rl-training/`

**Not acceptable**: SKILL.md over 500 lines, first-person descriptions, vague names, nested references (SKILL.md -> ref1.md -> ref2.md)

## CI/CD

### Orchestra Marketplace Sync (`.github/workflows/sync-skills.yml`)

Triggers on push to `main`. Detects changed skill directories, extracts YAML frontmatter, ZIPs skill folder, uploads to Orchestra API (Supabase Storage). Author field determines badge: `"Orchestra Research"` = official, anything else = community.

**Secrets**: `ORCHESTRA_API_URL`, `ORCHESTRA_SYNC_API_KEY`

### npm Publishing (`.github/workflows/publish-npm.yml`)

Triggers when version in `packages/ai-research-skills/package.json` changes on `main`. Uses OIDC trusted publishing (no npm tokens). The trusted publisher config on npmjs.com must match repo name exactly (case-sensitive).

**Common issue**: `npm ci` fails = `package-lock.json` out of sync. Fix: `npm install` locally and commit the lockfile.

## Naming Conventions

- **Skill names**: Gerund form in kebab-case: `processing-pdfs`, `serving-llms`, `grpo-rl-training`
- **Tags**: Title Case for words, UPPERCASE for acronyms
- **Descriptions**: Third person, include what AND when to use
- **Directories**: Lowercase with hyphens within numbered categories

## Adding a New Skill

1. Create directory in appropriate category: `mkdir -p XX-category/skill-name/references`
2. Copy `docs/SKILL_TEMPLATE.md` to `skill-name/SKILL.md`
3. Write YAML frontmatter + 200-500 lines of guidance
4. Add reference documentation (target 300KB+ from official sources)
5. Validate: YAML syntax, line count, language tags on code blocks, references one level deep
6. Add entry to `.claude-plugin/marketplace.json`
7. Bump version in SKILL.md frontmatter if updating existing skill
