<div align="center">

# GitHub Publisher Skill

<p align="center">
  <img src="assets/demo.gif" alt="GitHub Publisher Demo" />
</p>

> *自动为 Claude Skill 生成专业 GitHub 文档，一行命令完成发布。*

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Agent Skills](https://img.shields.io/badge/Agent%20Skills-Standard-green)](https://agentskills.io)
[![skills.sh](https://img.shields.io/badge/skills.sh-Compatible-blue)](https://skills.sh)
[![Multi-Runtime](https://img.shields.io/badge/Runtime-Claude%20Code%20·%20Codex%20·%20Cursor%20·%20Hermes-blueviolet)](#installation)

<br>

**每次创建新 Skill 后，只需一行命令，自动产出符合开源社区标准的专业文档。**

<sub>基于开放的 [Agent Skills](https://agentskills.io) 协议，可在 Claude Code、Codex、Cursor、OpenClaw、Hermes Agent、CodeBuddy、Workbuddy、Gemini CLI、OpenCode 等 50+ 兼容 runtime 中运行。</sub>

<br>

[功能演示](#功能演示) · [安装](#安装) · [使用方法](#使用方法) · [工作原理](#工作原理) · [项目结构](#项目结构)

<br>

**其他语言 / Other Languages / 他の言語 / 다른 언어 / Otros Idiomas:**

[English](README_EN.md) · [日本語](README_JA.md) · [한국어](README_KO.md) · [Español](README_ES.md)

<br>

[![Star History Chart](https://api.star-history.com/svg?repos=JUJING-DEEP/github-publisher&type=Date)](https://star-history.com/#JUJING-DEEP/github-publisher&Date)

</div>

---

## 功能演示

```
用户      ❯ /publish skills/my-new-skill

GitHub    ❯ 正在读取 my-new-skill...
Publisher ❯ ✅ 已读取 SKILL.md、scripts/、references/
          ❯ 📝 正在生成专业 README...
          ❯ ✅ README 生成完成
          ❯ 🔍 质量检查通过
          ❯ 📤 正在提交到 GitHub...

用户      ❯ yes

GitHub    ❯ 🎉 发布成功！
Publisher ❯ https://github.com/JUJING-DEEP/my-new-skill
```

**自动生成的文档包含：**

- 项目标题 + 徽章行（Stars / License / Version）
- 一句话精准介绍
- 核心功能（3-5 项具体说明）
- 快速开始（5 分钟内跑起来）
- 详细使用说明
- 配置项表格
- 至少 3 个使用示例
- 项目结构目录树
- 贡献指南
- MIT License

---

## 工作原理

```
你创建新 Skill
         ↓
/publish 命令触发
         ↓
┌──────────────────────────────────────┐
│       GitHub Publisher Skill          │
│  1. 读取 Skill 代码（SKILL.md 等）    │
│  2. 调用文档生成逻辑                  │
│  3. 润色成高星项目风格                │
│  4. 写入 README.md                   │
│  5. git add / commit / push          │
└──────────────────────────────────────┘
         ↓
GitHub 仓库（完整专业文档）
```

### Phase 1：信息收集

1. 确认目标 Skill 的路径
2. 读取以下文件：
   - `SKILL.md` 或主逻辑文件
   - 所有 `references/` 下的文档
   - 所有 `scripts/` 下的代码
   - 已有的 `README.md`（如果存在）
3. 提取关键信息：
   - 技能名称和核心功能
   - 输入/输出格式
   - 依赖项和兼容性
   - 使用场景和触发条件

### Phase 2：生成 README

必须包含的章节（按顺序）：

1. **项目标题 + 徽章行**
2. **一句话介绍**
3. **功能演示 GIF 或截图占位**
4. **核心功能**（3-5 个要点）
5. **快速开始**
6. **详细使用说明**
7. **配置项**（表格形式）
8. **使用示例**（至少 3 个）
9. **项目结构**
10. **贡献指南**
11. **License**

### Phase 3：质量检查

- [ ] 所有代码块都有语言标注
- [ ] 安装步骤可以一步步跟着做
- [ ] 没有"TODO"或空白占位符
- [ ] 配置表格的每一行都有默认值

### Phase 4：Git 发布

```bash
cd <skill-path>
git add README.md
git commit -m "docs: auto-generate README"
git push origin main
```

---

## 安装

GitHub Publisher 基于开放的 [Agent Skills](https://agentskills.io) 协议，可在任何 skills-compatible 的 AI agent runtime 中运行。

### 方式一：一行命令（推荐，跨 runtime）

打开你正在用的 agent（Claude Code、Codex、Cursor、OpenClaw、Hermes、CodeBuddy、Workbuddy、Gemini CLI、OpenCode 等），告诉它：

```
帮我安装这个 skill：https://github.com/JUJING-DEEP/github-publisher
```

或者用通用 CLI 安装器（[vercel-labs/skills](https://github.com/vercel-labs/skills)，支持 55+ runtime）：

```bash
npx skills add JUJING-DEEP/github-publisher
```

它会自动识别你当前的 runtime 并把 skill 放到正确目录。需要指定时加 `-a claude-code` / `-a codex` / `-a cursor` / `-a openclaw` 等参数。

### 方式二：手动安装

<details>
<summary>展开查看各 runtime 的 skills 目录</summary>

| Runtime | 安装路径 |
|---|---|
| Claude Code | `~/.claude/skills/github-publisher/` |
| Codex CLI | `~/.codex/skills/github-publisher/` |
| Cursor | `~/.cursor/skills/github-publisher/` |
| OpenClaw | `~/.openclaw/workspace/skills/github-publisher/` |
| Hermes Agent | 跑 `tools/install_hermes_skill.py` |
| CodeBuddy | `~/.codebuddy/skills/github-publisher/` |
| Workbuddy | `~/.workbuddy/skills/github-publisher/` |
| Gemini CLI | `~/.gemini/skills/github-publisher/` |
| OpenCode | `~/.opencode/skills/github-publisher/` |
| 其他 runtime | clone 到对应 runtime 的 `skills/` 目录 |

```bash
git clone https://github.com/JUJING-DEEP/github-publisher <上面对应的路径>
```

</details>

### 方式三：作为参考资料使用

即使 runtime 不支持 Agent Skills 自动加载，你也可以直接把 `SKILL.md` 的内容粘贴进对话——它本质就是一份 markdown + YAML frontmatter。

---

## 使用方法

### 基本命令

```
/publish
```

### 指定路径

```
/publish skills/my-new-skill
```

### 在其他 Agent 中触发

```
帮我发布这个 Skill 到 GitHub：skills/my-data-analyzer
```

### 完整工作流

```
1. /publish [可选：Skill路径]
2. GitHub Publisher 自动读取 Skill 的所有文件
3. 生成专业 README 预览
4. 展示预览，询问是否满意
5. 确认后执行 git add / commit / push
6. 返回 GitHub 链接
```

---

## 支持的平台

| 平台 | 状态 | 安装命令 |
|------|------|---------|
| Claude Code | ✅ 完全支持 | `/skill add JUJING-DEEP/github-publisher` |
| Codex | ✅ 完全支持 | `npx skills add JUJING-DEEP/github-publisher` |
| Cursor | ✅ 完全支持 | `npx skills add JUJING-DEEP/github-publisher` |
| OpenClaw | ✅ 完全支持 | `npx skills add JUJING-DEEP/github-publisher` |
| Hermes Agent | ✅ 完全支持 | 参考手动安装 |
| CodeBuddy | ✅ 完全支持 | 参考手动安装 |
| Workbuddy | ✅ 完全支持 | 参考手动安装 |
| Gemini CLI | ✅ 完全支持 | 参考手动安装 |
| OpenCode | ✅ 完全支持 | 参考手动安装 |
| 其他 | ✅ 兼容 | 参考 [Agent Skills 协议](https://agentskills.io) |

---

## 项目结构

```
github-publisher/
├── SKILL.md                         # 核心 Skill 逻辑
├── README.md                        # 本文档（中文）
├── README_EN.md                     # English 版本
├── README_JA.md                     # 日本語 版本
├── README_KO.md                     # 한국어 版本
├── README_ES.md                     # Español 版本
├── LICENSE                          # MIT License
├── assets/
│   └── demo.gif                     # 功能演示动画
├── references/
│   ├── readme-template.md           # 高星项目 README 模板
│   └── style-guide.md               # 写作风格规范
└── .claude/
    └── commands/
        └── publish.md              # /publish 命令定义
```

---

## 写作规范参考

生成的 README 遵循以下规范：

### 标题规范

- 使用 emoji 开头：`🚀 快速开始`、`📋 配置项`、`💡 使用示例`
- 避免标题过长，保持简洁有力

### 语言风格

- 专业但不生硬，像真人写的
- 每句话都有信息量
- 英文为主，中文辅助

### 代码块规范

- 所有代码块必须标注语言
- 代码示例必须可以直接运行
- 关键行添加注释说明

### 列表规范

**好的列表：**
- 3 种预设主题：深色、浅色、高对比
- 支持 12 种输出格式：PDF、Markdown、HTML 等

**差的列表：**
- 功能强大
- 使用方便

### 配置表格

| 参数 | 类型 | 默认值 | 说明 |
|------|------|--------|------|
| model | string | claude-sonnet-4 | 使用的 AI 模型 |
| language | string | zh | 输出语言 |

---

## 配置你的 GitHub Token

为了让 Skill 能够推送代码到 GitHub，你需要配置 GitHub Personal Access Token：

### Claude Code / Codex / Cursor

1. 创建 GitHub Personal Access Token：
   - 访问 https://github.com/settings/tokens
   - 点击 "Generate new token (classic)"
   - 勾选 `repo` 权限

2. 配置凭据：

**方法 A：添加到 Git remote URL**
```bash
git remote add origin https://YOUR_TOKEN@github.com/JUJING-DEEP/repo.git
```

**方法 B：使用 gh auth**
```bash
gh auth login
```

### Hermes Agent

参考 [Hermes Agent 文档](https://hermes.agent/docs/github-integration) 配置 `GITHUB_TOKEN` 环境变量。

### 其他 Runtime

参考各 runtime 的文档配置 GitHub 凭据。通常需要在对应配置文件中设置 `github_token` 或环境变量 `GITHUB_TOKEN`。

---

## 注意事项

1. **如果 Skill 已有 README**：先对比差异，只更新缺失部分
2. **如果 git push 失败**：检查 remote 配置和 Token 权限
3. **生成的文档语气**：要专业但不生硬，像真人写的一样
4. **信息源黑名单**：不包含知乎、微信公众号等低质量来源

---

## 背后的故事

每次创建新 Skill 后，编写 README 是最枯燥的重复性工作。GitHub Publisher Skill 将这个过程自动化，让你只需一行命令，就能获得：

- ✅ 完整的功能介绍
- ✅ 可运行的代码示例
- ✅ 清晰的配置说明
- ✅ 规范的目录结构说明
- ✅ 符合国际开源社区标准的格式

**一行命令，多出来的时间去创造真正的价值。**

---

## 关于作者

**巨鲸r** — AI Native Developer · 全网同号

| 平台 | 链接 |
|------|------|
| 🐧 公众号 | **巨鲸r** |
| 𝕏 Twitter | [@JUJING_DEEP](https://x.com/JUJING_DEEP) |
| GitHub | [JUJING-DEEP](https://github.com/JUJING-DEEP) |

> 扫码关注公众号，获取更多 AI 技能和工具分享 ↓
> <img src="assets/wechat-qrcode.jpg" alt="巨鲸r 公众号二维码" width="200"/>

---

**其他语言 / Other Languages / 他の言語 / 다른 언어 / Otros Idiomas:**

[English](README_EN.md) · [日本語](README_JA.md) · [한국어](README_KO.md) · [Español](README_ES.md)

## 许可证

MIT — 随便用，随便改，随便分发。

---

<div align="center">

**创建 Skill 是开始。<br>自动生成文档是标配。<br>用 GitHub Publisher 让你的 Skill 发行更专业。**

<br>

MIT License © [JUJING-DEEP](https://github.com/JUJING-DEEP)

</div>
