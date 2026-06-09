<div align="center">

# GitHub Publisher Skill

<p align="center">
  <img src="assets/demo.gif" alt="GitHub Publisher Demo" />
</p>

> *Auto-generate professional GitHub documentation for any Claude Skill — one command to publish.*

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Agent Skills](https://img.shields.io/badge/Agent%20Skills-Standard-green)](https://agentskills.io)
[![skills.sh](https://img.shields.io/badge/skills.sh-Compatible-blue)](https://skills.sh)
[![Multi-Runtime](https://img.shields.io/badge/Runtime-Claude%20Code%20·%20Codex%20·%20Cursor%20·%20Hermes-blueviolet)](#installation)

<br>

**Every time you create a new Skill, one command generates complete, open-source-community-standard documentation.**

<sub>Based on the open [Agent Skills](https://agentskills.io) protocol. Works in Claude Code, Codex, Cursor, OpenClaw, Hermes Agent, CodeBuddy, Workbuddy, Gemini CLI, OpenCode, and 50+ compatible runtimes.</sub>

<br>

[Demo](#demo) · [Installation](#installation) · [Usage](#usage) · [How It Works](#how-it-works) · [Project Structure](#project-structure)

</div>

---

## Demo

```
User      ❯ /publish skills/my-new-skill

GitHub    ❯ Reading my-new-skill...
Publisher ❯ ✅ Read SKILL.md, scripts/, references/
          ❯ 📝 Generating professional README...
          ❯ ✅ README generation complete
          ❯ 🔍 Quality check passed
          ❯ 📤 Committing to GitHub...

User      ❯ yes

GitHub    ❯ 🎉 Published successfully!
Publisher ❯ https://github.com/JUJING-DEEP/my-new-skill
```

**Auto-generated documentation includes:**

- Project title + badge row (Stars / License / Version)
- One-line precise description
- Core features (3-5 items with details)
- Quick start (running in 5 minutes)
- Detailed usage instructions
- Configuration table
- At least 3 usage examples
- Project structure tree
- Contributing guide
- MIT License

---

## How It Works

```
You create a new Skill
         ↓
/publish command triggers
         ↓
┌──────────────────────────────────────┐
│       GitHub Publisher Skill          │
│  1. Read Skill code (SKILL.md etc.)   │
│  2. Invoke documentation generator    │
│  3. Polish to high-star style        │
│  4. Write README.md                  │
│  5. git add / commit / push          │
└──────────────────────────────────────┘
         ↓
GitHub Repository (complete professional docs)
```

### Phase 1: Information Collection

1. Confirm target Skill path
2. Read files:
   - `SKILL.md` or main logic file
   - All files under `references/`
   - All files under `scripts/`
   - Existing `README.md` (if any)
3. Extract key info:
   - Skill name and core functionality
   - Input/output format
   - Dependencies and compatibility
   - Use cases and trigger conditions

### Phase 2: Generate README

Required sections (in order):

1. **Project Title + Badges**
2. **One-Line Description**
3. **Demo GIF/Screenshot Placeholder**
4. **Core Features** (3-5 points)
5. **Quick Start**
6. **Detailed Usage**
7. **Configuration** (table format)
8. **Usage Examples** (at least 3)
9. **Project Structure**
10. **Contributing Guide**
11. **License**

### Phase 3: Quality Check

- [ ] All code blocks have language labels
- [ ] Installation steps are followable
- [ ] No "TODO" or blank placeholders
- [ ] Every row in config table has default value

### Phase 4: Git Publish

```bash
cd <skill-path>
git add README.md
git commit -m "docs: auto-generate README"
git push origin main
```

---

## Installation

GitHub Publisher is an [Agent Skill](https://agentskills.io) protocol-based skill that runs in any skills-compatible AI agent runtime.

### Method 1: One-Line Command (Recommended, Cross-Runtime)

Open your agent (Claude Code, Codex, Cursor, OpenClaw, Hermes, CodeBuddy, Workbuddy, Gemini CLI, OpenCode, etc.) and tell it:

```
Install this skill for me: https://github.com/JUJING-DEEP/github-publisher
```

Or use the universal CLI installer ([vercel-labs/skills](https://github.com/vercel-labs/skills), supports 55+ runtimes):

```bash
npx skills add JUJING-DEEP/github-publisher
```

It auto-detects your current runtime and places the skill in the correct directory. Use `-a claude-code` / `-a codex` / `-a cursor` / `-a openclaw` to specify.

### Method 2: Manual Installation

<details>
<summary>Show skills directories for each runtime</summary>

| Runtime | Installation Path |
|---|---|
| Claude Code | `~/.claude/skills/github-publisher/` |
| Codex CLI | `~/.codex/skills/github-publisher/` |
| Cursor | `~/.cursor/skills/github-publisher/` |
| OpenClaw | `~/.openclaw/workspace/skills/github-publisher/` |
| Hermes Agent | Run `tools/install_hermes_skill.py` |
| Other runtimes | Clone to that runtime's `skills/` directory |

```bash
git clone https://github.com/JUJING-DEEP/github-publisher <path from table above>
```

</details>

### Method 3: Use as Reference

Even if your runtime doesn't support automatic Agent Skills loading, you can paste the content of `SKILL.md` directly into the conversation — it's essentially markdown + YAML frontmatter.

---

## Usage

### Basic Command

```
/publish
```

### With Skill Path

```
/publish skills/my-new-skill
```

### Trigger from Other Agents

```
Publish this Skill to GitHub for me: skills/my-data-analyzer
```

### Complete Workflow

```
1. /publish [optional: Skill path]
2. GitHub Publisher auto-reads all Skill files
3. Generate professional README preview
4. Show preview, ask if satisfied
5. Confirm and execute git add / commit / push
6. Return GitHub link
```

---

## Project Structure

```
github-publisher/
├── SKILL.md                         # Core Skill logic
├── README.md                        # This file (Chinese)
├── README_EN.md                     # English version
├── LICENSE                          # MIT License
├── assets/
│   └── demo.gif                     # Demo animation
├── references/
│   ├── readme-template.md            # High-star README template
│   └── style-guide.md                # Writing style guide
└── .claude/
    └── commands/
        └── publish.md              # /publish command definition
```

---

## Writing Standards

The generated README follows these standards:

### Title Conventions

- Start with emoji: `🚀 Quick Start`, `📋 Configuration`, `💡 Usage Examples`
- Keep titles concise

### Language Style

- Professional but not stiff
- Every sentence carries information
- English primary, Chinese secondary

### Code Block Conventions

- All code blocks must have language labels
- Code examples must be runnable
- Add comments on key lines

### List Conventions

**Good lists:**
- 3 preset themes: dark, light, high-contrast
- Supports 12 output formats: PDF, Markdown, HTML, etc.

**Bad lists:**
- Powerful features
- Easy to use

### Configuration Tables

| Parameter | Type | Default | Description |
|------|------|---------|-------------|
| model | string | claude-sonnet-4 | AI model to use |
| language | string | zh | Output language |

---

## Configure Your GitHub Token

To let the Skill push code to GitHub, configure a GitHub Personal Access Token:

### Claude Code

1. Create GitHub Personal Access Token:
   - Visit https://github.com/settings/tokens
   - Click "Generate new token (classic)"
   - Select `repo` permission

2. Configure credentials:

**Method A: Add to Git remote URL**
```bash
git remote add origin https://YOUR_TOKEN@github.com/JUJING-DEEP/repo.git
```

**Method B: Use gh auth**
```bash
gh auth login
```

### Other Runtimes

Refer to each runtime's documentation for GitHub credential configuration. Usually set `github_token` in config file or `GITHUB_TOKEN` environment variable.

---

## Notes

1. **If Skill already has README**: Compare differences, update only missing parts
2. **If git push fails**: Check remote config and Token permissions
3. **Generated document tone**: Professional but human-written feeling
4. **Information source blacklist**: Zhihu, WeChat public accounts excluded

---

## Behind the Story

Writing README after creating a new Skill is the most tedious repetitive work. GitHub Publisher Skill automates this — one command gives you:

- ✅ Complete feature introduction
- ✅ Runnable code examples
- ✅ Clear configuration notes
- ✅ Standard directory structure documentation
- ✅ International open-source community standard format

**One command. Time saved for creating real value.**

---

## About Author

**JUJING-DEEP** — AI Native Developer

| Platform | Link |
|------|------|
| 𝕏 Twitter | [@JUJING_DEEP](https://x.com/JUJING_DEEP) |
| GitHub | [JUJING-DEEP](https://github.com/JUJING-DEEP) |

## License

MIT — Use freely, modify freely, distribute freely.

---

<div align="center">

**Creating a Skill is the start.<br>Auto-generating documentation is the standard.<br>Use GitHub Publisher for professional Skill publishing.**

<br>

MIT License © [JUJING-DEEP](https://github.com/JUJING-DEEP)

</div>
