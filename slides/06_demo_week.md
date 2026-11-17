# 챕터 6: 시연 — A주임의 오늘 (11슬라이드)

> 톤 가이드: 발표의 본체. 단일 시나리오에 4개 기능을 차례로 묶어 임팩트 극대화.
> **시연 환경**: 모든 시연은 VS Code + Claude Code 확장 화면. 터미널 노출 X.
> 시각: BEFORE 슬라이드 = 페인포인트 텍스트만, AFTER 슬라이드 = 기능 타이틀 + 핵심 키워드만 띄우고 즉시 VS Code 화면 전환.
> 라이브 시연 실패 대비 사전 녹화 캡처를 모든 AFTER에 백업으로 준비.
> 슬라이드는 비개발자 청중 기준으로 쉬운 말·짧은 문구만 남겼다. 파일 이름·설정 키·실행 조건 같은 세부는 슬라이드마다 **근거·세부** 항목에 둔다.

---

## 슬라이드 6-0 — A주임의 오늘을 같이 보겠습니다 (30초)

**핵심 메시지**: "하나의 작업, 4개 기능이 각자 시점에 켜진다."

**본문 콘텐츠**:

```
Demo · 지금부터 시연

하나의 작업, 4개 기능이 각자 시점에 켜집니다.

  BDI 정책 연구원 A주임(가상 인물)의 오늘 할 일 —
  부산 16개 구·군 인구 데이터 → 임원 보고용 PPT.

  CLAUDE.md → rule → skill → hook

  평소: 엑셀 16개 열고, 차트 만들어 PPT에 붙이기. 데이터 바뀌면 처음부터.
  오늘: 한 줄 요청 → 분석·PPT·형식 점검까지 자동. 데이터 바뀌어도 같은 한 줄.

  시연은 전부 VS Code + Claude Code 확장에서 — 터미널 없이 진행.
```

**발표 노트**:
> "이제 시연입니다. 가상의 'A주임'이라는 BDI 연구원의 오늘 작업 하나를 같이 보겠습니다. 부산 16개 구/군 인구 데이터를 받아서 임원 보고용 PPT를 만드는 일이에요. 오늘은 이 작업 하나를 통해서 Claude Code의 핵심 기능 4개가 각각 어느 시점에 켜지는지 차례로 보여드리겠습니다. 한 마디씩 미리 말씀드리면 — CLAUDE.md는 매번 자동으로 읽는 작업 폴더 지침, rule은 특정 폴더에서만 켜지는 규칙, skill은 한 줄 요청으로 꺼내 쓰는 작업 절차서, hook은 정해진 순간 자동으로 실행되는 동작입니다. 시연은 전부 VS Code 안에서 진행합니다."

**근거·세부**:
- "형식 점검까지 자동": 자동 점검 범위는 디자인 8항목(verify_design.py)과 숫자 있는 슬라이드의 출처·자료 표기 여부(PostToolUse hook)까지. 수치가 원본과 맞는지는 사람이 본다(6-9 "수치 대조는 사람"). "분석부터 PPT·형식 점검까지"를 "분석·PPT·형식 점검까지"로 줄인 것은 '오늘' 칸이 한 줄에 들어가게 하려는 것.

**시각 표현 메모**:
- 오늘 할 일 한 줄 + 4개 기능 이름(CLAUDE.md · rule · skill · hook) 강조.
- 6장 기능 칩·상단 띠에는 ①②③④ 번호를 붙이지 않는다. 5장의 ①~⑦(② skills · ③ rules)과 순서가 달라 헷갈리므로, 시연 순서는 화살표로만 보인다.
- 평소/오늘 대비는 마지막 굵은 구절("데이터 바뀌면 처음부터" / "데이터 바뀌어도 같은 한 줄")로.

---

## 슬라이드 6-1 — BEFORE (30초)

**핵심 메시지 (페인포인트 1줄)**: "엑셀 16개 열고, 피벗 만들고, 차트 복사-붙여넣기. 데이터 바뀌면 처음부터."

**본문 콘텐츠**:

```
부산 구·군 인구 현황 PPT — BEFORE

  데이터가 바뀌면 — 처음부터 다시.

  평소 작업 절차
  → 구·군별 엑셀 16개 하나씩 열기
  → 수치 복사 → 비교 시트에 붙이기
  → 피벗 테이블 → 차트 만들기
  → 차트를 한 장씩 PPT에 붙이기
  → 보고용 디자인 맞추기

     🔁 업데이트마다 같은 작업 반복
```

**발표 노트**:
> "평소 작업입니다. 구/군 파일 16개를 하나씩 열어서 수치를 비교 시트에 옮기고, 피벗 만들고, 차트 복사해서 PPT에 붙입니다. 마지막엔 임원 보고용 디자인 톤까지 맞추고요. 데이터가 바뀌면 전부 처음부터예요. 자, 이제 같은 작업을 Claude Code로 해보겠습니다."

**시각 표현 메모**:
- 페인포인트 텍스트만. 큰 글자.

---

## 슬라이드 6-2 — AFTER · CLAUDE.md (2분)

**핵심 메시지**: "작업 폴더 헌법 — 톤·출처 규칙을 대화마다 자동으로 읽는다."

**본문 콘텐츠**:

```
CLAUDE.md  (작업 폴더 헌법)

  따로 지시하지 않아도 — Claude가 이미 알고 있다.

  .claude/CLAUDE.md
  ─────────────────────────────
  한국어 · ~다 체 · 수치엔 (출처: 파일명) · 요약 → 현황 → 시사점

  → "현황을 한 줄로 요약해줘"만 입력 → 답에 (출처: 파일명)이 자동으로 붙음
  → 강제 장치는 아님 — 반드시 지킬 규칙은 hook·권한 설정으로

   📺 시연 화면 — 한 줄 질문에 출처가 붙는지 확인
```

**발표 노트**:
> "(VS Code 화면 전환) .claude 폴더에 있는 CLAUDE.md를 먼저 보겠습니다. 언어, 문체, 출처 표기 방식, 보고서 구조가 여기 정의돼 있어요. 이 파일이 있으면 — 제가 아무 말 안 해도 Claude는 이 규칙을 이미 알고 있습니다. 한 번 확인해 볼게요. '현황을 한 줄로 요약해줘'라고만 입력해 보겠습니다. (입력) 보시면 — 출처 파일명이 자동으로 붙어 나옵니다. 제가 '출처 써줘'라고 하지 않았는데도요. 이게 CLAUDE.md의 역할 중 하나입니다. 다만 CLAUDE.md는 대화마다 자동으로 읽히는 지침이지 강제 장치는 아니라서, 반드시 지켜야 하는 규칙은 정해진 순간 반드시 실행되는 hook이나, 설정대로 차단하는 권한 설정으로 처리합니다. 사실 출처가 자동으로 붙은 데에는 이유가 하나 더 있는데, 잠시 후 hook 설명에서 같이 보겠습니다."

**근거·세부 (슬라이드에서 옮김)**:
- 시연 폴더 `.claude/CLAUDE.md` 실제 항목: 언어(한국어) · 문체(~다 체, 경어체는 발표 스크립트에만) · 출처 표기(모든 수치에 `(출처: 파일명)`, 출처 없는 수치는 쓰지 않음) · 보고서 구조(요약 → 현황 분석 → 시사점, 요약 3줄 이내) · 데이터 기준(최신 연도, 비교 기준 연도 명시). 슬라이드에는 앞의 네 가지만 줄여 표기.
- 로드 시점: 대화(세션)마다 시작 때 자동("loaded at the start of every conversation"). 위치는 `./.claude/CLAUDE.md` 또는 `./CLAUDE.md`.
- 강제 장치가 아님: "Claude treats CLAUDE.md files as context, not enforced configuration" / "To block an action regardless of what Claude decides, use a PreToolUse hook instead." https://code.claude.com/docs/en/memory
- 용어: "작업 폴더" = VS Code에서 연 폴더(공식 문서의 project). "권한 설정" = settings.json의 허용·금지 목록(permissions).

**시각 표현 메모**:
- CLAUDE.md 칩 강조. CLAUDE.md 파일 내용은 한 줄 요약(회색 보조 줄).

---

## 슬라이드 6-3 — AFTER · rule (1분 30초)

**핵심 메시지**: "특정 폴더 전용 규칙 — reports/ 폴더 파일을 다룰 때만 켜진다."

**본문 콘텐츠**:

```
rule  (특정 폴더 전용 규칙)

  CLAUDE.md가 "항상", rule은 "특정 자리에서만".

  .claude/rules/reports.md  맨 위 설정: 적용 폴더 reports/
  ─────────────────────────────
  최대 5장 · 전년 대비 변화율 표기 · 결론 슬라이드 필수

  → reports/ 밖 파일만 다룰 때 → 꺼진 상태
  → reports/ 안 파일을 읽거나 쓰거나 고칠 때 → 자동으로 켜짐

   📺 시연 화면 — reports/ 안팎 비교
```

**발표 노트**:
> "다음은 rule입니다. .claude/rules 폴더에 reports.md라는 파일이 있어요. 파일 맨 위 설정 자리, 그러니까 --- 표시 두 줄 사이(frontmatter라고 부릅니다)에 paths 한 줄 — 'reports 폴더 파일을 다룰 때만'이라고 적혀 있습니다. 이 --- 표시가 빠지면 paths 줄이 그냥 본문으로 읽혀서 대화마다 항상 켜지는 규칙이 되니 주의하세요. 슬라이드 수 제한, 변화율 표기, 결론 슬라이드 필수 같은 보고서 전용 규칙이에요. (경로 바꿔서 확인) reports 폴더 밖 파일을 다룰 때는 이 규칙이 켜지지 않습니다. Claude가 reports 폴더 안 파일을 읽거나 쓰거나 고치는 순간 자동으로 켜집니다. CLAUDE.md가 항상 켜져 있는 규칙이라면, rule은 '특정 자리에서만' 켜지는 규칙입니다."

**근거·세부 (슬라이드에서 옮김)**:
- "맨 위 설정" = frontmatter: 파일 첫 줄의 `---`와 다음 `---` 사이. 시연 파일은 `paths: "reports/**"` 한 줄(슬라이드의 "적용 폴더 reports/" — reports/ 아래 모든 파일). paths가 없는 rule은 매 세션 시작 때 로드.
- "켜짐" = 로드 조건(Read·Write·Edit): "A path-scoped rule loads when Claude uses the Read, Write, or Edit tool on a matching file. It also loads when Claude views a matching file with a Bash command that counts as a read, such as `cat` or `head` on a single file." https://code.claude.com/docs/en/memory
- 시연 파일의 실제 규칙: 슬라이드 수 최대 5장 · 결론 슬라이드 필수 · 모든 수치에 전년 대비 변화율과 단위 · 각 슬라이드에 출처 · 출처 없는 수치 제외.

**시각 표현 메모**:
- rule 칩 강조. 맨 위 설정(frontmatter)의 "적용 폴더 reports/"(실제 paths 줄) 강조색.
- "밖 → 꺼진 상태 / 안 → 자동으로 켜짐" 대비 표현.

---

## 슬라이드 6-4 — AFTER · skill (2분)

**핵심 메시지**: "재사용 절차서 — 한 줄 요청 → 16개 파일 동시 분석 → BDI 디자인 PPT."

**본문 콘텐츠**:

```
skill  (재사용 절차서)

  Claude가 skill의 설명(description)을 보고 알아서 꺼내 쓴다.

  .claude/skills/busan-population-report/SKILL.md
  ───────────────────────────────────────────────
  설명 요약: "부산 구/군 인구 데이터로 BDI 디자인 PPT 보고서 생성"

  → "부산 인구 현황 보고서 만들어줘" 한 줄로 시작
  → subagent(보조 작업자) 16개가 파일 1개씩 동시 분석
  → BDI 디자인 틀로 5장 조립 → reports/에 저장

   📺 시연 화면 — 16개 동시 분석 진행
```

**발표 노트**:
> "자, 이제 skill입니다. .claude/skills 폴더 안에 busan-population-report라는 skill 폴더가 있고, 그 안의 SKILL.md가 skill 본체입니다. 맨 위의 설명, description이 '언제 이 skill을 쓸지' 알려 주는 열쇠예요 — 요약하면 '부산 구/군 인구 데이터로 BDI 디자인 PPT 보고서 생성'입니다. (VS Code 채팅창) 여기에 입력합니다: '부산 인구 현황 보고서 만들어줘'. Claude가 이 설명을 보고 skill을 자동으로 선택합니다. (진행 화면) 보시면 — 구/군 파일 16개를 subagent 16개가 동시에 처리하고 있어요. subagent는 따로 떨어져 일하고 결과만 돌려주는 보조 작업자라고 보시면 됩니다. 한 파일씩 순서대로가 아닙니다. subagent 분석에서 나온 시사점과 결론 문장은 BDI 디자인 틀로 조립하는 단계에 들어가고, 수치와 차트는 스크립트가 원본 엑셀에서 다시 읽어 부산연구원 브랜드 디자인으로 그립니다. (완료 후) reports 폴더에 '부산_16개구군_인구현황.pptx' 파일이 생성됐습니다."

**근거·세부 (슬라이드에서 옮김)**:
- skill 선택: Claude가 description을 보고 자동 호출을 판단. `/busan-population-report`로 직접 호출도 가능. https://code.claude.com/docs/en/skills
- 0단계: `bootstrap.sh`가 가상환경(.venv)과 python-pptx·openpyxl을 준비(첫 실행만 설치, 인터넷 필요).
- 1단계 subagent: Agent 도구로 구·군 xlsx 16개(파일명에 '전체'가 든 파일 제외)에 subagent 16개를 한 응답에서 동시에 호출, 각자 xlsx 1개만 분석해 JSON 한 줄로 반환. VS Code에서는 백그라운드로 실행되고 끝난 순서대로 도착 → 16개가 모두 도착한 뒤 다음 단계.
- 2단계 조립: `generate_ppt.py`가 `bdi_slides.py`(부산연구원 브랜드 디자인을 코드로 담은 라이브러리 = 슬라이드의 "BDI 디자인 틀")를 호출해 5장 조립. Claude가 subagent 결과로 도출한 시사점 4개·결론 1~2문장을 넣고, 수치·차트는 원본 xlsx에서 다시 읽음.
- 저장 파일: `reports/부산_16개구군_인구현황.pptx` (구·군 6개 이상이면 `부산_N개구군_인구현황.pptx` 형식으로 자동 이름).

**시각 표현 메모**:
- skill 칩 강조. 설명(description) 텍스트 강조.
- "subagent" + "BDI 디자인 틀" 키워드 굵게(내부 이름 bdi_slides는 슬라이드에서 뺌).

---

## 슬라이드 6-5 — AFTER · skill 결과 확인 (2분)

**핵심 메시지**: "5장 완성 — BDI 디자인 가이드대로. AI식 장식을 뺀 디자인을 skill 속 프로그램이 고정하고 자동 점검까지 통과."

**본문 콘텐츠**:

```
skill 결과  (5장 · 디자인 가이드 준수)

  AI식 장식 11종을 뺀 디자인 — skill 속 프로그램이 틀을 고정, 8개 항목 자동 점검.

  SLIDE 1  Cover              진한 남색 배경 + 로고 + 큰 제목     [표지]
  SLIDE 2  주민등록인구 비교    가로 꽉 찬 막대차트                [출처 표기]
  SLIDE 3  순이동인구           좌우 데이터 표 · 색은 증감에만      [변화율 표]
  SLIDE 4  합계출산율 + 시사점  왼쪽 출산율 표 + 오른쪽 목록        [시사점 목록]
  SLIDE 5  Closing            진한 남색 배경 + 큰 결론 문장       [결론 장]

  디자인 자동 점검 결과(요약)
    📋 부산_16개구군_인구현황.pptx  (5장, 모든 도형 검사)
    ✅ 디자인 가이드 모든 검사 통과 — AI식 장식 없음
```

**발표 노트**:
> "(PPT 파일 열기) 슬라이드가 5장 나왔습니다. 보시면 — 흔히 보는 AI가 만든 PPT 같지 않죠? 풀폭 컬러 띠도 없고, 카드 좌측에 강조 보더도 없고, 큰 숫자 박스 3개로 KPI 자랑하지도 않습니다. 이게 우연이 아니라 — skill 폴더 안에 DESIGN_GUIDE.md라는 디자인 룰 문서가 있고, 그 안에 AI가 만든 티가 나는 장식 11가지(안티패턴)가 명시돼 있습니다. 이 룰은 skill 속 프로그램, 그러니까 BDI 디자인 틀에 이미 반영돼 있어서 만들 때마다 같은 디자인이 나오고, SKILL.md에는 검사에서 결함이 나오면 DESIGN_GUIDE.md를 다시 읽고 고치라고 적어 뒀습니다. 폴더에 넣어 두는 것만으로는 부족하고, SKILL.md에서 이 파일을 언제 읽을지 적어 줘야 합니다. 카드 아래 빨간 글씨로 적은 출처 표기·변화율 표·시사점 목록·결론 장 같은 형식도 skill 안의 스크립트가 고정합니다. 그리고 skill 절차 안에서 디자인 점검 프로그램(verify_design.py)이 8개 검사 항목으로 자동 점검합니다. 방금 슬라이드 안의 도형(shape)을 모두 검사해서 결함 0건이 나왔습니다. 검사는 파일이 만들어진 직후에 돌고, 결함이 나오면 Claude가 고쳐서 다시 만들도록 skill 절차에 적혀 있습니다. PPT를 만든 직후 검사를 hook으로 거는 방법은 잠시 후 hook 설명에서 보겠습니다. 결과적으로 *기계가 만들었지만 사람이 만든 듯한* 보고서가 나옵니다."

**근거·세부 (슬라이드에서 옮김)**:
- 상자 "디자인 자동 점검 결과(요약)" = `verify_design.py` 출력을 우리말로 줄인 것. 실제 첫 줄은 `📋 부산_16개구군_인구현황.pptx  (5장, N개 shape 검사)`이고 N은 내용에 따라 달라진다(5차 검증 실행 때 112개) → 슬라이드는 "모든 도형 검사". 실제 둘째 줄 `✅ DESIGN_GUIDE 모든 검사 통과 — AI 안티패턴 없음` → 슬라이드는 "디자인 가이드 모든 검사 통과 — AI식 장식 없음"(뜻 같음). 시연 화면에는 실제 출력이 그대로 보인다.
- DESIGN_GUIDE.md 5항의 AI 안티패턴 11종(슬라이드의 "AI식 장식 11종"): 풀폭 컬러 헤더 스트립 · 헤드라인 밑 짧은 액센트 라인 · 카드 좌측 컬러 보더 · 번호 grid(01/02/03) · ▲▼ 이모지 + 컬러 헤더 · "큰 숫자 + 작은 라벨" 통계(KPI) grid · 그라데이션 배경 · drop shadow 카드 · 둥근 모서리 카드 · 모든 슬라이드 같은 위치 로고 · 시안 풀폭 구분선.
- `verify_design.py` 자동 검사 8종: 풀폭 컬러 스트립 · 짧은 액센트 바 · 카드 좌측 컬러 보더 · drop shadow · 라운드 코너 · 이모지 기호 · 강조색 과다(3종 이상) · Pretendard 외 폰트. 번호 grid·KPI grid는 bdi_slides가 처음부터 만들지 않아 자동 검사에서 뺐다.
- 카드 설명에서 줄인 내용(피한 패턴): 1 Cover = 다크 네이비 + BDI 로고 + 큰 타이틀 + 하단 인라인 메타 / 2 = 풀폭 막대차트, 헤더 스트립·차트 자체 타이틀 없음 / 3 = 좌 순유입·우 순유출 데이터 표, 카드·▲▼ 이모지 없음, 색은 변화율(+/-)에만 / 4 = 좌 출산율 표 + 우 "—" 들여쓰기 시사점 목록, 번호 grid 없음 / 5 Closing = 다크 네이비 + 큰 결론 + 인라인 통계, KPI grid 없음. 폰트는 Pretendard 단일.
- 카드 태그(출처 표기 = 출처 푸터 · 변화율 표 · 시사점 목록 · 결론 장)는 skill 스크립트(`generate_ppt.py`·`bdi_slides.py`, 리드의 "skill 속 프로그램")가 고정하는 형식이다. CLAUDE.md·rule이 만든 결과가 아니다.

**시각 표현 메모**:
- 5장 구성을 카드 5개로 (Cover / 본문 3 / Closing). 카드 아래 빨간 태그 = skill 스크립트가 고정하는 형식.
- 하단 상자 "디자인 자동 점검 결과(요약)"에 verify_design.py 출력 요약(✅ 통과) 강조.
- 시연: 생성된 PPT 파일 열기 + 검증 결과.

---

## 슬라이드 6-6 — AFTER · hook — SessionStart (1분 30초)

**핵심 메시지**: "대화 시작 순간 — 데이터·도구 준비 자동 점검. hook = 정해진 순간 자동 실행되는 동작."

**본문 콘텐츠**:

```
hook · SessionStart  (시작 시점)

  hook = 정해진 순간 자동 실행되는 동작. 확장을 열기만 해도 실행.

  → .claude/settings.json에 등록 → 결과는 기록 파일(trigger.log)에
  → ❌ 데이터 없음 · ⚠️ 도구 미설치 · ✅ 준비 완료
       '도구 미설치'는 정상(첫 보고서 때 자동 설치) · 'Python 3 없음'이면 Python부터 설치

  SESSION START — trigger.log 자동 기록
    [시각] SessionStart · busan_data 17개 파일 · ✅ 보고서 환경 준비 완료
      - 부산_인구통계_강서구.xlsx
      - 부산_인구통계_금정구.xlsx
      ... (16개 구·군 + 전체)

   📺 시연 화면 — VS Code 사이드바의 trigger.log
```

**발표 노트**:
> "hook을 보겠습니다. hook은 정해진 순간 자동으로 실행되는 동작이에요. 오늘은 세 순간을 보여 드립니다. 첫 번째는 SessionStart hook입니다. settings.json에 설정돼 있어요. Claude Code 확장을 열면 — 아무것도 하지 않았는데 — 자동으로 check_data.sh가 실행됩니다. 결과는 사이드바에 띄운 기록 파일 trigger.log에 바로 기록돼요 — busan_data 폴더의 파일 수와 파일 목록, 환경 준비 여부가 보이죠. 판정은 세 가지예요. 데이터가 없으면 ❌, 보고서 도구(파이썬 패키지)가 아직 없으면 ⚠️ 도구 미설치, 다 갖춰지면 ✅. 지금 따라 하시는 분들 PC처럼 이 폴더를 처음 여는 PC에서는 '도구 미설치' ⚠️가 찍히는 게 정상입니다. 패키지는 skill이 처음 실행될 때 설치하니까, 보고서를 한 번 만든 뒤 새 대화부터는 ✅로 바뀝니다. 다만 ⚠️ 옆에 'Python 3 없음'이 보이면 자동 설치로는 해결되지 않으니, Python부터 설치하셔야 합니다. 오늘 시연을 시작할 때 trigger.log에 찍혀 있던 첫 줄, 그게 SessionStart hook이었습니다."

**근거·세부 (슬라이드에서 옮김)**:
- 등록: `.claude/settings.json`의 `SessionStart` 이벤트 → `bash "$CLAUDE_PROJECT_DIR"/.claude/hooks/check_data.sh`. 세션 시작·재개 때마다 실행되고 막지 않는다(종료 코드 항상 0). 프로젝트 설정의 hook은 폴더 신뢰("Trust this folder in Claude Code?") 수락 후 실행.
- 기록 위치: `.claude/hooks/trigger.log`. VS Code 탐색기에서 열어 에디터 분할로 옆에 띄워 둔다(슬라이드의 "사이드바"). 자세한 방법은 실습 폴더 README "Hook 기록 보기".
- 판정(데이터 + 의존성): busan_data 폴더 없음·xlsx 0개 → ❌ / python-pptx·openpyxl을 불러오지 못함 → `⚠️ python-pptx·openpyxl 미설치 (skill bootstrap.sh가 자동 처리)` (슬라이드의 "도구 미설치") / 모두 정상 → `✅ 보고서 환경 준비 완료`. Python 3 자체가 없으면 `⚠️ Python 3 없음 — python3·python·py 실행 실패`(슬라이드의 "Python 3 없음") — 이때는 skill의 bootstrap.sh도 `❌ Python 3를 찾지 못했습니다` 후 멈추므로 자동 설치로 해결되지 않는다(Python 3 설치는 사전 준비). 점검 스크립트 자체가 실패하면 `⚠️ 점검 스크립트 실행 실패`.
- ⚠️ 해소: skill 첫 실행 때 `bootstrap.sh`가 .venv에 두 패키지를 설치(인터넷 필요) → 다음 새 세션부터 ✅. 확인 기준은 .venv의 python, 없으면 시스템 python이라 시스템 python에 두 패키지가 이미 있으면 처음부터 ✅.
- 출력 방식: 사용자에게 보이는 안내는 JSON `systemMessage`, Claude에 들어가는 내용은 `hookSpecificOutput.additionalContext`. https://code.claude.com/docs/en/hooks

**시각 표현 메모**:
- hook 칩 강조. trigger.log 기록 내용 코드블록으로 표현.

---

## 슬라이드 6-7 — AFTER · hook — UserPromptSubmit (2분)

**핵심 메시지**: "질문을 보내는 순간 — 데이터 목록 자동 첨부. 내 화면엔 안 보이고 Claude에게만 전달된다."

**본문 콘텐츠**:

```
hook · UserPromptSubmit  (질문 시점)

  내 화면엔 안 보이고 Claude에게만 전달된다.

  → 질문할 때마다 자동 실행 → trigger.log에도 기록
  → 보고서 요청인데 데이터가 없으면 → Claude가 "데이터 없음" 안내

  USER PROMPT SUBMIT — Claude에 전달되는 내용(요약)
    [자동 컨텍스트 — busan_data]
    📂 사용 가능한 17개 파일 (강서구, 금정구, … 해운대구)
    ✅ 수치 인용 시 (출처: 파일명) 형식으로 자동 표기 가능

   📺 시연 — 질문 입력 + 데이터 없음 안내
```

**발표 노트**:
> "두 번째 hook은 UserPromptSubmit입니다. 제가 채팅창에 메시지를 입력하고 엔터를 누르는 순간 — Claude한테 메시지가 전달되기 직전에 — inject_context.sh가 자동으로 실행돼서, busan_data 폴더의 파일 목록이 참고 정보로 함께 붙어 들어갑니다. 앞의 CLAUDE.md 시연에서 '출처 써줘'라고 안 했는데도 응답에 출처가 자동으로 붙었던 거 기억하시죠? 그건 CLAUDE.md 규칙 *플러스* 이 hook이 함께 작동한 결과입니다. CLAUDE.md는 '출처를 써라'는 규칙이고, 이 hook은 '쓸 출처가 어디 있는지'를 매번 자동으로 알려줍니다. 사용자 화면엔 이 내용이 안 보여요 — Claude한테만 전달됩니다. 참고로 subagent가 결과를 보고할 때도 이 hook이 돌아서, skill 실행 중에는 trigger.log에 주입 기록이 여러 번 더 쌓일 수 있어요. 데이터 폴더가 빈 채로 보고서를 요청하면 이 hook이 '데이터 없음' 안내를 대신 넣어서, Claude가 보고서 대신 그 사실을 안내하도록 해 뒀습니다(시간 되면 시연)."

**근거·세부 (슬라이드에서 옮김)**:
- 등록: `.claude/settings.json`의 `UserPromptSubmit` 이벤트 → `bash "$CLAUDE_PROJECT_DIR"/.claude/hooks/inject_context.sh`. 프롬프트를 막지 않는다.
- 실행 시점: 질문을 제출할 때마다, Claude가 처리하기 전("When a prompt is submitted, before Claude processes it"). 백그라운드 subagent가 결과를 보고할 때처럼 Claude Code가 스스로 시작하는 턴에도 실행("A background subagent reporting back to the session that started it"). https://code.claude.com/docs/en/hooks#userpromptsubmit
- 화면 표시: 일반 텍스트 stdout은 Claude 컨텍스트로 들어가고 채팅에는 보이지 않는다("Neither channel produces a visible transcript entry"). 같은 내용을 trigger.log에도 남긴다(미러링).
- 상자 이름의 "(요약)": 실제 주입 본문은 `📂 사용 가능한 17개 파일:` 다음 줄부터 파일 17개를 한 줄씩 나열한다. 슬라이드는 한 줄로 줄여 적었다.
- 데이터 없음 안내(가드레일): 질문에 "보고서·PPT·ppt·pptx·인구"가 있는데 busan_data의 xlsx가 0개면, "데이터가 없다"는 사실 문장을 주입 → Claude가 보고서 대신 그 사실을 안내. 명령형이 아니라 사실 진술로 쓴다("Text framed as out-of-band system commands can trigger Claude's prompt-injection defenses"). 데이터도 없고 일반 질문이면 아무것도 주입하지 않는다. 시연 순서는 실습 폴더 README "UserPromptSubmit 가드레일 — 데이터 없음 안내 (옵션)".

**시각 표현 메모**:
- hook 칩 강조. UserPromptSubmit 굵게.
- "질문을 보내는 순간" 강조.
- 데이터 없음 안내 시연은 시간이 될 때만 하는 옵션이다. 발표자 메모라 슬라이드에는 "(시간 되면)"을 적지 않는다.
- 자동 컨텍스트 블록은 배경색 다르게 (Claude에게만 보이는 메시지 느낌).
- 6-2와의 연결(출처 자동 표기의 또 하나의 요인 = CLAUDE.md 규칙 + 파일 목록 주입)은 슬라이드에 따로 표시하지 않고 발표 노트로 설명.

---

## 슬라이드 6-8 — AFTER · hook — PostToolUse (2분)

**핵심 메시지**: "PPT를 만든 직후 — 출처 표기 자동 검사·기록 (막지는 않음)."

**본문 콘텐츠**:

```
hook · PostToolUse  (생성 직후)

  숫자가 있는 슬라이드마다 '출처'·'자료' 표기가 있는지 확인.

  → PPT 생성 명령 직후에만 검사·기록
  → 결과는 trigger.log에 ✅ / ❌ — 기록만 하고 저장은 막지 않음

  POST TOOL USE — trigger.log 자동 기록
    ✅ 모든 슬라이드 출처 표기 확인 (5/5) · 파일: 부산_16개구군_인구현황.pptx

  출처 누락이 있을 경우
    ❌ 출처 누락: 2·4번 슬라이드 · 정상: 1·3·5번 · 파일: 부산_16개구군_인구현황.pptx

   📺 시연 화면 — 출처 뺀 PPT로 ❌ → 다시 만들어 ✅
```

**발표 노트**:
> "세 번째 hook은 PostToolUse입니다. generate_ppt.py로 PPT가 만들어진 직후에 verify_report.sh가 자동으로 실행돼요. 이 검사는 슬라이드마다 수치와 함께 '출처'나 '자료'라는 표기가 있는지 보는 방식이에요. Claude에게 '방금 보고서를 같은 시사점·결론 그대로, 검증 hook 시연용 옵션(--omit-source 2,4)을 붙여 다시 빌드해 줘'라고 요청해 보겠습니다. 이 옵션은 2번과 4번 슬라이드의 출처 표기를 뺀 채 다시 만들고, 시사점·결론을 그대로 두라고 덧붙이면 4·5장 문장이 처음 보고서와 같게 유지됩니다. (시연) 보시죠 — trigger.log에 '출처 누락: 2·4번 슬라이드'가 찍힙니다. PostToolUse는 파일이 이미 만들어진 뒤에 돌기 때문에 저장을 막지는 못하고, 사후 검사를 맡아요. 실행 자체를 막으려면 도구가 실행되기 전에 도는 PreToolUse를 씁니다. 이제 '이번엔 옵션 없이 같은 내용으로 다시 빌드해 줘'라고 하면 — 통과로 기록됩니다. 정리하면 — SessionStart는 *시작 시점*, UserPromptSubmit는 *질문 시점*, PostToolUse는 *PPT를 만든 직후*. hook 하나면 한 순간만 잡지만, 세 개를 같이 쓰면 작업의 앞·중·뒤를 모두 잡을 수 있습니다."

**근거·세부 (슬라이드에서 옮김)**:
- 등록: `.claude/settings.json`의 `PostToolUse` 이벤트, matcher(어떤 작업에 반응할지) `Bash` → `bash "$CLAUDE_PROJECT_DIR"/.claude/hooks/verify_report.sh`. Claude의 Bash 도구 호출이 성공한 직후마다 실행된다.
- "PPT 생성 명령 직후에만": 명령에 `generate_ppt`가 들어 있고 그 명령이 실행되는 동안 reports/의 PPT가 새로 저장됐을 때만 검사·기록한다. bootstrap.sh·verify_design.py 같은 다른 Bash 호출, `generate_ppt.py --help`·grep처럼 PPT를 저장하지 않은 명령, 사람이 PPT를 직접 열어 고쳐 저장한 경우는 기록이 없다. 명령이 실패하면(예: Windows에서 PPT를 열어 둔 채 다시 빌드) hook 자체가 실행되지 않는다.
- 판정: 숫자가 있는 슬라이드에 '출처' 또는 '자료'가 함께 있으면 정상, 없으면 누락. trigger.log 실제 줄은 `[시각] PostToolUse · 출처 검증 — ✅ 모든 슬라이드 출처 표기 확인 (5/5) · 파일: …`(누락이 있으면 `… — ❌ 출처 누락: 2·4번 슬라이드 · 정상: 1·3·5번 · 파일: …`)이고, 슬라이드 상자는 "출처 검증 — " 뒷부분을 옮긴 것.
- 막지 않음: PostToolUse는 도구가 실행된 뒤에 돌아 차단할 수 없다. 이 hook은 종료 코드를 항상 0으로 두고 Claude 컨텍스트에도 넣지 않으며 trigger.log에만 기록한다. 실행 전 차단은 PreToolUse. https://code.claude.com/docs/en/hooks
- 시연 옵션: `--omit-source 2,4`(지정 슬라이드의 출처 표기를 빼는 시연·테스트 전용). Claude가 다시 빌드할 때는 빌드 코드에 `omit_source=[2, 4]`를 넣고 직전 시사점·결론을 그대로 쓴다(SKILL.md "다시 빌드할 때"). 순서는 실습 폴더 README "검증 hook 시연".

**시각 표현 메모**:
- hook 칩 강조. "누락 감지 → 수정 → 재빌드 통과" 흐름은 하단 시연 줄(❌ → ✅)로 표현.
- SessionStart / UserPromptSubmit / PostToolUse 3시점("시작 / 질문 / PPT를 만든 직후") 요약은 슬라이드에 따로 표시하지 않고 발표 노트 마지막 문장으로 전달.

---

## 슬라이드 6-9 — Before / After (1분 30초)

**핵심 메시지**: "4개 기능이 제 시점에 켜지면 — 반복 작업이 정해진 절차가 된다."

**본문 콘텐츠**:

```
Before → After
  사람이 하던 단계를 기능이 하나씩 맡는다.

  항목             Before (수동)        After (Claude Code)
  ──────────────   ─────────────        ──────────────────
  엑셀 16개 처리    직접 열고 복사         subagent 16개 동시 분석
  톤·출처 규칙      매번 직접 지시          CLAUDE.md에 한 번 적어 두기
  보고서 형식       기억해서 맞추기          skill이 틀을 고정 · rule은 reports/ 파일을 직접 읽고 고칠 때 켜짐
  전 과정 자동화    없음                   한 줄 요청(skill) + BDI 디자인 틀
  데이터 목록       매번 직접 첨부          질문마다 hook이 자동 첨부
  품질 점검         사람이 매번 확인        hook이 출처 표기 자동 검사(수치 대조는 사람)

  ※ 한 번 설정 → 다음 달 데이터 바뀌어도 같은 한 줄로
  ※ 작업 폴더째 공유하면(개인 설정 파일 제외) 동료도 같은 효과 — 7장
```

**발표 노트**:
> "정리한 표입니다. 수동으로 하던 작업들을 CLAUDE.md, rule, skill, hook이 나눠 맡습니다. 보고서 형식은 이번 시연에선 skill 스크립트가 고정합니다. PPT는 Claude가 실행한 파이썬 스크립트가 저장해서 rule이 켜지는 조건에 해당하지 않고, rule은 Claude가 reports 폴더 파일을 직접 읽거나 쓰거나 고칠 때 켜집니다. 특히 hook은 한 종류가 아니라 여러 시점에 걸 수 있어요 — 공식 문서 기준 이벤트가 33개이고, 오늘은 그중 시작(SessionStart), 질문(UserPromptSubmit), PPT를 만든 직후(PostToolUse) 세 시점을 썼습니다. 마지막 줄의 hook, 그러니까 PostToolUse hook은 출처 표기가 있는지만 자동으로 검사해 기록하고, 수치가 원본과 맞는지 대조하는 건 여전히 사람 몫이에요. 중요한 건 — 이 설정을 한 번 만들어두면 다음 달 데이터가 업데이트돼도 '부산 인구 현황 보고서 만들어줘' 한 줄로 새 PPT가 나옵니다. 그리고 이 작업 폴더를 .claude 폴더까지 통째로 동료와 공유하면 — git 저장소에 올리든 zip으로 묶어 보내든 — 옆자리 동료도 똑같은 효과를 봅니다. 이때 settings.local.json 같은 개인 설정 파일은 빼고 보내세요. 동료는 그 폴더에서 Claude Code를 처음 열 때 뜨는 'Trust this folder in Claude Code?' 창에서 신뢰를 눌러야 hook이 돌아갑니다. 공유하는 방법은 다음 챕터에서 보겠습니다."

**근거·세부 (슬라이드에서 옮김)**:
- 표 After 칸의 원래 용어: subagent 16개 병렬(Agent 도구) / CLAUDE.md 매 세션 자동 로드 / skill 스크립트(`generate_ppt.py`·`bdi_slides.py`)가 형식 고정(슬라이드의 "skill이 틀을 고정"), rule은 reports/ 파일을 Read·Write·Edit할 때 로드(슬라이드의 "직접 읽고 고칠 때") / skill 한 줄 + bdi_slides 라이브러리 / UserPromptSubmit hook 자동 주입 / PostToolUse hook이 출처 표기 유무 자동 기록(수치 대조는 사람).
- rule 로드 조건: Claude가 매칭 파일에 Read·Write·Edit 도구를 쓸 때(cat·head로 한 파일을 읽는 Bash 명령 포함). Bash로 실행한 파이썬이 PPT를 저장하는 것은 해당하지 않는다. https://code.claude.com/docs/en/memory
- hook 이벤트는 공식 문서 기준 33개. https://code.claude.com/docs/en/hooks
- 공유: `.claude/`(+ 루트에 둔 경우 CLAUDE.md)를 프로젝트 저장소에 git으로 커밋하거나 프로젝트 폴더를 zip으로 전달 — 둘 다 settings.local.json 등 개인 파일은 뺀다. Claude Code가 이 파일을 git 제외 목록에 자동으로 넣는 것은 git 저장소 안에서 처음 쓸 때뿐이고("The first time Claude Code writes the file in a git repository that doesn't already ignore it…"), 커밋된 settings.local.json은 저장소가 준 설정으로 취급돼 동료가 폴더를 신뢰하면 그 허용 규칙이 동료 PC에도 적용된다("When the file is tracked in git … holds its rules until you trust the folder"). zip으로 받은 파일은 git 추적 대상이 아니라 동료 자신의 파일로 취급돼 신뢰 단계 없이 바로 적용된다("normally your own file, so Claude Code applies its allow rules … without the trust step"). https://code.claude.com/docs/en/settings · https://code.claude.com/docs/en/permissions
- 동료 쪽 절차: VS Code 상단 신뢰 배너(Restricted Mode) → Manage → Trust, 이어서 "Trust this folder in Claude Code?" 수락 → 그 뒤 hook 실행. 자세한 공유 방법은 7장. (슬라이드 ※ 줄에서는 "(폴더 신뢰 후)"를 빼고 이 노트로 옮김. "작업 폴더째" = .claude/ 폴더를 포함한 작업 폴더 전체)

**시각 표현 메모**:
- 6행 비교표. 우측 열에 기능명 색깔 다르게.
- 하단 ※ 2줄 ("작업 폴더째"만 강조색). hook 3시점(시작·질문·PPT를 만든 직후)은 슬라이드에 따로 넣지 않고 발표 노트로만 언급.

---

## 슬라이드 6-10 — 다음 챕터로 연결 (30초)

**핵심 메시지**: "한 번 정의해두면 매번, 옆자리에도."

**본문 콘텐츠**:

```
한 번 정의해두면

  내 다음 달에도 · 옆자리 동료에게도 · 팀 전체에도
  그대로 작동합니다.

  다음 챕터 — 옆자리로 넘기는 방법, 사내 공유 4단계
```

**발표 노트**:
> "오늘의 핵심 한 마디 — 한 번 정의해두면 매번, 옆자리에도. 어떻게 그 옆자리로 넘기는지를 다음 챕터에서 보겠습니다."

**시각 표현 메모**:
- 텍스트만, 줄간격 넓게.
- 마지막 줄에서 챕터 7로 자연 연결.

---

## 챕터 6 합산

- 슬라이드 11장 (6-0 ~ 6-10)
- 발표 노트 합산: 30 + 30 + 120 + 90 + 120 + 120 + 90 + 120 + 120 + 90 + 30 = 960초 = 16분
- 시연 흐름: SessionStart hook → CLAUDE.md → rule → (UserPromptSubmit hook 매 입력·subagent 결과 보고마다 자동) → skill (subagent 16개 → bdi_slides 라이브러리) → PostToolUse hook(PPT를 만든 직후) → PPT 5장 결과
- 안정성 보강 사항:
  - 모든 입력: 로컬 파일 (busan_data/*.xlsx). 단, 첫 skill 실행 때 bootstrap.sh가 PyPI에서 python-pptx·openpyxl을 설치하므로 인터넷이 필요 — 리허설 때 시연 폴더에서 한 번 실행해 .venv를 만들어 둘 것
  - 라이브 시연 실패 대비 녹화 캡처 준비
  - subagent 병렬 진행 화면 사전 녹화
  - PostToolUse 시연: verify_report.sh는 Claude의 Bash 명령에 generate_ppt가 들어 있을 때만 검증(PPT를 직접 고쳐 저장하면 미발동) — "같은 시사점·결론 그대로 --omit-source 2,4를 붙여 재빌드" → "옵션 없이 같은 내용으로 재빌드" 요청 흐름을 리허설로 확인(CLAUDE.md·rule의 "출처 없는 수치는 작성하지 않는다"와 부딪히지 않게 시연 전용 옵션 사용)
  - UserPromptSubmit hook stdout 노출 방식: 사용자 화면엔 안 보이고 Claude에만 전달됨을 슬라이드에서 명확히 표현
- 차별화 포인트:
  - CLAUDE.md: 매 세션 자동 로드 (입력 없이 출처·톤 확인)
  - rule: 경로 기반 로드 (reports/ 안팎 비교)
  - skill: description 트리거 + subagent 16개 병렬 + bdi_slides 라이브러리 호출로 5장 조립
  - 결과물: Cover · 본문 3 · Closing — BDI 네이비/시안/공식 로고 일관 적용
  - 이번 시연의 hook 3시점: SessionStart(시작) + UserPromptSubmit(질문) + PostToolUse(PPT를 만든 직후) — 작업 앞·중·뒤를 각각 담당
