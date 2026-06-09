# 🎯 GitHub Publisher

<p align="center">
 <img src="demo.gif" alt="demo" width="600"/>
</p>

> Automate professional GitHub documentation generation for any Claude Skill — read code, generate README, push to GitHub in one command.

<p align="center">
 <a href="https://github.com/JUJING-DEEP/github-publisher/stargazers"><img src="https://img.shields.io/github/stars/JUJING-DEEP/github-publisher?style=flat-square"/></a>
 <a href="https://github.com/JUJING-DEEP/github-publisher/blob/main/LICENSE"><img src="https://img.shields.io/badge/license-MIT-blue?style=flat-square"/></a>
 <a href="https://github.com/JUJING-DEEP/github-publisher/releases"><img src="https://img.shields.io/badge/version-1.0.0-green?style=flat-square"/></a>
</p>

---

## 🚀 Features

- **📖 Auto README Generation** — Reads your Skill's SKILL.md, scripts/, and references/ to generate complete professional documentation
- **🏆 High-Star Project Style** — Follows best practices from top open source projects
- **✅ Quality Checklist** — Automatically validates code blocks, installation steps, and configuration tables
- **🔄 Git Automation** — Handles git add, commit, and push for one-click publishing
- **📝 Bilingual Support** — Generates documentation in both Chinese and English

## ⚡ Quick Start

```bash
# 1. Navigate to your skills repository
cd your-skills-repo

# 2. Trigger the publisher
/publish

# 3. Or specify a skill path
/publish skills/my-new-skill
```

## 📋 Usage

### Basic Command

```
/publish
```

### With Skill Path

```
/publish skills/my-new-skill
```

## 🔧 Workflow

```
You create a new Skill
         ↓
/publish command triggers
         ↓
┌─────────────────────────────┐
│  GitHub Publisher Skill     │
│  1. Read Skill code         │
│  2. Generate documentation  │
│  3. Polish to high-star style│
│  4. Write README.md        │
│  5. Git add / commit / push │
└─────────────────────────────┘
         ↓
GitHub Repository (complete professional docs)
```

## 📁 Project Structure

```
github-publisher/
├── SKILL.md                        # Core skill logic
├── README.md                       # This file
└── references/
    ├── readme-template.md          # High-star README template
    └── style-guide.md              # Writing style guide
```

## 📖 Documentation Sections

The generated README includes:

1. **Project Title + Badges** — Stars, License, Version
2. **One-Line Description** — Core value proposition
3. **Demo Media Placeholder** — GIF/screenshot slot
4. **Features** — 3-5 concrete bullet points
5. **Quick Start** — Minimal path to first success
6. **Detailed Usage** — All parameters and options
7. **Configuration Table** — Defaults and descriptions
8. **Usage Examples** — At least 3 real scenarios
9. **Project Structure** — Directory tree with file descriptions
10. **Contributing Guide**
11. **License**

## 🎨 Writing Standards

- Titles start with emoji for visual hierarchy
- Code examples must be runnable
- No fluff — every sentence carries information
- Configuration in table format (clearer than lists)
- English primary, Chinese optional

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch
3. Submit a pull request
4. Follow the style guide in `references/style-guide.md`

## 📄 License

MIT License
