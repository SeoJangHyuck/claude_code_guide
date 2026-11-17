# 챕터 7: 사내 공유 4단계 (4슬라이드 / 5분)

> 톤 가이드: 시연(챕터 6)에서 본 skill·subagent(보조 작업자)·hook을 옆자리·팀·전사로 어떻게 넘기는지 4단계로. 청중 대부분이 비개발자라 슬라이드는 단계마다 "누가 무엇을 보내고, 받는 사람은 어떻게 하는지" 두 줄 + 적합 규모·장단점만 둔다. **단계 사이 차이가 화면만으로 보이게** 같은 칸에 같은 기준을 쓴다: 태그 = git 필요 여부(1·2단계 git 불필요, 3·4단계 git 필요), 동료 칸 결과 줄 = 어디서 쓰이고 새 버전을 어떻게 받는지(그 작업 폴더에서만 / 다음 대화부터 내 모든 작업 폴더에서 / 새 버전은 그 폴더에서 다시 받기 / 목록에서 골라 설치·이름으로 업데이트), 적합 규모 = 1~2명 / 3~5명 / 6~10명 / 11명 이상(2·3단계가 겹치지 않게). 명령·JSON·설정 키·Windows 경로·자격 증명·자동 업데이트 설정·이름 규칙 같은 세부는 슬라이드마다 아래 **자세한 방법 (슬라이드에서 옮긴 세부)** 에 두고, 청중에게는 슬라이드 하단 📖 공식 문서 링크로 안내한다. 핵심 용어는 장에서 처음 나올 때 쉬운 말을 붙인다(skill = 재사용 가능한 절차서, plugin = 설치 꾸러미, git 저장소 = 변경 이력이 남는 공유 폴더, 마켓플레이스 = 팀 플러그인 목록). 슬라이드 용어는 덱 전체와 같게 "세션" → "대화", "프로젝트" → "작업 폴더"(VS Code에서 연 폴더). CLAUDE.md·rules는 플러그인에 못 넣으므로 작업 폴더째 공유(개인 설정 파일 제외) — 6장 "— 7장"이 가리키는 이 길을 7-1 하단 ※ 한 줄로 장 앞쪽에서 안내한다(플러그인에 넣으려면 skill로 옮기고 paths 유지). 마지막 4단계는 부서·전사용 팀 목록. `claude …` 셸 명령은 CLI 별도 설치가 필요하다는 점(VS Code 확장만으로는 터미널에 `claude` 없음)은 7-2 노트에서 짚는다.

> 모든 명령어는 2026-11 기준 (Claude Code v2.1.326) 공식 형식.

(장 표지 부제: "skill 폴더 → 묶음 zip → 묶음 git → 팀 목록." — 이전 부제 "옆자리 한 명부터 전사까지 — 규모에 맞춰 고르는 4단계."는 표지에서 말로 소개)

---

## 슬라이드 7-1 — 1단계: skill 폴더 하나로 공유 (1분, git 불필요)

**핵심 메시지**: "skill 1개는 폴더째 메신저로 보내면 끝. 받는 사람은 자기 작업 폴더의 .claude/skills/ 아래에 넣기만 — 그 작업 폴더에서만 쓰인다. git 불필요, 명령어도 거의 불필요. CLAUDE.md·rules는 플러그인에 못 넣으니 작업 폴더째 공유(개인 설정 파일 제외)."

**본문 콘텐츠** (슬라이드와 같은 내용):

```
1단계 — skill 폴더 하나로 공유
skill(재사용 가능한 절차서) 1개를 옆자리 동료에게 넘기는 가장 쉬운 방법.

  ───────────────────────────────────────────

  1  skill 폴더 전달                              [git 불필요]

  당신:
    skill 폴더를 통째로 메신저·이메일로 전달

  동료:
    자기 작업 폴더의 .claude/skills/ 아래에 폴더째 넣기
    → 그 작업 폴더에서만 사용 (안 보이면 새 대화 열기)

  ───────────────────────────────────────────

  적합 규모 : 1~2명
  장점      : 명령어 거의 없이 바로 사용
  단점      : skill 1개씩만 (묶음은 2단계)

  ※ CLAUDE.md·rules는 플러그인에 못 넣음 → 작업 폴더째 공유 (개인 설정 파일 제외)
  📖 skill 만드는 법: code.claude.com — Skills 가이드
```

**자세한 방법 (슬라이드에서 옮긴 세부)**:

```
보내는 것: .claude/skills/<skill 이름>/ 폴더를 통째로 (SKILL.md·보조 파일 포함)
  · 전달 수단은 메신저·이메일·USB·공유드라이브 등 무엇이든 가능
  · SKILL.md 파일만 떼어 보내지 않는다 — 이름이 모두 SKILL.md라 서로 덮어쓰고 보조 파일도 빠짐

받는 사람:
  · 작업 폴더(VS Code에서 연 폴더)의 .claude/skills/<skill 이름>/SKILL.md 가 되도록 넣는다
    → 그 작업 폴더에서만 쓰임 (내 모든 작업 폴더에서 쓰려면 사용자 폴더의
      ~/.claude/skills/ — 2단계 플러그인을 넣는 자리와 같음)
  · zip으로 받아 풀었을 때 같은 이름 폴더가 한 겹 더 생기면
    (예: Windows 기본 압축 풀기 → 내-skill\내-skill\SKILL.md) 안쪽 폴더를 넣는다
    — 바깥 폴더째 넣으면 오류 없이 인식되지 않음
  · 대화(세션) 중에 추가한 skill은 바로 인식
    (대화 시작 후 skills 폴더를 새로 만들었다면 /reload-skills 또는 새 대화
     — 슬라이드의 "안 보이면 새 대화 열기"가 이 경우. 처음 skill을 받는 동료는
     skills 폴더를 새로 만드는 일이 흔함)

단점 보충:
  · subagent(보조 작업자)·hook까지 묶어 보내려면 2단계(플러그인)
  · CLAUDE.md·rules는 작업 폴더째 공유 (슬라이드 하단 ※ 줄, 아래 "같은 작업 폴더를 쓰는 팀").
    플러그인에 넣으려면 skill로 옮기고 paths 유지 — 꼭 지킬 규칙은 hook으로

같은 작업 폴더를 쓰는 팀 (하단 ※ 줄의 자세한 내용 — 이전에는 7-3 하단에 있던 줄):
   .claude/ + 루트 .mcp.json(루트에 둔 CLAUDE.md 포함)을 작업 폴더의 git 저장소에 커밋하거나
   작업 폴더를 zip으로 전달 — 어느 쪽이든 settings.local.json 등 개인 파일은 제외
   → CLAUDE.md·rules·권한 설정·hook까지 공유
   동료는 처음 열 때 폴더 신뢰와 MCP 서버 승인 한 번씩
   (CLAUDE.md·rules·권한 설정은 플러그인에 넣을 수 없음 —
    플러그인에 넣으려면 skill로 옮기고 paths 유지, 꼭 지킬 규칙은 hook으로)

태그의 git: 1~4단계 태그는 "git 필요 여부" 한 기준(1·2단계 불필요, 3·4단계 필요).
  git 풀이("변경 이력이 남는 공유 폴더")는 3단계 리드 — 1·2단계는 git을 몰라도 됨.

skill 형식 (이전 슬라이드 하단 "핵심 형식"):
  SKILL.md 상단 frontmatter(파일 맨 위 설정) — 필드는 모두 선택,
  description: 권장(Claude가 이것을 보고 자동 호출 판단 → 핵심 용도를 앞쪽에).
  name: 생략 시 폴더 이름이 명령 이름.

📊 적합도 (이전 표기)
   소요 시간 : 2분
   적합 규모 : 1~2명, 비개발자(git이 어려운 분)
   장점      : 가장 직관적, git 불필요 · 명령어 거의 없음
```

**발표 노트 (1분)**:
> "1단계, 가장 쉬운 방법입니다. 태그에 'git 불필요'라고 돼 있죠 — git이 뭔지는 3단계에서 말씀드릴 텐데, 1·2단계는 몰라도 됩니다. skill은 폴더 하나예요. 내 skill 폴더를 통째로 메신저·이메일로 동료한테 보내고, 동료는 자기 작업 폴더, 그러니까 VS Code에서 연 폴더의 .claude/skills 아래에 그 폴더째 넣으면 끝. 이렇게 넣은 skill은 그 작업 폴더에서만 쓰입니다. 모든 작업 폴더에서 쓰는 방법은 다음 단계에서 나와요. SKILL.md 파일만 떼어서 보내면 안 됩니다 — 파일 이름이 다 SKILL.md라서 서로 덮어쓰고, 보조 파일도 빠지거든요. zip으로 받아서 풀었더니 같은 이름 폴더가 한 겹 더 생겼다면 안쪽 폴더를 넣으셔야 인식됩니다. 명령어는 보통 필요 없고, 대화 도중에 skills 폴더를 처음 만들었다면 skill이 안 보일 수 있는데 그때는 새 대화를 여시면 됩니다(`/reload-skills`도 됩니다). 한계는 한 번에 한 개씩만 가능하다는 것. 묶음으로 보내려면 다음 단계입니다.
>
> 아래 ※ 한 줄도 짚고 가겠습니다. 6장에서 본 CLAUDE.md나 rules는 skill이 아니라서 다음 단계의 플러그인에 넣을 수 없습니다. 이건 작업 폴더째 공유하세요. `.claude` 폴더와 루트 `.mcp.json`을 작업 폴더의 git 저장소에 올리든 폴더를 zip으로 보내든, CLAUDE.md·rules·권한 설정·hook까지 넘어갑니다. 어느 쪽이든 개인용 `settings.local.json`은 빼시고요."

**시각 표현 메모**:
- 좌우 흐름 (당신: 폴더째 전달 / 동료: 자기 작업 폴더 .claude/skills/ 아래에 폴더째 넣기 → 그 작업 폴더에서만 사용).
- "그 작업 폴더에서만"을 굵게 — 2단계 동료 칸의 "내 모든 작업 폴더에서"(굵게)와 대비되게.
- 하단 적합도 3칸 + ※ CLAUDE.md·rules 한 줄(7-3 하단에서 옮김, 6장 "— 7장" 연결을 장 앞쪽에서 받음) + 📖 Skills 가이드 한 줄.
- "git 불필요" 태그(1~4단계 태그는 git 필요 여부 한 기준).
- 이전 하단 "핵심 형식"(frontmatter)과 단점 칸의 rules 문구는 위 "자세한 방법"으로 옮김.

**근거 (공식 문서)**:
- skill은 폴더 단위: `.claude/skills/<skill-name>/SKILL.md` + 보조 파일. 프로젝트 skill은 `.claude/skills/<skill-name>/SKILL.md`, 개인 skill은 `~/.claude/skills/<skill-name>/SKILL.md` — 이 깊이에 SKILL.md가 있어야 인식되므로 폴더가 한 겹 더 있으면 안쪽 폴더를 넣는다. https://code.claude.com/docs/en/skills
- "그 작업 폴더에서만 사용": 프로젝트 skill의 적용 범위는 "Sessions in this repository", 개인 skill(`~/.claude/skills/`)은 "All your projects on this machine". https://code.claude.com/docs/en/skills (Where skills live 표)
- 세션 중에 추가한 skill은 바로 인식("Claude Code picks up the change within the current session, without a restart"). 세션 시작 때 없던 skills 폴더를 새로 만들었으면 `/reload-skills`("If you create a top-level skills directory that didn't exist when the session started, run `/reload-skills` to pick up the skills you put there.") 또는 새 대화 → 슬라이드 "(안 보이면 새 대화 열기)". https://code.claude.com/docs/en/skills
- skill 형식(자세한 방법의 frontmatter 줄): 필드는 모두 선택이고 `description`만 권장. Claude가 description을 보고 자동 호출을 판단하며, `description`과 `when_to_use`는 합쳐 1,536자에서 잘리므로 핵심 용도를 앞쪽에 쓴다. `name`을 생략하면 폴더 이름이 명령 이름.
- rules 문구(7장 전체 통일, 자세한 방법·7-1 하단 ※ 줄): "CLAUDE.md·rules는 플러그인에 못 넣음 → 작업 폴더째 공유(개인 설정 파일 제외). 플러그인에 넣으려면 skill로 옮기고 paths 유지."
  - 플러그인에는 rules 컴포넌트가 없고 플러그인 루트의 CLAUDE.md도 로드되지 않음("To include instructions in a plugin, write them as a skill"). https://code.claude.com/docs/en/plugins/components
  - CLAUDE.md(`./CLAUDE.md` 또는 `./.claude/CLAUDE.md`)는 "Team members via source control" — 프로젝트 저장소로 공유. https://code.claude.com/docs/en/memory
  - skill도 `paths` frontmatter 지원: 설정하면 매칭 파일을 다룰 때만 자동 로드. https://code.claude.com/docs/en/skills
  - 동작 차이: `paths` 없는 rule은 세션 시작 때 로드("Rules without `paths` frontmatter are loaded at launch"), skill 본문은 호출될 때 로드("full skill content only loads when invoked"). 매번 지켜야 하는 규칙은 hook으로("If a rule must hold every time … add it to the plugin as a hook rather than a skill").
- 같은 작업 폴더를 쓰는 팀(7-1 하단 ※ 줄 — 이전에는 7-3 하단): 프로젝트 파일을 git에 커밋하면 팀이 함께 씀("Commit project files to git to share them with your team", "keep personal ones such as `settings.local.json` out of your commits"). `.claude/settings.json`을 커밋하면 권한·hook·플러그인 설정이 같아짐. CLAUDE.md는 `./CLAUDE.md` 또는 `./.claude/CLAUDE.md`(루트에 두었다면 함께 커밋). MCP는 루트 `.mcp.json`(project 범위)을 커밋하고, 동료는 처음 쓸 때 서버 승인. 프로젝트 설정의 hook·allow 규칙은 폴더 신뢰 후 적용. https://code.claude.com/docs/en/claude-directory · https://code.claude.com/docs/en/settings · https://code.claude.com/docs/en/mcp#project-scope
- 개인 설정 파일은 git·zip 모두 제외(9장 3단계와 같은 표현): Claude Code가 `settings.local.json`을 git 제외 목록에 자동으로 넣는 것은 git 저장소 안에서 그 파일을 처음 쓸 때뿐("The first time Claude Code writes the file in a git repository that doesn't already ignore it, it adds `**/.claude/settings.local.json` to your global git excludes file"). git 없이 쓰던 폴더를 나중에 `git init` 해서 커밋하면 이 파일이 들어갈 수 있고, 그러면 동료가 폴더를 신뢰하는 순간 내 허용 규칙이 동료 PC에도 적용됨("When the file is tracked in git … Claude Code treats it as repository-supplied instead and holds its rules until you trust the folder"). zip으로 보내면 git에서 추적되지 않는 파일이라 동료 PC에서 동료 본인 파일처럼 읽혀 신뢰 단계 없이 허용 규칙이 쓰일 수 있음("`.claude/settings.local.json` is normally your own file, so Claude Code applies its allow rules and additional directories without the trust step"). https://code.claude.com/docs/en/settings · https://code.claude.com/docs/en/permissions

---

## 슬라이드 7-2 — 2단계: 플러그인 zip 공유 (1분 30초, git 불필요)

**핵심 메시지**: "여러 skill 등을 plugin(설치 꾸러미) 하나로 묶어 zip으로 보낸다. 받는 사람은 풀어서 사용자 폴더의 .claude/skills/ 아래에 넣으면 다음 대화부터 내 모든 작업 폴더에서 쓴다(1단계는 그 작업 폴더에서만)."

**본문 콘텐츠** (슬라이드와 같은 내용):

```
2단계 — 플러그인 zip 공유
여러 skill 등을 plugin(설치 꾸러미) 하나로 묶어 zip 파일로 전달.

  ───────────────────────────────────────────

  2  플러그인 zip 전달                            [git 불필요]

  당신:
    5장 ⑦ 구조대로 플러그인 폴더 만들기
    → zip으로 압축해 메신저로 전달

  동료:
    압축을 풀어 사용자 폴더의 .claude/skills/ 아래로 폴더째 이동
    → 다음 대화부터 내 모든 작업 폴더에서 사용

  ───────────────────────────────────────────

  적합 규모 : 3~5명
  장점      : 여러 개를 한 번에 설치
  단점      : 고칠 때마다 zip 다시 전달

  📖 폴더 구조·흔한 실수: 플러그인 만들기 가이드
```

**자세한 방법 (슬라이드에서 옮긴 세부)**:

```
① 플러그인 디렉토리 구조 (이름·위치 자유)

  my-plugin/                          ← 플러그인 루트
    ├── .claude-plugin/
    │   └── plugin.json               ← 권장 (~/.claude/skills/에 넣어 쓸 때 필수)
    ├── skills/<이름>/SKILL.md
    ├── agents/<이름>.md
    └── hooks/hooks.json              ← 선택

  ⚠️ 흔한 실수: skills·agents·hooks를 .claude-plugin/ 안에 넣지 말 것.
     .claude-plugin/ 폴더 '옆'(플러그인 루트)에 같은 레벨로.

② plugin.json (4필드면 충분, 필수 키는 name 하나)

  {
    "name": "research-team-plugin",       ← 호출 prefix
    "description": "정책 연구원 업무 자동화 묶음",
    "version": "1.0.0",
    "author": { "name": "BDI 데이터팀" }
  }

  → 동료가 호출할 때:  /research-team-plugin:skill-name
                       (네임스페이스 = name 필드)

③ 로컬 검증 → zip 압축 → 메신저 전달

  $ claude --plugin-dir ./my-plugin    ← 보내기 전 검증

동료의 설치 (명령 없이):

  ① zip 압축 풀기
  ② 풀린 폴더째 ~/.claude/skills/ 아래로 이동 (사용자 폴더 = ~)
     (Windows: C:\Users\<이름>\.claude\skills\)
     (~/.claude/skills/my-plugin/.claude-plugin/plugin.json 이 되도록 —
      압축을 풀었을 때 같은 이름 폴더가 한 겹 더 생기면(my-plugin\my-plugin)
      plugin.json이 든 안쪽 폴더를 옮김. 바깥 폴더를 옮기면 오류 없이 인식 안 됨)
     (Mac Finder: .claude가 숨김 폴더 → ⌘⇧G로 ~/.claude/skills 입력해 이동,
      skills 폴더가 없으면 ~/.claude 안에 새로 만들기)
     (폴더 이름은 skills지만 .claude-plugin/plugin.json이 든 폴더를 넣으면
      플러그인으로 읽힘 — skill만 넣는 자리가 아님)
     → 다음 대화(세션)부터 내 모든 작업 폴더에서 자동으로 읽힘
     → 지금 대화에 바로 적용: /reload-plugins

  ※ 1회 시험만: claude --plugin-dir ./my-plugin.zip (그 세션에만 로드)

  ※ 셸 명령(claude …)은 CLI 별도 설치 필요 — VS Code 확장만으로는
     터미널에 claude 없음 · 확장에서 플러그인 관리는 입력창 /plugins

📊 적합도 (이전 표기)
   소요 시간    : 30분 (1회성)
   적합 규모    : 3~10명, git이 어려운 팀
                 (슬라이드는 3단계와 겹치지 않게 3~5명 — zip은 고칠 때마다
                  받는 사람 모두에게 다시 보내야 하므로 소수에 맞음. git 여부는 태그로)
   장점        : 묶음 설치, git 서버·계정 불필요, 네임스페이스로 충돌 방지
   단점        : 자동 업데이트 X (수정 시 zip 다시 전달)
```

**발표 노트 (1분 30초)**:
> "2단계, 플러그인 zip 공유입니다. 1단계가 skill 하나였다면 여기는 묶음이에요. 플러그인은 skill·subagent(보조 작업자)·hook을 한 번에 설치하도록 묶은 꾸러미입니다. 그리고 1단계와 달리 받는 쪽이 사용자 폴더에 넣기 때문에, 그 작업 폴더 하나가 아니라 내 모든 작업 폴더에서 쓰입니다.
>
> 만드는 분은 5장에서 본 ⑦번 구조대로 폴더를 만들면 됩니다. `.claude-plugin` 폴더 안에는 `plugin.json` 하나만 두고 — 동료가 `~/.claude/skills/`에 넣어 쓰려면 이 파일이 꼭 있어야 합니다 — `skills`·`agents`·`hooks` 폴더는 그 옆, 플러그인 루트에 둡니다. 이 폴더들을 `.claude-plugin/` 안에 넣는 게 흔한 실수인데, 그러면 로드가 안 됩니다. `plugin.json`의 `name`이 불러 쓸 때 앞에 붙는 이름이 되고요. 다 만들면 압축해서 메신저로 보냅니다. 보내기 전에 `claude --plugin-dir`로 시험해 볼 수 있는데, `claude`로 시작하는 건 터미널 명령이라 VS Code 확장만 있으면 CLI를 따로 설치하셔야 합니다. 확장에서는 입력창 `/plugins`로 플러그인을 관리하고요.
>
> 받는 분은 zip을 풀어 그 폴더째 내 사용자 폴더의 `.claude/skills` 아래로 옮기면 끝이에요. Mac은 `~/.claude/skills` — Finder에선 `.claude`가 숨김 폴더라 ⌘⇧G를 누르고 경로를 입력해 이동하시고, Windows는 `C:\Users\<이름>\.claude\skills\`고요. skills 폴더가 아직 없으면 새로 만드세요. 폴더 이름이 skills라서 헷갈리실 수 있는데, 플러그인도 이 폴더에 넣으면 됩니다. 주의할 점 하나 — 압축을 풀었을 때 같은 이름 폴더가 한 겹 더 생기면 `plugin.json`이 든 안쪽 폴더를 옮기셔야 합니다. 바깥 폴더를 옮기면 오류도 없이 인식이 안 돼요. 다음 대화부터 내 모든 작업 폴더에서 자동으로 읽히고, 지금 대화에 바로 쓰려면 `/reload-plugins`. 단점은 자동 업데이트가 없다는 것 — 고치면 zip을 다시 보내야 합니다. 그게 부담되면 다음 3단계로 갑니다."

**시각 표현 메모**:
- 좌측(당신): 만들기 2줄(5장 ⑦ 구조로 폴더 만들기 → zip 전달). 우측(동료): 받기 2줄(사용자 폴더 .claude/skills/ 아래로 이동 → 다음 대화부터 **내 모든 작업 폴더에서** 사용 — 굵게, 1단계 "그 작업 폴더에서만"과 대비).
- 적합 규모는 3~5명(3단계 6~10명과 겹치지 않게), "git 없이"는 태그 "git 불필요"와 겹쳐 뺌.
- 폴더 트리·plugin.json·`--plugin-dir`·Windows 경로·`/reload-plugins`·네임스페이스·CLI 안내·흔한 실수는 슬라이드에서 빼고 위 "자세한 방법"으로 옮김. 슬라이드에는 📖 플러그인 만들기 가이드(흔한 실수 포함) 링크만.
- 글이 줄어 2단계만 쓰던 촘촘한 레이아웃(compact)과 좌우 1.3:1 비율을 없애고 1·3·4단계와 같은 기본 레이아웃으로 맞춤.

**근거 (공식 문서)**:
- 플러그인 정의: skills·agents·hooks·MCP 서버를 담은 디렉토리 + 매니페스트 `plugin.json` (이름·위치 자유). https://code.claude.com/docs/en/plugins/create (Create a plugin)
- 자세한 방법의 plugin.json 예시(4필드)는 그대로 쓸 수 있는 전체 JSON으로 이전 라운드에서 검증 통과 확인(이전 슬라이드는 공간상 필드 목록만 표시).
- 매니페스트는 선택이고, 두면 `name`만 필수 키. 단 `~/.claude/skills/` 아래 폴더는 `.claude-plugin/plugin.json`이 있어야 플러그인으로 로드됨("a folder there that contains a `.claude-plugin/plugin.json` is a skills-directory plugin"). https://code.claude.com/docs/en/plugins/manifest-reference · https://code.claude.com/docs/en/plugins/create
- 흔한 실수 경고 원문: "Only `plugin.json` goes inside `.claude-plugin/`. Components saved there don't load."
- 호출 prefix: 플러그인 `skills/` 아래 skill은 `/플러그인이름:skill이름`("`my-plugin/skills/review/SKILL.md` → `/my-plugin:review`"). https://code.claude.com/docs/en/skills
- 로컬 테스트: `--plugin-dir` 플래그 (zip 압축 파일도 지원, v2.1.128+)
- 받는 쪽: 플러그인 디렉토리를 `.claude-plugin/plugin.json`째 `~/.claude/skills/` 아래로 옮기면 세션 시작 때 로드("they move the plugin directory, with its `.claude-plugin/plugin.json`, under `~/.claude/skills/`" — 관리자가 skills 폴더 플러그인을 막아 두면 로드 안 됨). 지금 세션은 `/reload-plugins`, 한 세션만 쓰려면 `claude --plugin-dir <폴더 또는 .zip>`. https://code.claude.com/docs/en/plugins/publish#share-a-plugin-without-a-marketplace
- "내 모든 작업 폴더에서 사용": 개인 skills 폴더 `~/.claude/skills/`는 이 컴퓨터의 모든 프로젝트가 함께 씀("which all your projects on this machine share"). https://code.claude.com/docs/en/plugins/create
- "다음 대화부터": skills 폴더 플러그인은 세션 시작 때 로드("loads each one when a session starts, with no flag and no install step"), 지금 세션은 `/reload-plugins`. 폴더 이름이 skills여도 `.claude-plugin/plugin.json`이 든 폴더는 플러그인으로 로드("a folder there that contains a `.claude-plugin/plugin.json` is a skills-directory plugin"). https://code.claude.com/docs/en/plugins/create
- 같은 이름 폴더가 한 겹 더 생기는 경우: Windows 기본 압축 풀기는 zip 이름으로 폴더를 만들어 그 안에 풀기 때문에, zip 안에 `my-plugin/`이 들어 있으면 `my-plugin\my-plugin\`이 됨(0장 bdi_demo 안내와 같은 현상). 바깥 폴더를 옮기면 `~/.claude/skills/my-plugin/my-plugin/.claude-plugin/plugin.json`이 되어 skills 폴더 바로 아래에 매니페스트가 없으므로 플러그인으로 인식되지 않고 오류도 없음.
- Windows에서 `~/.claude`는 `%USERPROFILE%\.claude` (예: `C:\Users\이름\.claude\skills\`). 원문: "On Windows, `~/.claude` resolves to `%USERPROFILE%\.claude`." https://code.claude.com/docs/en/claude-directory · macOS Finder는 이름이 `.`으로 시작하는 폴더를 기본으로 숨기므로 ⌘⇧G(폴더로 이동)에 경로를 입력해 이동.
- 셸 명령: VS Code 확장 설치만으로는 터미널에 `claude`가 생기지 않음("Installing the extension does not put `claude` on your shell PATH") → `claude --plugin-dir` 같은 셸 명령은 CLI를 별도 설치해야 함. 확장에서는 입력창 `/plugins`로 Manage plugins 화면(Plugins·Marketplaces 탭)을 연다. https://code.claude.com/docs/en/vs-code#manage-plugins
- 공식 안내: 플러그인 루트는 `.claude/`가 아닌 별도 디렉토리, 기존 `.claude/` 설정은 별도 폴더로 복사해 변환 ("The plugin root is the plugin's own directory, not `~/.claude/` itself." / "Convert an existing `.claude/` setup").

---

## 슬라이드 7-3 — 3단계: 플러그인 git 공유 (1분 15초, git 필요)

**핵심 메시지**: "플러그인 폴더를 git 저장소(변경 이력이 남는 공유 폴더)에 올리면, 동료는 한 번 내려받고 새 버전은 그 폴더에서 다시 받는다(git pull). zip 재전달이 없다. git에 익숙한 팀용."

**본문 콘텐츠** (슬라이드와 같은 내용):

```
3단계 — 플러그인 git 공유
git 저장소(변경 이력이 남는 공유 폴더)에 올려 두고 동료가 직접 내려받는 방식.

  ───────────────────────────────────────────

  3  플러그인 git 공유                            [git 필요]

  당신:
    2단계의 플러그인 폴더를 팀 git 저장소에 올리기

  동료:
    사용자 폴더의 .claude/skills/ 아래로 내려받기
    → 다음 대화부터 사용 · 새 버전은 그 폴더에서 다시 받기

  ───────────────────────────────────────────

  적합 규모 : 6~10명
  장점      : zip 재전달 없음 · 변경 이력 남음
  단점      : git 사용법을 익혀야 함

  📖 code.claude.com — 마켓플레이스 없이 공유
```

**자세한 방법 (슬라이드에서 옮긴 세부)**:

```
당신 — 2단계와 같은 플러그인 디렉토리를 git 저장소에 push:

  $ cd my-plugin/
  $ git init -b main && git remote add origin <git-url>
  $ git add . && git commit -m "share plugin"
  $ git push -u origin main

동료의 설치 (한 줄 — skills 폴더에 바로 clone):

  $ git clone <git-url> ~/.claude/skills/research-team-plugin
  → 다음 대화(세션)부터 자동으로 읽힘

새 버전 받기 (동료 — 슬라이드의 "그 폴더에서 다시 받기", 터미널 명령):

  $ cd ~/.claude/skills/research-team-plugin && git pull
  → /reload-plugins (또는 새 대화)
  ※ 플러그인마다 받은 폴더에서 각각 실행 — 이름으로 업데이트는 4단계

※ Windows: 위 git 명령은 모두 VS Code 터미널을 Git Bash로 열어 실행
   (사전 준비의 Git for Windows에 포함)

핵심 형식: git URL은 HTTPS(https://github.com/팀/플러그인.git) 또는
          SSH(git@github.com:팀/플러그인.git) 모두 가능.
          private 저장소는 동료의 평소 git 로그인으로 clone·pull
→ 이름으로 설치·명령 한 줄 업데이트는 4단계 (marketplace.json)

⭐ 2단계(zip) 대비 차별점 (슬라이드 장점 칸 "zip 재전달 없음")
   업데이트      : zip 재전달 대신 동료가 그 폴더에서 git pull
   버전 관리      : git 이력으로 변경 추적
   설치 한 줄     : zip 풀기·폴더 옮기기 단계 없음

같은 작업 폴더를 쓰는 팀(CLAUDE.md·rules 공유): 이전 슬라이드 하단 ※ 줄과 그 세부는
   장 앞쪽 7-1로 옮김(6장 "— 7장" 연결을 1단계에서 받도록).

📊 적합도 (이전 표기)
   소요 시간    : 30분 (1회성)
   적합 규모    : 3~10명, git에 익숙한 팀
                 (슬라이드는 2단계와 겹치지 않게 6~10명, git 여부는 태그 "git 필요"로)
   장점        : pull 한 줄 업데이트, 버전 추적, 설치 더 간결
   단점        : git 사용 학습 필요
```

**발표 노트 (1분 15초)**:
> "3단계, 플러그인 git 공유입니다. 여기서부터 태그가 'git 필요'로 바뀝니다. git 저장소는 파일의 변경 이력이 남는 공유 폴더라고 보시면 돼요. git을 쓸 수 있는 분이라면 이 단계가 훨씬 편합니다.
>
> 2단계랑 똑같이 만든 플러그인 폴더를 팀 git 저장소에 올립니다(push). 그러면 동료는 `git clone` 한 줄로 그 저장소를 자기 사용자 폴더의 `.claude/skills/` 아래에 받으면 끝이에요. 다음 대화부터 자동으로 읽히고, zip 풀고 옮기는 단계가 없습니다.
>
> Windows에서는 VS Code 터미널을 Git Bash로 열어서 실행하세요. 터미널 + 옆 화살표에서 고를 수 있어요. 기본으로 열리는 PowerShell, 특히 Windows에 들어 있는 5.1은 `&&`를 지원하지 않고 git에 넘기는 `~`를 홈 폴더로 바꿔 주지 않아서, 명령이 멈추거나 엉뚱한 폴더에 받아질 수 있습니다.
>
> 2단계 zip과의 차이는 업데이트입니다. zip을 다시 보낼 필요가 없어요. 여러분이 skill을 수정해서 올리면, 동료는 받은 그 폴더에서 새 버전을 다시 받습니다 — 터미널에서 `git pull` 한 줄이에요. 올리기만 해서 동료 환경이 저절로 바뀌지는 않으니까, 새 버전을 올리면 한마디 알려 주세요. 그리고 git 이력으로 누가 언제 뭘 바꿨는지 추적도 됩니다.
>
> 플러그인이 여러 개면 폴더마다 이 일을 해야 하죠. 목록에서 이름으로 골라 설치하고 이름으로 업데이트까지 하게 하려면 marketplace.json이 필요한데, 그게 다음 4단계입니다. 개발자 분들이나 git에 익숙한 팀이면 이 단계로, 비개발자 분들은 2단계 zip이 더 편하시고요. 본인 환경에 맞게 선택하세요."

**시각 표현 메모**:
- 좌우 흐름 (당신: 팀 git 저장소에 올리기 / 동료: 사용자 폴더 .claude/skills/ 아래로 내려받기 → 새 버전은 **그 폴더에서 다시 받기** — 굵게, 4단계 "이름으로 업데이트"와 대비).
- 태그 "git 필요"(이전 "git 사용" — 1~4단계 태그를 git 필요 여부 한 기준으로). 장점 칸 "zip 재전달 없음"은 2단계 단점 칸 "고칠 때마다 zip 다시 전달"과 짝. 적합 규모 6~10명(2단계 3~5명과 겹치지 않게).
- 리드·동료 칸·장점 칸의 "명령 한 줄"은 뺌 — 명령 한 줄 업데이트는 4단계 기능이고, 3단계의 git pull은 터미널에서 폴더마다 실행(V-03).
- git 명령 4줄·clone·pull 명령·Windows Git Bash 안내·git URL 형식·⭐ 차별점은 슬라이드에서 빼고 위 "자세한 방법"으로 옮김.
- 하단 안내 칸: 📖 링크만. 이전 ※ 줄(CLAUDE.md·rules는 작업 폴더째 공유)은 7-1로 옮김.

**근거 (공식 문서)**:
- 마켓플레이스 없이 공유: 저장소를 clone해 쓰고 다음 버전은 다시 pull("To get your next version they pull or download again." → 슬라이드 "새 버전은 그 폴더에서 다시 받기"). 플러그인 폴더를 `~/.claude/skills/` 아래에 두면 세션 시작 때 로드. 원문: "Adding a `.claude-plugin/marketplace.json` to that same repository is what lets people install by name and update with a command" → 이름으로 설치·업데이트는 4단계. https://code.claude.com/docs/en/plugins/publish#share-a-plugin-without-a-marketplace
- `git init -b main`: git의 기본 첫 브랜치 이름은 아직 `master`라서, `-b main` 없이 만들면 `git push -u origin main`이 "src refspec main does not match any"로 실패. https://git-scm.com/docs/git-init
- Windows는 Git Bash에서 실행: VS Code의 Windows 기본 터미널은 PowerShell("The default terminal profile shell defaults to `$SHELL` on Linux and macOS and PowerShell on Windows." https://code.visualstudio.com/docs/terminal/profiles — 새 터미널 드롭다운에서 다른 프로필 선택). `&&`는 PowerShell 7부터 지원("Beginning in PowerShell 7, PowerShell implements the `&&` and `||` operators" https://learn.microsoft.com/powershell/module/microsoft.powershell.core/about/about_pipeline_chain_operators) → Windows 기본 Windows PowerShell 5.1에서는 문법 오류. `~`는 PowerShell 명령의 경로 맨 앞에서만 홈 폴더로 펼쳐지고 git 같은 외부 명령에는 글자 그대로 전달("When it's used with PowerShell commands at the beginning of a path, PowerShell expands the tilde character to the user's home directory." 외부 명령용 펼치기는 PowerShell 7.5-preview.2의 실험 기능 https://learn.microsoft.com/powershell/module/microsoft.powershell.core/about/about_parsing) → clone이 현재 폴더 아래 `~` 폴더로 받아져 플러그인이 로드되지 않음(오류 없음). Git Bash는 Git for Windows에 포함("Installing Git for Windows is optional. It provides Git Bash" https://code.claude.com/docs/en/setup).
- `/plugin install <이름>@<git-url>` 형식은 동작하지 않음 — `@` 뒤에는 등록된 마켓플레이스 이름이 와야 함. https://code.claude.com/docs/en/plugins/install
- private 저장소: 3단계는 동료가 직접 `git clone`·`git pull`하므로 평소처럼 git 로그인을 거치면 됨(미리 저장할 필요 없음). 로그인 창 없이 저장된 자격 증명만 쓰는 쪽은 4단계(Claude Code가 marketplace add·install·update 때 대신 clone) → 4단계 "팀원 준비물". https://code.claude.com/docs/en/plugins/install#add-a-private-marketplace
- 하단 ※ 줄(CLAUDE.md·rules는 작업 폴더째 공유)은 장 앞쪽 7-1로 옮김 — 그 근거(같은 작업 폴더를 쓰는 팀, 개인 설정 파일 제외)도 7-1 근거에 있음.

---

## 슬라이드 7-4 — 4단계: 팀 마켓플레이스 (1분 15초)

**핵심 메시지**: "마켓플레이스(팀 플러그인 목록) 파일 하나를 팀 저장소에 두면, 팀원은 목록 주소를 한 번 등록하고 필요한 플러그인을 목록에서 골라 설치한다. 새 버전도 이름으로 업데이트(3단계는 폴더마다 다시 받기)."

**본문 콘텐츠** (슬라이드와 같은 내용):

```
4단계 — 팀 마켓플레이스
마켓플레이스(팀 플러그인 목록)를 한 번 등록하면 이름으로 골라 설치.

  ───────────────────────────────────────────

  4  팀 마켓플레이스                              [git 필요]

  당신 (1회 준비):
    팀 git 저장소에 플러그인 목록 파일(marketplace.json) 작성
    → 새 플러그인은 목록에 항목만 추가

  팀원:
    ① 팀 목록 주소 등록 (최초 1회)
    ② 필요한 플러그인만 골라 설치
    VS Code: 입력창 /plugins → Marketplaces 탭에서 등록 → Plugins 탭에서 설치

  ───────────────────────────────────────────

  적합 규모 : 11명 이상 (부서·전사)
  장점      : 목록에서 골라 설치 · 이름으로 업데이트
  단점      : 처음 준비가 번거로움

  ⚠️ 비공개 저장소면 팀원 PC에 git 로그인 정보를 미리 저장 — 없으면 로그인 창 없이 실패
  📖 마켓플레이스 만들기 가이드
```

**자세한 방법 (슬라이드에서 옮긴 세부)**:

```
팀 공용 git 저장소에 .claude-plugin/marketplace.json 1회 생성
(name·owner·plugins 필수)

  {
    "name": "bdi-plugins",
    "owner": { "name": "BDI 데이터팀" },
    "plugins": [
      { "name": "busan-report",
        "source": { "source": "url", "url": "git@...:busan.git" } },
      { "name": "thursday-mail",
        "source": { "source": "url", "url": "git@...:mail.git" } }
    ]
  }
  (git@... 자리에 사내 git 서버 주소)

이름 규칙: 마켓플레이스 name과 plugins 항목의 name은 영문·숫자·.·_·-만,
  첫 글자는 영문·숫자 — 한글·공백 불가 (설치 안 됨)
  owner.name은 표시용이라 한글 가능 (비우면 안 됨)

→ 신규 플러그인은 항목만 추가 · 팀원은 이름@bdi-plugins로 바로 설치
  (이름@마켓플레이스로 설치하면 설치 직전에 카탈로그를 새로 받음)
→ 새 버전: 해당 플러그인의 plugin.json version 올려 push

팀원 한 번만 등록:
  /plugin marketplace add <git-url>
  (<git-url>: SSH 주소 git@서버:팀/bdi-plugins.git 또는
   .git으로 끝나는 HTTPS 주소)

필요한 것만 골라 설치:
  /plugin install busan-report@bdi-plugins

VS Code: /plugins → Marketplaces 탭에 <git-url> 등록 → Plugins 탭에서 설치

새 버전 받기 (슬라이드 장점 칸의 "이름으로 업데이트" — 셸 명령, CLI 설치 필요):
  claude plugin update busan-report@bdi-plugins
  (새 버전은 다음 대화(세션)부터, 실행 중인 대화는 /reload-plugins)
  (또는 아래 자동 업데이트 설정 — 이 경우 팀원이 명령을 칠 필요 없음)

3단계와의 차이: 3단계는 플러그인마다 git clone·git pull을 N번(받은 폴더마다 다시 받기).
               4단계는 카탈로그 1번 add → 목록에서 골라 설치·이름으로 업데이트.

자동 업데이트(기본 꺼짐):
  프로젝트 .claude/settings.json의 extraKnownMarketplaces 항목에 "autoUpdate": true를
  넣어 커밋 → 등록·자동 업데이트까지 미리 설정 (팀원이 그 폴더를 신뢰한 뒤 적용)

팀원 준비물: git 설치 (슬라이드 태그 "git 필요" — 이전 하단 "팀원 PC에 git 필요"를 태그로 올림)
  · private 저장소는 자격 증명 미리 저장 (Claude Code는 로그인 창 없이 clone —
    저장돼 있지 않으면 등록·설치·업데이트가 실패. 슬라이드 하단 ⚠️ 줄)
    HTTPS: credential helper (GitHub는 gh auth login 후 gh auth setup-git)
    SSH: 암호를 묻지 않고 동작하는 키(예: ssh-agent에 등록) + known_hosts 등록

📊 적합도 (이전 표기)
   소요 시간    : 초기 4시간 (1회) + 신규 플러그인당 30분
   적합 규모    : 11명 이상 (팀·부서·전사 표준화)
   장점        : 표준 플러그인 카탈로그, 이름 설치·명령 한 줄 업데이트
   단점        : 초기 셋업 부담
   (직전 슬라이드 태그 "전사 표준화"·장점 "팀 표준 목록 · 명령 한 줄 업데이트"는
    1~3단계와 같은 기준이 되도록 태그 "git 필요"·장점 "목록에서 골라 설치 · 이름으로 업데이트"로)
```

**발표 노트 (1분 15초)**:
> "4단계, 팀 마켓플레이스입니다. 마켓플레이스는 팀 플러그인 목록, 일종의 사내 카탈로그예요. 부서나 전사 단위로 표준화할 때 쓰는 방식입니다.
>
> 팀 공용 저장소에 marketplace.json이라는 목록 파일을 한 번 만들어 두면 그게 팀 카탈로그가 됩니다. 마켓플레이스 이름과 플러그인 이름은 영문·숫자와 점·밑줄·하이픈만 쓸 수 있어요 — 한글이나 공백이 들어가면 설치가 안 됩니다. 새 플러그인은 목록에 항목만 추가하면 되고요.
>
> 팀원은 목록 주소를 처음 한 번 등록하고, 필요한 것만 목록에서 `이름@bdi-plugins`처럼 이름으로 골라 설치합니다. VS Code 확장에서는 `/plugins`의 Marketplaces 탭에 주소를 넣고 Plugins 탭에서 설치하시면 되고, 사내 서버 HTTPS 주소는 끝에 `.git`까지 붙이세요. 3단계와 달리 업데이트도 이름으로 합니다. version을 올려 push 하면 팀원이 터미널에서 `claude plugin update` 한 줄로 받습니다. 플러그인마다 폴더에 들어가 다시 받을 필요가 없죠. 자동 업데이트는 기본이 꺼져 있는데, 팀이 함께 쓰는 작업 폴더의 `.claude/settings.json`에 자동 업데이트 설정을 넣어 커밋해 두면 그 폴더를 신뢰한 팀원은 등록과 자동 업데이트를 한 번에 받습니다.
>
> 태그대로 팀원 PC에도 git이 있어야 합니다. 그리고 아래 경고 한 줄 — 비공개 저장소면 git 로그인 정보를 팀원 PC에 미리 저장해 두셔야 합니다. Claude Code는 로그인 창을 띄우지 않아서, 저장이 안 돼 있으면 등록이나 설치가 그냥 실패합니다. BDI처럼 11명 이상이 공유한다면 이 단계가 맞습니다.
>
> 정리하면 — 1단계는 skill 폴더 하나, 2단계는 묶음 zip, 3단계는 묶음 git, 4단계는 팀 목록. 표지에 적은 그대로입니다. 옆자리 한 명부터 전사까지, 본인 규모와 git 친숙도에 맞게 시작하시면 됩니다. 그리고 다음으로 — 제가 직접 매일 쓰는 플러그인 하나 추천하고 마무리하겠습니다."

**시각 표현 메모**:
- 좌우 흐름 (당신 1회 준비: 목록 파일 작성 / 팀원: 목록 주소 등록 1회 → 골라 설치 + VS Code 경로 한 줄).
- 태그 "git 필요"(1~4단계 같은 기준). 장점 칸 "목록에서 골라 설치 · 이름으로 업데이트" — 3단계 "그 폴더에서 다시 받기"와 업데이트 차이가 보이게(V-03).
- JSON 예시·이름 규칙·등록·설치·업데이트 명령·자동 업데이트 설정(`extraKnownMarketplaces`·`"autoUpdate": true`)·자격 증명 세부는 슬라이드에서 빼고 위 "자세한 방법"으로 옮김.
- 하단 안내 칸: ⚠️ 비공개 저장소 로그인 정보 미리 저장(없으면 로그인 창 없이 실패) — 이전 "(로그인 창이 뜨지 않음)"이 편해진다는 뜻으로 오독돼 경고로 바꿈 + 📖 마켓플레이스 만들기 가이드(https://code.claude.com/docs/en/plugins/create-marketplace).
- 마지막 줄에서 챕터 8(superpowers)로 자연 연결.

**근거 (공식 문서)**:
- marketplace.json: 위치는 `.claude-plugin/marketplace.json`, `name`·`owner`·`plugins` 필수. `name`은 영문자·숫자·`.`·`_`·`-`만 쓰고 첫 글자는 영문·숫자(`..` 불가) — 그 밖의 이름은 `claude plugin validate`가 실패시키고 설치도 안 됨. 한글 등 비ASCII 글자가 들어가면 공식 마켓 사칭으로 거부("Marketplace name impersonates an official Anthropic/Claude marketplace"). `plugins` 항목의 `name`도 같은 글자 규칙. `owner`는 `name`이 필수("Author name cannot be empty")이고 글자 제한은 없음. 플러그인 `source`는 `./`로 시작하는 상대 경로 문자열이거나 `{ "source": "url", "url": … }`·`{ "source": "github", "repo": … }` 같은 객체. https://code.claude.com/docs/en/plugins/marketplace-reference
- `version`은 plugin.json과 marketplace 항목에 중복으로 넣지 않는다(plugin.json 값이 우선). https://code.claude.com/docs/en/plugins/host-marketplace
- 자세한 방법의 예시 JSON(owner.name 한글 포함)은 `claude plugin validate`(v2.1.316)로 통과 확인(경고: description 없음 1건). 이전 슬라이드의 4줄 압축본도 같은 결과. 이전 예시(이름 공백·owner 누락·문자열 source)는 실패.
- `<git-url>` 형식: `user@host:path.git`(SSH)과 `.git`으로 끝나는 HTTPS 주소는 저장소로 clone. github.com·gitlab.com 주소는 `.git`을 자동으로 붙임. 그 밖의 HTTPS 주소(자체 git 서버에 `.git` 없음)는 marketplace.json 파일 주소로 해석돼 등록 실패("To clone a repository there instead, append `.git`"). https://code.claude.com/docs/en/plugins/cli-reference#plugin-marketplace-add
- 팀원 준비물(태그 "git 필요"·하단 ⚠️ 줄): git 호스트 마켓플레이스는 팀원 PC에 `git` 필요("What users need: `git`"). Windows는 Git for Windows가 선택 설치라 없을 수 있음. private 저장소는 Claude Code가 로그인 창 없이 저장된 자격 증명으로 clone("clones it with the git credentials already on your machine and never prompts"), 저장돼 있지 않으면 실패("A credential the helper already stores works; one it would have to ask for fails.") — HTTPS는 credential helper에 저장된 자격 증명(GitHub: `gh auth login` 후 `gh auth setup-git`), SSH는 암호를 묻지 않고 동작하는 키(예: ssh-agent에 등록 — 암호를 지울 필요는 없음) + `known_hosts` 등록("the key must work without a passphrase prompt, for example because it's loaded in `ssh-agent`. The host must already be in `known_hosts`."). `/plugin install`·`/plugin marketplace update`·`claude plugin update`에도 같은 자격 증명이 쓰임. https://code.claude.com/docs/en/plugins/host-marketplace#grant-access-to-a-private-marketplace · https://code.claude.com/docs/en/setup
- VS Code 확장: 입력창 `/plugins` → Marketplaces 탭에서 GitHub 저장소·URL·로컬 경로를 입력해 마켓플레이스 등록(문서 표현 "add") → Plugins 탭에서 Install. `claude plugin update`는 셸 명령이라 CLI 별도 설치 필요. https://code.claude.com/docs/en/vs-code#manage-plugins
- 설치: `/plugin install <이름>@<마켓플레이스명>` — `@` 뒤는 marketplace.json의 `name`. `이름@마켓플레이스` 형식은 설치 직전에 그 마켓플레이스 카탈로그를 새로 받음. https://code.claude.com/docs/en/plugins/loading#when-claude-code-refreshes-a-marketplace-before-an-install
- 업데이트(장점 칸 "이름으로 업데이트"): 마켓플레이스가 있어야 이름으로 설치·업데이트("install by name and update with a command" https://code.claude.com/docs/en/plugins/publish#share-a-plugin-without-a-marketplace). `version`을 올려 push → 팀원 `claude plugin update <이름>@<마켓플레이스명>`(셸 명령). version을 안 올리고 push하면 "already at the latest version"으로 그대로. 새 버전은 다음 세션부터 로드(실행 중 세션은 `/reload-plugins`). https://code.claude.com/docs/en/plugins/publish#ship-updates-to-users
- 자동 업데이트: 서드파티 마켓플레이스는 기본 꺼짐. 노트·자세한 방법은 화면과 관계없는 설정 파일 방식으로 안내 — `extraKnownMarketplaces` 항목의 `source` 옆에 `"autoUpdate": true`("Set `"autoUpdate": true` alongside `source` to make Claude Code refresh that marketplace and update its installed plugins in the background after startup." https://code.claude.com/docs/en/settings-reference#extraknownmarketplaces). 설정 파일 값이 `/plugin` 토글 값보다 우선(https://code.claude.com/docs/en/plugins/loading#which-marketplaces-and-plugins-auto-update). 터미널·데스크톱 앱·VS Code 확장은 같은 설정 파일을 읽음("read the same settings files" https://code.claude.com/docs/en/plugins/install#choose-an-install-scope) — `/plugin`의 켜기 스위치는 터미널 화면에만 안내돼 있지만 설정 파일은 VS Code 확장도 같이 읽음. 터미널 세션에서는 `/plugin` → Marketplaces → 마켓플레이스 선택 → Enable auto-update로도 켬. VS Code Manage plugins의 Marketplaces 탭 설명에는 추가·새로고침·삭제만 있음(https://code.claude.com/docs/en/vs-code#manage-marketplaces). 켜도 실행 중인 세션은 이미 로드한 버전을 계속 씀. https://code.claude.com/docs/en/plugins/install#keep-plugins-updated
  - 백그라운드 자동 업데이트는 "In an interactive session, after you send your first message"에 돈다고만 적혀 있고, VS Code 확장 세션에서도 도는지는 문서에 명시가 없음 — 리허설 때 확인 권장.
  - 터미널에서 바로 받기: `/plugin` → Installed 탭에서 플러그인 선택 → Update now(셸에서는 `claude plugin update <이름>@<마켓플레이스명>`).
- 미리 등록: 팀 프로젝트 저장소에서 `claude plugin marketplace add <git-url> --scope project`를 한 번 실행하고, 생긴 `.claude/settings.json`(`extraKnownMarketplaces` 항목)을 커밋 → 팀원이 그 폴더를 신뢰하면 등록됨. 그 항목에 `"autoUpdate": true`를 함께 넣으면 자동 업데이트도 켜짐. https://code.claude.com/docs/en/plugins/host-marketplace#register-the-marketplace-for-everyone-in-a-repository
- "새 플러그인 자동 알림" 기능은 없음. 비슷한 relevance 추천은 관리자가 managed settings에서 마켓플레이스를 허용해야 동작. https://code.claude.com/docs/en/plugins/relevance

---

## 챕터 7 합산

- 슬라이드 4장 (git 공유를 별도 단계로 분리)
- 발표 노트 합산: 60 + 90 + 75 + 75 = 300초 = 5분 정확 (CLAUDE.md·rules 안내를 7-3에서 7-1로 옮기며 15초 이동)
- 4단계 구조 (장 표지 부제 "skill 폴더 → 묶음 zip → 묶음 git → 팀 목록"):
  - **1단계**: skill 폴더 공유 — git 불필요, 1~2명, 그 작업 폴더에서만 사용
  - **2단계**: 플러그인 zip 공유 — 묶음, git 불필요, 3~5명, 다음 대화부터 내 모든 작업 폴더에서
  - **3단계**: 플러그인 git 공유 — 묶음, git 필요, 6~10명, 새 버전은 그 폴더에서 다시 받기(git pull)
  - **4단계**: 팀 마켓플레이스 — git 필요, 11명 이상(부서·전사), 목록에서 골라 설치·이름으로 업데이트
- 태그는 git 필요 여부 한 기준: git 우회 경로(1·2단계)와 git 활용 경로(3·4단계)를 모두 명확히 제시
- CLAUDE.md·rules는 플러그인에 못 넣음 → 작업 폴더째 공유(개인 설정 파일 제외) — 7-1 하단에서 먼저 안내
- 슬라이드는 흐름 두 줄 + 적합도만 두고, 명령·설정 세부는 슬라이드마다 "자세한 방법 (슬라이드에서 옮긴 세부)"에 보관
