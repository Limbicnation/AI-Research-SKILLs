# AGENTS.md - AI Research Engineering Skills Library

This file provides essential guidance for AI coding agents working with the AI Research Engineering Skills repository.

## Project Overview

**AI Research Engineering Skills Library** is the most comprehensive open-source library of AI research engineering skills for AI agents. It provides 83 expert-level skills across 20 categories, enabling AI agents to autonomously conduct AI research experiments—from hypothesis to experimental verification.

**Key Facts:**
- **83 Skills** covering the full AI research lifecycle
- **20 Categories** from model architecture to paper writing
- **~130,000 lines** of documentation (SKILL.md + references)
- **MIT License** (Copyright 2025 Orchestra Research)
- **Primary Language**: English
- **Repository**: https://github.com/Orchestra-Research/AI-research-SKILLs

## Project Mission

Provide the layer of **Engineering Ability** that enables coding agents to write and conduct AI research experiments, including:
- Preparing datasets
- Executing training pipelines
- Deploying models
- Building AI agents

## Repository Structure

```
AI-research-SKILLs/
├── README.md                    # Project overview and all skills listing
├── CONTRIBUTING.md              # Complete contribution guidelines
├── CLAUDE.md                    # Claude Code specific guidance
├── LICENSE                      # MIT License
├── package.json                 # Root package metadata
├── .gitignore                   # Git ignore patterns
│
├── 01-model-architecture/       # 5 skills: LitGPT, Mamba, NanoGPT, RWKV, TorchTitan
├── 02-tokenization/             # 2 skills: HuggingFace Tokenizers, SentencePiece
├── 03-fine-tuning/              # 4 skills: Axolotl, LLaMA-Factory, PEFT, Unsloth
├── 04-mechanistic-interpretability/  # 4 skills: TransformerLens, SAELens, pyvene, nnsight
├── 05-data-processing/          # 2 skills: Ray Data, NeMo Curator
├── 06-post-training/            # 8 skills: TRL, GRPO, OpenRLHF, SimPO, verl, slime, miles, torchforge
├── 07-safety-alignment/         # 4 skills: Constitutional AI, LlamaGuard, NeMo Guardrails, Prompt Guard
├── 08-distributed-training/     # 6 skills: DeepSpeed, FSDP, Accelerate, Megatron-Core, Lightning, Ray Train
├── 09-infrastructure/           # 3 skills: Modal, Lambda Labs, SkyPilot
├── 10-optimization/             # 6 skills: Flash Attention, bitsandbytes, GPTQ, AWQ, HQQ, GGUF
├── 11-evaluation/               # 3 skills: lm-eval-harness, BigCode, NeMo Evaluator
├── 12-inference-serving/        # 4 skills: vLLM, TensorRT-LLM, llama.cpp, SGLang
├── 13-mlops/                    # 3 skills: Weights & Biases, MLflow, TensorBoard
├── 14-agents/                   # 4 skills: LangChain, LlamaIndex, CrewAI, AutoGPT
├── 15-rag/                      # 5 skills: Chroma, FAISS, Pinecone, Qdrant, Sentence Transformers
├── 16-prompt-engineering/       # 4 skills: DSPy, Instructor, Guidance, Outlines
├── 17-observability/            # 2 skills: LangSmith, Phoenix
├── 18-multimodal/               # 7 skills: CLIP, Whisper, LLaVA, BLIP-2, SAM, Stable Diffusion, AudioCraft
├── 19-emerging-techniques/      # 6 skills: MoE, Model Merging, Long Context, Speculative Decoding, Distillation, Pruning
├── 20-ml-paper-writing/         # 1 skill: ML Paper Writing with LaTeX templates
│
├── packages/ai-research-skills/ # npm package for one-command installation
│   ├── package.json             # npm package config (version 1.3.6)
│   ├── bin/cli.js               # CLI entry point
│   └── src/                     # Source code
│       ├── index.js             # Main logic
│       ├── agents.js            # Agent detection
│       ├── installer.js         # Installation logic
│       ├── prompts.js           # Interactive prompts
│       └── ascii.js             # ASCII art/UI
│
├── .claude-plugin/
│   └── marketplace.json         # Claude Code marketplace configuration
│
├── .github/workflows/
│   ├── sync-skills.yml          # Auto-sync skills to Orchestra marketplace
│   ├── publish-npm.yml          # Auto-publish npm package
│   └── claude.yml               # Claude Code GitHub Action
│
├── docs/
│   ├── ROADMAP.md               # Development roadmap
│   ├── SKILL_TEMPLATE.md        # Template for new skills
│   ├── SKILL_CREATION_GUIDE.md  # Guide for creating skills
│   └── assets/                  # Documentation assets
│
├── demos/                       # Demo gallery with example projects
├── dev_data/                    # Development data and metadata
└── anthropic_official_docs/     # Anthropic's best practices for skills
```

## Skill Structure

Each skill follows a standardized battle-tested format:

```
skill-name/
├── SKILL.md                     # Main guidance (200-600 lines with YAML frontmatter)
├── references/                  # Deep documentation (300KB+ target)
│   ├── README.md               # From official docs/GitHub
│   ├── api.md                  # API reference
│   ├── tutorials.md            # Step-by-step guides
│   ├── issues.md               # Real GitHub issues & solutions
│   └── releases.md             # Version history
├── scripts/                     # Helper scripts (optional)
├── templates/                   # Code templates (optional)
├── examples/                    # Example implementations (optional)
└── assets/                      # Templates & examples (optional)
```

### SKILL.md Format (CRITICAL)

Every SKILL.md **MUST** include YAML frontmatter:

```yaml
---
name: skill-name-here              # kebab-case, no quotes, gerund form preferred
description: Third-person description of what AND when to use this skill
version: 1.0.0                     # Semantic versioning
author: Orchestra Research         # Standard author
license: MIT                       # Standard license
tags: [Tag One, Tag Two, GRPO]    # Title Case, UPPERCASE for acronyms
dependencies: [pkg>=1.0.0]         # Optional, with version constraints
---
```

**Critical Rules:**
- `name`: Use gerund form (e.g., `serving-llms`, `grpo-rl-training`)
- `description`: Third person, include WHAT and WHEN to use
- `tags`: Title Case for words, UPPERCASE for acronyms (GRPO, TRL, RLHF)
- No quotes around field values (except in arrays)
- SKILL.md body: **200-500 lines maximum**

### Quality Standards

**Core Requirements:**
- ✅ YAML frontmatter with all required fields
- ✅ 200-500 lines focused guidance
- ✅ Progressive disclosure (overview in SKILL.md, details in references/)
- ✅ Workflows with copy-paste checklists
- ✅ "When to use vs alternatives" section
- ✅ Common issues section with solutions
- ✅ Code examples with language detection (```python, ```bash)
- ✅ References ONE level deep from SKILL.md (no nested references)

**Gold Standard** (emulate `06-post-training/grpo-rl-training/`):
- 2-3 complete workflows with step-by-step checklists
- Reference files for advanced topics
- Feedback loops for quality-critical operations
- Real GitHub issues with solutions
- 300KB+ documentation in references/

**NOT Acceptable:**
- ❌ SKILL.md over 500 lines
- ❌ First-person descriptions ("I can help you...")
- ❌ Vague skill names ("helper", "utils")
- ❌ Nested references (SKILL.md → ref1.md → ref2.md)
- ❌ Missing workflows with checklists

## Technology Stack

### Core Technologies
- **Markdown**: All documentation is in Markdown format
- **YAML**: Frontmatter for skill metadata
- **JSON**: Configuration files (marketplace.json, package.json)

### npm Package (Node.js 18+)
```json
{
  "dependencies": {
    "chalk": "^5.3.0",         // Terminal styling
    "inquirer": "^9.2.12",      // Interactive prompts
    "ora": "^8.0.1"             // Loading spinners
  }
}
```

### CI/CD (GitHub Actions)
- **sync-skills.yml**: Auto-syncs skills to Orchestra marketplace on push to main
- **publish-npm.yml**: Auto-publishes npm package when version changes
- **claude.yml**: Claude Code GitHub Action for issue/PR automation

## Build and Development Commands

### npm Package Development
```bash
cd packages/ai-research-skills

# Install dependencies
npm install

# Run CLI locally
npm start
# or
node bin/cli.js

# Run tests
npm test

# Version bump (use this, not manual edits)
npm version patch   # 1.3.6 → 1.3.7
npm version minor   # 1.3.7 → 1.4.0
npm version major   # 1.4.0 → 2.0.0
```

### Skill Quality Validation
```bash
# Check YAML frontmatter exists
head -20 skill-name/SKILL.md

# Verify SKILL.md line count (target 200-500 lines)
wc -l skill-name/SKILL.md

# Check documentation size (target 300KB+)
du -sh skill-name/references/

# Verify code blocks have language tags
grep -A 1 '```' skill-name/SKILL.md | head -20

# Validate YAML frontmatter syntax
python -c "import yaml; yaml.safe_load(open('skill-name/SKILL.md').read().split('---')[1])"
```

### Global npm Installation
```bash
# Interactive installer (recommended)
npx @orchestra-research/ai-research-skills

# Direct commands
npx @orchestra-research/ai-research-skills list      # View installed skills
npx @orchestra-research/ai-research-skills update    # Update installed skills
npx @orchestra-research/ai-research-skills uninstall # Remove all skills
```

## Code Style Guidelines

### Markdown Style
- Use ATX-style headers (`#` not `===`)
- Code blocks **MUST** have language tags: ```python, ```bash
- Use `-` for unordered lists (not `*`)
- Use `1.` for ordered lists
- Wrap lines at ~100 characters for readability
- Use reference-style links for repeated URLs

### Naming Conventions
- **Skill names**: Gerund form in kebab-case (e.g., `processing-pdfs`, `serving-llms`)
- **Directory names**: lowercase with hyphens (e.g., `grpo-rl-training`)
- **Tags**: Title Case for words, UPPERCASE for acronyms
- **File names**: lowercase with hyphens (e.g., `SKILL.md`, `api-reference.md`)

### Code Examples
Always include language detection:
```python
# Good - has language tag
from transformers import AutoModel
```

NOT:
```
# Bad - no language tag
from transformers import AutoModel
```

## Testing Strategy

### Pre-Submission Checklist
Before submitting a new skill or changes:

1. **Structure Validation:**
   ```bash
   # SKILL.md exists and is well-formatted
   cat category/skill-name/SKILL.md
   
   # All reference files exist
   ls -R category/skill-name/references/
   
   # Documentation size is adequate (300KB+ target)
   du -sh category/skill-name/references/
   ```

2. **Content Validation:**
   ```bash
   # Code blocks have language tags
   grep -A 1 '```' category/skill-name/SKILL.md | head -20
   
   # No broken links (manual check)
   # Open SKILL.md and verify all [links](urls) work
   
   # Marketplace entry added and valid (if applicable)
   python3 -c "import json; json.load(open('.claude-plugin/marketplace.json'))"
   ```

3. **YAML Frontmatter Validation:**
   ```bash
   python -c "import yaml; yaml.safe_load(open('category/skill-name/SKILL.md').read().split('---')[1])"
   ```

## Deployment Process

### Auto-Sync to Orchestra Marketplace
When skills are committed to `main`, GitHub Actions automatically syncs them:

1. **Trigger**: Push to `main` branch
2. **Detection**: Workflow detects changed skill directories
3. **Extraction**: Reads metadata from SKILL.md frontmatter
4. **Packaging**: Creates ZIP of skill directory
5. **Upload**: Sends to Orchestra API endpoint
6. **Storage**: Stored in Supabase with database record

**Source Detection:**
- `author: Orchestra Research` → Source = `orchestra` (Official badge)
- `author: Other Name` → Source = `community` (Community badge)

### npm Package Publishing
- **Trigger**: Version change in `packages/ai-research-skills/package.json` on `main`
- **Auth**: OIDC trusted publishing (no tokens stored)
- **Provenance**: Signed with Sigstore for supply chain security
- **Manual**: Use `npm version` command, not manual edits

## Adding a New Skill

### Step-by-Step Process

1. **Choose Category**: Pick the appropriate numbered category (01-20)

2. **Create Directory**:
   ```bash
   mkdir -p XX-category/skill-name/references
   ```

3. **Write SKILL.md**:
   - Copy from `docs/SKILL_TEMPLATE.md`
   - Add YAML frontmatter
   - Write 200-500 lines of focused guidance
   - Include workflows with checklists

4. **Add References**:
   - Create 300KB+ documentation in `references/`
   - Include README.md (from official docs)
   - Add api.md, tutorials.md, issues.md (if applicable)

5. **Validate Quality**:
   ```bash
   # Check line count
   wc -l XX-category/skill-name/SKILL.md
   
   # Check documentation size
   du -sh XX-category/skill-name/references/
   
   # Validate YAML
   python -c "import yaml; yaml.safe_load(open('XX-category/skill-name/SKILL.md').read().split('---')[1])"
   ```

6. **Update Marketplace** (if Claude Code plugin):
   Add entry to `.claude-plugin/marketplace.json`

7. **Submit PR**:
   ```bash
   git add XX-category/skill-name/
   git commit -m "Add [Skill Name] skill
   
   - X lines of documentation
   - Y GitHub issues with solutions
   - API reference and examples included"
   git push origin add-skill-name
   ```

## Key Configuration Files

| File | Purpose |
|------|---------|
| `package.json` | Root npm metadata |
| `packages/ai-research-skills/package.json` | npm package config (v1.3.6) |
| `.claude-plugin/marketplace.json` | Claude Code marketplace entries |
| `.github/workflows/sync-skills.yml` | Auto-sync to Orchestra |
| `.github/workflows/publish-npm.yml` | Auto-publish npm package |
| `.gitignore` | Ignore patterns for Python/Node/ML artifacts |

## Important Conventions

### Progressive Disclosure Pattern
SKILL.md should link directly to reference files (one level deep):

```markdown
## Advanced Features

**API Reference**: See [references/api.md](references/api.md)
**Troubleshooting**: See [references/issues.md](references/issues.md)
```

### Documentation Philosophy
- **Quality over Quantity**: 200-500 focused lines beats 1000+ vague lines
- **Assume Intelligence**: Claude knows Python/ML basics; focus on domain expertise
- **Actionable Guidance**: Every section should enable immediate action
- **Real-World Content**: Include actual GitHub issues, performance benchmarks, troubleshooting

### Git Workflow
```bash
# Create feature branch
git checkout -b add-skill-name

# Add and commit changes
git add category/skill-name/
git commit -m "Add [Skill Name] skill

- X lines of documentation
- Y GitHub issues with solutions
- API reference and examples included"

# Push to fork and create PR
git push origin add-skill-name
```

## Security Considerations

1. **No Secrets in Code**: API keys, tokens are in GitHub Secrets only
2. **OIDC for npm**: Uses trusted publishing, no long-lived tokens
3. **License Compliance**: Individual skills may reference libraries with different licenses
4. **Content Safety**: Skills include safety/alignment category for responsible AI

## External Resources

- **Main Website**: https://www.orchestra-research.com/research-skills
- **npm Package**: https://www.npmjs.com/package/@orchestra-research/ai-research-skills
- **GitHub**: https://github.com/Orchestra-Research/AI-research-SKILLs
- **Slack Community**: https://join.slack.com/t/orchestrarese-efu1990/shared_invite
- **Twitter/X**: https://x.com/orch_research
- **LinkedIn**: https://www.linkedin.com/company/orchestra-research/

## Troubleshooting

### Common Issues

**Issue**: YAML frontmatter validation fails
```bash
# Fix: Ensure no quotes around field values (except arrays)
# Bad: name: "skill-name"
# Good: name: skill-name
```

**Issue**: SKILL.md too long (>500 lines)
```bash
# Fix: Split content into reference files
# Move detailed API docs to references/api.md
# Move tutorials to references/tutorials.md
```

**Issue**: npm publish fails in CI
```bash
# Fix: Ensure package-lock.json is in sync
npm install  # Regenerates lockfile
git add package-lock.json
git commit -m "chore: sync lockfile"
```

## Contact

- **Issues**: https://github.com/Orchestra-Research/AI-research-SKILLs/issues
- **Discussions**: https://github.com/Orchestra-Research/AI-research-SKILLs/discussions
- **Email**: zechen@orchestra-research.com

---

*Last Updated: February 2026 | Version: 0.15.0 | 83 Skills | 20 Categories*
