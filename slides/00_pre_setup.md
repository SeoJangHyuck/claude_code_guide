# 챕터 0: 사전 준비 안내 (표지 앞 1슬라이드 / 2분)

> 톤 가이드: 발표 시작 전 청중과 함께 환경을 맞추는 시간. 가볍게, 친근하게. 외부 URL은 모두 새 창 링크로 클릭 가능하게.

---

## 슬라이드 0-0 — 사전 준비 (2분)

**핵심 메시지**: "지금 따라 준비해주시면 시연을 함께 해볼 수 있습니다."

**본문 콘텐츠**:

```
[ 헤더 ]
함께 준비해주세요
아래 5단계만 따라오시면 시연을 같이 해볼 수 있습니다.
각 카드의 주황색 링크를 클릭하면 새 창에서 열립니다.

[ ★ STEP 0 · 슬라이드 주소 — 지금 노트북에서 함께 열어주세요 ]
  → 박스 전체 클릭 가능 (새 창 링크)
  seojanghyuck.github.io/claude_code_guide ↗

[ STEP 1 — VSCode 설치 ]
  • 공식 사이트 접속
  • OS 자동 감지 → 설치 파일 다운로드
  • (Mac) zip 풀어 Applications로 이동
    (Win) .exe 실행 → 안내대로 설치
  ↗ code.visualstudio.com

[ STEP 2 — Claude Code 확장 설치 ]
  • VSCode 좌측 확장(Extensions) 패널 열기
  • 검색창에 "Claude Code" 입력
  • Anthropic 공식 확장 선택 → Install
  단축키 ⌘/Ctrl + Shift + X

[ STEP 3 — 데모 파일 다운로드 ]
  • 아래 링크 → Google Drive 이동
  • 좌측 상단 ↓ 다운로드 아이콘 클릭
  • bdi_demo.zip 저장
  ↗ drive.google.com/file/d/1EhIkJetYFAw6oqvNAeCQaKEuQ4w-Aejj/view?usp=sharing

[ STEP 4 — 압축 해제 + 폴더 열기 ]
  • bdi_demo.zip 압축 풀기 → bdi_demo 폴더 생성
  • VSCode 실행 → File › Open Folder…
  • 방금 푼 bdi_demo 폴더 선택 → 열기
```

**발표 노트 (talk track, 2분)**:
> "본격적으로 시작하기 전에, 5분만 세팅 시간을 갖겠습니다.
> 우선 화면에 보이는 슬라이드 주소를 여러분 노트북에서 열어주세요 — `seojanghyuck.github.io/claude_code_guide` 입니다. 이 주소만 띄워두시면 발표 내내 같은 화면을 보면서 따라오실 수 있습니다.
> 그 다음 4가지를 같이 준비합니다. VSCode 설치, Claude Code 확장 설치, 시연용 데모 파일 zip을 구글 드라이브 링크에서 받아주시고, 받은 zip을 풀어서 VSCode로 그 폴더를 열어주시면 됩니다.
> 각 카드의 주황색 링크는 클릭하면 새 창에서 바로 열리니까, 슬라이드 보면서 따라 누르시면 됩니다.
> 준비 끝나신 분은 손 들어주세요. 다 같이 모이면 본 발표 시작하겠습니다."

**시각 표현 메모**:
- 슬라이드 클래스: `slide` (white background — 깨끗하고 정보 전달 위주)
- 최상단: headline "함께 준비해주세요" + 리드 한 줄(19px) — 링크 안내 포함
- STEP 0: KRAFTON 오렌지 강조 박스 (높이 ~110px) — ★ 아이콘 + URL을 28px 모노스페이스로 큼지막하게. **박스 전체가 `<a target="_blank">` 링크**.
- STEP 1~4: 4열 그리드 카드
  - 상단 오렌지 보더(4px) + STEP 라벨(KRAFTON Headline 15px) + 카드 제목(19px) + 3개 bullet 목록(14px, line-height 1.65)
  - STEP 1·3 하단: 외부 URL을 `<a target="_blank" rel="noopener noreferrer">` 처리 (오렌지, 모노스페이스, ↗ 표기)
  - STEP 2 하단: 단축키 표기 (⌘/Ctrl + Shift + X)
  - STEP 4 하단: 단축키 없음 — 3개 bullet으로 절차 완결
- 결론 줄 없음 — 안내 슬라이드이므로 따로 마무리 멘트를 슬라이드에 박지 않고 발표자가 구두로 처리
- 표지보다 먼저 등장 — `active` 클래스 보유, 기존 표지에서 제거

**외부 링크 (모두 새 창)**:
- 슬라이드: `https://seojanghyuck.github.io/claude_code_guide`
- VSCode: `https://code.visualstudio.com`
- Drive: `https://drive.google.com/file/d/1EhIkJetYFAw6oqvNAeCQaKEuQ4w-Aejj/view?usp=sharing`
