<div align="center">

# GitHub Publisher Skill

<p align="center">
  <img src="assets/demo.gif" alt="GitHub Publisher Demo" />
</p>

> *Claude Skill用のプロフェッショナルなGitHubドキュメントを自動生成、一コマンドで公開完了。*

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Agent Skills](https://img.shields.io/badge/Agent%20Skills-Standard-green)](https://agentskills.io)
[![skills.sh](https://img.shields.io/badge/skills.sh-Compatible-blue)](https://skills.sh)
[![Multi-Runtime](https://img.shields.io/badge/Runtime-Claude%20Code%20·%20Codex%20·%20Cursor%20·%20Hermes-blueviolet)](#installation)

<br>

**新しいSkillを作成するたびに、一コマンドでオープンソースコミュニティ標準的专业的なドキュメントを自動生成。**

<sub>オープンな [Agent Skills](https://agentskills.io) プロトコルに基づいて、Claude Code、Codex、Cursor、OpenClaw、Hermes Agent、CodeBuddy、Workbuddy、Gemini CLI、OpenCode など50+の互換性のあるruntimeで動作。</sub>

<br>

[デモ](#デモ) · [インストール](#インストール) · [使用方法](#使用方法) · [動作原理](#動作原理) · [プロジェクト構造](#プロジェクト構造)

<br>

**他の言語 / Other Languages:**

[中文](README.md) · [English](README_EN.md) · [한국어](README_KO.md) · [Español](README_ES.md)

</div>

---

## デモ

```
ユーザー    ❯ /publish skills/my-new-skill

GitHub      ❯ my-new-skill を読み込み中...
Publisher   ❯ ✅ SKILL.md、scripts/、references/ を読み込みました
            ❯ 📝 プロフェッショナルなREADMEを生成中...
            ❯ ✅ README 生成完了
            ❯ 🔍 品質チェック完了
            ❯ 📤 GitHubにコミット中...

ユーザー    ❯ yes

GitHub      ❯ 🎉 公開成功！
Publisher   ❯ https://github.com/JUJING-DEEP/my-new-skill
```

**自動生成されるドキュメントの内容：**

- プロジェクトタイトル + バッジ行（Stars / License / Version）
- 一言説明
- コア機能（3-5項目の詳細説明）
- クイックスタート（5分で起動）
- 詳細な使用方法
- 設定項目テーブル
- 至少3つの使用例
- プロジェクト構造ツリー
- コントリビュートガイド
- MIT License

---

## 動作原理

```
新しいSkillを作成
         ↓
/publish コマンドがトリガー
         ↓
┌──────────────────────────────────────┐
│       GitHub Publisher Skill          │
│  1. Skillコードを読み込み              │
│  2. ドキュメント生成ロジックを呼び出し │
│  3. 高星プロジェクト風に|POLISH        │
│  4. README.md を書き込み              │
│  5. git add / commit / push           │
└──────────────────────────────────────┘
         ↓
GitHub リポジトリ（完全な專業的なドキュメント）
```

### Phase 1：情報収集

1. 対象Skillのパスを確認
2. 以下のファイルを読み込み：
   - `SKILL.md` またはメインロジックファイル
   - `references/` 下の全ファイル
   - `scripts/` 下の全ファイル
   - 既存の `README.md`（存在する場合）
3. 关键情報を抽出：
   - Skill名とコア機能
   - 入力/出力フォーマット
   - 依存関係と互換性
   - 使用シナリオとトリガー条件

### Phase 2：README 生成

必須セクション（順不同）：

1. **プロジェクトタイトル + バッジ**
2. **一言説明**
3. **デモGIF/スクリーンショットプレースホルダー**
4. **コア機能**（3-5項目）
5. **クイックスタート**
6. **詳細な使用方法**
7. **設定項目**（テーブル形式）
8. **使用例**（3つ以上）
9. **プロジェクト構造**
10. **コントリビュートガイド**
11. **License**

### Phase 3：品質チェック

- [ ] 全コードブロックに言語ラベルあり
- [ ] インストール手順が追跡可能
- [ ] 「TODO」や空白のプレースホルダーなし
- [ ] 設定テーブルの全行にデフォルト値あり

### Phase 4：Git 公開

```bash
cd <skill-path>
git add README.md
git commit -m "docs: auto-generate README"
git push origin main
```

---

## インストール

GitHub Publisher はオープンな [Agent Skills](https://agentskills.io) プロトコルに基づいており、skills互換のAI agent runtimeならどこでも動作します。

### 方法1：一コマンド（推奨、クロス-runtime）

使用中のagent（Claude Code、Codex、Cursor、OpenClaw、Hermes、CodeBuddy、Workbuddy、Gemini CLI、OpenCodeなど）を開き、次のように指示します：

```
このskillをインストール帮我安装这个 skill：https://github.com/JUJING-DEEP/github-publisher
```

または汎用CLIインストーラー（[vercel-labs/skills](https://github.com/vercel-labs/skills)、55+ runtime対応）を使用：

```bash
npx skills add JUJING-DEEP/github-publisher
```

### 方法2：手動インストール

<details>
<summary>各runtimeのskillsディレクトリを表示</summary>

| Runtime | インストールパス |
|---|---|
| Claude Code | `~/.claude/skills/github-publisher/` |
| Codex CLI | `~/.codex/skills/github-publisher/` |
| Cursor | `~/.cursor/skills/github-publisher/` |
| OpenClaw | `~/.openclaw/workspace/skills/github-publisher/` |
| Hermes Agent | `tools/install_hermes_skill.py` を実行 |
| 他のruntime | 該当runtimeの`skills/`ディレクトリにclone |

```bash
git clone https://github.com/JUJING-DEEP/github-publisher <上の表のパス>
```

</details>

---

## 使用方法

### 基本コマンド

```
/publish
```

### パス指定

```
/publish skills/my-new-skill
```

### 他のAgentからトリガー

```
このSkillをGitHubに公開帮我发布这个 Skill 到 GitHub：skills/my-data-analyzer
```

---

## サポートプラットフォーム

| プラットフォーム | ステータス | インストールコマンド |
|------|------|---------|
| Claude Code | ✅ 完全サポート | `/skill add JUJING-DEEP/github-publisher` |
| Codex | ✅ 完全サポート | `npx skills add JUJING-DEEP/github-publisher` |
| Cursor | ✅ 完全サポート | `npx skills add JUJING-DEEP/github-publisher` |
| OpenClaw | ✅ 完全サポート | `npx skills add JUJING-DEEP/github-publisher` |
| Hermes Agent | ✅ 完全サポート | 手動インストールを参照 |
| その他のプラットフォーム | ✅ 互換 | [Agent Skills プロトコル](https://agentskills.io)を参照 |

---

## プロジェクト構造

```
github-publisher/
├── SKILL.md                         # コアSkillロジック
├── README.md                        # このファイル（中文）
├── README_EN.md                     # English版
├── README_JA.md                     # このファイル
├── README_KO.md                    # 한국어版
├── README_ES.md                     # Español版
├── LICENSE                          # MIT License
├── assets/
│   └── demo.gif                     # デモアニメーション
├── references/
│   ├── readme-template.md           # 高星READMEテンプレート
│   └── style-guide.md               # ライティングスタイルガイド
└── .claude/
    └── commands/
        └── publish.md              # /publish コマンド定義
```

---

## 注意事項

1. **Skillに既にREADMEがある場合**：差分を比較し、欠落部分のみ更新
2. **git pushが失敗した場合**：remote設定とToken権限を確認
3. **生成されたドキュメントのトーン**：专业的だが機械的ではない
4. **情報源ブラックリスト**：知乎、微信公眾號などを含まない

---

## 著者について

**巨鯨r** — AI Native Developer · 全プラットフォーム同名

| プラットフォーム | リンク |
|------|------|
| 🐧 WeChat | **巨鯨r**（WeChatで検索） |
| 𝕏 Twitter | [@JUJING_DEEP](https://x.com/JUJING_DEEP) |
| GitHub | [JUJING-DEEP](https://github.com/JUJING-DEEP) |

> QRコードは assets/wechat-qrcode.jpg にあります ↓

## ライセンス

MIT — 自由に使ってください、自由に変えてください、自由롭게配布してください。

---

<div align="center">

MIT License © [JUJING-DEEP](https://github.com/JUJING-DEEP)

</div>
