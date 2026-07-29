# Lucy 랜딩페이지 — 원고 (Copy Deck)

> 배포 파일 `Lucy Marketing Site.dc.html`의 전체 원고. 화면 순서대로.
> **세일즈 페이지 구성**: 섹션 순서가 제품 동작 순서가 아니라 **구매자가 의심하는 순서**를 따른다.
> 100% 영어. 어두운 배경은 **세 구역** — ①The problem + Proof(연속된 한 덩어리) ②Coverage ③Final CTA.

## 구매자가 의심하는 순서

| 순서 | 구매자의 질문 | 대응 섹션 |
|---|---|---|
| 1 | 이게 뭔가 | Hero |
| 2 | 왜 문제인가 | **The problem** (어두움) |
| 3 | 왜 믿어야 하나 | **Proof** (어두움) |
| 4 | 왜 직접 못 만드나 | Why it works |
| 5 | 뭘 물어볼 수 있나 | What you can ask |
| 6 | 뭐가 들어 있나 | **Coverage** (어두움) |
| 7 | 우리 스택에 맞나 | Integration |
| 8 | 어떻게 시작하나 | **Final CTA** (어두움) |

**CTA 규칙 (전 위치 공통)**: 주 버튼은 항상 **Request dataset access**(솔리드), 보조는 항상 **Open the playground**(아웃라인). 플레이그라운드는 판매 대상이 아니라 주장을 검증하는 수단이다.

**배치**: 히어로와 최종 CTA에서는 **보조가 왼쪽, 주가 오른쪽**. 우선순위는 색·채움으로만 표현한다.

---

## 0. Nav — LIGHT

| 위치 | 문구 | 링크 |
|---|---|---|
| 로고 | **Lucy** DATA | `/` |
| 링크 | Proof | `#proof` |
| 링크 | Why it works | `#why-it-works` |
| 링크 | What you can ask | `#what-you-can-ask` |
| 링크 | Integration | `#integration` |
| 보조 CTA | Open the playground | `rag-playground.lucydata.ai` |
| 주 CTA | Request dataset access (모바일: Request access) | `/request-access` |

---

## 1. Hero — LIGHT · "이게 뭔가"

**Eyebrow** · SEC filing data for AI systems

**H1**
Financial answers your team can actually check.

**Sub**
Lucy turns SEC filings into structured, source-linked data — and shows the full path from question to answer, so every statement resolves to the filing text behind it.

**Meta row**
Ten years of filings · item-level chunks · every claim traceable

**CTA** · Open the playground (보조, 왼쪽) / Request dataset access (주, 오른쪽)

**Media** — `assets/hero.mp4` 전체폭 자동재생 루프 영상 (1904×1080, 무음·무컨트롤). `hero-3panel.png`는 poster로 사용

**Caption**
Question, retrieval, answer, and score — in one view.

---

## 2. The problem — **DARK** · "왜 문제인가"

*제품을 설명하기 전에 구매자의 문제를 먼저 이름 붙인다. 이미지 없음, 4줄. **Proof와 함께 하나의 어두운 덩어리**를 이루며, 사이에는 경계선도 전환 문장도 없이 **세로 화살표**만 놓인다(카피 없음).*

**Eyebrow** · The problem

**H2**
Nobody can tell you where a financial answer came from.

**Body**
A model reads a filing, flattens the tables, loses the footnote that qualified the number, and produces a confident paragraph. The output looks right. Nobody downstream can check it, and in financial work an unverifiable answer is not a usable one.

*경쟁사 이름을 쓰지 않는다.*

---

## 3. Proof — **DARK** · "왜 믿어야 하나"

*후크 위치. 삭제된 "3-panel 인터페이스 투어" 섹션의 내용이 여기로 흡수됐다.*

**Eyebrow** · Proof

**H2**
Every step is on the screen while it runs.

**Body**
Lucy answers from retrieved filing text and shows the whole path as it happens — the stages that ran, every chunk that came back, the passage each statement rests on, and a score on whether the answer is actually supported by it.

**01 The path**
Pipeline Graph and Trace Log show the route the question took and every chunk that was retrieved, as it runs rather than after the fact.
*프레임 4:3* — `pipeline-detail.png` — pipeline graph with stages lit in sequence

**02 The source**
The passage an answer rests on is highlighted where it sits in the filing. No opening EDGAR, no downloading anything.
*프레임 4:3* — `chunk-highlight.png` — retrieved chunk with the supporting passage highlighted

**03 The score**
An LLM judge runs on each response in real time.

| 지표 | 설명 |
|---|---|
| Relevance | How well the answer corresponds to the question. |
| Retrieval Relevance | How well the retrieved chunks correspond to it. |
| Groundedness | Whether the response is factually supported by the source context; in effect, hallucination detection. |

*프레임 4:3* — `judge-metrics.png` — the three judge scores as reported per response

**마무리**
Loaded chunks are also browsable on their own — filtered by filing item, as text or table units.

*총점·평균 점수는 어디에도 표시하지 않는다.*

---

## 4. Why it works — LIGHT · "왜 직접 못 만드나"

*페이지에서 가장 세로 공간을 많이 쓰는 섹션. 기능 목록이 아니라 "EDGAR는 무료인데 왜 돈을 내야 하나"에 대한 답으로 구성했다.*

**Eyebrow** · Why it works

**H2**
EDGAR is free. Making it retrievable is not.

**Intro**
Pulling filings is the easy part. The difficulty is everything that happens before retrieval — and it is where most financial RAG quietly breaks.

**10행 대조표** — 왼쪽은 일반적인 파이프라인에서 무엇이 어긋나는지, 오른쪽은 Lucy의 처리(문구 그대로 유지)

| What goes wrong *(일반적 경향, 경쟁사 지목 아님)* | What Lucy does |
|---|---|
| Fixed-length chunks split a statement mid-row. | **Item-level separation** — Body text is split by filing item, so chunk boundaries follow the document's own structure. |
| A chunk arrives with no record of which filing it came from. | **Document metadata** — Metadata ships with every chunk for search and filtering. |
| A long item has to be read whole or not at all. | **Summaries** — Item-level and document-level summaries are generated alongside the source text. |
| Tables flatten into unlabeled runs of numbers. | **Table structure** — Tables are structured as JSON. Irregular layouts, including merged cells, are recognized rather than flattened. |
| A cross-reference dead-ends at the mention of it. | **Reference resolution** — Internal and external references carry the information needed to reach the referenced document. |
| Charts and diagrams are dropped on the way in. | **Images** — Image content is described, not discarded. |
| Tagged financial values arrive as plain prose. | **XBRL** — Figures in the financial statements carry their XBRL information. |
| Exhibits and statement attachments are skipped as boilerplate. | **Attachments** — Exhibits and financial statements attached to the filing are provided. |
| Cover pages and signature blocks compete with real content in retrieval. | **Boilerplate handling** — Cover pages, signature blocks, and similar non-content are separated out. |
| Extraction errors surface only when a user hits one. | **QA** — Data quality is maintained through a review pass on the output. |

⚠ **왼쪽 열 10줄은 제가 작성한 문구입니다.** 브리프가 "일반적 경향으로 서술하고 특정 경쟁사에 대한 사실 주장으로 쓰지 말 것"만 지정했습니다. 문구 검토가 필요합니다.

---

## 5. What you can ask — LIGHT · "뭘 물어볼 수 있나"

**Eyebrow** · What you can ask

**H2**
Two kinds of question, one retrieval surface.

**Intro (우측 열)**
Financial statement data is normalized and loaded into a relational database, so questions that need filtering, aggregation, sorting, and comparison resolve against structured facts. Narrative sections are handled by vector search. Hybrid search covers statements and footnotes together.

**카드 3개 (각 2줄)**

| 카드 | 1줄 | 2줄 |
|---|---|---|
| RDB | Filtering, aggregation, sorting, and comparison over normalized `financialstatement.json`. | Questions with a complete answer set — every match, not a sample. |
| Vector search | Narrative sections of the filing. | Risk factors, business description, management discussion. |
| Lucy Intelligence | Interpretation, assessment, and forward-looking context. | Layered on top of retrieved filing data, not generated in place of it. |

**대조 블록** (전체폭, 카드 아래) — 이전의 "What the data model supports" 박스를 대체

표본 질문 (mono):
> "Are there cheaper alternatives to VOO with similarly low expense ratios and comparable assets under management?"

| Similarity search | Structured retrieval |
|---|---|
| Returns passages that read like the question. | Filters, aggregates, and sorts across filings that match the conditions. |
| A near-match is indistinguishable from a match. | Completeness is a property of the query, not of the ranking. |
| One omission makes the answer wrong. | Every filing that matches is returned, not the closest few. |

보조 예시 (두 열 **아래 전체폭**, 작은 mono): Also: Show all US large-cap ETFs with expense ratios below 0.10%.

마무리: These describe what the data model supports. Scope and availability are confirmed per dataset.

*실행 버튼·입력창 없음. 경쟁사 지목 없음 — "similarity search"로만 서술.*
⚠ 좌우 대조 문구 5줄은 브리프 제공 문구다. 좌측이 일반적 경향 서술인지 확인 필요.

---

## 6. Coverage — **DARK** · "뭐가 들어 있나"

**Eyebrow** · Coverage

**H2**
Ten years of SEC filings, preprocessed at a granular level.

**전체폭 블록** (카드 짝짓기 없음)

- **FUND AND ETF FILINGS** *(우선 — 15px 라벨 + 큰 chip)*
  NPORT-P · 485APOS · 485BPOS · 497K · 497J · DSR
- **CORPORATE AND OWNERSHIP FILINGS** *(2차 — 13px 뮤트 라벨 + 작은 chip)*
  10-K · 10-Q · 8-K · 6-K · 20-F · 40-F · S-1 · S-3 · DEF 14A · 13F-HR · 13D · 13G · Forms 3, 4, 5

구분선 후 한 줄: XBRL search covers both SEC and DART.

*filing 개수·기간은 넣지 않는다. 라이브 노출 범위(열람/검색 구분) 표기는 삭제됐다 — 커버리지를 데이터셋 범위로 한 번만 진술한다.*

---

## 7. Integration — LIGHT · "우리 스택에 맞나"

**Eyebrow** · Integration

**H2**
The same retrieval, called from your own stack.

*카드 2장. 내용량이 다른 문제는 **폭을 1.5 : 1로 기울이고**(MCP 648px / API 432px) **짧은 카드를 늘리지 않는 것**(align-items:start)으로 해결했다.*

### 카드 1 — MCP
MCP connects Lucy's filing search to any MCP-capable host. `rag_context(question, thread_id?)` returns roughly 20 source chunks with scores and filing references, and the trace arrives as progress notifications while the call runs. Pass the returned `thread_id` on the next call for follow-ups.

*구분선 후, 작고 조용하게*: The MCP endpoint returns chunks only — the calling model composes the answer.

**SUPPORTED HOSTS** *(mono 텍스트 칩만 — 로고·아이콘 없음)*

| 접근 방식 | 호스트 |
|---|---|
| API key | Claude Desktop · Cursor · Cline · Codex |
| OAuth | ChatGPT — requires Developer mode and issued credentials |

그 아래: …and any other MCP-capable host.

### 카드 2 — API
Retrieve chunks and traces from your own orchestration layer, on your own schedule.
Endpoint shape and auth model [TO CONFIRM]

*의도적으로 짧은 카드다. 채우거나 MCP 카드 높이에 맞추지 않는다.*

**설정 줄** (두 카드 아래)
Register one endpoint URL and a Bearer API key. `stdio` for local clients, streamable HTTP for remote. ChatGPT connects over OAuth instead.

---

## 8. Final CTA — **DARK** · "어떻게 시작하나"

**H2**
Tell us what you need covered.

**Sub**
Access is granted per dataset. Send the markets and filing types you need and we will scope it. The playground is open if you want to check the output first.

**CTA** · Open the playground (보조, 왼쪽) / Request dataset access (주, 오른쪽)

**요청 항목 줄** *(mono, 폼 자체는 범위 밖)*
Company · Intended use · Expected volume

---

## 9. Footer — LIGHT

**Tagline** · Lucy DATA — Citation-grade filing evidence for financial AI.

| 열 | 항목 |
|---|---|
| Product | Overview · Playground · Why it works |
| Coverage | Dataset · Live forms |
| Developers | Docs · API reference · MCP server |
| Company | About · Contact |

**Bottom** · © 2026 Lucy Data · Privacy · Terms · United States (English)

---

## 이번 패스에서 사라진 것

| 항목 | 사유 |
|---|---|
| 3-panel 인터페이스 투어 섹션 (구 Verification 3분할) | 판매 기능이 없는 제품 워크스루였다. 내용은 §3 Proof로 흡수 |
| The contract 섹션 (키 대조표) | 새 순서에 없음. "chunks only" 사실은 §6 MCP 주석으로 남음 |
| Architecture 섹션 (RAG/Playground/MCP 3열) | 새 순서에 없음 |
| §9의 응답 JSON 블록 | 브리프가 명시적으로 제외 |
| Foundation · Coverage 독립 섹션 | §5 What you get으로 병합 |
| 예시 질문 2개(economic moat, mid-cap value funds) | SEC 서류에 없는 분류에 의존 |
| **Licensing 섹션 전체** | 삭제. Source of record / Delivery / Terms 문구가 페이지에서 빠졌다 |
| 피벗 문장 "So the path ships with the answer." | 세로 화살표로 대체 — 카피가 아니라 방향 표시로 전환 |
| **"Live in the playground today" 카드 전체** | 삭제. 열람/검색 범위 구분 표기가 페이지에서 빠졌다 — 커버리지를 데이터셋 범위로 한 번만 진술 |
| **"What the data model supports" 박스** | 대조 블록(유사도 vs 구조화)으로 대체 |
| Integration의 동일 크기 카드 2장 | 폭을 1.5 : 1로 기울인 카드로 대체 — 내용량 차이를 폭에 반영 |
| 호스트 로고 슬롯 5개 | 삭제 — 제3자 상표 사용 허가가 없어 mono 텍스트 칩만 남겼다 |
| What you get 섹션의 청크 이미지 | 삭제 — 서술형 청크 화면이라 "구조화 질의"를 설명하지 못했다 |

## 미확정 항목

| 항목 | 상태 |
|---|---|
| Delivery 방식 (batch / vector store / RDB export) | `[TO CONFIRM]` — 화면 노출 |
| 라이선스 조건 (재배포·모델 학습·클라이언트 산출물) | `[TO CONFIRM]` — 화면 노출 |
| API 엔드포인트 구조·인증 모델 | `[TO CONFIRM]` — 화면 노출 |
| §4 왼쪽 열 10줄 | **제가 작성한 문구 — 검토 필요** |
| 로고 워드마크 | 임시 (`Lucy DATA`) |
| 라우트 경로 (`/request-access`, `/docs`, `/company`, `/legal/*`) | 가정 |
| MCP 엔드포인트 호스트명 | **의도적으로 미출력** |

## 이미지 현황 및 요청 목록

**현재 상태**: 히어로 영상 1개 + **예약 프레임 4개**(Proof 3 · Why it works 1). Coverage · What you can ask · Integration에는 이미지가 없다(브리프 지시).

| 파일 | 위치 |
|---|---|
| `assets/hero.mp4` | Hero 전체폭 — 자동재생 루프 영상 |
| `assets/hero-3panel.png` | 위 영상의 poster (정지 첫 프레임) |
| `assets/chunk-highlight.png` | Proof 02 프레임에 재배치 — **다만 현재 파일은 세로 2:3이라 4:3 프레임에 맞지 않는다. 4:3 컷 필요** |

**요청하면 좋은 이미지 (우선순위 순)**

| 순위 | 필요한 화면 | 들어갈 자리 | 증명하는 것 |
|---|---|---|---|
| 1 | **Companies 열람 화면** — 서류 항목별 필터, 텍스트/표 단위 전환 | 별도 섹션 신설 검토 — Coverage는 브리프가 이미지 없음을 지정 | "10년치를 실제로 뒤질 수 있다" |
| 2 | **MCP 클라이언트 호출 화면** (Claude Desktop 등에서 Lucy 호출) | Integration | "실제로 붙는다" |
| 3 | **전처리 결과물** — 표가 JSON으로 구조화된 화면, 또는 XBRL 태그가 붙은 숫자 | Why it works, 10행 표 아래 | 10줄 주장이 눈으로 확인됨 |
| 4 | judge-metrics | Proof "The score" 열 또는 별도 라이트 밴드 | 실시간 채점 |

**이미지를 넣지 않는 섹션**: The problem(다크, 4줄 긴장 유지) · Final CTA(전환 구간, 시선 분산 금지).
