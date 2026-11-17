# 챕터 0: 사전 준비 안내 (표지 앞 1슬라이드 / 2분)

> 톤 가이드: 발표 시작 전 청중과 함께 환경을 맞추는 시간. 가볍게, 친근하게. 외부 URL은 모두 새 창 링크로 클릭 가능하게.

---

## 슬라이드 0-0 — 사전 준비 (2분)

**핵심 메시지**: "지금 따라 준비해주시면 시연을 함께 해볼 수 있습니다."

**본문 콘텐츠**:

```
[ 헤더 ]
함께 준비해주세요
5단계 준비 후 시연을 함께 진행합니다.
유료 Claude 플랜 또는 개발자용 Console 계정 필요 · 시연용 Python 3 ↗ 설치

[ ★ STEP 0 · 슬라이드 주소 — 노트북에서 열기 ]
  → 박스 전체 클릭 가능 (새 창 링크)
  seojanghyuck.github.io/claude_code_guide ↗

[ STEP 1 — VS Code 설치 ]
  • 아래 링크에서 설치 파일 받기
  • (Mac) .dmg 열기 → 앱을 Applications로 드래그
  • (Win) .exe 실행
    + Git for Windows ↗ (시연 필수)
  ↗ code.visualstudio.com

[ STEP 2 — Claude Code 확장 설치 ]
  • 확장(Extensions) 패널에서
    "Claude Code" 검색
  • Anthropic 공식 확장 → Install
  • Claude Code 패널 → Sign in
    → 브라우저 로그인
  확장 패널 ⌘/Ctrl + Shift + X

[ STEP 3 — 데모 파일 받기 ]
  • 아래 링크 → ↓ 다운로드
  • bdi_demo.zip 저장
  ↗ drive.google.com (화면에는 도메인만 표시 — 실제 링크는 아래 "외부 링크"의 Drive 주소)

[ STEP 4 — 압축 풀기 + 폴더 열기 ]
  • bdi_demo.zip 압축 풀기
  • VS Code → File › Open Folder…
  • README.md가 바로 보이는 bdi_demo 선택
  • 상단 배너 Manage → Trust
    + Claude Code 신뢰 창도 수락
```

**발표 노트 (talk track, 2분)**:
> "본격적으로 시작하기 전에, 5분만 세팅 시간을 갖겠습니다.
> 우선 화면에 보이는 슬라이드 주소를 여러분 노트북에서 열어주세요 — `seojanghyuck.github.io/claude_code_guide` 입니다. 이 주소만 띄워두시면 발표 내내 같은 화면을 보면서 따라오실 수 있습니다.
> 그 다음 4가지를 같이 준비합니다. VS Code 설치, Claude Code 확장 설치, 시연용 데모 파일 zip을 구글 드라이브 링크에서 받아주시고, 받은 zip을 풀어서 VS Code로 그 폴더를 열어주시면 됩니다.
> VS Code는 STEP 1 링크(공식 사이트)에 들어가면 쓰시는 OS에 맞는 설치 파일을 자동으로 골라 줍니다. 맥은 받은 .dmg를 열어 앱을 Applications 폴더로 끌어 놓으시고, Windows는 .exe를 실행해 안내대로 설치하시면 됩니다. Claude Code 확장은 VS Code 왼쪽의 확장(Extensions) 패널을 열고(단축키 ⌘/Ctrl+Shift+X) 검색창에 'Claude Code'를 입력해서, Anthropic이 만든 공식 확장을 골라 Install을 누르시면 됩니다. 데모 파일은 STEP 3 링크를 누르면 구글 드라이브 화면이 열리는데, ↓ 모양 다운로드 아이콘을 눌러 bdi_demo.zip을 저장해 주세요.
> 한 가지 꼭 확인해 주세요. Claude Code는 무료 플랜으로는 쓸 수 없어서, Pro 같은 유료 Claude 플랜이나 개발자용 Claude Console 계정(API 사용량만큼 결제하는 계정)이 있어야 합니다. 확장을 설치하고 창 오른쪽 아래의 ✻ Claude Code를 누르면 패널이 열리면서 Sign in 화면이 나오는데, 거기서 로그인하고 브라우저 인증까지 마쳐 주세요.
> 시연에서 보고서를 만드는 skill은 Python 3로 가상환경을 만들고 python-pptx·openpyxl 패키지를 자동으로 설치합니다. 그래서 Python 3도 미리 설치해 두셔야 합니다. 맨 위 줄의 주황색 Python 3 링크가 공식 다운로드 페이지(python.org/downloads)이고, OS별 설치·확인 방법은 실습 폴더 README.md에 있습니다. Windows를 쓰시는 분은 Git for Windows가 시연에 꼭 필요합니다. STEP 1 카드의 주황색 Git for Windows 링크(git-scm.com/downloads/win)에서 받으시면 됩니다. 이 실습 폴더는 Windows에서 셸 명령을 Git Bash로 실행하도록 설정돼 있어서, Git for Windows가 없으면 Claude Code 세션이 아예 시작되지 않습니다('requires either Git for Windows (for bash) or PowerShell' 오류). 설치한 뒤에는 VS Code를 다시 열어 주세요.
> 폴더를 고를 때는 README.md 파일과 .claude 폴더가 바로 보이는 폴더를 여셔야 합니다. Windows 기본 압축 풀기는 bdi_demo 폴더 안에 bdi_demo를 한 번 더 만들 수 있는데, 그때는 안쪽 폴더를 여세요. 바깥 폴더를 열면 설정·hook·skill이 세션 시작 때 로드되지 않습니다. 맥의 폴더 선택 창에서는 .claude가 숨김 폴더라 안 보일 수 있으니 README.md로 확인하시면 됩니다.
> 폴더를 열면 VS Code는 따로 묻지 않고 제한 모드(Restricted Mode)로 엽니다. 제한 모드에서는 Claude Code 확장이 동작하지 않으니, 창 위쪽 배너의 Manage를 누르고 열리는 화면에서 Trust를 눌러 주세요. 배너를 닫았다면 아래쪽 상태 표시줄의 Restricted Mode 표시를 눌러도 같은 화면이 열립니다. 그다음 Claude Code 패널을 열면 'Trust this folder in Claude Code?'라고 한 번 더 묻습니다. 여기서도 신뢰를 눌러 주세요. 거절해도 대화는 되지만, 이 폴더의 설정·hook·MCP 서버가 적용되지 않아서 시연이 그대로 동작하지 않습니다.
> 각 카드의 주황색 링크는 클릭하면 새 창에서 바로 열리니까, 슬라이드 보면서 따라 누르시면 됩니다.
> 준비 끝나신 분은 손 들어주세요. 다 같이 모이면 본 발표 시작하겠습니다."

**시각 표현 메모**:
- 슬라이드 클래스: `slide` (white background — 깨끗하고 정보 전달 위주)
- 최상단: headline "함께 준비해주세요" + 리드 두 줄(19px) — 5단계 안내 + 계정 조건(굵게, Console은 덱에서 처음 나오므로 "개발자용 Console 계정") · Python 3(주황 링크 ↗, python.org/downloads 새 창). 주황색 링크 새 창 안내·무료 플랜 미지원은 발표 노트로
- STEP 0: KRAFTON 오렌지 강조 박스 (높이 ~110px) — ★ 아이콘 + URL을 28px 모노스페이스로 큼지막하게. **박스 전체가 `<a target="_blank">` 링크**.
- STEP 1~4: 4열 그리드 카드
  - 상단 오렌지 보더(4px) + STEP 라벨(KRAFTON Headline 15px) + 카드 제목(19px) + 2~4개 bullet 목록(14px, line-height 1.65)
  - STEP 1·3 하단: 외부 URL을 `<a target="_blank" rel="noopener noreferrer">` 처리 (오렌지, 모노스페이스 12px, ↗ 표기). 화면에는 도메인만 표시(code.visualstudio.com · drive.google.com), 실제 주소는 아래 외부 링크
  - STEP 2 하단: 확장 패널 단축키 표기 (⌘/Ctrl + Shift + X)
  - STEP 1: Windows 줄에 Git for Windows(주황 링크 ↗, git-scm.com/downloads/win 새 창 — 실습 폴더 README와 같은 주소) (시연 필수) — 이 실습 폴더는 셸 명령을 Git Bash로 실행하도록 설정돼 있어 없으면 세션이 시작되지 않음(이유는 발표 노트)
  - STEP 4 하단: 단축키 없음 — 4개 bullet(README.md가 바로 보이는 폴더 선택, 상단 배너 Manage → Trust, Claude Code 신뢰 창 수락)으로 절차 완결. .claude 숨김 폴더·이중 폴더(bdi_demo 안의 bdi_demo)·Restricted Mode 설명은 발표 노트로
- 결론 줄 없음 — 안내 슬라이드이므로 따로 마무리 멘트를 슬라이드에 박지 않고 발표자가 구두로 처리
- 표지보다 먼저 등장 — `active` 클래스 보유, 기존 표지에서 제거

**외부 링크 (모두 새 창)**:
- 슬라이드: `https://seojanghyuck.github.io/claude_code_guide`
- VS Code: `https://code.visualstudio.com`
- Python 3: `https://www.python.org/downloads/`
- Git for Windows: `https://git-scm.com/downloads/win`
- Drive: `https://drive.google.com/file/d/1EhIkJetYFAw6oqvNAeCQaKEuQ4w-Aejj/view?usp=sharing`
