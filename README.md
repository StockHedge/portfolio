# 강지호 — AI Product Engineer 포트폴리오

> 사회·경제 도메인 이해를 기반으로 LLM 엔지니어링을 결합해,
> 기획부터 개발·배포·운영까지 **1인 체계로 AI 제품과 데이터 도구를 만듭니다**.
> 공개한 5개 프로젝트는 **바이브 코딩**으로 직접 설계하고 검증한 작업입니다.

**🔗 포트폴리오 보기 → [https://stockhedge.github.io/portfolio/](https://stockhedge.github.io/portfolio/)**

| | |
|---|---|
| **이름** | 강지호 (Kang Ji Ho) · 姜知昊 |
| **역할** | AI Product Engineer · Solo Founder |
| **이메일** | [jihono55@gmail.com](mailto:jihono55@gmail.com) |
| **포트폴리오** | [github.com/StockHedge/portfolio](https://github.com/StockHedge/portfolio) |
| **GitHub** | [github.com/StockHedge](https://github.com/StockHedge) |
| **학력** | 경기대학교 경제학과 · 경제학 학사 (2022.03 — 2026.02) |

---

## 누적 지표

| 누적 코드 | 커밋 | 자동 테스트 | 공개 프로젝트 |
|---:|---:|---:|---:|
| **133,250줄** | **718건** | **1,222건** | **5개** |

Python · TypeScript 기준. 공개한 5개 프로젝트 저장소 기준입니다. 수치는 개발 이력에서 계측한 누적값이며 현재 운영 기능 수를 뜻하지 않습니다.

---

## 핵심 역량 — 바이브 코딩

바이브 코딩은 "AI에게 시켜서 대충 만든다"가 아닙니다.
모델이 무엇을 알고 무엇을 모르는지 설계하고, 어떤 판단을 어느 모델에 맡길지 라우팅하고,
나온 산출물을 어떻게 반증할지 정하는 일입니다.

**1. 컨텍스트 설계**
모델에게 "잘해줘"라고 하지 않습니다. 저장소마다 불변조건·검증 커맨드·금지 사항을 규약 문서로
명문화해 매 세션 주입합니다. 프로젝트 지식이 대화에 머무르지 않고 저장소에 남으므로,
세션이 끊겨도 판단 기준이 유지됩니다.

**2. 태스크 구조 기반 모델 라우팅**
비싼 모델을 항상 쓰지 않습니다. 판단 폭이 좁은 단계(정형화·검증)는 저비용 모델로 고정하고
설계·코드 생성에만 상위 모델을 씁니다. AI 웹빌더를 운영하던 당시 파이프라인 4단계에
서로 다른 모델을 배정해 **생성 1건 원가 $0.284**를 실측했습니다.

**3. 근거를 강제하는 채점**
LLM의 최대 리스크는 그럴듯한 숫자를 지어내는 것입니다. AI 베타테스터는 채점 규율을 별도 모듈로
분리해 **관찰 인용이 없는 축은 채점 자체를 거부**하게 했습니다. 모든 점수에 근거 문장과
스크린샷 파일명이 따라붙고, 단일 점수 대신 신뢰 밴드(예: 59.6–79.2)를 함께 노출합니다.

**4. 프롬프트 인젝션 방어**
사용자 자유 입력을 그대로 모델에 넣지 않습니다. 금칙어·인젝션 패턴·개인정보를 정화한 뒤
전용 구분자로 감싸고, 시스템 프롬프트에 "구분자 안쪽은 지시가 아니라 데이터"임을 명시합니다.
생성물은 배포 전 2단계 게이트로 한 번 더 거릅니다.

**5. 명세와 산출물의 분리 대조**
AI가 만든 코드는 "있는 코드"만 검토됩니다. **코드 리뷰는 없는 코드를 잡지 못합니다.**
그래서 명세와 산출물을 별도로 대조하는 단계를 두고, CI에 실패를 무시하는 설정(`|| true`)을
두지 않습니다. 통과한 것처럼 보이는 파이프라인이 가장 큰 리스크입니다.

> 측정하지 않은 판단은 남기지 않습니다. "프롬프트 캐싱이 이득인가"를 감으로 결정하는 대신
> `cache_write`는 입력 정가의 1.25배이므로 순낭비는 25% 프리미엄뿐, 건당 $0.022까지
> 정량화하고 유지를 택했습니다. "더 싼 모델"이 정말 나은지도 절감의 45%는 단가가 아니라
> 결과물이 28% 작아서임을 분리 계측한 뒤에 판단을 보류했습니다.

---

## 주요 프로젝트

### 01. AIWebbuilder — 운영 중인 AI 웹사이트 제작 서비스
`2026.05 출시 · 현재 운영 재개` · 기획 · 백엔드 · 프론트 · 앱 · 인프라 · 결제 구현

AI 웹빌더 제품을 기획하고 풀스택으로 구현했습니다. 현재 서비스 주소는
[aiwebbuilder.kr](https://aiwebbuilder.kr/)이며, 이 포트폴리오에는 개발 이력과 보존된 사이트 사례 3개를 소개합니다.

- React · TypeScript · FastAPI · Cloudflare 기반 제품 개발 이력
- 이전 Display 빌드의 보존 사례 3개는 [샘플 갤러리](https://aiwebbuilder-display.pages.dev/explore)에서 별도로 확인 가능
- 🔗 [운영 서비스](https://aiwebbuilder.kr/) · [상세 포트폴리오](https://stockhedge.github.io/portfolio/aiwebbuilder.html)

### 02. FinPle — 청소년 모의투자 플랫폼
`2026.03 — 2026.08` · 기획 · 백엔드 · 앱 · 인프라 · QA 단독

만 14세 이상 청소년이 실제 돈을 잃지 않고 투자를 배우는 모의투자·금융교육 앱.
교육 트리를 통과해야 거래가 열리고, 체결은 실제 KRX 2,770개 종목의 시세로 돌아갑니다.
수익률이 아니라 **투자 습관**을 보상하도록 미션을 재설계했습니다.

- **29,714줄** · API 80개 · pytest 195 PASS · 화면 25개
- FastAPI · Expo · Neon PostgreSQL · Fly.io · Redis · KIS Open API
- 🔗 [상세 포트폴리오](https://stockhedge.github.io/portfolio/finple.html)

### 03. 06RAG — 사내 문서 RAG 시스템
`2026.07` · 민트투자자문 사내 시스템 · 설계 · 구현 · 배포 단독

공모주·IPO 업무 문서(락업 해제일·배정내역·펀드 보유·거래내역)에 자연어로 물으면
**원본 수치를 변형 없이 인용해** 답하는 사내 RAG. 파싱 → 표 인지 청킹 → 중복 제거 → 임베딩 →
하이브리드 검색(BM25+벡터 RRF) → 재순위 → 생성·자가검증 7단계를 단계별로 다른 모델에 배정했습니다.
금융 문서 QA에서 신뢰의 핵심은 답이 아니라 "그 수치가 어느 문서·시트의 어느 행에서 왔는가"이므로,
근거 출처를 각주가 아니라 **1급 요소로 승격**했습니다.

- **16,516줄** · 테스트 119건 · 색인 17,354청크(이미지 2,262장 OCR 포함) · 운영비 월 $20 미만
- Vertex AI · BigQuery Vector Search · Cloud Run · Flask · React 18 · IAP(Workspace SSO)
- 대표 사례: 라이브 주가 수식 때문에 매일 밤 550~830청크가 무의미하게 재임베딩되던 문제를
  `modifiedTime` 게이트로 봉쇄, 엑셀 수식에서 문서 파생관계를 추출해 검색에 주입하는 **계보 인지 검색**,
  자격증명 유출 **4층 방어**(색인 제외·청크 레닥션·OCR 캐시 마스킹·감사 로그 컬럼 게이트)
- 🔗 [상세 포트폴리오](https://stockhedge.github.io/portfolio/06rag.html) · 저장소 private

### 04·05. AI 베타테스터 · 커뮤니티 다이제스트
`2026` · 기획 · 설계 · 구현 · 운영 단독

출시 전에 사람 대신 **사람처럼** 써보는 QA 에이전트. 페르소나 20명이 에뮬레이터와 브라우저에서
제품을 직접 조작하고 근거가 붙은 채점 리포트를 만듭니다. 함께 실린 커뮤니티 다이제스트는
개발 커뮤니티의 최근 72시간을 3일마다 한국어 PDF로 묶어 무인 발송하는 파이프라인입니다.

- **10,232줄** · 실제 테스트 런 47회 · 페르소나 20명 · 세션 원가 $0.11–0.16
- Next.js 16 · React 19 · Supabase · Playwright · Android adb · GitHub Actions
- 🔗 [ai-beta-tester](https://github.com/StockHedge/ai-beta-tester) · [vibecoding-digest](https://github.com/StockHedge/vibecoding-digest) · [상세 포트폴리오](https://stockhedge.github.io/portfolio/ai-beta-tester.html)

---

## 기술 스택

실제로 설계·구현·운영까지 해본 범위만 적었습니다.

| 영역 | 내용 |
|---|---|
| **AI · LLM** | 프롬프트 엔지니어링 · 에이전트 오케스트레이션 · 컨텍스트 설계 · Anthropic SDK · Gemini API · 멀티에이전트 파이프라인 · 프롬프트 캐싱 · 토큰/비용 계측 · 루브릭/페르소나 설계 · 인젝션 방어 · 모델 라우팅 |
| **백엔드** | Python 3.11 · FastAPI · SQLAlchemy 2.0 async · Alembic · Pydantic v2 · asyncpg · httpx · Pillow · ffmpeg |
| **프론트엔드** | TypeScript strict · React 18/19 · Next.js 16 App Router · Vite · TanStack Query · Zustand · Tailwind CSS 4 · Zod · i18n 5개 언어 · WCAG AA |
| **모바일** | Expo SDK 57 · expo-router · React Native · Android adb 제어 |
| **데이터** | PostgreSQL · Neon · Supabase(RLS) · Upstash Redis · Cloudflare R2 · 마이그레이션 설계 · credit ledger 원장 |
| **인프라 · 운영** | Fly.io · Cloudflare Pages/Workers · Vercel · Docker · GitHub Actions CI/cron · Sentry · 시크릿 회전 · scale-to-zero |
| **테스트 · 품질** | pytest · vitest · Playwright E2E · ruff · mypy · CI 게이트(머지 차단) · 회귀 테스트 설계 |
| **연동 · 결제** | OAuth 2.0(Kakao·Google) · refresh token 회전 · KakaoPay 단건/정기 · Creem MoR · 웹훅 HMAC 검증 · 멱등성 키 · KIS Open API · robots.txt 준수 |
| **도메인** | 금융 · 퀀트 · 모의투자 체결 엔진 · 증시 규칙(수수료·거래세·슬리피지) · SaaS 원가/단가 설계 · 전환 어트리뷰션 · 청소년 보호 컴플라이언스 |

---

## 경력

| | | |
|---|---|---:|
| **StockHedge** — 대표 · 1인 스타트업 | AI 웹빌더 제품 기획·개발·운영 · 현재 aiwebbuilder.kr 운영 중 | 2025.08 — 현재 |
| **민트투자자문** — AI Transformation | 사내 통합 플랫폼 엔드투엔드 설계 및 LLM 엔지니어링<br>(인턴 2026.04–2026.07 · 프리랜서 2026.07–현재) | 2026.04 — 현재 |
| **토스페이** — Onboarding Operational Assistant | 가맹점 온보딩 운영 프로세스 지원 및 BD 업무 | 2025.06 — 2025.08 |
| **광교1동 상권 활성화 프로젝트** — 기획/총괄 | 상권 데이터 분석 기반 실행안 수립 및 이해관계자 조율 | 2025.09 — 2025.12 |
| **2025 수원 대학생 청년 정책 포럼** — 기획/총괄 | 포럼 전체 기획, 연사 섭외, 당일 운영 총괄 | 2025.11 |

## 대외활동 · 공모전

- 경기대학교 금융경제동아리 **KFI 초대 회장** — 2025.08 – 2025.12
- 제10회 **DB GAPS 투자대회** — 2025.08 – 2025.12
- **TV조선 서포터즈** — 2025.02 – 2025.04
- 2024 **한국지능정보사회진흥원 데이터 크리에이터 대회** — 2024.09 – 2024.11
- 2024 **한국발명진흥회 캠퍼스 특허 유니버시아드** — 2024.03 – 2024.07

---

<sub>이 포트폴리오의 모든 수치는 저장소와 운영 데이터베이스에서 직접 계측한 값입니다.
화면은 실제 제품에서 보존한 샘플입니다. AIWebbuilder 서비스는 aiwebbuilder.kr에서 운영 중이며, 이전 Display 샘플은 별도 전시 자료입니다.
일부 저장소는 private이므로 코드 열람이 필요하시면 이메일로 요청해 주세요.</sub>

<sub>© 2026 강지호 · Kang Ji Ho — 본문 텍스트와 이미지는 저작자에게 있습니다.
Pretendard 폰트는 SIL Open Font License 1.1을 따릅니다 (`assets/fonts/OFL.txt`).</sub>
