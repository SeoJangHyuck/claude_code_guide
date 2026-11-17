# 챕터 8: 추천 플러그인 — superpowers (1슬라이드 / 3분)

> 톤 가이드: superpowers는 원래 코딩 에이전트용 개발 방법론(skill 묶음 + 세션 시작 때 지시문을 넣는 SessionStart hook 1개)이라는 점을 숨기지 않는다. 실행을 막지 않으므로 "강제·게이트·차단" 대신 "기본 절차로 넣도록 지시", "줄인다"로 말한다(3장: Skill은 Claude가 판단, 꼭 지킬 일은 Hook(정해진 순간 반드시 실행)·권한 설정(설정대로 차단)). 카드 4개 중 2개가 코드 전용이라 "강제 아님, 코드 작업 중심"은 리드에서 먼저 밝힌다. 설문 1순위 환각 우려와는 "확인을 습관으로 만드는 도구"로 연결하고, 보고서 수치·출처 대조는 사람 몫이라는 점을 슬라이드와 노트에서 분명히 한다. 한 슬라이드로. 청중이 대부분 비개발자라 카드는 "언제 → 무엇을 → 효과"를 짧게만 두고, 설치 칸은 VS Code 경로만 둔다. 원래의 자세한 카드 문구·터미널 설치 명령·자체 마켓플레이스 설치법은 아래 **자세한 방법 (슬라이드에서 옮긴 세부)** 에 둔다.

---

## 슬라이드 8-1 — superpowers: 검증 단계를 기본 절차로 넣는 플러그인 (3분)

**핵심 메시지**: "AI가 서두르다 건너뛰기 쉬운 확인 단계(설계 확인·테스트 먼저·원인 진단·완료 전 검증)를 기본 절차로 넣도록 지시하는 플러그인. 강제 아님, 코드 작업 중심 — 확인을 습관으로 만드는 도구이고, 보고서 수치·출처 대조는 사람 몫."

**본문 콘텐츠** (슬라이드와 같은 내용):

```
superpowers — 검증 단계를 기본 절차로 넣는 플러그인
AI가 건너뛰기 쉬운 확인 4단계를 거치도록 지시 — 강제 아님, 코드 작업 중심.

  ───────────────────────────────────────────

  🧠 brainstorming — 만들기 전
     질문을 하나씩 하며 의도·성공 기준 확인 → 설계 승인 후 시작
     → 잘못된 방향으로 시작하는 일 감소

  🧪 test-driven-development — 코드 작성 전
     테스트(합격 기준)부터 작성 → 통과할 만큼만 코드 작성
     → '다 했다'의 기준이 명확

  🔍 systematic-debugging — 오류 발견 시
     바로 고치지 않고 원인부터 — 오류 읽기·재현·정상 코드와 비교
     → 임시방편 수정 감소

  ✅ verification-before-completion — 완료 직전
     검증 명령(테스트 등)을 직접 실행해 결과 확인
     → 확인 없는 '완료' 선언 감소

  ───────────────────────────────────────────

  💡 왜 추천하나
     설문 1순위 고민(60%): AI 결과물 신뢰성·환각·검증 부담.
     확인을 습관으로 만드는 도구 — 보고서 수치·출처 대조는 사람 몫.

  ───────────────────────────────────────────

  설치 (VS Code):  입력창 /plugins → Plugins 탭에서 superpowers 설치
  안 보이면 Marketplaces 탭에 공식 목록 anthropics/claude-plugins-official 등록
  · 📖 github.com/obra/superpowers
```

(장 표지 부제: "확인 단계를 기본 절차로 넣는 skill(재사용 가능한 절차서) 묶음.")

**자세한 방법 (슬라이드에서 옮긴 세부)**:

```
동작 방식: skill(지시문) 기반 — 실행을 막지 않음 (슬라이드 리드의 "강제 아님")
  (hook(정해진 순간 자동 실행)은 대화(세션) 시작 때 지시문을 넣는 SessionStart 1개뿐)

슬라이드에서 옮긴 문구:
  이전 리드: "AI가 서두를 때 건너뛰기 쉬운 4단계를 거치도록 지시 — 실행을 막는 장치는 아님."
  이전 💡 문구: "설문 1순위 고민 — AI 결과물 신뢰성·환각·검증 부담 (60%). 확인 절차를
    습관화하는 도구 — 단, 코드 작업 중심이라 보고서 수치·출처 대조는 사람이 따로."
    ('코드 작업 중심'은 리드로 올림)

터미널 설치 명령 (슬라이드에서 뺌 — 5장과 같이 /plugin·/plugins 혼동 방지):
  터미널에서 claude를 실행한 뒤 Claude Code 입력창에:
  /plugin install superpowers@claude-plugins-official
  (셸에 그대로 치는 명령이 아님. VS Code 확장만 쓰면 슬라이드의 /plugins 경로로)

카드의 원래 문구 (언제 → 하는 일 → 효과)
  🧠 brainstorming — 만들기 전 확인 단계
     작업에 맞춘 질문을 한 번에 하나씩 — 의도·성공 기준 확인, 설계 승인 후 착수
     → 잘못된 방향으로 시작하는 시간 감소
  🧪 test-driven-development — 코드 구현 전 확인 단계
     실패하는 테스트부터 작성·실패 확인 → 통과할 최소 코드 작성
     → "다 했다"의 기준이 명확해짐
  🔍 systematic-debugging — 버그 발견 시 확인 단계
     즉시 수정 금지 — 오류 읽기·재현·최근 변경 확인 → 정상 동작 코드와 비교부터
     → 임시방편 수정의 연쇄 문제 감소
  ✅ verification-before-completion — 완료 선언 직전 확인 단계
     테스트·빌드 등 검증 명령을 직접 실행해 결과 확인 — 증거 없는 '완료' 선언 금지
     → 확인 없이 끝내는 미완성 결과 감소

💡 상자의 원래 제목: "왜 부산연구원 청중에게 추천하나"
설치 칸의 원래 이름: "설치 (Anthropic 공식 마켓플레이스)" → 직전 "설치 (공식 마켓플레이스)"
  → 지금 "설치 (VS Code)" (터미널 명령을 빼고 VS Code 경로만 남김)

VS Code 확장 설치 순서:
  입력창 /plugins → Marketplaces 탭에 anthropics/claude-plugins-official 등록
  (Plugins 탭에 superpowers가 안 보일 때 — 공식 마켓플레이스는 터미널에서 대화형 세션을
   처음 열 때 자동 추가되므로 VS Code만 쓰면 목록이 비어 있을 수 있음)
  → Plugins 탭에서 superpowers 설치
  (설치 범위를 물으면 Install for you = 내 모든 작업 폴더에서 사용)

또는 자체 마켓플레이스 (관련 플러그인 포함):
  /plugin marketplace add obra/superpowers-marketplace
  /plugin install superpowers@superpowers-marketplace
```

**발표 노트 (3분)**:
> "마지막 추천 하나 드리고 마무리하겠습니다. superpowers라는 플러그인입니다. 제가 매일 쓰는 거예요.
>
> 한 줄 요약 — 'AI가 서두르다 건너뛰기 쉬운 확인 단계를 기본 절차로 넣도록 지시하는 플러그인'입니다. AI는 답을 빨리 주고 싶어 해서 충분히 확인하지 않고 '다 됐습니다'라고 할 때가 있는데, superpowers는 주요 단계마다 멈추고 확인하라고 지시합니다. 다만 화면에 적은 대로 강제가 아니라 skill로 된 지시라서 100% 보장은 아니에요. 꼭 지켜야 할 일은 3장에서 말씀드린 대로 hook(정해진 순간 반드시 실행)이나 권한 설정(설정대로 차단)으로 거셔야 합니다.
>
> 4가지 핵심이 있어요. brainstorming은 뭔가 만들기 전에 그 작업에 맞는 질문을 한 번에 하나씩 해서 무엇을 왜 만드는지, 성공 기준이 뭔지 확인하고, 설계를 승인받은 뒤에 시작합니다. test-driven-development는 코드를 짜기 전에 테스트부터 씁니다. 테스트는 '이렇게 동작하면 합격'이라는 자동 채점표 같은 건데, 이걸 먼저 쓰고 실제로 실패하는 걸 확인한 다음 통과할 만큼만 코드를 씁니다. systematic-debugging은 '버그 보자마자 고치지 말고 원인부터 찾아라'는 절차예요. 오류 메시지 읽기, 재현, 최근 변경 확인을 먼저 하고, 같은 코드에서 정상 동작하는 부분과 비교해 원인을 좁힙니다. verification-before-completion은 '다 했다'고 하기 전에 테스트나 빌드 같은 검증 명령을 직접 돌려 결과를 확인하게 합니다. 증거 없이 '완료'라고 하지 않게 하는 거죠.
>
> 솔직히 말씀드리면 원래 코딩 작업용 방법론입니다. 검증도 테스트·빌드를 실제로 돌려 확인하는 방식이라, 보고서의 수치나 출처가 원자료와 맞는지 대조해 주지는 않아요. 그건 여전히 사람이 따로 확인하셔야 합니다. 그래도 오늘 설문에서 60%가 가장 걱정한 게 'AI 결과물 신뢰성·환각·검증 부담'이었죠? 확인 없이 '완료'라고 하지 않는 습관을 작업 절차에 기본으로 넣어 준다는 점에서, 확인을 습관으로 만드는 도구로 추천드립니다.
>
> 설치는 VS Code에서 입력창에 `/plugins`를 열고 Plugins 탭에서 superpowers를 찾아 설치하시면 됩니다. 목록에 안 보이면 Marketplaces 탭에 공식 목록 주소 `anthropics/claude-plugins-official`을 먼저 등록하세요. 터미널에서 Claude Code를 쓰시는 분은 명령 한 줄로도 됩니다.
>
> 그럼 마지막 정리로 넘어가겠습니다."

**시각 표현 메모**:
- 4분면 카드 그리드.
- 각 카드: 이모지 + 언제(짧게: 만들기 전·코드 작성 전·오류 발견 시·완료 직전) + 하는 일 한 줄 + 효과(→ ○○ 감소).
- 리드: "강제 아님, 코드 작업 중심"을 먼저 밝힘(카드 4개 중 2개가 코드 전용이라 "나와 무슨 상관?"을 막음).
- 하단 💡 박스: 설문 1순위 고민(60%)과의 연결(확인을 습관으로 만드는 도구)과 한계(보고서 수치·출처 대조는 사람 몫)를 대시 하나로 정리.
- 설치 칸: VS Code 경로만(입력창 /plugins → Plugins 탭) + 안 보일 때 Marketplaces 탭에 공식 목록 등록 + GitHub 링크. 터미널 명령(/plugin install …)과 자체 마켓플레이스 설치법은 위 "자세한 방법"으로 옮김.
- 마지막 줄에서 챕터 9(마무리)로 자연 연결.

**근거 (공식 문서·GitHub 원문)**:
- 정체: README 첫 줄 "Superpowers is a complete software development methodology for your coding agents, built on top of a set of composable skills" — 코딩 에이전트용 개발 방법론. plugin.json description "Core skills library for Claude Code: TDD, debugging, collaboration patterns, and proven techniques". Anthropic 공식 마켓 항목 category `"development"`. https://github.com/obra/superpowers
- 동작 방식: hook은 SessionStart 1개뿐(matcher `startup|clear|compact`) — 세션 시작·`/clear`·압축 때 using-superpowers 지시문을 컨텍스트에 넣는다(`hooks/hooks.json`, `hooks/session-start`). 도구 실행을 막는 hook은 없고, 나머지는 skill(지시문).
- skill의 지시는 보장이 아님: "An instruction like "never edit `.env`" in CLAUDE.md or a skill is a request, not a guarantee. A `PreToolUse` hook that blocks the edit is enforcement." https://code.claude.com/docs/en/features-overview — 3장의 "부탁(CLAUDE.md·skill) / 정해진 순간 반드시 실행(Hook)·설정대로 차단(권한 설정)"과 같은 구분. README의 "Mandatory workflows, not suggestions"는 지시문을 얼마나 강하게 썼는지에 대한 표현.
- brainstorming: 질문은 한 번에 하나씩("Ask one at a time"), 작업에 맞춰("Make every question specific to their project"), 준비된 질문 목록을 그대로 읽지 않음("This is territory, not a script. Never read these out as questions"). 요청이 명확한 작은 일은 바로 수행("Do it, and say what you did."). 설계 문서 승인 전에는 만들지 않으며("Nothing gets built until your human partner approves the design doc"), 사용자가 질문을 건너뛰면 이 단계도 끝남.
- test-driven-development: "Use when implementing any feature or bugfix, before writing implementation code" / "Write the test first. Watch it fail. Write minimal code to pass." — 카드의 "테스트(합격 기준)"는 테스트가 통과해야 할 기준이라는 뜻의 쉬운 말 풀이.
- systematic-debugging: "Use when encountering any bug, test failure, or unexpected behavior, before proposing fixes" / "NO FIXES WITHOUT ROOT CAUSE INVESTIGATION FIRST" — 오류 읽기·재현·최근 변경 확인("Read Error Messages Carefully", "Reproduce Consistently", "Check Recent Changes") → 같은 코드베이스의 정상 동작 코드 찾아 비교("Find Working Examples - Locate similar working code in same codebase") → 가설 검증 → 수정. 카드의 "정상 코드와 비교"는 같은 코드베이스에서 정상 동작하는 코드와 비교한다는 뜻이며, 과거 비슷한 버그를 찾는다는 뜻이 아님.
- verification-before-completion: "requires running verification commands and confirming output before making any success claims" / "NO COMPLETION CLAIMS WITHOUT FRESH VERIFICATION EVIDENCE". 확인 대상은 테스트·린터·빌드 출력, 버그 증상 재현, VCS diff, 요구사항 체크리스트 — 보고서 수치·출처를 원자료와 대조하는 절차는 없음.
- 설치 명령(자세한 방법으로 옮긴 `/plugin install` 줄): README의 Claude Code 설치 절과 글자 그대로 같음. 공식 마켓(`claude-plugins-official`)에 등록돼 있음. `/plugin install`은 Claude Code 대화 입력창에 치는 명령이고, VS Code 확장만 쓰는 경우의 CLI 전용 기능은 "run `claude` in VS Code's integrated terminal. This requires the standalone CLI install" https://code.claude.com/docs/en/vs-code
- VS Code: 입력창 `/plugins` → Manage plugins(Plugins·Marketplaces 탭). 공식 마켓플레이스는 터미널에서 대화형 세션을 처음 열 때 자동 추가되므로, VS Code만 썼다면 Plugins 탭이 비어 있을 수 있음("If the tab lists no plugins, add `anthropics/claude-plugins-official` on the **Marketplaces** tab first"). VS Code 입력창에서 `/plugin install …`을 그대로 쓸 수 있는지는 문서에 명시가 없음. 슬라이드의 "안 보이면"은 목록이 비었을 때와, 다른 마켓플레이스만 등록돼 있어 superpowers가 없을 때를 함께 가리킴. 공식 마켓플레이스가 이미 등록돼 있는데도 안 보이면 Marketplaces 탭의 새로고침 아이콘으로 목록 갱신("Click the refresh icon to update a marketplace's plugin list"). https://code.claude.com/docs/en/plugins/install · https://code.claude.com/docs/en/vs-code#manage-plugins

---

## 챕터 8 합산

- 슬라이드 1장
- 발표 노트: 180초 = 3분 정확
- 핵심 메시지: "superpowers = 검증 절차를 습관화하는 도구(코드 작업 중심). 설문 1순위 고민을 덜어 주는 보조 수단이고, 보고서 수치·출처 대조는 사람이 따로"
