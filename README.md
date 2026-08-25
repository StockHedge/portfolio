# 강지호 — AI Product Engineer 포트폴리오

> 사회·경제 도메인 이해를 기반으로 LLM 엔지니어링을 결합해,
> 기획부터 개발·배포·운영까지 **1인 체계로 SaaS 제품을 만들고 운영**합니다.
> 아래 5개 제품은 전부 **바이브 코딩**으로 만들었고, 지금도 실제로 돌아갑니다.

**🔗 포트폴리오 보기 → [https://stockhedge.github.io/portfolio/](https://stockhedge.github.io/portfolio/)**

| | |
|---|---|
| **이름** | 강지호 (Kang Ji Ho) · 姜知昊 |
| **역할** | AI Product Engineer · Solo Founder |
| **이메일** | [jihono55@gmail.com](mailto:jihono55@gmail.com) |
| **서비스** | [aiwebbuilder.kr](https://aiwebbuilder.kr) |
| **GitHub** | [github.com/StockHedge](https://github.com/StockHedge) |
| **학력** | 경기대학교 경제학과 · 경제학 학사 (2022.03 — 2026.02) |

---

## 누적 지표

| 누적 코드 | 커밋 | 자동 테스트 | 운영 중 제품 |
|---:|---:|---:|---:|
| **171,596줄** | **870건** | **2,055건** | **5개** |

Python · TypeScript 기준. 5개 저장소 합계이며, 모든 수치는 저장소와 운영 데이터베이스에서 직접 계측한 값입니다.

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
설계·코드 생성에만 상위 모델을 씁니다. AI 웹빌더 파이프라인은 4단계를 각각 다른 모델에 배정해
**생성 1건 원가 $0.284**로 운영합니다.

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

### 01. AIWebbuilder — AI 웹빌딩 SaaS
`2026.05 — 운영 중` · 기획 · 백엔드 · 프론트 · 앱 · 인프라 · 결제 · 운영 단독

한국 소상공인이 업종별 폼을 채우면 4단계 멀티에이전트 파이프라인이 단일 HTML을 생성하고
Cloudflare에 실제 URL로 배포합니다. 미리보기는 무료, 배포 시점에 과금하는 try-before-pay 구조입니다.

- **76,788줄** · 테스트 908건 · 커밋 471 · 생성 1건 원가 $0.284
- FastAPI · React 18 · Expo · Neon PostgreSQL · Cloudflare · Fly.io · KakaoPay · Claude · Gemini
- 🔗 [aiwebbuilder.kr](https://aiwebbuilder.kr) · [상세 포트폴리오](https://stockhedge.github.io/portfolio/aiwebbuilder.html)

### 02. FinPle — 청소년 모의투자 플랫폼
`2026.03 — 2026.08` · 기획 · 백엔드 · 앱 · 인프라 · QA 단독

만 14세 이상 청소년이 실제 돈을 잃지 않고 투자를 배우는 모의투자·금융교육 앱.
교육 트리를 통과해야 거래가 열리고, 체결은 실제 KRX 2,770개 종목의 시세로 돌아갑니다.
수익률이 아니라 **투자 습관**을 보상하도록 미션을 재설계했습니다.

- **29,714줄** · API 80개 · pytest 195 PASS · 화면 25개
- FastAPI · Expo · Neon PostgreSQL · Fly.io · Redis · KIS Open API
- 🔗 [상세 포트폴리오](https://stockhedge.github.io/portfolio/finple.html)

### 03. 마케팅 자동화 허브
`2026.08 — 운영 중` · 설계 · 구현 · 배포 · 운영 전 구간

두 SaaS가 만드는 마케팅 활동을 수집 → 지능 → 게이트 → 실행 → 피드백 5계층으로 자동화하고
하나의 대시보드에서 관제합니다. 북극성 지표는 좋아요가 아니라 **가입·결제 전환**이며,
광고 예산 상한은 설정으로도 못 푸는 코드 상수로 못 박았습니다.

- **54,862줄** · 테스트 952건 · 배치 잡 17개 · 22일간 커밋 177
- FastAPI · React 18 · 13-state machine · Bandit · UTM 어트리뷰션 · GitHub Actions
- 🔗 [상세 포트폴리오](https://stockhedge.github.io/portfolio/marketing-hub.html)

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
| **StockHedge** — 대표 · 1인 스타트업 | AI 웹빌더 SaaS 기획·개발·배포·운영 단독 수행 | 2025.08 — 현재 |
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

## 이 저장소에 대하여

원래 프로젝트마다 따로 존재하던 포트폴리오 4건(HTML·PDF)을 **하나의 사이트로 통합**한 것입니다.

```
portfolio/
├─ index.html              프로필 (이 README의 웹 버전)
├─ aiwebbuilder.html       AI 웹빌딩 SaaS
├─ finple.html             청소년 모의투자 플랫폼
├─ marketing-hub.html      마케팅 자동화 허브
├─ ai-beta-tester.html     AI 베타테스터 · 커뮤니티 다이제스트
├─ assets/
│  ├─ css/shell.css        공유 셸 — 폰트 · 상단 네비 · 하단 페이저
│  ├─ fonts/               Pretendard 통합 서브셋 (400/600/700/800)
│  └─ …                    각 프로젝트 스크린샷
└─ pdf/                    원본 PDF + 통합본 (25p)
```

**통합하면서 정리한 것**

- **폰트 일원화** — 네 문서가 Pretendard를 쓰면서도 로딩 방식이 제각각이었습니다.
  한 곳은 base64 임베드 woff2(400/600/800), 세 곳은 외부 `.otf`(400/600/700)라
  제목 굵기가 페이지마다 달랐습니다. 네 굵기를 **동일한 코드포인트 집합(3,735자)**으로
  서브셋해 woff2로 통일했습니다. 굵기별 커버리지가 다르면 특정 글자만 fallback 폰트로 튀기 때문입니다.
  → 원본 5.7MB에서 **0.93MB (−84%)**
- **base64 이미지 외부화** — FinPle 페이지가 이미지를 전부 인라인으로 품고 있어 1,553KB였습니다.
  중복을 md5로 접어 6개 파일로 분리 → **45KB (−97%)**. 이미지가 병렬로 받아지고
  페이지 간 캐시가 공유됩니다.
- **공유 셸** — 각 페이지의 CSS는 그대로 두고(디자인 언어는 그 프로젝트의 자산입니다),
  `pf-` 접두를 쓰는 상단 네비와 하단 페이저만 얹었습니다. 전역으로 선언하는 것은
  `@font-face`와 `--pf-*` 커스텀 프로퍼티뿐이라 기존 스타일과 충돌하지 않습니다.
- **통합 PDF** — 원본 4건이 HTML을 한 장에 통째로 내보낸 초장축 페이지(최대 1440×9153pt)라
  이력서와 페이지 크기가 뒤섞였습니다. 벡터를 유지한 채 A4로 분할해 **25페이지 단일 PDF**로
  묶었습니다. 텍스트 선택·검색이 그대로 살아 있습니다.

**정적 사이트**입니다. 빌드 도구도 의존성도 없습니다. 로컬에서 보려면:

```bash
python -m http.server 8000
# http://localhost:8000
```

---

<sub>이 포트폴리오의 모든 수치는 저장소와 운영 데이터베이스에서 직접 계측한 값입니다.
화면은 운영 중인 서비스의 실제 캡처이며, 가입자 개인정보가 보이는 영역은 가렸습니다.
일부 저장소는 private이므로 코드 열람이 필요하시면 이메일로 요청해 주세요.</sub>

<sub>© 2026 강지호 · Kang Ji Ho — 본문 텍스트와 이미지는 저작자에게 있습니다.
Pretendard 폰트는 SIL Open Font License 1.1을 따릅니다 (`assets/fonts/OFL.txt`).</sub>
