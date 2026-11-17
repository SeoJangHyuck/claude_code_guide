# 챕터 5: .claude 폴더 구조 심화 (9슬라이드 / 10분)

> 톤 가이드: 청중에 비개발자 비중이 큼. 익힐 순서 — **CLAUDE.md → skills → rules**가 메인. settings.json/hooks는 후순위(짧게). subagents·MCP·plugins은 1분 내 압축.

> 슬라이드에는 헤드라인과 짧은 항목만 둔다. 조건·예외·설정 키·OS별 주의·버전·문서 링크는 슬라이드마다 "근거·세부 (슬라이드에서 옮김)"에 모았다.

> 모든 코드 예시는 2026-11 기준 (Claude Code v2.1.326) 공식 형식 준수. 슬라이드 코드 블록은 실습 폴더 `examples/chapter5` 예제 파일의 줄을 글자 그대로 옮긴 것이다. 비개발자에게 뜻 없는 설정 줄은 슬라이드에서 뺐고(남은 줄은 그대로), 뺀 줄은 슬라이드마다 "근거·세부"에 "실제 파일엔 이 줄도 있음"으로 적었다. 5-5는 코드 대신 한국어 요약 상자를 두고, 원래 JSON은 5-5 "근거·세부"로 옮겼다. 5-7·5-8의 `#` 안내 줄은 슬라이드 설명용(실습 파일에는 없음).

> 용어(덱 전체 통일): 프로젝트 → "작업 폴더"(= VS Code에서 연 폴더), hook = "정해진 순간 자동 실행되는 동작"(짧게 "자동 실행"), 권한 = "권한 설정(허용·금지 목록)", subagent = "보조 작업자", MCP = "외부 서비스 연결", 마켓플레이스 = "팀 플러그인 목록"(동작은 "등록"). 슬라이드에서는 세션 → "대화", 호출 → "꺼내 씀", 로드 → "읽힘".

(장 표지 부제: "주요 7가지 요소 — 익힐 순서: CLAUDE.md → skills → rules." — 이전 표기 "우선순위는 …"는 어느 규칙이 이기는지(적용 순서)로 읽혀 바꿈)

---

## 슬라이드 5-1 — 전체 폴더 트리 (1분 30초)

**핵심 메시지**: ".claude 폴더 = Claude Code의 설정 보관함. 7가지 요소 중 먼저 익힐 것은 ① CLAUDE.md ② skills ③ rules."

**본문 콘텐츠**:

```
.claude 폴더 = Claude Code의 설정 보관함
7가지 요소 중 먼저 익힐 것은 ①②③. 나머지는 익숙해진 뒤에.

내 작업 폴더/  (VS Code에서 연 폴더)
├── .claude/
│   ├── CLAUDE.md                   ① 작업 폴더의 헌법 (매번 자동으로 읽힘)
│   ├── skills/                     ② 반복 작업 절차서 (필요할 때 꺼내 씀)
│   │   └── 내-skill-이름/
│   │       └── SKILL.md
│   ├── rules/                      ③ 주제·폴더별 규칙
│   │   └── 내-rule-이름.md
│   ├── settings.json               ④ 권한 설정 + hook(정해진 순간 자동 실행되는 동작)
│   ├── settings.local.json         (개인 설정 파일)
│   └── agents/                     ⑤ subagent (보조 작업자)
│       └── 내-subagent-이름.md
├── .mcp.json                       ⑥ MCP (외부 서비스 연결)
├── my-plugin/                      ⑦ plugin (나눠 줄 묶음 원본 — 이 자리에선 동작 안 함)
│   ├── .claude-plugin/plugin.json
│   └── skills/ 등
└── (엑셀·보고서 등 내 파일)

작업 폴더째 공유(개인 설정 파일 제외) → 동료도 같은 설정
```

**발표 노트 (1분 30초)**:
> "Claude Code 설정은 대부분 .claude 폴더에 모입니다. 맨 위 '내 작업 폴더'는 VS Code에서 연 바로 그 폴더예요. 엑셀·보고서 같은 내 파일은 지금처럼 작업 폴더에 두고, .claude 폴더에는 설정만 넣습니다. MCP 설정인 .mcp.json은 작업 폴더 바로 안(루트)에, 나만 쓰는 전역 설정은 홈 폴더의 ~/.claude에 있고요. 오늘은 주요 요소 7가지를 하나씩 짧게 보겠습니다.
>
> 익힐 순서가 중요합니다. ① 작업 폴더의 헌법 CLAUDE.md, ② 반복 작업 절차서 skills, ③ 주제별 규칙 rules — 이 셋이 가장 자주 손대는 것들이에요. 비개발자 분도 이 셋만 알아도 90%입니다.
>
> ④ 권한 설정과 hook — hook은 정해진 순간 자동 실행되는 동작입니다 — ⑤ 보조 작업자 subagent, ⑥ 외부 서비스 연결 MCP — 이건 좀 더 익숙해진 다음에. ⑦ plugin은 skill·subagent·hook·MCP를 별도 폴더 하나로 묶어 동료에게 나눠줄 때 씁니다. 그림의 my-plugin/은 나눠 줄 묶음 원본이라 이 자리에 두기만 해서는 동작하지 않습니다. 받는 쪽이 설치하거나 skills 폴더에 넣어야 동작하는데, 방법은 7장에서 봅니다. rules와 CLAUDE.md는 plugin에 안 들어가고 작업 폴더째 공유합니다.
>
> 한 가지 팁만 — 이 작업 폴더를 통째로 공유하면, git 저장소에 올리든 폴더째 묶어 보내든, 동료도 같은 설정을 받아 씁니다. 어느 쪽이든 개인 설정 파일인 settings.local.json은 빼고요. 동료는 처음 열 때 폴더 신뢰와 MCP 서버 승인을 한 번 하면 됩니다. 사내 공유의 출발점이 바로 이 폴더예요."

**근거·세부 (슬라이드에서 옮김)**:
- '작업 폴더' = VS Code에서 연 폴더 = 공식 문서의 프로젝트 루트(project root). 이 덱은 '프로젝트'(연구원에게는 연구 과제로 읽힘) 대신 '작업 폴더'라고 부른다. 원래 트리 표기: "프로젝트/", "(그 외 일반 프로젝트 파일)", 헤드라인 ".claude 폴더 = Claude Code의 작업 공간"(내 파일까지 .claude에 넣어야 하는 것으로 읽혀 "설정 보관함"으로 바꿈).
- 요소 위치: ①~⑤는 `.claude/` 안, ⑥ `.mcp.json`은 프로젝트 루트, ⑦ 플러그인은 `.claude/`와 별개인 폴더.
- hook 풀이: "정해진 순간 자동 실행되는 동작"(덱 전체 통일 표현). 검사·자료 첨부·차단은 hook이 하는 일의 예다("…execute automatically at specific points in Claude Code's lifecycle." https://code.claude.com/docs/en/hooks). 원래 트리 표기: "권한 + hook(자동 검사) 설정".
- CLAUDE.md는 `./.claude/CLAUDE.md` 또는 `./CLAUDE.md`(루트) 둘 다 공식 지원(5-2 참고). https://code.claude.com/docs/en/memory
- ③ rules는 paths(파일 맨 위 설정)로 적용 경로를 한정할 수 있다(5-4 참고). ④ settings.json에는 권한·환경 변수·hooks를 적는다.
- `settings.local.json`: 개인용이라 커밋·공유에서 뺀다. Claude Code가 이 파일을 처음 쓸 때는 자동으로 git 제외 목록에 넣지만, 직접 만들었다면 `.gitignore`에 직접 추가한다. https://code.claude.com/docs/en/settings
- 공유 범위: `.claude/` + 루트 `.mcp.json`(+ 루트에 둔 경우 `CLAUDE.md`)을 프로젝트 저장소에 커밋하면 동료가 CLAUDE.md·rules·settings(권한·hook)·skills·subagents·MCP 설정을 함께 받는다. 동료는 처음 열 때 폴더 신뢰(Trust)와 MCP 서버 승인을 한다.
- ⑦ my-plugin/ (5차 검수 F3): 플러그인 폴더 구조는 `.claude-plugin/plugin.json` + 같은 루트의 `skills/` · `agents/` · `hooks/hooks.json` · `.mcp.json`. 프로젝트 안에 두기만 해서는 로드되지 않는다. 마켓플레이스로 설치하거나, 폴더째 `.claude/skills/`(저장소로 공유) 또는 `~/.claude/skills/`(나만 사용) 아래에 두면 로드되고, 한 세션만 시험할 때는 `claude --plugin-dir`를 쓴다("To share a plugin through a repository, list it under `enabledPlugins` in `.claude/settings.json` or place it under `.claude/skills/`."). https://code.claude.com/docs/en/plugins/loading
- ⑦ 트리 표기(최종 검수 V-07): 원래 "(배포용 묶음 — 설치해야 동작)"은 7장(skills 폴더에 넣기만 하면 동작)과 어긋나 "(나눠 줄 묶음 원본 — 이 자리에선 동작 안 함)"으로 바꿨다. skills 폴더 플러그인은 설치 단계 없이 로드된다("…loads each one when a session starts, with no flag and no install step." https://code.claude.com/docs/en/plugins/create).
- 하단 공유 문구(원래 ".claude/와 .mcp.json을 프로젝트 폴더째 공유 → 동료도 같은 설정 (개인용 파일 제외)"): 작업 폴더째 공유하면 그 안의 `.claude/`와 `.mcp.json`이 함께 간다. 개인 설정 파일 = `settings.local.json`.

**시각 표현 메모**:
- 폴더 트리 한 화면. 7요소 번호·강조색. 맨 위 줄에 "(VS Code에서 연 폴더)".
- ①②③ 강한 강조색 (메인 3종), ④⑤⑥⑦은 옅은 색.
- ⑦ my-plugin/ 설명에 "이 자리에선 동작 안 함" 표시.
- 하단 한 줄: "작업 폴더째 공유(개인 설정 파일 제외) → 동료도 같은 설정".

---

## 슬라이드 5-2 — ① CLAUDE.md (1분 30초)

**핵심 메시지**: "작업 폴더의 헌법. 한 번 적어두면 대화를 시작할 때마다 자동으로 읽힘(강제 장치는 아님)."

**본문 콘텐츠**:

```
① CLAUDE.md — 작업 폴더의 헌법
대화를 시작할 때마다 자동으로 읽히는 지침. 따로 부를 필요 없음.

  [정의] 매번 알려 줄 내용을 적는 텍스트 파일
  • 위치: 작업 폴더 또는 그 안 .claude/
  • 분량: 200줄 이하 권장
  • 내용: 글쓰기 규칙·폴더 설명·자주 쓰는 작업
  • 강제 장치는 아님 — 꼭 막을 일은 hook·권한 설정으로

  ──────────────────────────────────────────

  # 우리 정책 연구 프로젝트 가이드

  ## 글쓰기 규칙
  - 추측 표현(예상된다 등) 금지 — 근거 출처 필수

  ## 폴더 구조
  - reports/   : 정기 보고서·정책 브리핑 (.md)
  - data/      : 원본 엑셀·CSV·PDF
  - minutes/   : 회의록 (.md)
  - drafts/    : 발송 전 초안 (메일 등)

  ## 자주 쓰는 작업
  - "주간 동향 정리해줘"     → 주간 다이제스트
  - "회의록 → 담당자 메일"   → 후속 메일 초안

  ──────────────────────────────────────────

  분량 관리: 길어지면 절차는 skill로, 폴더별 규칙은 rules로 분리
```

**발표 노트 (1분 30초)**:
> "첫 번째, CLAUDE.md입니다. .claude 폴더 안에 마크다운 파일 하나 두는 거예요. 메모장으로도 열리는 텍스트 파일입니다 (작업 폴더 바로 안에 둬도 공식 지원, 취향 차이). 대화를 시작할 때마다 Claude Code가 알아서 읽습니다. 따로 부를 필요 없어요.
>
> 여기에 뭘 적나? 매번 똑같이 알려줘야 하는 것들요. 우리 팀 글쓰기 규칙, 폴더마다 무엇을 두는지, 자주 하는 작업 같은 거요. 개발 프로젝트라면 빌드·테스트 명령도 여기 적습니다. 적어 놓으면 다음부터 안 알려줘도 대부분 알아서 따릅니다. 다만 강제는 아니어서, 반드시 지켜야 하는 건 hook이나 권한 설정으로 막습니다.
>
> 한 가지 주의 — 200줄이 넘어가면 길어요. 다단계 절차나 가끔 필요한 작업은 다음에 볼 'skill'로 빼는 게 좋습니다. 그리고 특정 폴더에만 적용되는 규칙은 그 다음에 볼 'rules'로 빼고요. 이 예시에서도 보고서에만 해당하는 문체·인용 표기 규칙은 rules 쪽으로 옮겨 뒀습니다."

**근거·세부 (슬라이드에서 옮김)**:
- 정확한 위치: `./.claude/CLAUDE.md` 또는 `./CLAUDE.md`(프로젝트 루트). 둘 다 공식 지원.
- 로드: 세션(대화) 시작 때 자동, 별도 호출 없음("Claude reads them at the start of every session").
- 적는 내용(원래 슬라이드 표현): 빌드·테스트 명령, 코딩·문서 컨벤션, 디렉토리 구조. 문서도 build commands, conventions, project layout, "always do X" rules를 예로 든다.
- 분량: "target under 200 lines per CLAUDE.md file. Longer files consume more context and reduce adherence." 200줄을 넘으면 다단계 절차는 skill로, 일부 영역에만 해당하는 규칙은 paths를 지정한 rule로 나눈다.
- 강제 장치 아님: "Claude treats CLAUDE.md files as context, not enforced configuration." 반드시 막을 일은 hook(PreToolUse)·권한 설정(deny 규칙)으로.
- 코드 예시: 실습 파일 `.claude/CLAUDE.md`와 글자 그대로 같다(비개발자용으로 머리글을 "글쓰기 규칙"·"폴더 구조"로 실습 파일과 함께 바꿈).
- 문서: https://code.claude.com/docs/en/memory

**시각 표현 메모**:
- 상단: 정의 박스
- 하단: 실제 CLAUDE.md 예시 (가상의 연구원 프로젝트 톤)

---

## 슬라이드 5-3 — ② skills (1분 30초)

**핵심 메시지**: "반복 작업 절차서. description(skill 설명)이 Claude가 알아서 꺼내 쓰는 기준."

**본문 콘텐츠**:

```
② skills — 반복 작업 절차서
요청이 skill 설명과 맞으면 Claude가 알아서 꺼내 씀. 입력창 /이름으로도 가능.

  [정의] 필요할 때만 꺼내 쓰는 절차
  • 위치: .claude/skills/<이름>/SKILL.md
  • 적합: 여러 단계 작업·반복 업무
  • 맨 위 description(skill 설명)에 "언제 쓰는지" 명확히

  ──────────────────────────────────────────

  ---
  name: weekly-policy-digest
  description: 매주 정책기관 4곳의 신규 자료를
    수집·요약해 다이제스트로 만든다.
    "주간 동향" 요청 시 사용.
  ---

  ## 절차
  1. 4개 기관 사이트에서 신규 자료 목록 수집
  2. 각 자료 요약 (subagent 4개 병렬)
  3. reports/주간동향-{날짜}.md 로 저장

  ──────────────────────────────────────────

  CLAUDE.md vs skills: CLAUDE.md는 매번 읽힘, skill은 필요할 때만. 매번 필요하지 않은 내용은 skill로.
```

**발표 노트 (1분 30초)**:
> "두 번째, skill입니다. 오늘 발표의 핵심 도구예요. 여러 단계 작업을 한 번 정리해두는 거예요.
>
> 보시면 맨 위 --- 사이에 설정 부분(frontmatter)이 있고, 그 아래에 절차가 있습니다. 이 설정의 'description'이 가장 중요한데요, Claude가 사용자 요청을 듣고 '이 skill을 자동으로 부를까?' 결정하는 기준이 됩니다.
>
> 예시는 '매주 정책기관 동향 다이제스트' skill입니다. 한 번 만들어 두면 다음 주에 '주간 동향 정리해줘' 한 마디로 Claude가 description을 보고 이 skill을 꺼내 4기관 수집·요약·저장까지 합니다. 확실히 부르고 싶으면 입력창에 /weekly-policy-digest 라고 직접 입력하면 됩니다. 참고로 skill이 날짜에 맞춰 스스로 돌지는 않아요. 매주 월요일 자동 실행은 예약 작업으로 따로 설정합니다.
>
> 슬라이드에서는 뺐지만 실제 파일에는 allowed-tools 줄도 있습니다. allowed-tools는 이 skill을 호출한 그 턴 동안(다음 메시지를 보내면 해제) 확인 없이 쓸 도구 목록이고, 사용 제한은 아닙니다. 목록에 없는 도구도 쓸 수 있고, 그때는 평소 권한 설정대로 처리됩니다. Manual 모드라면 승인 창이 뜨고, VS Code 기본인 Auto 모드라면 대부분 승인 창 없이 진행되면서 필요한 작업은 별도 검토 모델(분류기)이 실행 전에 확인합니다.
>
> CLAUDE.md와 차이는 — CLAUDE.md는 '항상' 읽히고, skill은 '필요할 때만' 호출됩니다. 매번 적용할 게 아니면 skill로 빼는 게 맞아요."

**근거·세부 (슬라이드에서 옮김)**:
- 로드: 필요할 때만 — Claude가 description을 보고 자동 호출하거나, 사용자가 입력창에 `/weekly-policy-digest`처럼 `/이름`으로 직접 호출. https://code.claude.com/docs/en/skills (원래 리드: "요청이 description과 맞으면 Claude가 알아서 호출. /이름으로 직접 호출도 가능.")
- 슬라이드 코드에서 뺀 줄(실제 파일엔 이 줄도 있음): `allowed-tools: Read, Write, WebFetch` — `---` 바로 위, description 다음 줄. 실습 파일 `.claude/skills/weekly-policy-digest/SKILL.md`, `my-plugin/skills/weekly-policy-digest/SKILL.md`.
- skill은 폴더 단위(`.claude/skills/<이름>/SKILL.md` + 보조 파일). 맨 위 설정(frontmatter, `---` 사이) 필드는 모두 선택이고 description을 권장. 커스텀 commands는 skills로 통합됨.
- 적합(원래 슬라이드 표현): 다단계 절차, 외부 도구 호출, 반복 작업.
- `allowed-tools`(5차 검수 F2 반영): 그 skill을 호출한 턴 동안 확인 없이 쓸 도구. 사용 제한이 아니며 목록 밖 도구는 평소 권한 설정을 따른다("your permission settings still govern tools that are not listed"). v2.1.283부터 VS Code·터미널 대화의 기본 시작 모드는 Auto — 승인 창 대신 별도 분류기가 실행 전에 검토("A separate classifier model reviews actions before they run"). Manual 모드에서는 승인 창. https://code.claude.com/docs/en/permission-modes

**시각 표현 메모**:
- 맨 위 설정(frontmatter)과 본문을 구분선으로 분리.
- 하단 비교 박스(CLAUDE.md vs skills)로 핵심 강조.

---

## 슬라이드 5-4 — ③ rules (1분)

**핵심 메시지**: "주제·폴더별 규칙 파일. 지정한(paths) 폴더·파일을 다룰 때만 읽히고, 지정 안 하면 매번 읽힘."

**본문 콘텐츠**:

```
③ rules — 주제·폴더별 규칙
지정한 폴더·파일을 다룰 때만 읽힘 (지정 안 하면 매번).

  [정의] CLAUDE.md를 영역별로 나눈 파일
  • 위치: .claude/rules/<이름>.md
  • paths(맨 위 설정)에 폴더·파일 지정
  • 예: 보고서 폴더 전용 문체 규칙

  ──────────────────────────────────────────

  파일: .claude/rules/report-style.md

  ---
  paths:
    - "reports/**/*.md"
  ---

  ## 보고서 작성 규칙

  - 항상 "~다" 체로 작성
  - 모든 인용에 파일 경로 + 줄번호 명시
  - 분량 2장 이내
  - "결론" 섹션 필수

  ──────────────────────────────────────────

  CLAUDE.md vs rules: CLAUDE.md는 매번, rules는 지정한 파일을 다룰 때만 읽힘 → Claude가 읽는 양 절약.
```

**발표 노트 (1분)**:
> "세 번째, rules입니다. CLAUDE.md와 비슷하지만 결정적 차이가 있어요. CLAUDE.md는 프로젝트 전체에 매 세션마다 자동 로드되는 헌법이라면, rules는 위쪽 'paths'에 적은 경로의 파일을 Claude가 읽거나 수정할 때만 자동 로드됩니다. paths를 빼면 CLAUDE.md처럼 매 세션 로드되니, 영역별 규칙엔 꼭 paths를 넣으세요. 그리고 이 --- 부분이 파일 맨 첫 줄에 있어야 paths가 적용됩니다.
>
> 예시처럼 'reports 폴더의 마크다운 파일을 다룰 때만 이 규칙이 발동된다' 이런 식이에요. 보고서 작업할 때만 적용되는 글쓰기 톤, 코드 폴더에서만 적용되는 컨벤션 — 영역별로 규칙을 쪼개 두면 컨텍스트도 가벼워지고 CLAUDE.md도 비대해지지 않습니다."

**근거·세부 (슬라이드에서 옮김)**:
- 로드 조건: paths가 있으면 Claude가 매칭 파일을 Read·Write·Edit로 다룰 때, 없으면 세션 시작 때 `.claude/CLAUDE.md`와 같은 우선순위로 로드("Rules without `paths` frontmatter are loaded at launch with the same priority as `.claude/CLAUDE.md`").
- 파일 첫 줄부터 `---`로 시작해야 paths가 적용된다(원래 코드 위 표시: "첫 줄부터 --- 로 시작").
- 원래 리드: "paths에 적은 파일을 다룰 때만 읽힘 (paths가 없으면 매번 읽힘)." 비교 박스 원래 표현: "rules는 paths에 맞는 파일을 다룰 때만 읽힘".
- 슬라이드 코드에서 뺀 줄(실제 파일엔 이 줄도 있음): `(reports/ 폴더의 .md 파일 작업 시 자동 로드)` — "## 보고서 작성 규칙" 바로 아래 줄. 실습 파일 `.claude/rules/report-style.md`. paths 값 `"reports/**/*.md"` = reports/ 폴더(하위 폴더 포함)의 .md 파일.
- 적합(원래 슬라이드 표현): 보고서·코드 등 영역별 형식·톤 규칙. CLAUDE.md 비대화 방지 — 영역별 분리, 컨텍스트 절감.
- 출처(원래 슬라이드 좌측 하단 표기): https://code.claude.com/docs/en/memory

**시각 표현 메모**:
- 상단: rules 정의 + 실제 예시(맨 위 설정 `paths` 강조)
- 하단: CLAUDE.md vs rules 한 줄 비교 박스

---

## 슬라이드 5-5 — ④ settings.json + hooks (1분)

**핵심 메시지**: "자주 하는 실수를 1차로 거르는 설정 — 권한 설정(허용·금지 목록) + hook(정해진 순간 자동 실행되는 동작)."

**본문 콘텐츠**:

```
④ settings.json + hooks — 권한 설정·자동 실행
자주 하는 실수를 1차로 거르는 설정.

  [정의] 권한 설정 + hook
  • 위치: .claude/settings.json
  • 권한 설정(허용·금지 목록): allow = 묻지 않고 허용, deny = 금지
  • hook: 정해진 순간 자동 실행되는 동작

  ──────────────────────────────────────────

  [예시] settings.json에 적은 것 (요약)
  • 허용: 부산시 사이트 읽기 · reports 폴더 수정
  • 금지: 비밀 설정 파일(.env) 읽기 · 파일 삭제 명령
  • 자동 실행: 파일을 쓰거나 고친 직후 → 출처 표기 검사
  실제 파일: 실습 폴더 examples/chapter5/.claude/settings.json
```

**발표 노트 (1분)**:
> "네 번째, settings.json입니다. 한 마디로 Claude가 묻지 않고 해도 되는 일, 하면 안 되는 일, 그리고 정해진 순간 자동으로 실행할 일을 적는 파일이에요. 위험한 명령은 차단하고, 매번 잊어버리는 검증 작업은 자동으로 돌게 합니다.
>
> 오른쪽 상자가 실습 폴더 settings.json의 내용을 우리말로 요약한 겁니다. 허용(allow)에는 부산시 사이트 자료 가져오기와 reports 폴더 수정을 넣었습니다. allow에 넣은 작업은 Manual 모드에서는 승인 창 없이, VS Code 기본인 Auto 모드에서는 별도 검토 없이 바로 실행됩니다. 금지(deny)에는 비밀 설정 파일인 '.env 파일 읽기'와 파일 삭제 명령인 'rm 명령'을 넣었습니다. 경로를 붙인 쓰기 허용 규칙은 Write(경로)가 아니라 Edit(경로)로 적어야 실제로 적용돼요. 그리고 '보고서를 저장한 직후엔 자동으로 출처 검사 스크립트 돌려라' 같은 건 hook으로 겁니다. 이렇게 한 번 설정해두면 매번 말하지 않아도 됩니다. 다만 Bash 차단 규칙은 명령 문구를 비교하는 방식이라 돌려 쓴 명령까지 다 막지는 못해요. 그래서 슬라이드에 '1차로' 거른다고 적었습니다. 운영체제 수준에서 막아야 하면 sandbox를 쓰는데, sandbox는 macOS·Linux·WSL2에서 셸 명령에만 걸리고 Windows에선 WSL2 안에서 써야 해요. 그리고 Windows에서는 Git for Windows가 설치돼 있어야 이런 bash hook이 제대로 실행됩니다. 없으면 hook이 PowerShell로 실행돼서 이 예시는 실패할 수 있어요.
>
> 6장 시연에도 비슷한 검증 hook이 나옵니다. 거기서는 PPT를 스크립트(Bash)로 만들기 때문에 matcher(어떤 작업에 반응할지)를 Bash로 잡고, 검사 결과는 trigger.log에 기록해요. PostToolUse는 저장 '뒤'에 도는 검사라 저장 자체를 막지는 못하고, 막아야 할 땐 저장 '전'에 도는 PreToolUse를 씁니다. 디테일은 익숙해진 다음에 손대셔도 늦지 않아요."

**근거·세부 (슬라이드에서 옮김)**:
- 원래 슬라이드 코드(실습 파일 `examples/chapter5/.claude/settings.json` 전체, 글자 그대로). 슬라이드에는 이 JSON 대신 한국어 요약 상자를 둔다.

  ```json
  {
    "permissions": {
      "allow": ["WebFetch(domain:www.busan.go.kr)", "Edit(./reports/**)"],
      "deny":  ["Read(./.env)", "Bash(rm *)"]
    },
    "hooks": {
      "PostToolUse": [{
        "matcher": "Edit|Write",
        "hooks": [{
          "type": "command",
          "command": "bash \"$CLAUDE_PROJECT_DIR\"/.claude/hooks/check_sources.sh"
        }]
      }]
    }
  }
  ```

- 요약 상자와 JSON의 대응: 허용 = `permissions.allow` — `WebFetch(domain:www.busan.go.kr)`(부산시 사이트 읽기, 이 도메인만), `Edit(./reports/**)`(reports 폴더 수정 — Edit 규칙은 새로 쓰기·고치기 등 파일을 바꾸는 모든 기본 도구에 적용). 금지 = `permissions.deny` — `Read(./.env)`(비밀 설정 파일 읽기), `Bash(rm *)`(파일 삭제 명령 rm). 자동 실행 = `hooks.PostToolUse` + matcher `Edit|Write` → `check_sources.sh`(저장한 파일이 reports/ 아래 .md·.txt이고 숫자가 있는데 '출처' 표기가 없으면 Claude에 알림). https://code.claude.com/docs/en/permissions
- 원래 정의 박스 표현: "permissions: allow = 바로 허용, deny = 금지", "hooks: 정해진 순간에 자동으로 도는 검사", "예: 보고서 저장 직후 출처 표기 검사". 원래 헤드라인 "④ settings.json + hooks — 안전장치"는 덱 전체 hook 표현 통일("자동 검사·장치·안전장치"로 부르지 않음)에 따라 바꿨다.
- 권한 규칙: 경로를 붙인 쓰기·수정 규칙은 `Write(경로)`가 아니라 `Edit(경로)`로 적는다(`Write(경로)`는 아무것에도 매칭되지 않음, v2.1.210부터 시작 시 경고). 읽기는 `Read(경로)`. 프로젝트 allow 규칙과 설정 파일의 hook은 폴더 신뢰 수락 뒤에 적용된다. https://code.claude.com/docs/en/permissions
- allow의 의미(5차 검수 F2 반영): Manual 모드에서는 승인 창 없이, Auto 모드(v2.1.283부터 VS Code 기본)에서는 분류기 검토 없이 바로 실행("Actions matching your allow, ask, or deny rules resolve immediately"). https://code.claude.com/docs/en/permission-modes
- "1차로" 거른다는 단서: Bash deny는 명령 문구 비교라 보안 경계가 아니다. OS 수준 차단은 sandbox — macOS·Linux·WSL2에서만 동작하고 셸 명령에만 적용(네이티브 Windows에서는 WSL2 안에서 실행). https://code.claude.com/docs/en/sandboxing
- hook 시점: 세션 시작·프롬프트 제출·도구 실행 전후·응답 종료 등 정해진 시점(SessionStart · UserPromptSubmit · PreToolUse · PostToolUse · Stop 등 33개 이벤트). https://code.claude.com/docs/en/hooks
- 예시 hook: PostToolUse + matcher(어떤 작업에 반응할지) `Edit|Write` → 저장 직후 `check_sources.sh` 실행. 문제가 있으면 종료 코드 2로 끝나고 stderr 내용이 Claude에 전달된다. 이미 저장된 뒤라 저장을 막지 못한다 — 저장 전에 막으려면 PreToolUse. `$CLAUDE_PROJECT_DIR`는 세션을 시작한 프로젝트 루트 경로.
- Windows: Git for Windows 설치 전제. 없으면 hook이 PowerShell로 실행되어 bash 스크립트 hook이 실패할 수 있다.
- 실습: hook 스크립트(`check_sources.sh`·`check_sources.py`)와 시험 방법은 실습 폴더 `examples/chapter5/README.md`.

**시각 표현 메모**:
- JSON 코드 대신 한국어 요약 상자(허용·금지·자동 실행) + 아래 한 줄 "실제 파일: 실습 폴더 examples/chapter5/.claude/settings.json".
- 정의 박스 3줄(위치·권한 설정·hook)로 비개발자 의미 전달.

---

## 슬라이드 5-6 — ⑤ agents/ — subagent (50초)

**핵심 메시지**: "subagent = 보조 작업자. 많은 자료 훑기·동시 처리에 적합."

**본문 콘텐츠**:

```
⑤ agents/ — subagent (보조 작업자)
별도 공간에서 일하고 결과 요약만 돌려줌. 많은 자료 훑기·동시 처리에 적합.

  [정의] 독립된 보조 작업자
  • 위치: .claude/agents/<이름>.md
  • 내 대화가 길어지지 않음
  • 예: 기관 사이트 4곳 동시 수집

  ──────────────────────────────────────────

  ---
  name: site-crawler
  description: 한 사이트의 자료 목록을 수집·요약한다.
  ---

  당신은 정책기관 사이트 수집 전문가입니다.
  지정된 URL에서 지난 주 신규 자료를 모두 가져와
  각 자료의 핵심 3줄을 정리해 반환합니다.

  ──────────────────────────────────────────

  skill vs subagent: skill은 기본적으로 지금 대화 안에서, subagent는 별도 공간에서 실행한 뒤 요약만 전달.
```

**발표 노트 (50초)**:
> "다섯 번째, subagent입니다. 보조 작업자라고 보시면 됩니다. .claude 안의 agents 폴더에 파일 하나로 정의합니다. skill과 비슷해 보이지만 별도 작업 공간에서 독립적으로 일하다 결과만 반환합니다. 정책기관 4곳을 동시에 수집해야 할 때처럼 많은 자료를 훑거나 동시에 처리할 때 적합해요. 한 줄 기준 — 많은 자료 훑기·동시 처리가 필요하거나 내 대화가 길어지는 걸 막고 싶으면 subagent, 그냥 절차 재사용이면 skill. 슬라이드에서는 뺐지만 실제 파일에는 쓸 도구(tools)와 쓸 모델(model)을 정하는 줄도 있습니다. 참고로 skill도 맨 위 설정에 context: fork를 넣으면 별도 공간에서 돌릴 수 있습니다."

**근거·세부 (슬라이드에서 옮김)**:
- 실행: 별도 컨텍스트(작업 공간)에서 독립 실행하고 결과 요약만 메인 대화로 반환. 적합: 큰 탐색 / 병렬 처리 / 메인 대화 보호. https://code.claude.com/docs/en/sub-agents
- 예(원래 슬라이드 표현): 4개 사이트 동시 크롤링, 5명 담당자 메일 동시 작성. 직전 표현: "큰 탐색·동시 처리에 적합", "메인 대화가 길어지지 않음", 헤드라인 "subagent (따로 일하는 작업자)".
- 슬라이드 코드에서 뺀 줄(실제 파일엔 이 줄도 있음): `tools: WebFetch, Read, Write`(이 subagent가 쓸 수 있는 도구 — 빼면 쓸 수 있는 도구를 모두 물려받음), `model: sonnet`(쓸 모델 — 빼면 Claude Code가 정한 순서대로 고름). description 다음, `---` 바로 위 두 줄. 실습 파일 `.claude/agents/site-crawler.md`. https://code.claude.com/docs/en/sub-agents
- skill도 맨 위 설정(frontmatter)에 `context: fork`를 지정하면 별도 컨텍스트에서 실행된다. https://code.claude.com/docs/en/skills

**시각 표현 메모**:
- 상단: subagent 정의 예시
- 하단: skill vs subagent 한 줄 비교 박스

---

## 슬라이드 5-7 — ⑥ MCP (50초)

**핵심 메시지**: "MCP = 외부 서비스 연결 표준. 등록해 두면 Claude가 알아서 골라 씀."

**본문 콘텐츠**:

```
⑥ MCP — 외부 서비스 연결
외부 서비스를 Claude가 직접 쓰게 해 주는 연결 표준.

  [정의] 등록해 두면 Claude가 알아서 골라 씀
  • 위치: 작업 폴더 바로 안 .mcp.json
  • 연결: 처음 한 번 승인 + 각자 로그인
  • 예: Notion · Slack · Google Drive · GitHub

  ──────────────────────────────────────────

  # 등록: .mcp.json
  {
    "mcpServers": {
      "notion": {
        "type": "http",
        "url": "https://mcp.notion.com/mcp"
      }
    }
  }

  # 연결: 승인 → /mcp에서 Authenticate → 로그인

  # 사용: 말로 요청
  "이번 주 회의록 Notion에서 가져와 요약해줘"
```

**발표 노트 (50초)**:
> "여섯 번째, MCP입니다. 외부 서비스 연결이라고 기억하시면 됩니다. Claude Code가 외부 시스템에 직접 손을 뻗을 수 있게 해주는 다리예요. MCP는 Anthropic이 2024년 11월 공개한 오픈 표준이고, 2025년 12월 Linux Foundation 산하 Agentic AI Foundation에 기증됐습니다. GitHub MCP 붙이면 PR을 직접 읽고 답을 달고, Slack MCP 붙이면 채널 메시지 정리하고, DB MCP 붙이면 직접 쿼리합니다. 예시는 Notion이 운영하는 원격 서버 주소를 등록한 거예요. 파일을 저장하고 새 세션을 열면, 파일을 만든 본인에게도 이 서버를 쓸지 승인 창이 한 번 뜹니다. 승인한 뒤 /mcp에서 notion을 골라 Authenticate를 누르면 브라우저 로그인으로 연결됩니다. 그다음부터는 '이번 주 회의록 Notion에서 가져와 요약해줘'처럼 말로만 요청해도 Claude가 notion MCP를 골라 씁니다. .mcp.json을 프로젝트 저장소에 커밋하면 동료도 같은 서버를 씁니다. 동료도 처음 열 때 승인 한 번, 로그인이나 토큰은 각자 해야 해요. 참고로 claude mcp add 명령으로 추가하면 기본은 나만 쓰는 local 범위라 .mcp.json에 안 들어갑니다. 팀과 나누려면 --scope project를 붙이세요. 이 claude mcp add는 터미널 명령이라, VS Code 확장만 설치했다면 CLI를 따로 설치해야 씁니다. VS Code 패널에서는 입력창에 /mcp를 입력해 여는 창의 서버 추가 기능으로도 등록할 수 있습니다(v2.1.261 이상)."

**근거·세부 (슬라이드에서 옮김)**:
- MCP = Model Context Protocol. Anthropic이 2024년 11월 공개한 오픈 표준이고, 2025년 12월 Linux Foundation 산하 Agentic AI Foundation에 기증됨(원래 슬라이드 표기: "현재 Linux Foundation 산하 재단 소속"). 역할: Claude가 외부 서비스 API를 직접 호출할 수 있도록 인증·요청·응답을 중간에서 처리.
- 범위: 프로젝트 루트 `.mcp.json` = project 범위(커밋해 공유). 작성자·동료 모두 첫 실행 때 서버 승인 후 연결, 로그인·토큰은 각자. `claude mcp add` 기본값은 개인용 local 범위(`.mcp.json`에 안 들어감, 팀 공유는 `--scope project`). https://code.claude.com/docs/en/mcp
- 연결 절차(원래 코드 주석): 새 세션 → 서버 승인 → `/mcp` → notion → Authenticate → 브라우저 로그인 → `/mcp`에 `notion ✔ Connected`. 이후에는 직접 부르지 않아도 Claude가 작업 맥락을 보고 등록된 MCP 중 필요한 것을 골라 호출.
- 코드 상자의 `#` 안내 줄(슬라이드 설명용, 실습 파일엔 없음) 직전 표기: "# ① 등록: 프로젝트 맨 위 .mcp.json", "# ② 연결: …", "# ③ 사용: …". 5장 요소 번호 ①~⑦과 겹치지 않게 번호를 뺐다. JSON 부분은 실습 파일 `examples/chapter5/.mcp.json`과 글자 그대로 같다. 위치 "작업 폴더 바로 안" = 프로젝트 루트(원래 "프로젝트 맨 위"). 원래 제목 "⑥ MCP 서버", 정의 "Claude가 알아서 골라 호출".
- 연결 대상(원래 슬라이드 표현): 평소 업무에 쓰는 SaaS·DB — Slack · Notion · Google Drive · GitHub · Confluence · Figma · PostgreSQL 등.
- VS Code: `claude mcp add`는 터미널 명령이라 CLI를 따로 설치해야 쓴다. VS Code 패널에서는 입력창 `/mcp` 창의 서버 추가 기능으로 등록 가능(v2.1.261 이상).

**시각 표현 메모**:
- json 코드블록 짧게 (등록 → 연결 → 사용 3단계 주석).
- 정의 박스에 대표 서비스 예시 한 줄.

---

## 슬라이드 5-8 — ⑦ plugins (50초)

**핵심 메시지**: "plugin = skill 등을 묶은 설치 꾸러미. skill·subagent·hook·MCP를 별도 폴더 하나로 묶어 배포·설치 (rules·CLAUDE.md·권한 설정 제외)."

**본문 콘텐츠**:

```
⑦ plugins — skill 등을 묶은 설치 꾸러미
skill·subagent·hook·MCP를 폴더 하나로 묶어 동료에게 배포. 여기서는 설치하는 쪽.

  [정의] 동료에게 나눠 주는 단위
  • 못 담는 것: rules·CLAUDE.md·권한 설정
  • 배포: zip · git · 마켓플레이스(팀 플러그인 목록)
  • VS Code: 입력창 /plugins → 마켓플레이스 등록 → Install
  → 직접 만들어 배포하는 방법은 7장

  ──────────────────────────────────────────

  # 만드는 쪽이 작성하는 이름표: .claude-plugin/plugin.json
  {
    "name": "research-team-plugin",
    "version": "1.0.0",
    "description": "정책 연구원 업무 자동화 묶음",
    "author": { "name": "BDI 데이터팀" }
  }
```

**발표 노트 (50초)**:
> "일곱 번째, plugin입니다. 지금까지 본 것 중 skill·subagent·hook·MCP를 한 묶음으로 패키징해서 동료에게 나눠주는 거예요. rules, CLAUDE.md, 권한 설정은 plugin에 못 넣으니 작업 폴더째 공유합니다. 그 지침을 꼭 plugin에 넣고 싶으면 skill로 옮기고, 경로 조건은 skill의 paths로 유지하면 됩니다. 만들 때는 .claude 폴더와 별도로 플러그인 폴더를 만들고, 그 바로 아래에 .claude-plugin/plugin.json과 skills·agents 폴더를 나란히 두면 됩니다. .claude-plugin 폴더 안에는 plugin.json만 넣어요. 설치하는 쪽은 VS Code 확장에서 입력창에 /plugins를 입력해 Manage plugins 화면을 열고, Marketplaces 탭에서 사내 마켓플레이스(팀 플러그인 목록) 주소를 등록한 다음 Plugins 탭에서 Install을 누르고, 나만 쓸지 이 저장소 전원에게 켤지 설치 범위를 고르면 됩니다. 터미널에서 claude를 실행해 쓰는 분은 그 대화 입력창에 /plugin install 다음에 '이름@마켓플레이스'를 입력해도 같습니다. 셸에 바로 치는 명령이 아니라 Claude Code 대화 입력창에 치는 명령이에요. 저장소 범위로 켜도 동료 PC에 자동 설치되지는 않아서 동료도 각자 한 번 설치합니다. zip이나 git으로 받은 폴더를 쓰는 방법은 챕터 7에서 봅니다. 참고로 실습 폴더의 examples/chapter5/my-plugin/에 이 구조 그대로(.claude-plugin/plugin.json + skills/) 예시를 넣어 뒀습니다. 이 폴더는 나눠 줄 원본이라 그 자리에 두기만 해서는 로드되지 않고, 설치하거나 폴더째 .claude/skills/ 아래에 넣어야 동작합니다(실습 폴더 README '직접 해 보기' 4번). .claude/ 안에 .claude-plugin/을 두면 플러그인으로 읽히지 않으니 꼭 별도 폴더로 만드세요. 위 슬라이드 예시는 '우리가 만든 자산을 묶으면' 어떻게 되는지 가상 예시입니다. 사내 공유의 가장 깔끔한 방식 — 챕터 7에서 더 자세히 보겠습니다."

**근거·세부 (슬라이드에서 옮김)**:
- 구조: 별도 플러그인 폴더 = `.claude-plugin/plugin.json` + 같은 루트의 `skills/` · `agents/` · `hooks/hooks.json` · `.mcp.json`. `.claude-plugin/` 안에는 plugin.json만("Only `plugin.json` goes inside `.claude-plugin/`. Components saved there don't load."). plugin.json은 선택이고, 두면 name만 필수. https://code.claude.com/docs/en/plugins/create
- 묶을 수 있는 자산: skills · subagents · hooks · MCP · commands 등. rules · CLAUDE.md · 권한 설정은 제외.
- 배포(원래 슬라이드 표현): zip 파일 / git 저장소(clone) / 마켓플레이스.
- 설치(마켓플레이스, 터미널에서 `claude`를 실행한 뒤 그 대화 입력창에 입력): 마켓플레이스 등록 후 `/plugin install <이름>@<마켓플레이스>` → 설치 범위(user·project·local) 선택. 본체는 `~/.claude/plugins/cache/`에 복사되고, 선택한 범위의 settings에는 `enabledPlugins` 항목만 기록된다. `/plugin install`은 셸 명령이 아니라 Claude Code 대화 입력창 명령이다(최종 검수 V-08). 셸에서 바로 설치하려면 `claude plugin install <이름>@<마켓플레이스>`("install with `/plugin install <plugin>@<marketplace>` in a session or `claude plugin install <plugin>@<marketplace>` in your shell"). https://code.claude.com/docs/en/plugins/install
- 슬라이드 코드에서 뺀 줄(최종 검수 V-08·가독성 검토): "# 설치 (터미널): 사내 마켓플레이스 추가 후", "/plugin install research-team-plugin@<마켓플레이스>". 덱 전체가 VS Code 경로를 쓰고, 바로 위 VS Code 줄의 `/plugins`와 한 글자 차이라 헷갈려서 VS Code 경로(정의 박스)만 남겼다. 원래 정의 박스 표기: "마켓플레이스(플러그인 목록)", "마켓플레이스 추가". 원래 제목: "여러 자산을 묶은 설치 꾸러미".
- VS Code 전체 경로: 입력창 `/plugins` → Manage plugins 화면 → Marketplaces 탭에서 마켓플레이스(팀 플러그인 목록) 등록 → Plugins 탭에서 Install → 설치 범위 선택(7장 4단계와 같은 경로). 공식 마켓플레이스(claude-plugins-official)는 터미널에서 대화형 세션을 처음 열 때 자동 추가되므로, VS Code만 쓰면 Marketplaces 탭에서 anthropics/claude-plugins-official을 먼저 추가한다. VS Code 확장만 설치하면 터미널에 `claude` 명령이 없으니, 터미널 명령은 CLI를 따로 설치해서 쓴다.
- 만드는 쪽(plugin.json 작성·zip·git·marketplace)은 챕터 7 사내 공유 4단계 중 2~4단계.
- my-plugin/이 그 자리에서 로드되지 않는 이유와 로드 방법(5차 검수 F3): 5-1의 근거·세부 참고.

**시각 표현 메모**:
- json 코드블록 짧게 (plugin.json만 — 터미널 설치 줄은 뺌).
- 정의 박스: 못 담는 자산 · 배포 방법 · VS Code 설치 경로 한 줄(7장 4단계 경로를 줄인 표현).

---

## 슬라이드 5-9 — 의사결정 트리 (1분)

**핵심 메시지**: "이걸 만들 때 어디에 넣지? — 위에서부터 처음 YES가 나오는 곳."

**본문 콘텐츠**:

```
   "이걸 만들 때 어디에 넣지?"
   위에서부터 차례로 — 처음 YES가 나오는 곳에 넣는다.

            자동화·재사용하고 싶다
                  │
                  ▼
   ┌──────────────────────────────────────┐
   │ Claude 판단과 상관없이                 │
   │ 꼭 돌릴 검사·막을 일?                  │ ── YES ──▶  hook·권한 설정
   └────────────┬─────────────────────────┘
                │ NO
                ▼
   ┌──────────────────────────────────────┐
   │ 매번 Claude가 알아야 할 지침?          │ ── YES ──▶  CLAUDE.md
   └────────────┬─────────────────────────┘
                │ NO
                ▼
   ┌──────────────────────────────────────┐
   │ 특정 폴더·파일에만 적용?               │ ── YES ──▶  rules
   └────────────┬─────────────────────────┘
                │ NO
                ▼
   ┌──────────────────────────────────────┐
   │ 반복 절차 · 가끔 쓰는 참고 자료?       │ ── YES ──▶  skill
   └────────────┬─────────────────────────┘
                │ NO
                ▼
   ┌──────────────────────────────────────┐
   │ 많은 자료 훑기 · 동시 처리?            │ ── YES ──▶  subagent
   └────────────┬─────────────────────────┘
                │ NO
                ▼
   ┌──────────────────────────────────────┐
   │ 외부 서비스 연결?                      │ ── YES ──▶  MCP
   └────────────┬─────────────────────────┘
                │ NO
                ▼
        해당 없음 → 대화로 요청
        (반복되면 skill로)

   ※ 묶어서 나눠 줄 땐 plugin — 단, CLAUDE.md·rules는
     작업 폴더째 공유(개인 설정 파일 제외)
```

**발표 노트 (1분)**:
> "정리 한 장입니다. 'Claude Code로 뭘 자동화하고 싶다'는 생각이 들면, 이 트리를 따라 내려오시면 됩니다.
>
> 먼저, Claude 판단과 상관없이 정해진 순간 꼭 돌려야 할 검사나 막아야 할 일? hook이나 권한 설정. 매번 Claude가 알아야 할 지침? CLAUDE.md. 특정 폴더에만? rules. 반복해서 쓰는 절차나 가끔 필요한 참고 자료? skill. 많은 자료를 훑거나 동시에 처리? subagent. 외부 서비스 연결? MCP. 어디에도 해당 없으면 그냥 대화로 요청하시면 되고, 같은 요청이 반복되면 skill로 저장하세요. 그리고 skill·subagent·hook·MCP를 동료에게 나눠주고 싶으면? plugin으로 묶습니다. CLAUDE.md와 rules는 plugin에 안 들어가니 작업 폴더째 공유하고요(개인 설정 파일은 빼고). plugin에 꼭 넣어야 하면 skill로 옮기고 paths로 경로 조건을 유지합니다.
>
> hook을 맨 위에 둔 이유가 있습니다 — CLAUDE.md·rules·skill은 Claude가 읽고 판단해서 따르는 지침이라 강제가 아닙니다. '저장할 때마다 꼭 검사', '위험한 명령 차단'처럼 반드시 지켜야 하는 일이 지침 쪽으로 먼저 빠지지 않도록, 첫 질문에서 hook·권한 설정으로 걸러냅니다. 검사는 정해진 순간 반드시 실행되는 hook이, 차단은 설정대로 막는 권한 설정(또는 실행 전에 도는 hook)이 맡습니다.
>
> 이 한 장이 .claude 폴더의 90%입니다. 다음은 이걸 실제로 어떻게 쓰는지, 한 연구원의 하루를 같이 보겠습니다."

**근거·세부 (슬라이드에서 옮김)**:
- hook 질문 원래 표현: "Claude 판단과 무관하게 정해진 시점에 반드시 실행·차단?" — hook은 정해진 시점(이벤트)에 실행된다. 직전 표현 "Claude 판단과 무관하게 반드시 실행·차단?" → 결과 "hook (settings.json)". 무엇을 실행·차단하는지 보이게 "꼭 돌릴 검사·막을 일?"로 바꾸고, 덱 전체 강제 표현("정해진 순간 반드시 실행(Hook)·설정대로 차단(권한 설정)")에 맞춰 결과를 "hook·권한 설정"으로 했다(둘 다 settings.json에 적는다 — 5-5).
- subagent 질문 원래 표현: "큰 탐색 / 병렬 / 메인 대화 보호?" 직전 표현: "큰 탐색 · 동시 처리?"
- MCP 결과 직전 표기: "MCP 서버"(5-7 제목과 함께 "MCP"로 통일).
- 끝 칸 원래 표현: "해당 없음 → 대화로 요청 (같은 요청 반복 시 skill로 저장)".
- plugin 메모 원래 표현: "skill·subagent·hook·MCP를 한 묶음으로 배포 → plugin (CLAUDE.md·rules는 프로젝트 저장소로 공유 — 플러그인에 넣으려면 skill로 옮기고 paths 유지)". 직전 표현: "※ skill·hook 등을 한 묶음으로 배포 → plugin (CLAUDE.md·rules는 못 넣음 → 프로젝트 폴더째 공유)". 7장 전체 통일 문구와 같은 내용이다.

**시각 표현 메모**:
- flowchart 1장 (그림 사용 한정 자리).
- hook·권한 설정 분기를 맨 위에 배치 (반드시 실행·차단할 일이 지침 분기로 먼저 빠지지 않도록).
- rules 분기가 CLAUDE.md 바로 다음에 위치하도록 배치.
- 맨 아래 끝 칸: "해당 없음 → 대화로 요청 (반복되면 skill로)".
- 마지막 줄에서 챕터 6(시연)으로 자연 연결.

---

## 챕터 5 합산

- 슬라이드 9장 (rules 추가)
- 발표 노트 합산: 90 + 90 + 90 + 60 + 60 + 50 + 50 + 50 + 60 = 600초 = 10분 정확
- 익힐 순서 강조: CLAUDE.md → skills → rules가 메인 3종 / settings.json/hooks·subagents·MCP·plugin은 후순위
- 핵심 메시지 누적: "트리(익힐 순서 표시) → 메인 3종 → 후순위 4종 → 의사결정 트리로 묶음"
