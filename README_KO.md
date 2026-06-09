<div align="center">

# GitHub Publisher Skill

<p align="center">
  <img src="assets/demo.gif" alt="GitHub Publisher Demo" />
</p>

> *Claude Skill용 전문 GitHub 문서를 자동 생성하고, 한 번의 명령으로 게시 완료.*

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Agent Skills](https://img.shields.io/badge/Agent%20Skills-Standard-green)](https://agentskills.io)
[![skills.sh](https://img.shields.io/badge/skills.sh-Compatible-blue)](https://skills.sh)
[![Multi-Runtime](https://img.shields.io/badge/Runtime-Claude%20Code%20·%20Codex%20·%20Cursor%20·%20Hermes-blueviolet)](#installation)

<br>

**새 Skill을 만들 때마다 한 번의 명령으로 오픈소스 커뮤니티 표준의 전문적인 문서를 자동 생성합니다.**

<sub>오픈 [Agent Skills](https://agentskills.io) 프로토콜 기반으로, Claude Code, Codex, Cursor, OpenClaw, Hermes Agent, CodeBuddy, Workbuddy, Gemini CLI, OpenCode 등 50+ 호환 가능한 런타임에서 동작합니다.</sub>

<br>

[데모](#데모) · [설치](#설치) · [사용 방법](#사용-방법) · [작동 원리](#작동-원리) · [프로젝트 구조](#프로젝트-구조)

<br>

**다른 언어 / Other Languages:**

[中文](README.md) · [English](README_EN.md) · [日本語](README_JA.md) · [Español](README_ES.md)

</div>

---

## 데모

```
사용자    ❯ /publish skills/my-new-skill

GitHub    ❯ my-new-skill 읽기 중...
Publisher ❯ ✅ SKILL.md, scripts/, references/ 읽기 완료
           ❯ 📝 전문적인 README 생성 중...
           ❯ ✅ README 생성 완료
           ❯ 🔍 품질 검사 통과
           ❯ 📤 GitHub에 커밋 중...

사용자    ❯ yes

GitHub    ❯ 🎉 게시 성공!
Publisher ❯ https://github.com/JUJING-DEEP/my-new-skill
```

**자동 생성되는 문서内容包括：**

- 프로젝트 제목 + 배지 행 (Stars / License / Version)
- 한 줄 설명
- 핵심 기능 (3-5개 항목 상세 설명)
- 빠른 시작 (5분 내에 실행)
- 상세 사용 설명
- 설정 항목 테이블
- 최소 3개의 사용 예시
- 프로젝트 구조 트리
- 기여 가이드
- MIT 라이선스

---

## 작동 원리

```
새 Skill 생성
         ↓
/publish 명령어 트리거
         ↓
┌──────────────────────────────────────┐
│       GitHub Publisher Skill          │
│  1. Skill 코드 읽기                   │
│  2. 문서 생성 로직 호출                │
│  3. 고성 프로젝트 스타일로Polishing    │
│  4. README.md 쓰기                    │
│  5. git add / commit / push           │
└──────────────────────────────────────┘
         ↓
GitHub 저장소 (완전한 전문 문서)
```

### Phase 1: 정보 수집

1. 대상 Skill 경로 확인
2. 다음 파일 읽기:
   - `SKILL.md` 또는 메인 로직 파일
   - `references/` 하위의 모든 파일
   - `scripts/` 하위의 모든 파일
   - 기존 `README.md` (있는 경우)
3. 핵심 정보 추출:
   - Skill 이름과 핵심 기능
   - 입력/출력 형식
   - 의존성과 호환성
   - 사용 시나리오와 트리거 조건

### Phase 2: README 생성

필수 섹션 (순서대로):

1. **프로젝트 제목 + 배지**
2. **한 줄 설명**
3. **데모 GIF/스크린샷 플레이스홀더**
4. **핵심 기능** (3-5개 항목)
5. **빠른 시작**
6. **상세 사용 설명**
7. **설정 항목** (테이블 형식)
8. **사용 예시** (3개 이상)
9. **프로젝트 구조**
10. **기여 가이드**
11. **라이선스**

### Phase 3: 품질 검사

- [ ] 모든 코드 블록에 언어 레이블 있음
- [ ] 설치 단계가 따라갈 수 있음
- [ ] "TODO" 또는 빈 플레이스홀더 없음
- [ ] 설정 테이블의 각 행에 기본값 있음

### Phase 4: Git 게시

```bash
cd <skill-path>
git add README.md
git commit -m "docs: auto-generate README"
git push origin main
```

---

## 설치

GitHub Publisher는 오픈 [Agent Skills](https://agentskills.io) 프로토콜 기반으로, skills 호환 AI agent 런타임에서 모두 동작합니다.

### 방법 1: 한 번의 명령어 (권장, 크로스 런타임)

사용 중인 agent(Claude Code, Codex, Cursor, OpenClaw, Hermes, CodeBuddy, Workbuddy, Gemini CLI, OpenCode 등)를 열고 다음과 같이 말합니다:

```
이 skill을 설치해주세요: https://github.com/JUJING-DEEP/github-publisher
```

또는 범용 CLI 인스톨러([vercel-labs/skills](https://github.com/vercel-labs/skills), 55+ 런타임 지원)를 사용:

```bash
npx skills add JUJING-DEEP/github-publisher
```

### 방법 2: 수동 설치

<details>
<summary>각 런타임의 skills 디렉토리 보기</summary>

| 런타임 | 설치 경로 |
|---|---|
| Claude Code | `~/.claude/skills/github-publisher/` |
| Codex CLI | `~/.codex/skills/github-publisher/` |
| Cursor | `~/.cursor/skills/github-publisher/` |
| OpenClaw | `~/.openclaw/workspace/skills/github-publisher/` |
| Hermes Agent | `tools/install_hermes_skill.py` 실행 |
| 다른 런타임 | 해당 런타임의 `skills/` 디렉토리에 clone |

```bash
git clone https://github.com/JUJING-DEEP/github-publisher <위의 경로>
```

</details>

---

## 사용 방법

### 기본 명령어

```
/publish
```

### 경로 지정

```
/publish skills/my-new-skill
```

### 다른 Agent에서 트리거

```
이 Skill을 GitHub에 게시해주세요: skills/my-data-analyzer
```

---

## 지원 플랫폼

| 플랫폼 | 상태 | 설치 명령어 |
|------|------|---------|
| Claude Code | ✅ 완전 지원 | `/skill add JUJING-DEEP/github-publisher` |
| Codex | ✅ 완전 지원 | `npx skills add JUJING-DEEP/github-publisher` |
| Cursor | ✅ 완전 지원 | `npx skills add JUJING-DEEP/github-publisher` |
| OpenClaw | ✅ 완전 지원 | `npx skills add JUJING-DEEP/github-publisher` |
| Hermes Agent | ✅ 완전 지원 | 수동 설치 참조 |
| 기타 플랫폼 | ✅ 호환 | [Agent Skills 프로토콜](https://agentskills.io) 참조 |

---

## 프로젝트 구조

```
github-publisher/
├── SKILL.md                         # 핵심 Skill 로직
├── README.md                        # 이 파일 (중국어)
├── README_EN.md                     # 영어 버전
├── README_JA.md                    # 일본어 버전
├── README_KO.md                     # 이 파일
├── README_ES.md                    # 스페인어 버전
├── LICENSE                          # MIT 라이선스
├── assets/
│   └── demo.gif                     # 데모 애니메이션
├── references/
│   ├── readme-template.md           # 고성 README 템플릿
│   └── style-guide.md                # 작성 스타일 가이드
└── .claude/
    └── commands/
        └── publish.md              # /publish 명령 정의
```

---

## 주의사항

1. **Skill에 이미 README가 있는 경우**: 차이점을 비교하고, 누락된 부분만 업데이트
2. **git push가 실패하는 경우**: remote 설정과 Token 권한 확인
3. **생성된 문서의 어조**: 전문적이지만 인공적이지 않아야 함
4. **정보 출처 블랙리스트**: Zhihu, WeChat 공중 계정 등 포함 안 함

---

## 저자 소개

**거대고래r** — AI Native Developer · 전 플랫폼 동일 아이디

| 플랫폼 | 링크 |
|------|------|
| 🐧 WeChat | **거대고래r** (WeChat에서 검색) |
| 𝕏 Twitter | [@JUJING_DEEP](https://x.com/JUJING_DEEP) |
| GitHub | [JUJING-DEEP](https://github.com/JUJING-DEEP) |

> QR코드는 assets/wechat-qrcode.jpg에 있습니다 ↓

## 라이선스

MIT — 자유롭게 사용, 수정, 배포하세요.

---

<div align="center">

MIT License © [JUJING-DEEP](https://github.com/JUJING-DEEP)

</div>
