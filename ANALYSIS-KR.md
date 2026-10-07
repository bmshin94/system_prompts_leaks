# system_prompts_leaks 전수조사 분석 리포트 (한국어)

> 작성일: 2026-10-07
> 대상 저장소(포크): https://github.com/bmshin94/system_prompts_leaks
> 원본 저장소(upstream): https://github.com/asgeirtj/system_prompts_leaks
> 작성: Claude Code 세션 대화 정리

---

## 목차

1. [저장소 개요](#1-저장소-개요)
2. [쉬운 설명 — 시스템 프롬프트란?](#2-쉬운-설명--시스템-프롬프트란)
3. [폴더 구조 전수조사 결과](#3-폴더-구조-전수조사-결과)
4. [나에게 어떤 도움이 되는가](#4-나에게-어떤-도움이-되는가)
5. [Q&A — 설치/정체/토큰/에이전트/개발/영상](#5-qa)
6. [수익화 아이디어 상세](#6-수익화-아이디어-상세)
7. [로드맵 및 법적 체크리스트](#7-로드맵-및-법적-체크리스트)

---

## 1. 저장소 개요

**한 줄 요약: 세계 주요 AI 챗봇·코딩에이전트의 "시스템 프롬프트(숨겨진 행동 지침서)"를 모아놓은 아카이브.**

| 항목 | 내용 |
|------|------|
| 총 파일 수 | **1,235개** |
| 총 용량 | **38MB** (대부분 순수 텍스트) |
| 라이선스 | **CC0 1.0 Universal (퍼블릭 도메인)** — 상업적 이용·수정·재배포 전부 자유, 출처 표기 의무 없음 |
| 구성 | 실행 코드 없음. 100% 문서 저장소 |
| 주요 확장자 | `.md` 816 · `.xsd` 117 · `.yaml` 109 · `.py` 80 · `.json` 32 · `.mjs` 26 · `.ts` 16 |
| 공신력 | The Washington Post 인터랙티브 기사 인용 / CEPS AI World 분석 활용 / Simon Willison "가장 철저한 컬렉션" / Trendshift 등재 |
| 후원 | GitHub Sponsors (`asgeirtj`) |

### 최근 추가 항목 (원본 기준)

| 항목 | 날짜 |
|------|------|
| ChatGPT Dots (Dreamer/Voice/skills 28종) | 2026-10-05 |
| Muse Spark 1.3 Muse Code | 2026-10-04 |
| Meta Muse agent (VM 파일 전체) | 2026-10-03 |
| Grok 4.7 | 2026-10-03 |
| Fable 5.1 Claude Code on the web | 2026-09-30 |
| Claude Sonnet 5.5 / GPT-6.1-Sol Codex | 2026-09-29 |

---

## 2. 쉬운 설명 — 시스템 프롬프트란?

### 비유 1: "AI는 알바생, 시스템 프롬프트는 사장님 매뉴얼"

사용자가 AI에게 메시지를 보내기 **전에**, 회사가 미리 넣어둔 행동 지침서가 있다.

```
┌─────────────────────────────────────┐
│  [시스템 프롬프트]  ← 사용자는 못 봄    │
│  "너는 Claude야. 이럴 땐 이렇게 해..." │
├─────────────────────────────────────┤
│  [사용자 메시지]   ← 내가 쓰는 부분     │
│  "파이썬 코드 짜줘"                    │
└─────────────────────────────────────┘
```

이 저장소는 전 세계 AI 제품 약 1,000여 개의 "사장님 매뉴얼"을 모아놓은 것이다.

### 비유 2: 공략집이 아니라 소스코드

| 일반적으로 보는 것 | 이 저장소에 있는 것 |
|---|---|
| "이렇게 물어보면 잘 대답해요" (블로그 팁) | **AI 회사 직원이 직접 쓴 원본 설정 파일** |
| 게임 공략 위키 | **개발사 내부 설계 문서** |

### 실제 내용 예시 (`Anthropic/claude-opus-5.md`, 3,677줄)

- `default_stance`: "Claude defaults to helping. Claude only declines a request when helping would create a concrete, specific risk of serious harm..."
- `critical_child_safety_instructions`: 미성년자 보호 관련 강제 규칙
- `product_information`: 모델명·API 문자열·제품 라인업 안내
- `fable_safeguards_routing`: 안전장치에 의한 모델 라우팅 설명

→ **AI의 성격·말투·금지사항·도구 사용법이 전부 이 텍스트에서 결정된다.**

---

## 3. 폴더 구조 전수조사 결과

### 벤더별 규모

| 폴더 | 파일 수 | 용량 | 내용 |
|------|--------:|-----:|------|
| **Anthropic** | 558 | 24MB | Claude 전 제품 (웹/코드/디자인/카우워크/M365/Chrome/iOS) |
| **Meta** | 462 | 6.4MB | Muse agent VM 전체 + Muse Code |
| **OpenAI** | 124 | 4.9MB | ChatGPT, Codex, Dots, API 주입 프롬프트 |
| **Google** | 24 | 384KB | Gemini 3.x, Gemini CLI, NotebookLM, Jules, Antigravity |
| **Misc** | 23 | 376KB | Cursor, Zed, Warp, Devin, Amp, Raycast 등 23종 |
| **xAI** | 16 | 788KB | Grok 4.7까지 + 페르소나 + 세이프티 |
| **Microsoft** | 5 | 160KB | GitHub Copilot, VS Code Agent, Copilot CLI/Word/macOS |
| **Perplexity** | 5 | 116KB | Perplexity, Computer, Deep Research, Comet, Voice |
| Google 외 기타 | - | - | Kimi(2) · Mistral(2) · Qwen(2) · Cursor(1) · DeepSeek(1) · Notion(1) · Pi(1) · GLM(1) |

### Anthropic 내부 구조 (핵심)

```
Anthropic/
├── claude-opus-5.md, claude-sonnet-5.5.md, claude-fable-5.1.md ...
│       └─ claude.ai 웹/모바일 앱 시스템 프롬프트
├── claude-*-no-tools.md     ← 툴 비활성 버전
├── claude-code/             ← Claude Code CLI 일체
│   ├── claude-code-opus-5.md (8,002줄) 등 모델별 프롬프트
│   ├── agents/              ← 서브에이전트 6종 (Explore, Plan, general-purpose ...)
│   ├── commands/            ← 슬래시 명령어 (/btw, /compact, /rename)
│   ├── output-styles/       ← 출력 스타일 4종 (concise, explanatory, learning, proactive)
│   ├── prompts/             ← 내부 프롬프트 (advisor-tool, session-title ...)
│   └── skills/              ← 스킬 39종 전체 (py/ts/html/json 포함)
├── claude-cowork/           ← Claude Cowork + setup 스킬
├── claude-design/           ← Claude Design + starter-components
├── official/                ← Anthropic 공식 공개본 (2024-07-12 ~ 2026-02-17, 날짜별)
├── old/                     ← 구버전 아카이브 (Claude 3.7 등)
└── raw/                     ← 가공 전 원본 덤프
```

> `Anthropic/README.md`에 "어떤 파일이 어떤 제품인지" 대조표가 포함되어 있다.

### Meta/muse-agent — 에이전트 아키텍처 교과서

```
Meta/muse-agent/
├── SOUL.md                    ← 에이전트 핵심 가치관
├── IDENTITY.md                ← 정체성 정의
├── MEMORY.md                  ← 메모리 시스템 설계
├── USER.md                    ← 사용자 프로파일 관리
├── HEARTBEAT.md               ← 백그라운드 주기 실행 설계
├── TOOLS.md                   ← 툴 정의
├── PROACTIVE_PREFERENCES.md   ← 선제적 행동 규칙
├── AGENTS.md
├── skills/                    ← 89개 스킬 (github, figma, asana, canva, dropbox ...)
├── memory/ · subscriptions/ · docs/ · assets/
└── workspace/system/system_prompt.md
```

### OpenAI/dots — ChatGPT Dots 에이전트

```
OpenAI/dots/
├── dreamer.md · voice.md · tools.md · available-skills.md
└── skills/   ← 28종 (email, slack, flights, shopping, presentations ...)
```

### 최대 용량 파일 TOP 5

| 크기 | 파일 |
|-----:|------|
| 734KB | `Anthropic/claude-code/skills/plugin-authoring/types/claude-code.d.ts` |
| 541KB | `Anthropic/claude-code/claude-code-desktop-fable-5.1.md` |
| 540KB | `Anthropic/official/all.md` |
| 521KB | `Anthropic/claude-projects-thread-claude.md` |
| 495KB | `OpenAI/Codex/gpt-6.1-sol-chatgpt-work-local.md` |

### 특이사항

- `GLM/README.md` — "GLM은 시스템 프롬프트가 **존재하지 않음**"을 검증해서 기록한 네거티브 데이터.
- `.gitattributes` — 프롬프트 원문 보존을 위해 공백/CRLF 정규화를 비활성화.

---

## 4. 나에게 어떤 도움이 되는가

| # | 가치 | 설명 |
|---|------|------|
| 1 | **프롬프트 엔지니어링 최고급 교재** | 빅테크가 막대한 비용으로 튜닝한 결과물을 무료 열람. `NEVER`/`IMPORTANT` 강조 패턴, 조건 분기 서술법 등 |
| 2 | **AI 에이전트 설계 치트키** | `Meta/muse-agent/`, `Anthropic/claude-code/skills/` — 메모리·스킬·서브에이전트 실제 구현 |
| 3 | **버전 diff 분석** | `official/`이 날짜별로 정리 → AI 진화 추적 가능 (콘텐츠 소재) |
| 4 | **CC0 = 상업적 이용 자유** | 강의·SaaS·책·앱 전부 법적으로 가능 |
| 5 | **현재 사용 중인 도구의 내부** | `Anthropic/claude-code/claude-code-opus-5.md` = 지금 돌리는 Claude Code의 실제 프롬프트 |

### 주의사항

1. "Leaks(유출)" 저장소 — `official/` 외에는 각 회사의 공식 배포물이 아님
2. 추출 과정의 왜곡 가능성 — 100% 정확 보장 없음
3. 모델 업데이트마다 변경 → 금방 낡음
4. 타사 프롬프트 그대로 복붙해 서비스하면 상표/브랜드 이슈 발생 가능

---

## 5. Q&A

### Q1. 설치 및 사용법은?

**"설치"라는 개념 자체가 없다.** 실행 파일, `package.json`, 설치 스크립트가 전혀 없는 순수 문서 저장소다.

**방법 1 — 웹에서 열람**
```
https://github.com/bmshin94/system_prompts_leaks
```

**방법 2 — 로컬 클론 후 검색**
```bash
git clone https://github.com/bmshin94/system_prompts_leaks.git
cd system_prompts_leaks

# 키워드 전문 검색
grep -ri "artifact" --include="*.md" . | head -20

# 줄 수 비교
wc -l Anthropic/claude-code/*.md

# 버전 간 차이 비교
diff Anthropic/claude-opus-5.md Anthropic/claude-opus-5.5.md
```

**방법 3 — AI에게 분석시키기 (권장)**
```bash
claude
> Anthropic 폴더 프롬프트들 분석해서 공통 패턴 뽑아줘
```

**원본 최신화**
```bash
git remote add upstream https://github.com/asgeirtj/system_prompts_leaks.git
git fetch upstream
git merge upstream/main
```

### Q2. 플러그인? 스킬? MCP?

**셋 다 아니다. "데이터셋 / 참고자료"다.**

| 구분 | 정체 | 이 저장소 |
|------|------|-----------|
| 플러그인 | `.claude-plugin/` 가진 설치형 패키지 | ❌ 없음 |
| 스킬 | `SKILL.md` + frontmatter로 AI 능력 확장 | ⚠️ 내용물은 있으나 "수집된 사본"이지 설치용 아님 |
| MCP | 외부 도구 연결 프로토콜 (서버 실행 필요) | ❌ 서버 코드 없음 |
| **데이터셋** | 참고용 자료 모음 | ✅ **이것** |

단, 이 내용을 바탕으로 직접 스킬/플러그인을 **만들 수는 있다** (수익화 아이디어 3번 참고).

### Q3. API 토큰이 필요한가?

| 상황 | 필요 여부 |
|------|-----------|
| GitHub 열람 / `git clone` / 읽고 공부 | ❌ 불필요 |
| 내 저장소에 push | ✅ (계정 인증, 비용 없음) |
| **내용을 AI 모델에 입력해서 분석** | ✅ **이때만 필요 + 비용 발생** |

**비용 주의:** `claude-sonnet-5.5.md` 한 파일이 470KB ≈ 약 12만 토큰. 통째로 넣지 말고 `grep`/`sed`로 필요한 구간만 추출해서 투입할 것.

### Q4. AI 에이전트 구축에 도움이 되는가?

**매우 크게 도움된다. 이 저장소 최대 가치.**

필수 열람 3곳:

1. **`Meta/muse-agent/`** — SOUL / IDENTITY / MEMORY / HEARTBEAT / PROACTIVE_PREFERENCES. 에이전트 설계에서 가장 어려운 "메모리 관리"와 "선제적 행동 시점"의 실제 해법.
2. **`Anthropic/claude-code/skills/`** — 39개 스킬 + 실제 `.py`/`.ts` 코드. 특히 `skill-creator/`(스킬 만드는 스킬 + eval 스크립트), `plugin-authoring/types/claude-code.d.ts`(734KB 타입 정의).
3. **`Anthropic/claude-code/agents/`** — Explore/Plan/general-purpose 등 서브에이전트 역할 분담 프롬프트.

| 배울 패턴 | 참고 위치 |
|-----------|-----------|
| 툴 정의 작성법 | `OpenAI/dots/tools.md`, Anthropic 전반 |
| 거절/안전 규칙 설계 | Anthropic `refusal_handling` 섹션 |
| 상태 관리 & 메모리 | `Meta/muse-agent/memory/` |
| 서브에이전트 위임 | `Anthropic/claude-code/agents/` |
| 플랜 모드 구현 | `OpenAI/Codex/plan_mode.md` |
| 스킬 자동 트리거 | 모든 `SKILL.md`의 `description` 필드 |

### Q5. 수익화 아이디어는?

→ [6장](#6-수익화-아이디어-상세) 참고.

### Q6. React나 PHP로 만들 수 있는가?

**가능하며, 오히려 적합한 소재다.** 순수 텍스트 데이터라 어떤 언어로든 가공 가능.

**React (Next.js) 구성안**
```
src/
├── components/
│   ├── VendorSidebar.jsx    // 벤더별 사이드바
│   ├── PromptViewer.jsx     // 마크다운 렌더링
│   ├── DiffViewer.jsx       // 버전 비교 (킬러 기능)
│   ├── SearchBar.jsx        // 전문 검색
│   └── TokenCounter.jsx     // 토큰 수/비용 계산
└── data/index.json          // 빌드 타임 생성 메타데이터
```
스택: Next.js 15 (SSG) + react-markdown + FlexSearch/Fuse.js + diff2html + Tailwind → Vercel 무료 배포.
**주의:** 470KB 파일 직접 렌더링 시 브라우저 멈춤 → `react-window` 가상 스크롤 또는 청크 분할 필수.

**PHP 구성안**
```
├── index.php
├── lib/Parser.php      // Parsedown 마크다운
├── lib/Indexer.php     // MySQL FULLTEXT 인덱스
├── lib/Differ.php      // 버전 비교
├── api/search.php      // AJAX 검색
└── sync.php            // 원본 저장소 자동 동기화 (cron)
```
스택: Laravel 11 또는 순수 PHP 8.3 + Parsedown + MySQL FULLTEXT + Redis 캐시.

**차별화 기능 아이디어**

| 기능 | 난이도 |
|------|--------|
| 크로스 벤더 비교 (GPT vs Claude vs Gemini 나란히) | ★★★ |
| 토큰/비용 계산기 | ★★ |
| 타임라인 뷰 (2024.07 → 2026.10 진화 시각화) | ★★★★ |
| 패턴 자동 태깅 (안전규칙/툴정의/말투지시 분류) | ★★★★ |
| 프롬프트 플레이그라운드 | ★★★ |
| 변경 알림 (이메일/디스코드) | ★★ |

### Q7. 유튜브 강의 영상 제작이 가능한가?

**가능하며, 소재 경쟁력이 높다.** CC0라 화면 노출에 저작권 문제가 없고, 한국어 콘텐츠가 거의 없는 블루오션이다.

**시즌 1 — 폭로/후킹형 (조회수)**
1. ChatGPT가 몰래 읽는 2,000줄의 명령서
2. Claude는 왜 가끔 거절할까 — 실제 거절 규칙 분석
3. Gemini vs ChatGPT vs Claude — 성격이 다른 이유
4. AI 회사들이 말하지 않는 안전장치 TOP 10
5. GLM은 시스템 프롬프트가 없다? 검증 실험

**시즌 2 — 실전 활용형 (구독자)**
6. Anthropic 프롬프트에서 배우는 작성법 5원칙
7. Claude Code 스킬 시스템 완전 분해
8. Meta Muse 에이전트 구조 따라 만들기
9. 내 에이전트에 메모리 붙이기
10. 서브에이전트 멀티 구조 설계

**시즌 3 — 코딩 실습형 (수익화 연결)**
11~15. React 프롬프트 뷰어 만들기 (5부작)
16~18. PHP/Laravel 아카이브 사이트 구축 (3부작)
19. GitHub Actions 자동 동기화 봇
20. 프롬프트 분석 SaaS 7일 런칭

**제작 팁**
- 길이: 폭로형 8~12분 / 실습형 20~30분
- 터미널에서 `grep` 실시간 검색 장면 = 전문성 연출
- 오프닝 훅: "지금 ChatGPT에 무엇을 물어보든, 당신 메시지 앞에는 2,000줄이 먼저 들어갑니다"

**리스크**
- "해킹 방법"처럼 포장하면 수익창출 제한 위험 → "분석·교육" 포지셔닝
- 회사 로고는 CC0 적용 대상이 아님 (상표권 별개)
- "유출"보다 "공개된 프롬프트 분석" 표현이 안전

---

## 6. 수익화 아이디어 상세

### TIER S (최우선 추천)

#### 1. "Prompt Intelligence" 구독 SaaS

프롬프트 변경사항을 추적·분석해 알려주는 B2B 서비스.

| 항목 | 내용 |
|------|------|
| 타겟 | AI 스타트업, 프롬프트 엔지니어, AI 컨설턴트 |
| 가격 | Free / $19월(Pro) / $99월(Team) |
| 기능 | 변경 diff 알림 · 영향도 분석 · 크로스벤더 비교 · API |
| 스택 | Next.js + Supabase + GitHub Actions(cron) + Slack/Discord Webhook |
| 기간 | MVP 3~4주 |
| 예상 | 유료 100명 × $19 ≈ **월 $1,900 (약 250만원)** |

#### 2. 온라인 강의 (인프런 / Udemy / 클래스101)

"리버스 엔지니어링으로 배우는 프롬프트 엔지니어링" (총 8시간)

```
1부. 시스템 프롬프트의 이해            (1.0h)
2부. Anthropic 분석 — 안전성 설계      (1.5h)
3부. OpenAI 분석 — 툴 호출 설계        (1.5h)
4부. Meta Muse — 에이전트 아키텍처     (2.0h)  ← 핵심
5부. 실습: 내 에이전트 만들기           (1.5h)
6부. 실습: 프롬프트 뷰어 웹앱           (0.5h)
```

| 항목 | 내용 |
|------|------|
| 가격 | 99,000 ~ 149,000원 / Udemy $49 |
| 제작 기간 | 6~8주 |
| 예상 | 인프런 300명 × 99,000 × 0.7 ≈ **누적 2,000만원** |

> 유튜브 무료(시즌1) → 유료 강의(시즌2·3) 퍼널 구조가 가장 효율적.

#### 3. Claude Code 플러그인/스킬 마켓

```
prompt-master/
├── .claude-plugin/plugin.json
├── skills/
│   ├── prompt-patterns/     # 프롬프트 작성 패턴 가이드
│   ├── agent-architect/     # 에이전트 설계 도우미 (Muse 기반)
│   ├── safety-rules/        # 안전 규칙 작성기
│   └── tool-definition/     # 툴 정의 생성기
└── commands/analyze-prompt.md
```

무료 공개로 인지도 확보 → Pro 버전 유료화 / 기업 커스텀. 개발 2~3주. GitHub 스타 자체가 포트폴리오 자산.

### TIER A

#### 4. 전자책 / 기술서적

"AI는 무엇을 명령받는가 — 1,235개 시스템 프롬프트 해부"

| 플랫폼 | 가격 | 예상 |
|--------|------|------|
| 리디북스/교보 전자책 | 15,000원 | 500부 ≈ 750만원 |
| Gumroad 영문판 | $29 | 300부 ≈ $8,700 |
| 종이책 (출판사) | 25,000원 | 인세 10% |

#### 5. 광고형 웹서비스 (한국어 프롬프트 위키)

차별점은 **한국어 번역 + 전문가 해설** (원본에 없음).
수익: 애드센스 + 제휴 마케팅. SEO 키워드: "ChatGPT 시스템 프롬프트", "Claude 프롬프트".
개발 2주(Next.js SSG, 서버비 거의 0). 월 5만 PV 기준 **월 30~80만원**.

#### 6. 기업 컨설팅 / 사내 교육

| 서비스 | 가격 |
|--------|------|
| 프롬프트 감사(Audit) 리포트 | 300~500만원 |
| 사내 워크숍 (4시간) | 200~300만원 |
| 에이전트 설계 컨설팅 | 1,000만원~ |

강점: "빅테크 1,235개 프롬프트 전수 분석" 이라는 권위.

### TIER B (보조 수익)

| # | 아이디어 | 예상 수익 |
|---|---------|----------|
| 7 | 주간 뉴스레터 "프롬프트 변경 리포트" (Stibee/Substack) | 월 50만원~ |
| 8 | 프롬프트 검색/비교 API 판매 (RapidAPI) | 월 20~50만원 |
| 9 | Notion 프롬프트 패턴 DB 템플릿 판매 | 개당 2만원 |
| 10 | GPTs / Claude Project "프롬프트 분석 봇" | 간접 홍보 |
| 11 | 정제·태깅 데이터셋 판매 (Kaggle/HuggingFace) | 연구용 B2B |
| 12 | 해외 AI 기업 한국어 프롬프트 현지화 외주 | 건당 100만원~ |

---

## 7. 로드맵 및 법적 체크리스트

### 6개월 로드맵

| 시기 | 실행 | 목표 |
|------|------|------|
| 1개월차 | 유튜브 시즌1(5편) + 블로그 SEO | 인지도, 비용 0원 |
| 2개월차 | React 프롬프트 뷰어 무료 오픈 | 포트폴리오 + 트래픽 |
| 3개월차 | 뉴스레터 시작 + 애드센스 승인 | 첫 수익 |
| 4~5개월차 | 인프런 강의 출시 | 500만원 목표 |
| 6개월차 | SaaS 유료 전환 | 구독 매출 시작 |
| 7개월~ | 컨설팅 / 전자책 / 플러그인 | 수익 다각화 |

### 법적 체크리스트

| 항목 | 안전도 | 비고 |
|------|--------|------|
| 프롬프트 **텍스트** 사용 | 안전 | CC0 퍼블릭 도메인 |
| 회사 **로고/상표** 사용 | 주의 | 비교·논평은 가능, 브랜딩 사용 금지 |
| "공식 OO 프롬프트" 표현 | 위험 | 공식 사칭 오해 → "공개된/유출된"으로 표기 |
| 서비스명에 타사 브랜드 포함 | 위험 | 예: "ChatGPT프롬프트닷컴" 불가 |
| 원본 저장소 출처 표기 | 권장 | 법적 의무는 없으나 신뢰도 상승 |

---

## 참고 링크

- 포크 저장소: https://github.com/bmshin94/system_prompts_leaks
- 원본 저장소: https://github.com/asgeirtj/system_prompts_leaks
- 라이선스: CC0 1.0 Universal — https://creativecommons.org/publicdomain/zero/1.0/
- 저장소 내 길잡이: `README.md`, `Anthropic/README.md`, `GLM/README.md`
