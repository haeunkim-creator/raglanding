# DESIGN_HANDOFF.md

> 대상 산출물: `Lucy Marketing Site.dc.html` — 단일 확정 시안
> 사이트 카피는 100% 영어. 본 문서는 개발 인계용이므로 한국어. 원고 전문은 `COPY_DECK.md`.

**표기 규칙**: 이 문서에서 확인되지 않은 항목은 모두 **`[확인 필요]`** 로만 표시한다. 페이지가 화면에 실제로 렌더하는 영문 플레이스홀더 문자열은 `[TO CONFIRM]`이며, 이 둘은 다른 것이다 — 전자는 handoff의 미확정 표시, 후자는 배포 화면에 노출되는 카피다.

---

## 1. Design Summary

lucydata.ai 세일즈 랜딩페이지. 데스크톱 우선 1440px, 단일 페이지 12섹션. 미국 B2B 엔터프라이즈 대상이며 **마케팅 페이지이지 제품 빌드가 아니다** — 제품 UI를 새로 그리지 않고, 스크린샷 자리는 라벨된 프레임으로 둔다.

Lucy는 답변을 팔지 않는다. **citation-grade evidence**(SEC 원문에서 추출된 source-linked chunk, API/MCP 제공, retrieval trace 동봉)를 팔고, 답변은 고객의 모델이 쓴다. 구매자는 프론티어 AI 랩, 금융 데이터 벤더, RAG 엔지니어링 팀.

### 배열 원칙 (이번 패스의 핵심)

섹션을 **제품이 동작하는 순서가 아니라 구매자가 의심하는 순서**로 배열했다. 각 섹션은 아래 질문 하나에만 답하며, **섹션 제목은 기능 이름이 아니라 그 질문에 대한 답처럼 들려야 한다.**

| 순서 | 구매자의 질문 | 섹션 | 표면 |
|---|---|---|---|
| 1 | 이게 뭔가 | Hero | light |
| 2 | 왜 문제인가 | The problem | **dark** |
| 3 | 왜 믿어야 하나 | **Proof** | **dark** |
| 4 | 왜 직접 못 만드나 | Why it works | light |
| 5 | 뭘 물어볼 수 있나 | **What you can ask** | light |
| 6 | 뭐가 들어 있나 | **Coverage** | **dark** |
| 7 | 우리 스택에 맞나 | Integration | light |
| 8 | 어떻게 시작하나 | **Final CTA** | **dark** |
| — | — | Footer | light |

**5·6 분리 이유**: 이전의 "What you get" 한 섹션이 서로 다른 두 질문(무엇을 물어볼 수 있나 / 무엇이 들어 있나)을 함께 지고 있었다. 구매자의 의심은 두 개이므로 섹션도 두 개다.

**Licensing 섹션은 삭제됐다.** 법무·조달 관련 문구(Source of record / Delivery / Terms)는 페이지에서 제거됐으므로, 필요해지면 별도 페이지나 요청 폼 단계에서 다룬다.

**구매자 정의**: 미국 엔터프라이즈 데이터 구매자 — AI 랩, 금융 데이터 벤더, 리서치 플랫폼. **챗봇을 찾는 사람이 아니다.** 서류 데이터셋을 라이선스할지 평가하는 사람이며, **플레이그라운드는 주장을 검증하는 수단이지 판매 대상이 아니다.**

### CTA 규칙 (전 위치 공통)

주 버튼은 항상 **Request dataset access**(솔리드), 보조는 항상 **Open the playground**(아웃라인).

**배치 순서**: 히어로와 최종 CTA에서는 **보조가 왼쪽, 주가 오른쪽**이다. 내비는 기존대로 보조 → 주 순서. 시각적 우선순위는 색·채움으로만 표현하고 위치로는 표현하지 않는다.

### 표면 규칙

페이지 기본은 LIGHT. 다크는 **세 구역** — ①연속된 한 덩어리(2 The problem + 3 Proof) ②6 Coverage ③8 최종 CTA. ①의 두 섹션만 의도적으로 인접하고, 나머지는 라이트 섹션이 갈라준다.

- **2+3을 하나의 다크 블록으로 붙인 이유**: 문제 제기와 그 답(증거)은 한 호흡이다. **경계선도, 전환 문장도 두지 않는다** — 대신 **중앙 정렬 세로 화살표**(`.turn-arrow`, 1px 코랄 선 120px + 45° 회전 화살촉)가 아래로 시선을 끌어내린다. 선은 "두 섹션이 붙어 있다"로, 문장은 "카피가 하나 더 있다"로 읽히지만, 화살표는 **"여기서 아래로 이어진다"는 방향만** 말하고 읽을 것을 늘리지 않는다.
- **Integration을 라이트로 내린 이유**: Licensing이 사라지면서 Integration이 다크로 남으면 최종 CTA와 인접해 다크가 붙어버린다. 기술 상세 섹션이라 라이트에서 읽기도 낫고, What you get의 카드 스타일과 자연히 이어진다.
- 결과 리듬: **라이트(히어로) → 다크(문제+증거) → 라이트(why · what you can ask) → 다크(coverage) → 라이트(integration) → 다크(CTA) → 라이트(푸터)**.
- Coverage를 다크로 올린 이유: chip 그리드가 유일한 시각 요소인 섹션이라, 다크 표면에서 코랄 chip이 살아나고 긴 라이트 구간(why → what you can ask)이 끊긴다. 다크 위에서 chip 색은 `#e28a68`(6.9:1)로 자동 전환된다.

### 레이아웃 패턴 (신규 primitive 없음)

| 코드 | 패턴 | 사용처 |
|---|---|---|
| L1 | sticky nav | Nav |
| L2 | centered hero + 전체폭 프레임 미디어(영상) | Hero |
| L3 | two-column intro (좌 heading / 우 body) | Problem, Proof, Why, What you get |
| L4 | card grid | What you get(3-up + 2-up 비대칭), Integration(2-up) |
| L6 | 3열 + 수직 구분선 | Proof |
| L7 | mono eyebrow 라벨 | 전 섹션 |
| L8 | 브래킷 플레이스홀더 | Integration |
| **신규 조합** | **비대칭 대조 카드 2장** — 같은 `.card`에 `.dark`를 붙여 한쪽만 반전. 폭도 0.82 : 1.18로 기울여 다크 카드가 지배하게 함 | Why it works |

---

## 2. Screens

단일 페이지 10블록(내비 + 8섹션 + 푸터). DOM 순서 그대로. 문구는 `COPY_DECK.md` 동일 번호 참조.

| # | 섹션 (class) | 표면 | 답하는 질문 | 역할 |
|---|---|---|---|---|
| — | `.nav` | light | — | 로고, 4링크, CTA 2종, 모바일 토글 |
| 1 | `.hero` | light | 이게 뭔가 | H1 + 서브 + CTA + meta row + **전체폭 자동재생 루프 영상** |
| 2 | `.problem` | **dark** | 왜 문제인가 | 2열 4줄 + **세로 화살표**(Proof로 넘기는 방향 표시) |
| 3 | `.proof` | **dark** | 왜 믿어야 하나 | 3열 — **각 열이 4:3 프레임 → 번호 → 제목 → 본문 순서**. + 마무리 한 줄. **2와 경계선 없음** |
| 4 | `.why-it-works` | light | 왜 직접 못 만드나 | **16:9 프레임(카드 위, max-width 800px 중앙)** → **2장 대조 카드**(좌 라이트 0.74fr / 우 다크 1.26fr, 01–10 번호) |
| 5 | `.what-you-can-ask` | light | 뭘 물어볼 수 있나 | 3카드(각 2줄) + **대조 블록**(예시 질문 1개 + 유사도검색 vs 구조화검색 2열) |
| 6 | `.coverage` | **dark** | 뭐가 들어 있나 | **전체폭** 서류 2그룹(펀드 primary / 기업 secondary) + XBRL 한 줄 |
| 7 | `.integration` | light | 우리 스택에 맞나 | **상하로 쌓인 가로형 카드 2장**(전체폭, 좌 150px 제목 + 우 내용) + 설정 줄 |
| 8 | `.closing` | **dark** | 어떻게 시작하나 | 클로징 + CTA 2종 + 요청 항목 |
| — | `.site-footer` | light | — | 로고 + 태그라인 + **Company 1열** + 법적 표기 |

**주요 사용자 행동 / 다음 흐름**: 어느 섹션에서든 두 CTA로 분기한다 — `Request dataset access` → `/request-access` `[확인 필요]`, `Open the playground` → `rag-playground.lucydata.ai`(외부). 그 외 인터랙션은 내비 앵커 이동과 스크롤뿐이다.

이번 범위에 없는 화면: 데이터셋 요청 폼, Docs, Company, Legal → §17

---

## 3. User Flow

구매자의 의심 순서를 그대로 따른다.

1. 방문 (데스크톱 우선, 미국 B2B [확인 필요])
2. **Hero** — "확인 가능한 금융 답변"이라는 주장과 제품 화면을 본다
3. **The problem** — 자기 문제로 인식한다(출처를 댈 수 없는 답변은 쓸 수 없다)
4. **Proof** — 검증 수단이 실재하는지 확인한다. 설득되면 **Open the playground**로 직접 검증하러 이탈할 수 있다(의도된 경로)
5. **Why it works** — "EDGAR는 무료인데 왜 사야 하나"에 답을 얻는다. 10행 대조표가 이 판단의 근거다
6. **What you can ask** — 자기 질문이 되는 종류인지 판단한다. 대조 블록이 "유사도 검색으로는 안 되는 질문"을 보여준다
7. **Coverage** — 서류 범위를 확인한다. 부족하면 여기서 이탈한다
8. **Integration** — 자기 스택에 붙는지 판단한다
9. **Final CTA** — **Request dataset access**로 전환. 검증이 더 필요하면 보조 버튼으로 플레이그라운드

**법무·조달 단계가 페이지에서 빠졌다.** Licensing 섹션 삭제로 그 의심은 페이지가 답하지 않으며, 요청 폼 이후 영업 대화로 넘어간다 `[확인 필요]`

**주요 행동**: 어느 위치에서든 주 버튼은 `/request-access` [확인 필요], 보조는 `rag-playground.lucydata.ai`(외부). 그 외 인터랙션은 내비 앵커 이동과 스크롤뿐이다.

---

## 4. UI States

**정적 마케팅 페이지.** 클라이언트에서 데이터를 fetch하지 않으므로 아래 상태는 불필요하다.

| 상태 | 판정 |
|---|---|
| 로딩 | **불필요** — 서버/빌드 타임 렌더링. 런타임 데이터 요청 없음 |
| 빈 데이터 / 검색 결과 없음 | **불필요** — 검색·목록·쿼리 UI 없음. §6의 예시 질문은 **실행되지 않는 역량 서술**이다 |
| 오류 | **불필요** — 데이터 호출 없음 |
| 권한 없음 | **불필요** — 공개 페이지, 인증 없음 |

**실제로 구현해야 하는 상태**

| 상태 | 처리 |
|---|---|
| 기본 | 위 디자인 그대로 |
| 모바일 nav | open / closed (유일한 클라이언트 상태) |
| 이미지 로드 실패 | `alt` 필수(§19). 프레임(보더 + 종횡비)이 유지되어 레이아웃이 붕괴하지 않는다 |
| 이미지 미공급 (judge-metrics) | 라벨된 프레임이 무엇이 들어갈지 표시. **구현 시 `<img>`로 교체** (§10) |
| 일부 데이터 누락 | 미확정 항목은 화면에 `[TO CONFIRM]` 문자열로 노출된다 `[확인 필요]` |
| 0 / null / undefined | 값이 없으면 **문장을 렌더하지 않는다**. "0 filings"는 절대 노출 금지 |
| 긴 텍스트 | 고정 높이 없음. 200% 확대 시 줄바꿈으로 늘어남. `text-wrap: pretty` |
| 큰 숫자 | 페이지에 동적 수치 없음. `~20 source chunks`는 고정 문구 |
| JSON 코드 블록 가로 overflow | `overflow-x:auto` + `white-space:pre`. 모바일에서 폰트 12.5px로 축소, 줄바꿈하지 않고 가로 스크롤 |

---

## 5. Information Architecture

1. **가장 먼저** — H1
2. **두 번째** — hero 이미지, 서브카피, Primary CTA
3. **세 번째** — Proof 섹션(후크). 두 스크린 안에 들어와야 한다
4. **네 번째** — Why it works의 10행 대조표 (구매 판단의 근거)
5. **접거나 뒤로 미뤄도 되는 것** — meta row, footer 링크, Coverage의 기업 서류 chip 목록(2차)
6. **모바일 우선 노출** — H1 → 서브 → Primary CTA → hero 이미지 → The problem

**Coverage 내부 위계 (의도적)**: 펀드·ETF 그룹이 먼저 오고 라벨 15px + 큰 chip으로 우선하며, 기업·지분 그룹은 13px 뮤트 라벨 + 작은 chip이다. **펀드가 차별점이므로 이 위계를 뒤집지 않는다.** 라이브 노출 범위(열람/검색 구분) 표기는 이번 패스에서 삭제됐다 — 커버리지를 **데이터셋 범위로 한 번만** 진술한다.

---

## 6. Component Inventory

| 이름 | 역할 | 포함 정보 | 상호작용 | 필요한 상태 | 재사용 | 인스턴스 |
|---|---|---|---|---|---|---|
| `SiteHeader` | 상단 내비 | 로고, 4링크, CTA 2종, 토글 | 링크 이동, 토글 | default / hover / focus / open·closed | O | 1 |
| `Logo` | 브랜드 | "Lucy" + mono "DATA" | 홈 이동 | default / hover | O | 2 |
| `Button` | 액션 | label, href | click | default / hover / focus-visible | O | 6 |
| ↳ `variant="primary"` | 최우선 행동 | Request dataset access | — | — | — | 3 |
| ↳ `variant="secondary"` | 보조 행동 | Open the playground | — | — | — | 2 |
| ↳ `variant="ghost"` | nav 내 보조 | Open the playground | — | — | — | 1 |
| `Eyebrow` | 섹션 라벨 | mono 대문자 | 없음 | default | O | 6 |
| `Section` | 섹션 셸 | children | 없음 | **light(기본) / dark** | **O (핵심)** | 9 |
| `SectionHeadSplit` | L3 머리 | 좌 eyebrow+h2 / 우 intro | 없음 | default | **O (핵심)** | 4 |
| `CompareCard` | 대조 카드 | 헤더(mono) + 01–10 번호 목록 | 없음 | **light / dark**(`.card.dark`) | O | 2 (**Why it works**) |
| `ContrastBlock` | 검색 방식 대조 | mono 예시 질문 + 2열(유사도 / 구조화) + 보조 예시 + 마무리 | **없음 — 실행 어포던스 금지** | default | X (1회) | 1 (**What you can ask**) |
| `TurnArrow` | 다크 블록 내부 전환 표시 | 1px 세로선 + 화살촉 (텍스트 없음, `aria-hidden`) | 없음 | default | X (1회) | 1 (**The problem 끝**) |
| `MediaFrame` | 히어로 미디어 프레임 | 크롬 바 + 종횡비 박스 + 영상 + 캡션 | 없음 | playing / reduced-motion(poster) | X (1회) | 1 (Hero) |
| `PlaceholderFrame` | 이미지 예약 프레임 | 종횡비 박스 + 파일명 라벨 (+ 선택적 캡션) | 없음 | **empty(라벨) / filled** · **light / dark**(웜 저대비 보더) | **O (핵심)** | 4 (Proof 3 + Why 1) |
| `Caption` | 프레임 설명 | mono 텍스트 | 없음 | default | O | 1 |
| `StepColumn` | L6 번호 열 | 번호, 제목, 설명 | 없음 | default (우측 구분선 / 마지막 열 없음) | O | 3 (**Proof**) |
| `Card` | 일반 카드 | 제목 + 설명 | 없음 | default | O | 3 (§6) |
| `FormGroup` | 서류 그룹 | mono 라벨 + chip 목록 | 없음 | **primary(15px 라벨 + 큰 chip) / secondary(13px 뮤트 라벨 + 작은 chip)** | O | 2 (**Coverage**) |
| `Chip` | 서류 타입 | 짧은 라벨 | 없음 | **primary(코랄 40px) / secondary(뮤트 30px)** | O | 26 |
| `IntegrationCard` | 가로형 도입 방식 카드 | 좌 150px 제목 열 + 우 내용 | 없음 | default (≤1023에서 제목이 위로) | O | 2 (**Integration**) |
| `HostChip` | 지원 호스트 | **mono 텍스트만** — 아이콘·이미지 슬롯 없음 | 없음 | default | O | 5 (**Integration**) |
| `FactList` / `FactRow` | 라벨-설명 2열 | mono 라벨 + 설명 | 없음 | **accent 라벨**(Proof 점수) | O | 1 / 3 |
| `SiteFooter` | 푸터 | 로고, 4열 링크, 법적 표기 | 링크 이동 | default | O | 1 |

**동작 컴포넌트 (라이브러리 매핑 필요)**
- 모바일 내비 토글 (Disclosure/Sheet) — `[확인 필요]` 프로젝트 인터랙션 라이브러리 미확정 → **동작 컴포넌트 — 라이브러리 매핑 필요**
- 그 외 모달·드롭다운·탭·아코디언 **없음**

**컴포넌트 API 관습**
- `Button`은 boolean 여러 개가 아니라 `variant="primary" | "secondary" | "ghost"` 하나로
- `Section`은 `tone="light" | "dark"` — 다크는 토큰을 지역 재정의하므로 내부 컴포넌트는 표면을 몰라도 된다 (§10)
- `PlaceholderFrame` / `CoverageCard`는 `renderX` prop이 아니라 **children**으로 합성
- `Chip`·`CoverageCard`는 `variant` 하나로 위계 표현
- 역할 기반 이름 = 최종 컴포넌트 파일명과 동일하게 유지

---

## 7. Responsive Rules

**아래 두 블록은 배포 파일의 미디어쿼리 전문이다** (손으로 옮겨 적은 표가 아니므로 코드와 어긋날 수 없다). 1440 / 924 / 390 / 360에서 실측 확인 — 가로 overflow 0.

구현 방식: 레이아웃이 인라인 스타일이므로 미디어쿼리는 `!important`로 덮는다. production에서 인라인을 유틸리티로 옮기면 `!important`는 제거할 것.

분기점은 **1023px**(태블릿 이하)과 **599px**(모바일) 두 개뿐이다. 중간 단계는 **존재하지 않는다** — 태블릿은 모바일과 같은 햄버거·1열 처리를 받고, 폰트·여백만 데스크톱에 가깝다.

```css
@media (max-width:1023px){
  :root{--container:100%;--space-30:80px;--space-24:64px;--space-20:56px;--space-16:40px}
  .nav-links,.nav-actions .btn-ghost{display:none!important}
  .nav-toggle{display:inline-flex}
  .hero,.section-inner,.nav-inner{padding-left:var(--space-8)!important;padding-right:var(--space-8)!important}
  .split,.section-head-split,.card-grid,.compare-grid{grid-template-columns:minmax(0,1fr)!important}
  .step-list{grid-template-columns:minmax(0,1fr)!important}
  .step-card{padding:var(--space-8) 0!important;border-right:none!important}
  .step-card + .step-card{border-top:1px solid var(--border-strong)}
  .card-wide{flex-direction:column!important;gap:var(--space-4)!important}
  .card-wide > h3{flex:0 0 auto!important}
  .footer-grid{grid-template-columns:repeat(2,minmax(0,1fr))!important;gap:var(--space-8)!important}
  .footer-grid > div:first-child{grid-column:1/-1}
  h1{font-size:52px!important}
  h2{font-size:32px!important}
}
```

```css
@media (max-width:599px){
  :root{--space-30:56px;--space-24:48px;--space-20:40px;--space-16:32px;--space-12:24px}
  .hero,.section-inner,.nav-inner{padding-left:var(--space-5)!important;padding-right:var(--space-5)!important}
  .nav{height:64px!important}
  .nav-inner{gap:var(--space-3)!important}
  .nav-panel{top:64px;padding-left:var(--space-5);padding-right:var(--space-5)}
  .nav-cta-full{display:none}
  .nav-cta-short{display:inline}
  .nav-actions .btn-primary{padding:0 var(--space-4)!important}
  h1{font-size:36px!important;letter-spacing:-.025em!important}
  h2{font-size:27px!important}
  h3{font-size:20px!important}
  .hero-sub{font-size:16px!important}
  .turn-arrow span:first-child{height:72px!important}
  .cta-row{flex-direction:column!important;align-items:stretch!important;width:100%}
  .cta-row .btn{width:100%;justify-content:center;flex:1 1 auto!important}
  .fact-row{grid-template-columns:minmax(0,1fr)!important;gap:var(--space-2)!important}
  .chip-primary{height:34px;padding:0 var(--space-3);font-size:14px}
  .card,.contrast{padding:var(--space-6)!important}
  .footer-bottom{flex-direction:column;align-items:flex-start!important;gap:var(--space-3)!important}
}
```

**위 블록에서 읽어야 할 규칙**

- **1열 전환**: `.section-head-split`(6곳), `.card-grid`, `.coverage-grid`, `.step-list`(Proof), `.gap-row`(Why it works 10행) — 모두 ≤1023에서 1열
- **§7 비대칭 카드**: ≤1023에서 1열로 쌓이면 크기 대비가 사라진다. **순서(dataset 먼저)와 카드 내부 타이포 위계(24px vs 17px 제목)로 위계를 유지**한다
- **해상도 보호 규칙 (`.shot-portrait`)**: 세로 asset은 1열로 접힐 때 콘텐츠 폭 전체로 늘어나 원본 해상도를 넘겨 확대된다. chunk 이미지는 원본 1116px이므로 **`max-width:558px`(=1116/2) 상한 + 가운데 정렬**을 걸었다. 상한이 없으면 924px 뷰포트에서 1.30배로 떨어져 13px 모노 텍스트가 뭉갠다. **새 세로 이미지도 같은 계산(`원본 폭 / 2`)으로 상한을 정할 것.** hero는 4096px 가로라 상한이 필요 없다
- **L6 구분선(Proof 3열)**: 데스크톱 `border-right` → ≤1023에서 `border-top`으로 전환
- **푸터**: 5열 → ≤1023에서 로고 전체폭 + 2열
- **내비**: ≤1023에서 링크 숨김 + 햄버거 노출. ≤599에서 CTA 라벨이 "Request access"로 축약되고 gap 12px·높이 64px
- **CTA**: ≤599에서만 풀폭 세로 스택
- **fact-list**: ≤599에서만 1열(라벨 위·설명 아래)
- **Why it works 대조 카드(`.compare-grid`)**: 데스크톱 **0.74fr : 1.26fr**, `align-items:center`. **높이를 맞추지 않는다** — 좌측 카드는 자기 내용 높이(722px)로 줄고 우측 다크 카드(840px) 기준으로 **세로 중앙 정렬**된다. 높이를 맞추면 좌측 아래에 빈 여백이 생겼다. 다크 카드를 넓혀(683px) 긴 설명이 덜 감기게 한 것이 세로 길이를 줄이는 핵심이다. ≤1023에서 1열로 접히면 **좌(문제) → 우(해결)** 순서로 쌓인다. 두 목록의 01–10 번호가 대응 관계를 유지하는 유일한 장치이므로 **번호를 제거하면 매핑이 사라진다**
- **세로 길이 축소 내역**: 1184px → **840px (−29%)**. 행 패딩 20→12px, 라벨 여백 8→2px, 본문 16/1.6 → 15/1.5, 카드 패딩 40→32px, 좌측 카피 축약(디자인 작성 문구이므로 축약 가능 — 우측은 브리프 문구라 그대로). 더 줄여야 하면 **행 수를 10개에서 줄이는 것이 다음 수단**이며, 이는 콘텐츠 결정이라 임의로 하지 않았다 `[확인 필요]`
- **Chip**: primary chip은 ≤599에서 40px → 34px, 16px → 14px. secondary는 전 구간 동일
- **토큰 재정의로 처리되는 것**: 컨테이너 폭·섹션 여백·좌우 패딩은 개별 규칙이 아니라 `--container`/`--space-*` 값을 분기별로 다시 선언해 일괄 적용한다

**중간값이 필요해지면** 위 두 블록에만 손대고, 이 문서는 블록을 다시 붙여넣어 갱신한다.

**hero 이미지 크롭 규칙 (중요)**: 히어로 프레임은 실측 비율(4096/2326)로 고정돼 크롭이 없다. 종횡비를 바꿔야 하면 **오른쪽(answer 패널)부터** 자른다. 좌측 pipeline 열과 **중앙 trace 열은 절대 자르지 않는다 — 그 열이 제품이다.** 모바일에서 판독이 불가하면 **모바일 전용 크롭 이미지 별도 공급** `[확인 필요]`.

---

## 8. Accessibility Notes

- **heading 구조**: `h1` 1개(히어로) → `h2` 7개(각 섹션) → `h3`(카드·열 제목). eyebrow는 heading이 아니라 `<p>`. 건너뛴 레벨 없음
- **button vs link**: 모든 액션이 페이지 이동이므로 전부 `<a>`. `<button>`은 모바일 nav 토글에만
- **외부 링크**: playground는 외부 도메인. `target="_blank" rel="noopener"` 사용 시 스크린리더용 "(opens in a new tab)" 안내 필요 — **미구현, 남은 항목**
- **label**: 입력 요소 없음. §11의 요청 항목은 **문장으로만 안내**하며 실제 input이 아니다
- **keyboard**: DOM 순서 = 시각 순서. tabindex 조작 없음
- **focus state**: **구현 완료** — 전역 `:focus-visible{outline:2px solid var(--accent);outline-offset:2px}`
- **모바일 nav disclosure**: **구현 완료** — `aria-expanded`, `aria-controls="nav-panel"`, Escape로 닫고 토글로 포커스 복귀, 열릴 때 첫 링크로 포커스(`requestAnimationFrame` 1프레임 지연 — 조건부 렌더 서브트리가 동기적으로 DOM에 없기 때문)
- **Why it works 대조표**: `<ul>`/`<li>` 2열 그리드다. 스크린리더가 좌(문제)→우(해결) 순으로 읽으므로 DOM 순서가 의미 순서와 일치한다. 표 의미가 더 강하면 `<table>`로 바꿀지 검토 `[확인 필요]`

**실측 대비 (검증 완료)**

| 대상 | 대비 | 판정 |
|---|---|---|
| 라이트 본문 `--text-2 #5c564e` on `#faf8f4` | 7.1:1 | PASS |
| 라이트 caption `--text-3 #6d675e` on `#faf8f4` | **5.2:1** | PASS |
| 라이트 accent `--accent #b0492f` on `#faf8f4` | **5.2:1** | PASS |
| 라이트 accent `--accent #b0492f` on `--panel #ffffff` | **5.5:1** | PASS |
| 다크 본문 `rgba(237,232,222,.74)` on `#1c1815` | 8.0:1 | PASS |
| 다크 caption `rgba(237,232,222,.56)` on `#1c1815` | 4.9:1 | PASS |
| 다크 accent `#e28a68` on `#1c1815` | 6.9:1 | PASS |

⚠ **정정 기록 (2건)**

1. `--text-3`를 `#7a7368`로 두고 "4.6:1 PASS"라고 적었으나 **실측 4.42:1로 AA 미달**이었다. ①토큰을 `#6d675e`(5.2:1)로 어둡게 해 caption·meta·chip을 함께 올리고, ②Why it works 좌열 10개 문단(16px)과 "Additional form types…"(15px)을 `--text-2`로 옮겼다. 좌열의 "약한 역할"은 색이 아니라 **좌/우 위치 + mono 라벨 유무**로 표시된다.
2. 위를 고치면서 **바로 아래 줄의 accent는 그대로 틀린 채 남아 있었다** — `#c05a3e`는 지면에서 4.15:1, 흰 카드에서 4.40:1로 **라이트 표면의 모든 accent 사용(16곳)이 AA 미달**이었다(큰 글씨 사용은 0곳). 토큰을 `#b0492f`로 어둡게 해 두 표면 모두 통과시켰다. 링크 hover도 `#8f3a23`로 함께 내렸다.

**교훈**: accent 후보는 지면(`#faf8f4`)뿐 아니라 **흰 카드(`--panel #ffffff`)에서도** 검증해야 한다. 3-up 카드와 커버리지 카드가 `background:var(--panel)`이므로 흰 배경이 더 엄격한 기준이다.

- **다크 표면에서 악센트가 바뀐다**: 라이트의 코랄 `#b0492f`를 다크에 그대로 쓰면 2.5:1로 미달한다. `.dark`가 `--accent`를 밝은 코랄 `#e28a68`로 지역 재정의한다. **이 재정의를 이식하지 않으면 다크 섹션(3·9·11)의 eyebrow·번호·링크가 전부 접근성 미달이 된다**
- **`--text-3`는 13–14px caption/meta/chip에만 쓴다. 본문(15px 이상 독립 문장)에 쓰지 않는다** — 이 규칙을 어겼던 Why it works 좌열은 위 정정에서 `--text-2`로 옮겼다. 새 문단을 추가할 때도 같은 기준을 적용할 것
- **최소 폰트 크기**: 12px 텍스트 없음. **13px가 바닥**이며 caption/meta/mono 라벨 전용. 본문 16–18px, 보조 15px
- **색상 단독 구분 금지**: primary/secondary chip은 색상뿐 아니라 **크기·타이포·카드 위계**로도 구분된다. Proof 지표 라벨은 코랄 + mono 대문자 + 행 구조로, Why it works 대조표는 좌/우 위치 + mono 라벨 유무로 구분된다
- **경계선 대비**: `--border`/`--border-strong`은 장식용 헤어라인이며 정보 전달에 의존하지 않음. 세컨더리 버튼 테두리는 별도 토큰 `--border-btn`(≥3:1)
- **텍스트 200% 확대**: 고정 높이 카드 없음. 버튼 높이는 `min-height`로 구현할 것
- **`prefers-reduced-motion`**: 애니메이션 없음. 추가 시 대응 필요

---

## 9. Data Assumptions

**동적 데이터 없음.** 전부 정적 콘텐츠(카피 상수)이며, 향후 CMS로 뺄 경우의 스키마 제안이다. 문구 전문은 `COPY_DECK.md`.

| 필드 | 타입 | 값 | 확인 필요 | null | 빈 값 처리 | 긴 값 |
|---|---|---|---|---|---|---|
| `hero.headline` / `.sub` | string | 브리프 확정 문구 | **확정** | X | 필수 | 줄바꿈 |
| `hero.meta` | string | `"Ten years of filings · item-level chunks · every claim traceable"` | **확정** | X | 행 숨김 | 줄바꿈 |
| `hero.primaryCta.href` | string(URL) | `/request-access` — **가정 라우트** | `[확인 필요]` | X | 링크 대상 결정 전 배포 금지 | — |
| `hero.secondaryCta.href` | string(URL) | `https://rag-playground.lucydata.ai` | 확정 | X | 필수 | — |
| `problem.body` | string | 4문장 | **확정** | X | 섹션 숨김 | — |
| `whyItWorks.rows[]` | `{problem, label, body}` | **10항목.** `problem`(좌열)은 **디자인이 작성한 문구** [확인 필요] | body는 확정 | X | 행 숨김 | ≤1023 1열 |
| `proof.blocks[]` | `{n,title,body}` | 3항목 (The path / The source / The score) | **확정** | X | 필수 | — |
| `ask.surfaces[]` | `{label, line1, line2}` | 3항목 (RDB / Vector search / Lucy Intelligence). **line2는 이번 패스 신규 브리프 문구** | 확정 | X | 카드 숨김 | — |
| `contrast.specimen` | string | VOO 대안 질문 1개 (대조 블록의 표본) | **확정** | X | 블록 숨김 | mono 줄바꿈 |
| `contrast.similarity[]` / `.structured[]` | string[] | 3항목 / 2항목 | **디자인 작성 문구** `[확인 필요]` | X | 열 숨김 | — |
| `contrast.also` | string | ETF 비용비율 질문 1개 | **확정** | X | 줄 숨김 | — |
| `coverage.dataset.funds[]` | string[] | 6종 (NPORT-P … DSR) | **확정** | X | 그룹 숨김 | wrap |
| `coverage.dataset.corporate[]` | string[] | 13종 (10-K … Forms 3, 4, 5) | **확정** | X | 그룹 숨김 | wrap |
| ~~`coverage.*.filingCount` / `.dateRange`~~ | — | **존재하지 않음** | — | — | **넣지 않는다 — 수치 미확보** | — |
| `proof.metrics[]` | `{label,body}` | 3항목 (Relevance / Retrieval Relevance / Groundedness) | **이름 확정** | X | 행 숨김 | — |
| ~~`proof.aggregateScore`~~ | — | **존재하지 않음** | — | — | **총점·평균은 어떤 형태로도 노출 금지** | — |
| `mcp.toolSignature` | string | `rag_context(question, thread_id?)` | **확정** | X | 필수 | mono |
| `mcp.clients[]` | string[] | 6항목 (Claude Desktop · Cursor · Cline · Codex · ChatGPT · any MCP-capable host) | 확정 | X | 행 숨김 | 줄바꿈 |
| `mcp.setup` | string | endpoint URL + Bearer API key, stdio / streamable HTTP | 확정 | X | 행 숨김 | — |
| ~~`mcp.endpointHost`~~ | — | **의도적으로 미출력** | — | — | **실제 호스트명을 페이지에 쓰지 않는다** | — |
| `cta.requestFields[]` | string[] | 3항목 (Company / Intended use / Expected volume) | 확정 | X | 줄 숨김 | 줄바꿈 |
| `*.image.src` | string(path) | `assets/*.png` | judge-metrics 미수령 | X | 라벨된 프레임만 렌더 | — |
| `*.image.alt` | string | §19 참조 | 확정 | X | 필수 | — |

**날짜/시간**: 절대 날짜만, ISO `YYYY-MM-DD`. 요일 인덱스 사용 금지.
**불리언**: `showMetaRow`, `showBrowserChrome` — 다단계 문자열 아닌 boolean 유지.

---

## 10. Prototype Code Notes

프로토타입 파일: `Lucy Marketing Site.dc.html` (+ `image-slot.js`, `support.js`, `assets/`). **production 코드가 아니다.**

**그대로 참고해도 되는 구조**
- 섹션 분해: §2 표의 10개 블록이 그대로 컴포넌트 경계
- role 기반 class 이름: `site`, `nav`, `nav-inner`, `nav-links`, `nav-actions`, `nav-toggle`, `nav-panel`, `nav-cta-full`, `nav-cta-short`, `logo`, `btn`, `btn-primary`, `btn-secondary`, `btn-ghost`, `dark`, `hero`, `hero-sub`, `hero-meta`, `cta-row`, `eyebrow`, `shot`, `shot-frame`, `shot-bar`, `shot-media`, `dot`, `section-inner`, `section-head-split`, `split`, `split-copy`, `split-copy-first`, `code-block`, `base-block`, `step-list`, `step-card`, `card`, `card-grid`, `coverage-grid`, `chip`, `chip-primary`, `chip-secondary`, `chip-row`, `fact-list`, `fact-row`, `q-block`, `contract`, `architecture`, `preprocessing`, `data-model`, `coverage`, `verification`, `mcp`, `licensing`, `closing`, `site-footer`, `footer-grid`, `footer-col`, `footer-bottom` — 자동 생성·해시 이름 없음
- 8pt spacing scale
- **`.dark` 토큰 재정의 패턴**: 다크 섹션은 배경색만 바꾸는 것이 아니라 `--text` / `--text-2` / `--text-3` / `--accent` / `--border*` / `--panel`을 통째로 지역 재정의한다. 덕분에 내부 컴포넌트(`fact-row`, `code-block`, `step-card`, 버튼)는 자기가 어느 표면 위에 있는지 몰라도 된다. **이 패턴을 반드시 이식할 것**

**핵심 CSS (production 이식 대상) — 아래는 배포 파일의 `<style>` 전문이다 (손으로 옮겨 적은 요약이 아님)**

```css
:root{
  --dark:#1c1815; --light:#faf8f4; --panel:#ffffff;
  --text:#2a2723; --text-2:#5c564e; --text-3:#6d675e;
  --accent:#b0492f;
  --border:rgba(42,39,35,.13); --border-strong:rgba(42,39,35,.20); --border-btn:#8a8177;
  --radius-sm:3px; --radius-md:6px; --btn-radius:6px;
  --space-2:8px; --space-3:12px; --space-4:16px; --space-5:20px; --space-6:24px;
  --space-8:32px; --space-10:40px; --space-12:48px; --space-16:64px;
  --space-20:80px; --space-24:96px; --space-30:120px;
  --font-sans:'Archivo',Helvetica,Arial,sans-serif;
  --font-mono:'IBM Plex Mono',ui-monospace,Menlo,monospace;
  --font-num:'Pretendard Variable','Pretendard',-apple-system,system-ui,sans-serif;
  --container:1200px;
}
*{box-sizing:border-box}
html{scroll-behavior:smooth}
body{margin:0;background:var(--light);color:var(--text);font-family:var(--font-sans);-webkit-font-smoothing:antialiased;text-wrap:pretty}
a{color:var(--accent);text-decoration:none}
a:hover{color:#8f3a23;text-decoration:underline}
:focus-visible{outline:2px solid var(--accent);outline-offset:2px;border-radius:2px}

/* dark = 3 · 6 · 8 only */
.dark{background:var(--dark);color:#ede8de;
  --text:#ede8de; --text-2:rgba(237,232,222,.74); --text-3:rgba(237,232,222,.56);
  --accent:#e28a68; --panel:rgba(237,232,222,.03);
  --border:rgba(237,232,222,.13); --border-strong:rgba(237,232,222,.22); --border-btn:rgba(237,232,222,.44)}
.dark a:hover{color:#f0a689}

.shot-frame{border:1px solid var(--border);border-radius:var(--radius-md);overflow:hidden;background:var(--panel);box-shadow:0 1px 2px rgba(42,39,35,.04),0 14px 34px -20px rgba(42,39,35,.16)}
.shot-bar{height:36px;display:flex;align-items:center;gap:var(--space-3);padding:0 var(--space-4);border-bottom:1px solid var(--border)}
.dot{width:7px;height:7px;border-radius:50%;background:var(--border-strong)}

.chip{display:inline-flex;align-items:center;font-family:var(--font-mono);white-space:nowrap;border-radius:var(--radius-sm)}
.chip-primary{height:40px;padding:0 var(--space-4);font-size:16px;color:var(--accent);border:1px solid var(--border-strong)}
.chip-secondary{height:30px;padding:0 var(--space-3);font-size:13px;color:var(--text-3);border:1px solid var(--border)}
.card ul li:last-child{border-bottom:none;padding-bottom:0}
/* Proof: frames lead each column, so they align at the top by construction */
.proof .step-list{align-items:start}

.nav-toggle{display:none;align-items:center;justify-content:center;width:44px;height:44px;padding:0;background:transparent;border:1px solid var(--border-btn);border-radius:var(--radius-md);color:var(--text);cursor:pointer}
.nav-toggle span{display:block;width:18px;height:1.5px;background:currentColor;box-shadow:0 -5px 0 currentColor,0 5px 0 currentColor}
.nav-panel{position:sticky;top:76px;z-index:19;display:flex;flex-direction:column;gap:var(--space-2);padding:var(--space-4) var(--space-8) var(--space-6);background:var(--light);border-bottom:1px solid var(--border)}
.nav-panel a{display:flex;align-items:center;min-height:44px;font-size:17px;color:var(--text-2)}
.nav-cta-short{display:none}

@media (max-width:1023px){
  :root{--container:100%;--space-30:80px;--space-24:64px;--space-20:56px;--space-16:40px}
  .nav-links,.nav-actions .btn-ghost{display:none!important}
  .nav-toggle{display:inline-flex}
  .hero,.section-inner,.nav-inner{padding-left:var(--space-8)!important;padding-right:var(--space-8)!important}
  .split,.section-head-split,.card-grid,.compare-grid{grid-template-columns:minmax(0,1fr)!important}
  .step-list{grid-template-columns:minmax(0,1fr)!important}
  .step-card{padding:var(--space-8) 0!important;border-right:none!important}
  .step-card + .step-card{border-top:1px solid var(--border-strong)}
  .card-wide{flex-direction:column!important;gap:var(--space-4)!important}
  .card-wide > h3{flex:0 0 auto!important}
  .footer-grid{grid-template-columns:repeat(2,minmax(0,1fr))!important;gap:var(--space-8)!important}
  .footer-grid > div:first-child{grid-column:1/-1}
  h1{font-size:52px!important}
  h2{font-size:32px!important}
}
@media (max-width:599px){
  :root{--space-30:56px;--space-24:48px;--space-20:40px;--space-16:32px;--space-12:24px}
  .hero,.section-inner,.nav-inner{padding-left:var(--space-5)!important;padding-right:var(--space-5)!important}
  .nav{height:64px!important}
  .nav-inner{gap:var(--space-3)!important}
  .nav-panel{top:64px;padding-left:var(--space-5);padding-right:var(--space-5)}
  .nav-cta-full{display:none}
  .nav-cta-short{display:inline}
  .nav-actions .btn-primary{padding:0 var(--space-4)!important}
  h1{font-size:36px!important;letter-spacing:-.025em!important}
  h2{font-size:27px!important}
  h3{font-size:20px!important}
  .hero-sub{font-size:16px!important}
  .turn-arrow span:first-child{height:72px!important}
  .cta-row{flex-direction:column!important;align-items:stretch!important;width:100%}
  .cta-row .btn{width:100%;justify-content:center;flex:1 1 auto!important}
  .fact-row{grid-template-columns:minmax(0,1fr)!important;gap:var(--space-2)!important}
  .chip-primary{height:34px;padding:0 var(--space-3);font-size:14px}
  .card,.contrast{padding:var(--space-6)!important}
  .footer-bottom{flex-direction:column;align-items:flex-start!important;gap:var(--space-3)!important}
}
```

**Tailwind 등록용 토큰**

```css
@theme {
  --color-dark: #1c1815;          /* 웜 니어블랙, 브라운 틴트 — 블루블랙 아님 */
  --color-light: #faf8f4;         /* 웜 오프화이트 — 크림/베이지 아님 */
  --color-panel: #ffffff;
  --color-text: #2a2723;
  --color-text-2: #5c564e;
  --color-text-3: #6d675e;   /* 5.2:1 — caption/meta/chip 전용, 본문 금지 */
  --color-accent: #b0492f;         /* 코랄 — 유일한 악센트. 5.2:1(지면) / 5.5:1(흰 카드). 브랜드 확정 아님 */
  --color-accent-on-dark: #e28a68; /* 다크 표면 전용. 필수 — §8 참조 */
  --color-text-on-dark: #ede8de;
  --color-border: rgba(42,39,35,.13);
  --color-border-strong: rgba(42,39,35,.20);
  --color-border-btn: #8a8177;
  --radius-sm: 3px;
  --radius-md: 6px;
  --radius-btn: 6px;
  --spacing-2: 8px;   --spacing-3: 12px;  --spacing-4: 16px;
  --spacing-5: 20px;  --spacing-6: 24px;  --spacing-8: 32px;
  --spacing-10: 40px; --spacing-12: 48px; --spacing-16: 64px;
  --spacing-20: 80px; --spacing-24: 96px; --spacing-30: 120px;
  --font-sans: 'Archivo', Helvetica, Arial, sans-serif;
  --font-mono: 'IBM Plex Mono', ui-monospace, Menlo, monospace;
  --font-num: 'Pretendard Variable', 'Pretendard', system-ui, sans-serif;  /* 숫자 라벨 전용 */
  --container-page: 1200px;
}
```

**버려야 할 임시 코드**

| 항목 | 조치 |
|---|---|
| **모든 inline `style` 속성** | 스트리밍 프리뷰 제약 때문에 인라인으로 작성됨. **전부 클래스/유틸리티로 교체** |
| `style-hover` 속성 | 프로토타입 런타임 전용 문법. `:hover` CSS로 교체 |
| `<image-slot>` | 프로토타입 전용 드롭 플레이스홀더. **`<img src alt>`로 교체**. 드롭 시 1200px WebP로 재압축되므로 production에서는 반드시 원본 파일을 직접 참조할 것 |
| `<sc-if>` | 프로토타입 템플릿 문법. 프레임워크 조건부 렌더로 교체 |
| `.site` 래퍼 | 페이지 루트. production에서는 `body` 또는 최상위 레이아웃 컴포넌트로 승격 가능 |
| 미디어쿼리의 `!important` | 인라인 스타일을 덮기 위한 것. 인라인을 유틸리티로 옮긴 뒤 제거 |
| 라우트 경로 | 인페이지 앵커(`#problem`, `#proof`, `#why-it-works`, `#what-you-get`, `#integration`)는 실제 동작. `/docs`, `/docs/api`, `/docs/mcp`, `/company`, `/company/contact`, `/request-access`, `/legal/privacy`, `/legal/terms`는 **가정한 라우트이며 아직 존재하지 않음** `[확인 필요]` |
| `.nav-cta-full` / `.nav-cta-short` | 모바일 라벨 축약용 이중 스팬. i18n 도입 시 문자열 2개로 관리되는 점 주의 |
| 화면의 `[TO CONFIRM]` 문자열 2곳 | 더미 아님, **화면에 의도적으로 노출되는 미확정 표시**. 실제 값 확정 전 배포 금지 `[확인 필요]` |
| nav 4종 / footer 2종 링크 | **가정한 IA** `[확인 필요]`. Product · Coverage · Developers 열은 삭제됐다 — Docs · API reference · MCP server 링크가 페이지에서 사라졌으므로 개발자 문서 진입점이 없다 `[확인 필요]` |

- 의미 없는 div 중첩: 없음. 모든 래퍼는 레이아웃/의미 단위
- 애니메이션: 없음. hover는 `opacity`/배경만
- 접근성 **구현 완료**: `:focus-visible` 전역, 모바일 nav disclosure. **남은 항목: 외부 링크 새 탭 안내, 코드 블록 `tabindex`**
- 반응형 **구현 완료**: `@media (max-width:1023px)` / `(max-width:599px)` 2단

---

## 11. Implementation Brief for Claude Code

**작업 목표**: lucydata.ai 랜딩페이지(단일 페이지, 12섹션)를 이 시안대로 구현.

**구현 범위**
1. §2의 10개 부록 전체
2. 공통 컴포넌트 §6 (`Section`, `SectionHeadSplit`, `CompareCard`, `ContrastBlock`, `StepColumn`, `Chip`, `FormGroup`, `FactList`, `ClientTile`, `MediaFrame` 등)
3. 디자인 토큰 등록 §10 + **`.dark` 지역 재정의 패턴**
4. §7 반응형 분기
5. 모바일 nav 토글

**수정하지 않을 범위**: 제품 애플리케이션(`rag-playground.lucydata.ai`) 코드, 인증, API 클라이언트, 라우팅 구조 전반.

**필요한 상태**: 모바일 nav open/closed 1개. 그 외 클라이언트 상태 없음.

**반응형 조건**: §7. 360px에서 가로 overflow 0 (JSON 블록의 자체 가로 스크롤은 예외).

**접근성 조건**: §8. 특히 **다크 표면의 `--accent` 재정의**, `:focus-visible`, alt text, `--text-3` 사용 제한.

**데이터 조건**: 정적. 없는 숫자를 채우지 않는다. `[TO CONFIRM]` 2곳은 실제 값이 정해질 때까지 그대로 둔다.

**완료 기준**

- [ ] 1440 / 768 / 390 / 360에서 가로 스크롤 없음
- [ ] 섹션 순서가 구매자 의심 순서(§1 표)와 일치하고, 다크가 **[문제+증거] · Coverage · 최종 CTA** 세 구역이며 ①을 제외하면 서로 인접하지 않음
- [ ] **모든 위치에서 주 버튼이 Request dataset access**(솔리드), 보조가 Open the playground(아웃라인)
- [ ] 히어로·최종 CTA에서 **보조 버튼이 왼쪽**에 온다
- [ ] Licensing 섹션이 존재하지 않는다
- [ ] 푸터에 **Company 열만** 있다 (Product · Coverage · Developers 열 삭제)
- [ ] What you can ask 섹션 위에 구분선이 없다
- [ ] 히어로 영상이 자동재생·무음·루프로 재생되고, 저감모션 설정에서는 poster에서 멈춘다
- [ ] Integration이 **전체폭 가로형 카드 2장으로 상하 배치**되고, API 카드가 짧은 채로 남아 있다(억지로 채우지 않음)
- [ ] 호스트 칩에 **로고·이미지·점선 박스가 없다**(제3자 상표 미사용) 그리고 라벨이 "Supported hosts"다
- [ ] 다크 섹션의 eyebrow·번호·라벨이 밝은 코랄(`#e28a68`)로, 라이트 섹션은 `#b0492f`로 렌더되어 **양쪽 모두 대비 ≥4.5:1** (흰 카드 위 chip·카드 제목 포함)
- [ ] Why it works가 **대조 카드 2장**이고, 좌측 카드가 자기 내용 높이로 줄어 **세로 중앙 정렬**되며, 오른쪽 Lucy 카드만 다크로 반전되어 있음
- [ ] 두 카드의 01–10 번호가 유지되어 문제↔해결 대응이 읽힘
- [ ] The problem과 Proof 사이에 **경계선도 전환 문장도 없고**, 세로 화살표가 방향을 표시함
- [ ] Why it works 좌열이 **일반적 경향**으로만 서술되고 특정 경쟁사를 지목하지 않음
- [ ] Coverage가 **전체폭 단일 블록**이고 펀드 그룹이 기업 그룹보다 시각적으로 우선함 (카드 짝짓기·라이브 범위 표기 없음)
- [ ] What you can ask의 대조 블록이 **경쟁사를 지목하지 않고** "similarity search"로만 서술함
- [ ] 대조 블록의 예시 질문에 실행 버튼·입력창 등 **실행 가능함을 암시하는 어포던스가 없음**
- [ ] Proof 3열이 **프레임 → 번호 → 제목 → 본문** 순서이고 프레임 높이가 같다(실측 250px)
- [ ] Why it works의 16:9 프레임이 **대조 카드 위**에 max-width 800px 중앙 정렬로 놓임(캡션 포함)
- [ ] What you can ask · Coverage · Integration 세 섹션에 **이미지가 없음**
- [ ] 대조 블록의 좌우 열이 **각 3행**이고, "Also:" 줄이 두 열 아래 전체폭에 있음
- [ ] 총점·평균 점수가 어디에도 없음
- [ ] Integration에 **JSON 블록이 없고**, 실제 MCP 호스트명도 없음
- [ ] 페이지에 그라데이션·블러·글래스·쿨 색상이 없음
- [ ] 모바일 본문 ≥15px, 터치 타깃 ≥44px
- [ ] inline style / `image-slot` / `sc-if` 가 코드에 남아 있지 않음

**구현 전 확인할 질문**: §14

---

## 11b. 추가 의존성 후보

**확정이 아니다.** 실제 필요 여부와 채택은 Claude Code 단계에서 판단한다. 전부 **무의존으로도 구현 가능**하다.

| 후보 | 용도 | 무의존 대안 | 판단 |
|---|---|---|---|
| 인터랙션 라이브러리 (base-ui / Radix / shadcn 중 프로젝트 바인딩) | 모바일 nav disclosure의 포커스·ARIA·Escape 처리 | 현재 프로토타입이 이미 무의존으로 구현함 (§16) | 프로젝트 바인딩 표를 따른다 `[확인 필요]` |
| 웹폰트 로딩 방식 (Google Fonts CDN / self-host / next/font) | Archivo + IBM Plex Mono | CDN `<link>` (현재 방식) | 스택 확정 후 결정 `[확인 필요]` |

- **신택스 하이라이터 라이브러리는 쓰지 않는다.** §3 JSON은 정적 리터럴이며, 브리프가 무지개 하이라이트를 금지한다. 키/값 2색 강조는 CSS만으로 충분하다
- **애니메이션·차트·아이콘 패키지 불필요.** 애니메이션이 없고, 차트는 스크린샷으로 대체되며, 아이콘을 쓰지 않는다
- 상태 관리 라이브러리도 불필요 — 클라이언트 상태가 모바일 nav open/closed 1개뿐이다
- 실제 스택은 Claude Code 단계에서 확인한다. React·TypeScript·Next.js 구조를 이 문서가 확정하지 않는다

---

## 12. Confirmed Facts

- 제품 URL: `rag-playground.lucydata.ai` (실존, secondary CTA 링크 대상)
- 마케팅 사이트 도메인: `lucydata.ai`
- 판매 대상은 답변이 아니라 citation-grade evidence. 답변은 고객 모델이 작성
- 구매자: 프론티어 AI 랩, 금융 데이터 벤더, RAG 엔지니어링 팀
- 사이트 카피 100% 영어, 한국어 미사용. 데스크톱 우선 1440px
- **섹션 순서·표면**: 구매자 의심 순서 8섹션(+내비·푸터), DARK는 Proof · Integration · Final CTA (§1 확정)
- **레이아웃 primitive를 새로 만들지 않는다** — L1~L8 재사용. 유일한 신규 조합은 Why it works의 2열 대조 행이며 기존 fact-row 구조의 변형이다 (§1)
- **응답 구조**: `rag_context`는 청크만 반환하고 답변은 호출한 모델이 구성한다. **이 사실은 Integration 섹션의 한 줄 주석으로만 남았다** — 이전 패스의 키 대조표·JSON 블록은 삭제됨
- **페이지에 accession number·JSON·호스트명을 출력하지 않는다**
- **MCP 도구 확정**: `rag_context(question, thread_id?)` → 약 20개 source chunk. trace는 progress notification으로 스트리밍. `thread_id` 재전달로 멀티턴. **엔드포인트는 청크만 반환한다**
- **MCP 클라이언트**: Claude Desktop · Cursor · Cline · Codex · ChatGPT · 그 외 MCP 지원 호스트
- **MCP 설정**: endpoint URL 1개 + Bearer API key. 로컬은 stdio, 원격은 streamable HTTP. **키는 수동 발급**
- **판정 지표 3종 이름 확정**: Relevance / Retrieval Relevance / Groundedness. 응답별 실시간 산출이므로 **고정 점수·총점·평균은 존재하지 않는다**
- **커버리지 확정**: dataset은 10년치 SEC 문서(펀드·ETF 6종 + 기업·지분 13종). **라이브 범위는 열람과 검색이 다르다** — Browsable 6종(10-K · 10-Q · 8-K · DEF 14A · 20-F · 6-K), **RAG 검색은 10-K 1종**. filing 수·기간 수치는 없음
- **팔레트**: 웜 단일 계열. 다크 `#1c1815`, 라이트 `#faf8f4`, 악센트 코랄 `#b0492f`(라이트) / `#e28a68`(다크), 다크 위 텍스트 `#ede8de`, 라이트 위 텍스트 `#2a2723`
- **코랄이 유일한 악센트**. eyebrow·활성 상태·citation 마커·링크에만 사용
- **타이포 3종**: Archivo(제목·본문) + IBM Plex Mono(eyebrow, chip, chunk id, 캡션, 코드) + **Pretendard(숫자 라벨 전용 — Proof 01·02·03, Why it works 01–10)**. 이전 브리프의 "2종만" 규칙에서 벗어난 것이며 사용자 요청에 따른 것이다 `[확인 필요]`
- 금지 준수: 그라데이션 웨이시, 글래스모피즘, 프로스티드 패널, 인디고·라벤더, 블루블랙, 장식적 배경 효과 — 없음. AI 마스코트, 일러스트, 스톡 사진, 가짜 대시보드, 없는 UI, 없는 차트 — 미사용
- 수치 미조작: 미확정 2건은 `[확인 필요]`

## 13. Assumptions

- 팔레트 hex 값은 브리프 근사치(`~#1C1815` 등)를 구체화한 것 — 브랜드 확정 아님 `[확인 필요]`
- 악센트 두 값 모두 **접근성 대비를 맞추기 위해 조정한 값** (§8) — 라이트 `#b0492f`, 다크 `#e28a68`. 브랜드 원본 색이 있으면 대비 검증 후 교체 필요 `[확인 필요]`
- 로고 표현 "Lucy + DATA" 워드마크는 **임시**. 실제 로고 파일 미수령. 제품 워드마크는 `lucy-rag`(세리프 이탤릭)로 다르다 `[확인 필요]`
- 폰트 Archivo + IBM Plex Mono는 **제안**. 브랜드 서체 미확정 `[확인 필요]`
- nav 4개 / footer 10개 링크 구조는 **가정**. 실제 사이트맵 미확인
- **Why it works 좌측 카드 10줄은 디자인이 작성한 문구다** — 브리프가 "일반적 경향으로 서술하고 특정 경쟁사에 대한 사실 주장으로 쓰지 말 것"만 지정했다. 사실 검토 필요 `[확인 필요]`
- **전환 장치는 텍스트가 아니라 세로 화살표다** — 이전 판의 피벗 문장("So the path ships with the answer.")은 삭제됐다. 화살표는 `aria-hidden="true"`이며 스크린리더에는 읽히지 않는다. 두 섹션의 heading 순서가 논리 순서를 이미 전달하므로 대체 텍스트가 필요 없다
- primary CTA는 폼 페이지로 이동한다고 가정 (모달 아님)
- 트래픽 대부분 데스크톱이라 가정

## 14. Open Questions

1. **judge-metrics 스크린샷을 받을 수 있는가?** Proof(다크)의 "The score" 열에 붙일 자리가 있으나, 다크 표면이라 크림 스크린샷과 충돌한다. 받으면 Why it works 끝이나 별도 라이트 밴드에 배치하는 안을 함께 검토한다 (§19 이미지 계획)
2. **Why it works 좌열 10줄** 문구가 사실로 적절한가? (§13)
3. 브랜드 컬러 확정 값은? 특히 다크용 밝은 코랄 `#e28a68` 승인 여부
4. 브랜드 서체 지정이 있는가? 없으면 Archivo + IBM Plex Mono로 확정해도 되는가?
5. **워드마크** — 제품은 `lucy-rag`(세리프 이탤릭), 사이트는 `Lucy DATA`(산스). 통일할 것인가?
6. "Request dataset access"의 이동 대상 — 별도 폼 페이지 / 모달 / 외부 폼?
7. 데이터셋 요청 폼을 실제로 구현할 것인가? 현재는 요청 항목 3개를 mono 한 줄로 안내만 한다
8. Delivery 방식 — batch / vector store / RDB export 중 무엇을 제공하는가?
9. 라이선스 조건 — 재배포·모델 학습·클라이언트 산출물 권리의 실제 범위는?
10. nav / footer 정보구조와 라우트 경로(`/docs`, `/company`, `/request-access`, `/legal/*`)는?
11. 기술 스택 및 인터랙션 라이브러리(base-ui / Radix / shadcn 등)는?
12. 모바일에서 hero 3열 스크린샷 판독이 어려울 경우 **모바일 전용 크롭 이미지**를 제공할 수 있는가?
13. hero 스크린샷에 NVDA 종목명과 실제 filing 번호가 보인다. 공개 페이지 노출 가능 여부는?

## 15. Source / Version

- 프로젝트명: Lucy (lucydata.ai) 마케팅 사이트
- 화면명: Marketing Landing — Full page
- 디자인 버전: **v4.4** (**세일즈 페이지로 재프레이밍** — 섹션을 구매자 의심 순서로 재배열, The problem 신설, Proof가 후크 위치로, 전처리를 10행 문제-해결 대조표로 전환, 데이터모델+커버리지 병합, CTA 우선순위 정정, 3-panel 투어·The contract·Architecture·JSON 블록 삭제)
- 작성 날짜: 2026-07-29
- 산출 파일: `Lucy Marketing Site.dc.html`, `image-slot.js`, `assets/hero-3panel.png`, `assets/chunk-highlight.png`, `DESIGN_HANDOFF.md`, `COPY_DECK.md`(원고 전문)
- 입력 자료: 3차 콘텐츠 브리프 / 2차·1차 디자인 브리프 / ezar 프론트엔드 디자인 가이드 / Claude Design 반응형 UI 기본 규칙 / 제품 스크린샷 2종
- 제품 스크린샷 제공 여부: **2/3 제공** — hero-3panel(4096×2326), chunk-highlight(1116×1666). judge-metrics 미제공

## 16. Interaction Details

| 요소 | 상호작용 |
|---|---|
| Nav 링크 | hover: `--text-2` → `--text`. focus-visible: 2px 코랄 아웃라인. 인페이지 앵커는 `scroll-behavior:smooth`로 이동 |
| Primary CTA | click: `/request-access` `[확인 필요]`. hover: `opacity .86` (150ms). disabled 상태 **없음** |
| Secondary CTA | click: `rag-playground.lucydata.ai`. 새 탭 권장(`rel="noopener"`) `[확인 필요]`. hover: 배경 미세 변화 |
| JSON 코드 블록 | **정적**. 복사 버튼·실행·토글 없음. 좁은 폭에서 가로 스크롤만 |
| 예시 질문 블록 | **정적. 실행 어포던스 금지** — 버튼·입력창·커서 변화·hover 강조 없음 |
| **히어로 영상** | 자동재생·무음·무한루프·인라인. **컨트롤 없음**, 클릭·확대·라이트박스 없음. `prefers-reduced-motion: reduce`에서는 재생하지 않고 poster 프레임을 유지한다. 무음 루프이므로 **재생 위치를 저장하지 않는다**(중간부터 시작하면 오히려 어색함) |
| 플레이스홀더 프레임 | **정적**. 클릭·확대·라이트박스 없음. 브라우저 크롬 바는 장식이며 동작하지 않음 |
| Chip | **비대화형**. 필터가 아님 |
| 지표 3행 | **비대화형** 표시용 |
| 페이지 로드 | 자동 스크롤·자동 포커스 **없음**. 초기 스크롤 위치 top |
| 실시간 갱신 | 없음. 타이머·폴링·시계 없음 |
| 애니메이션 | 진입 애니메이션 없음. hover transition 150ms만 |
| 모바일 nav 토글 | expanded/collapsed. Escape로 닫힘, 열릴 때 첫 링크로 포커스, 닫힐 때 토글로 복귀, `aria-expanded` 필수 |
| 조건부 표시 규칙 | `meta row 보임 = showMetaRow` / `크롬 바 보임 = showBrowserChrome` |
| keyboard | Tab 순서 = DOM 순서. 커스텀 키 핸들러는 Escape 하나뿐 |

## 17. Do Not Implement Yet

- 데이터셋 요청 **폼 자체**(필드·검증·전송) — 이번 범위는 CTA 링크까지
- Docs / Company / Legal 등 **하위 페이지**
- 로고월, 고객 인용, 컴플라이언스 배지
- **MCP 셀프서브 프로비저닝 UI** — 키는 수동 발급이므로 즉시 발급을 암시하는 어떤 UI도 만들지 않는다
- **§6 예시 질문의 실행 기능** — 역량 서술이며 데모가 아니다
- 애널리틱스/전환 트래킹 이벤트 `[확인 필요]`
- 다크 모드 전체 테마 (현재는 섹션별 명암이지 사용자 토글이 아니다)
- 코드 블록 복사 버튼·신택스 하이라이터
- 브래킷 수치를 임의 값으로 채워 배포하는 것
- 브랜드 컬러·서체 확정 (디자인이 스스로 확정하지 않음)

## 18. Handoff Quality Gate

**판정: WARN — 인계 가능하나 아래 미흡 항목 해소 필요**

| 점검 항목 | 상태 |
|---|---|
| UI States | PASS — 불필요 상태에 사유 명시, 코드 블록 overflow 상태 포함 |
| Responsive Rules | PASS — 1023/599 분기 구현, §7은 배포 미디어쿼리 전문을 그대로 싣는다. 1열 접힘 구간의 세로 asset 해상도 보호(`.shot-portrait` 558px 상한) 포함 |
| Accessibility Notes | PASS — 대비 실측 통과(다크·라이트), `:focus-visible` 구현, nav disclosure 구현. 남은 항목: 외부 링크 새 탭 안내, 코드 블록 `tabindex` |
| Implementation Brief | PASS |
| Confirmed / Assumptions / Open Questions 분리 | PASS |
| Data Assumptions 최종값 | **WARN** — 대부분 확정값으로 채움. 미확정 2건(Delivery 방식 / 라이선스 조건)만 `[확인 필요]` |
| 같은 역할 = 같은 마크업 | PASS — L1~L8 패턴 재사용, 신규 primitive 없음 |
| class 이름 | PASS — 전부 역할 기반. 이전 패스의 `.code-block b`/`i` 문제는 코드 블록 삭제로 해소됨 |
| 의미 없는 div 중첩 | PASS |
| 시안 = 문서 일치 | PASS — §7·§10은 배포 파일에서 그대로 생성 |
| 브리프 준수 | PASS — 구매자 의심 순서·다크 3곳 비인접·CTA 우선순위 정정·JSON 제거·호스트명 미출력·총점 미표시 전부 확인 |
| 콘텐츠 정확성 | **WARN** — 브리프 문구는 그대로. 단 **Why it works 좌열 10줄이 디자인 작성 문구**이며 사실 검토 전이다 (§13, §14-2) |
| Accessibility 실측 일치 | PASS — §8 대비 표 전체를 실측값으로 정정(text-3·accent 2건). 라이트 accent는 지면·흰 카드 두 표면 모두 검증 |
| Asset | **WARN** — hero 1장으로 충분하지만 **시각적 증거가 1장뿐**이다(§14-1). 로고 미수령 |

**BLOCK 아님** — 이름·구조·대비 통과. 남은 선행 조건은 **①Proof 이미지 방침 결정(§14-1) ②Why it works 좌열 문구 검토(§14-2) ③브랜드 컬러·서체·워드마크 승인 ④미확정 3건 `[확인 필요]`**이며, ①만 레이아웃에 영향이 있다. 컴포넌트 골격·토큰은 지금 구현 가능.

## 19. Asset Notes

| 파일 | 상태 | 용도 | 크기·비율 | alt text |
|---|---|---|---|---|
| **hero.mp4** | **수령 완료** — `assets/hero.mp4`, 1904×1080 | Hero 전체폭 자동재생 루프 | 프레임 `1904/1080` | `aria-label`: "Lucy playground: a question is asked, the pipeline runs, chunks are retrieved, and the answer is scored" |
| hero-3panel.png | **수령 완료** — 4096×2326 | 위 영상의 `poster` | 동일 | 영상과 같은 내용 |
| **pipeline-detail.png** | **미수령 — 예약 프레임** (`#proof-pipeline`) | Proof 01 The path | 4:3, 최소 1000px @2x | "The pipeline graph with each stage lit in sequence as the answer is produced." |
| **chunk-highlight.png** | **파일 있음, 프레임 재배치됨** (`#proof-source`) | Proof 02 The source | 4:3 — **현재 파일은 1116×1666 세로라 4:3에 맞지 않는다.** 4:3 크롭본 또는 다른 컷 필요 `[확인 필요]` | "A retrieved chunk with the supporting passage highlighted where it sits in the filing." |
| **judge-metrics.png** | **미수령 — 예약 프레임** (`#proof-score`) | Proof 03 The score | 4:3, 최소 1000px @2x | "The three judge scores reported alongside a response." |
| **table-before-after.png** | **미수령 — 예약 프레임** (`#why-table-before-after`) | Why it works 결론 | **16:9, 최소 2000px @2x** (표 두 벌이 나란히 들어가므로 폭이 필요) | "A merged-cell table from a 10-K: flattened text on the left, structured JSON on the right." |
| 로고 | **미수령** | 헤더 + 푸터 | SVG, 높이 20–24px | "Lucy" |

**플레이스홀더 처리 규칙**: 프레임은 종횡비만 잡고 **회색 블록으로 채우지 않는다.** 다크 표면(Proof)에서는 웜 저대비 보더(`rgba(237,232,222,.22)`)에 그림자 없음, 라이트 표면(Why it works)에서는 표준 헤어라인 + 부드러운 그림자. **카메라·이미지 아이콘을 넣지 않는다.** 각 프레임의 라벨은 파일명으로 시작해 드롭 대상이 명확하다.

**Proof 3열 프레임 정렬**: 프레임이 각 열의 **첫 요소**이므로 상단에서 자연히 정렬된다(이전의 flex 하단 정렬 규칙은 불필요해져 삭제). 단 **3열의 좌우 패딩 합을 32px로 균일화**해야 4:3 높이가 일치한다 — 이전 32/64/32에서는 250/226/251로 어긋났다.

- **영상 해상도 주의**: hero.mp4는 1904px 폭이고 데스크톱 표시 폭이 약 1198px이므로 **1.59배**다. 정지 이미지 기준(2배)에는 못 미친다 — 영상이라 텍스트 판독 요구가 낮아 허용 범위이나, **2560px 이상 export가 있으면 교체 권장** `[확인 필요]`. poster로 쓰는 hero-3panel.png는 4096px이라 첫 프레임은 선명하다
- **저감모션 대응**: `prefers-reduced-motion: reduce`일 때 `componentDidMount`에서 autoplay를 끄고 일시정지해 **poster 프레임을 유지**한다 (§16)
- **해상도 기준**: 표시 폭의 2배 이상. 데스크톱 1440에서 hero 3.4배, chunk-highlight 2.6배. **1열로 접히는 구간에서는 세로 asset이 늘어나 2배가 깨지므로 `.shot-portrait`에 폭 상한 558px을 둔다** (§7 참조). **`<image-slot>`에 드래그해 넣으면 1200px WebP로 재압축되므로**, 고해상도가 필요한 UI 스크린샷은 파일을 직접 `assets/`에 두고 `src`로 참조한다
- **프레임 처리 (전부 라이트 표면)**: 얇은 웜 헤어라인(`rgba(42,39,35,.13)`) + radius 6px + 아주 부드러운 2단 그림자. **디바이스 목업·원근 기울임·반사·글로우 금지**
- 아이콘·일러스트·스톡 사진: **사용 안 함**
- 배경 이미지·그라데이션·장식 효과: **없음.** 모든 표면이 단색
- 라이선스·출처: 제품 스크린샷은 자사 자산으로 가정. **스크린샷과 §3 JSON에 NVDA·Apple accession number 등 제3자 식별 정보가 노출된다** — 공개 가능 여부 `[확인 필요]` (§14-14, 15)
