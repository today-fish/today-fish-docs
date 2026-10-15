# 문서 일관성 검사 이력

## 2026-10-07 02:23 KST

### 검사 범위

Baseline: 없음 → `44fff1ee81fa2437d259f5bd474cf71ee8152106`

최초 검사로 다음 범위를 전체 확인했다.

* Repository root의 README와 INDEX
* `MVP/product/decisions/`의 PD-001~PD-012
* `MVP/research/user/`의 UR-001
* 파일명, 문서 ID, H1/H2, 상태, 용어, 내부 링크
* MVP 범위, Price Insight, 데이터 신뢰 및 AI 역할의 문서 간 정합성

검사 시작 시 Git 변경사항:

* 문서 변경 없음
* `.codex/skills/docs-consistency-check/SKILL.md` 미추적

### 검사 결과

* 파일명 규칙: 자동 수정
* 디렉토리 구조: 정상
* 문서 구조: 비차단 이슈 확인
* 프로젝트 용어: 자동 수정
* 내부 링크: 정상
* 문서 정합성: 사용자 결정 후 반영
* INDEX.md: 수정
* README.md: 수정

### 수행한 수정

* `PD-010-data-trust-policy.md`를 `PD-010-데이터-신뢰-정책.md`로 변경
* `PD-11-ai-role.md`를 `PD-011-AI-역할-정의.md`로 변경
* `PD-012-mvp-scope.md`를 `PD-012-MVP-범위.md`로 변경
* PD-005에서 MVP 기본 품목별 채팅과 Phase 3 참여형 커뮤니티의 범위를 구분
* PD-005 Follow-up에 PD-012 연결 추가
* PD-010의 중복 heading을 `정책이 지향하는 사용자 경험`으로 변경
* `타겟` 표기를 `타깃`으로 통일
* INDEX에 PD-010~PD-012를 추가하고 개정된 PD-008 목차를 동기화
* README에 PD-010~PD-012와 검사 이력 링크를 추가

### 사용자 검토

발견된 문제:

* PD-005는 참여형 커뮤니티를 Phase 3으로 정의하지만 PD-012는 실시간 채팅을 MVP 핵심 기능으로 정의함

사용자 결정:

* PD-012를 최신 MVP 기준으로 사용
* MVP에서는 최소 품목별 채팅을 제공
* Phase 3에서는 사용자 역할, 인증, Moderation과 참여자별 정보 구조를 포함한 참여형 커뮤니티로 확장

반영 결과:

* PD-005에 두 단계의 범위 차이를 명시하고 PD-012와 연결함

### 확인된 문제

다음 항목은 제품 결정 충돌을 만들지 않는 비차단 정리 과제로 남겼다.

* PD-001과 UR-001에 문서 전체 Status가 없음
* PD-003 이후 다수 문서가 번호 섹션에 H1을 사용하여 한 파일에 H1이 여러 개 존재함
* PD-005의 전년 동기 비교가 Phase 1 가격 정보와 Phase 2 주요 기능에 함께 나타나 단계별 범위가 불명확함
* 작성일, 수정일, Owner가 없어 Accepted 문서 간 시간적 우선순위를 문서만으로 판별하기 어려움
* API, ERD, Data Flow, NFR을 구현 수준으로 정의한 Tech Spec 또는 ADR이 아직 없음

### 검사 사용량

* 이번 검사 사용량: 확인 불가
* 잔여 사용량: 확인 불가

### 검사 상태

`완료`

### 다음 검사 기준

`44fff1ee81fa2437d259f5bd474cf71ee8152106`

현재 검사 수정사항을 커밋한 뒤 다음 검사에서는 해당 커밋을 새로운 baseline으로 갱신한다.

## 2026-10-07 02:38 KST

### 검사 범위

Baseline: `44fff1ee81fa2437d259f5bd474cf71ee8152106` → `d3e4da390fbba27383fdc14a366217b8e991a231`

직전 검사 결과가 반영된 commit과 현재 working tree의 검사 skill 변경을 증분 검사했다.

### 변경 감지

* 추가: 2개
* 수정: 5개
* 삭제: 0개
* 이동/파일명 변경: 3개
* Working tree 수정: 1개

### 검사 대상

* A `.codex/skills/docs-consistency-check/SKILL.md`
* A `DOCUMENT-CHECK-HISTORY.md`
* M `INDEX.md`
* M `MVP/product/decisions/PD-002-핵심-타깃-사용자.md`
* M `MVP/product/decisions/PD-005-서비스-성장-전략.md`
* R `PD-010-data-trust-policy.md` → `PD-010-데이터-신뢰-정책.md`
* R `PD-11-ai-role.md` → `PD-011-AI-역할-정의.md`
* R `PD-012-mvp-scope.md` → `PD-012-MVP-범위.md`
* M `MVP/research/user/UR-001-제철-음식-소비-트렌드-리서치.md`
* M `README.md`
* Working tree M `.codex/skills/docs-consistency-check/SKILL.md`

### 검사 결과

* 파일명: 정상
* 디렉토리 구조: 정상
* 문서 구조: 정상; 이전 검사에서 기록한 비차단 과제는 유지
* 프로젝트 용어: 정상
* 링크: 정상
* 문서 정합성: 정상
* INDEX.md: 정상
* README.md: 정상

### 수행한 수정

* 검사 이력에 현재 증분 검사 결과와 새 baseline을 추가

### 사용자 검토

* 없음

### 사용량

* 이번 검사 token 사용량: 확인 불가
* 잔여 token: 확인 불가
* Codex usage/quota: 확인 불가

### 검사 상태

`완료`

### 다음 검사 기준

`d3e4da390fbba27383fdc14a366217b8e991a231`

## 2026-10-07 04:14 KST

### 검사 범위

Baseline: `d3e4da390fbba27383fdc14a366217b8e991a231` → `0f7f3b69167a627328d5f7deeac7069bd9737334`

Baseline 이후 관리 파일 변경과 working tree에 추가된 `MVP/poc/` 문서 2개를 증분 검사했다. PoC 결과와 직접 관련된 PD-009, PD-010, PD-012만 정합성 비교 대상으로 확인했다.

### 변경 감지

* 추가: 2개
* 수정: 4개
* 삭제: 1개
* 이동/파일명 변경: 0개

### 검사 대상

* D `.codex/skills/docs-consistency-check/SKILL.md` — Git 추적에서 제외되고 로컬 파일로 유지
* M `.gitignore`
* M `DOCUMENT-CHECK-HISTORY.md`
* A `MVP/poc/POC-001-aT-공영도매시장-API-데이터.md`
* A `MVP/poc/POC-002-외부-가격-데이터-검증-체크리스트.md`
* M `INDEX.md`
* M `README.md`

### 검사 결과

* 파일명: 자동 수정
* 디렉토리 구조: 정상
* 문서 구조: 자동 수정
* 프로젝트 용어: 정상
* 링크: 자동 수정
* 문서 정합성: 정상
* INDEX.md: 수정
* README.md: 수정

### 수행한 수정

* `POC-001-at-wholesale-seafood-data.md`를 `POC-001-aT-공영도매시장-API-데이터.md`로 변경
* `POC-CHECKLIST.md`를 `POC-002-외부-가격-데이터-검증-체크리스트.md`로 변경
* 두 PoC 문서의 H1에 문서 ID를 반영
* POC-001과 POC-002에 PD-009, PD-010, PD-012 및 상호 참조 링크 추가
* INDEX에 `MVP/poc/` 구조, 문서 역할, 주요 heading과 관계 추가
* README에 `MVP/poc/` 파일 목차와 탐색 순서 추가

### 사용자 검토

* 없음

### 사용량

* 이번 검사 token 사용량: 확인 불가
* 잔여 token: 확인 불가
* Codex usage/quota: 확인 불가

### 검사 상태

`완료`

### 다음 검사 기준

`0f7f3b69167a627328d5f7deeac7069bd9737334`

현재 검사 수정사항을 커밋한 뒤 다음 검사에서는 해당 커밋을 새로운 baseline으로 갱신한다.

## 2026-10-14 01:40 KST

### 검사 범위

Baseline: `0f7f3b69167a627328d5f7deeac7069bd9737334` → `72037144813a1a41aa1ca7c6c20f45f2d9bc93e2`

Baseline 이후 커밋된 직전 검사 결과와 working tree에 추가된 `POC-003` 문서를 증분 검사했다. 신규 PoC의 제품 결정 정합성을 판단하기 위해 PD-009, PD-010, PD-012, POC-001, POC-002를 관련 문서로 확인했다.

### 변경 감지

* 추가: 3개
* 수정: 3개
* 삭제: 0개
* 이동/파일명 변경: 0개

### 검사 대상

* M `DOCUMENT-CHECK-HISTORY.md`
* M `INDEX.md`
* A `MVP/poc/POC-001-aT-공영도매시장-API-데이터.md`
* A `MVP/poc/POC-002-외부-가격-데이터-검증-체크리스트.md`
* A `MVP/poc/POC-003-수산물 가격 데이터 연계.md` — working tree
* M `README.md`

### 검사 결과

* 파일명: 자동 수정 — `POC-003-수산물-가격-데이터-연계.md`로 정리
* 디렉토리 구조: 정상
* 문서 구조: 자동 수정 — H1과 문서 역할 정리
* 프로젝트 용어: 정상
* 링크: 자동 수정 — 관련 PD·PoC 내부 링크 추가
* 문서 정합성: 정상 — 사용자 결정 반영
* INDEX.md: 수정
* README.md: 수정

### 수행한 수정

* `POC-003-수산물 가격 데이터 연계.md`를 `POC-003-수산물-가격-데이터-연계.md`로 변경
* POC-003의 H1을 문서 ID 형식에 맞게 정리
* POC-003에서 갈치·고등어·전복을 최종 제공 품목이 아닌 개발 검증 품목 및 최초 제공 후보로 구분
* POC-003의 원산지·상품 상태 분류를 확정값이 아닌 PoC 추정 규칙으로 명시
* POC-003에 관련 PD·PoC 내부 링크 추가
* `PD-013 가격 데이터 PoC 적용 원칙` 추가
* PD-013에서 PoC와 제품 결정의 역할, 대표가격 집계, 추정 분류, 결측값 적용 원칙 정의
* INDEX에 PD-013과 POC-003의 역할, 주요 섹션, 문서 관계 추가
* README에 PD-013과 POC-003 링크 및 탐색 순서 반영

### 사용자 검토

발견된 문제:

* POC-003은 갈치·고등어·전복을 MVP 최초 제공 품목으로 최종 선정하지만, PD-012의 품목 선정 기준 중 생산·출하 데이터, 환경·시장 이슈, 뉴스·공식자료 확보 가능성을 모두 검증했다는 근거가 없다. 정산정보도 일부 날짜와 시장만 검증했다고 명시한다.
* POC-003은 같은 날짜의 여러 시장 가격을 단순 평균한다고 결정하지만, PD-009는 시장 편차가 비정상적으로 큰 경우 단순 평균을 바로 대표가격으로 사용하지 않고 데이터 품질을 검증하도록 정한다.
* POC-003은 KAMIS 품목명에 `수입` 또는 `냉동` 표시가 없으면 국산 생물로 간주한다. 이 분류를 대표 가격에 적용할지, 추정 분류임을 사용자에게 표시할지는 기존 Accepted 문서에 확정되어 있지 않다.

가능한 처리 방향:

* POC-003을 최신 구현 근거로 채택하고, PD-009와 PD-012에 품목·집계·분류 정책을 후속 결정으로 반영한다.
* 기존 Accepted 결정을 유지하고, POC-003의 품목 선정은 잠정 후보로 낮추며 미검증 기준과 이상치 처리 검증을 완료한 뒤 최종 확정한다.
* 검증된 가격 차트 구현 가능성과 아직 미검증인 품목 확정·분류 정책을 분리하고, 별도 후속 PD에서 제품 결정을 내린다.

사용자 결정:

* 검증된 가격 차트 구현 가능성과 아직 미검증인 품목 확정·분류 정책을 분리
* 별도 후속 PD에서 제품 적용 원칙을 결정

반영 결과:

* PD-013을 Accepted 문서로 추가
* POC-003을 기술 검증 근거 문서로 정리하고 기존 Accepted 결정을 Source of Truth로 유지
* 갈치·고등어·전복은 추가 검증 전까지 최초 제공 품목 후보로 관리

### 사용량

* 이번 검사 token 사용량: 확인 불가
* 잔여 token: 확인 불가
* Codex usage/quota: 확인 불가

### 검사 상태

`완료`

### 다음 검사 기준

`72037144813a1a41aa1ca7c6c20f45f2d9bc93e2`

## 2026-10-14 02:51 KST

### 검사 범위

Baseline: `72037144813a1a41aa1ca7c6c20f45f2d9bc93e2` → `5e6f58cdd80bfe02f22b530e83e95e56c8308900`

Baseline 이후 커밋된 직전 검사 결과와 working tree에 추가된 PRD 1개 및 기능 명세 4개를 증분 검사했다. MVP 범위 정합성을 판단하기 위해 PD-012와 PD-013을 관련 문서로 확인했다.

### 변경 감지

* 추가: 7개
* 수정: 3개
* 삭제: 0개
* 이동/파일명 변경: 0개

### 검사 대상

* M `DOCUMENT-CHECK-HISTORY.md`
* M `INDEX.md`
* A `MVP/poc/POC-003-수산물-가격-데이터-연계.md`
* A `MVP/product/decisions/PD-013-가격-데이터-PoC-적용-원칙.md`
* M `README.md`
* A `MVP/product/PRD-001-MVP-제품-요구사항.md` — working tree
* A `MVP/product/features/PF-001-홈-화면.md` — working tree
* A `MVP/product/features/PF-002-수산물-가격-차트.md` — working tree
* A `MVP/product/features/PF-003-Price-Insight.md` — working tree
* A `MVP/product/features/PF-004-최근-이슈.md` — working tree

### 검사 결과

* 파일명: 정상
* 디렉토리 구조: 정상
* 문서 구조: 자동 수정 — PRD·PF의 H1 문서 ID 표기 통일
* 프로젝트 용어: 정상
* 링크: 자동 수정 — 미작성 PP-001~003 링크 11건을 작성 예정 참조로 변경
* 문서 정합성: 정상 — 사용자 결정 반영
* INDEX.md: 수정
* README.md: 수정

### 수행한 수정

* PD-012에서 회원가입·로그인을 제외하고 인증 없는 실시간 채팅 정책 반영
* PD-012의 초기 지원 품목을 갈치·고등어·전복 3종으로 확정
* PD-013과 POC-003에 초기 제공 품목 검증 완료 및 확정 결과 반영
* PRD-001에 초기 3종 검색과 품목별 실시간 채팅 요구사항·인수 조건·출시 기준 추가
* `PF-005 실시간 채팅` 문서 추가
* PF-001에 초기 지원 품목 검색 요구사항 추가
* PF-001~004에 PF-005 상호 참조 추가
* PRD·PF의 H1 문서 ID 형식을 통일하고 기존 문서 미검토 안내를 정합성 검토 완료 상태로 변경
* 존재하지 않는 PP-001~003 상대 링크를 작성 예정 참조로 변경
* INDEX에 PRD·PF 디렉토리, 문서 역할, 주요 섹션과 관계 추가
* README에 PRD-001과 PF-001~005 링크 및 탐색 순서 추가

### 사용자 검토

발견된 문제:

* PRD-001은 MVP 범위를 홈·가격 차트·Price Insight·최근 이슈 중심으로 정의하고 전체 수산물 검색을 후속 범위로 두지만, Accepted PD-012는 수산물 검색을 Must Have로 정의한다.
* PRD-001은 인증 없는 열람만 포함하고 회원가입·로그인을 제외하지만, PD-012는 최소 회원 기능과 회원/로그인을 Must Have로 정의한다.
* PRD-001과 PF-001~004는 실시간 채팅을 MVP 범위와 출시 기준에서 누락하지만, PD-012는 품목별 실시간 채팅을 MVP 핵심 경험 및 Must Have로 정의한다.
* PRD-001과 PF 문서는 갈치·고등어·전복을 초기 제공 품목으로 확정해 서술하지만, PD-013은 추가 기준 검증 전까지 최초 제공 품목 후보로 표현하도록 정한다.
* 신규 문서는 기존 PD·POC 원문을 아직 검토하지 않았다고 표시하지만 이번 검사에서 해당 원문을 직접 확인했으므로 상태 설명과 추적 링크를 갱신해야 한다.

가능한 처리 방향:

* 기존 Accepted 결정을 유지하고 PRD·PF에 검색, 최소 회원 기능, 품목별 실시간 채팅을 포함하며 세 품목을 후보로 정리한다.
* 신규 PRD를 최신 MVP 범위로 채택하고 검색·회원·채팅 제외와 세 품목 확정을 후속 PD로 승인한 뒤 PD-012·PD-013을 개정한다.
* 가격 정보 MVP와 커뮤니티 확장 단계를 분리하는 새 제품 결정을 작성하고, 각 단계에 맞춰 PRD·PF 범위를 재구성한다.

사용자 결정:

* 회원가입·로그인은 MVP에서 제외
* PRD와 PF에 실시간 채팅 포함
* 갈치·고등어·전복의 초기 제공 품목 검증 완료 및 확정

반영 결과:

* 인증 없이 참여하는 품목별 실시간 채팅으로 상위 결정과 요구사항을 통일
* 갈치·고등어·전복을 후보가 아닌 초기 제공 품목으로 통일
* 검색, 가격 차트, Price Insight, 최근 이슈, 실시간 채팅을 PRD와 PF 체계에 연결

### 사용량

* 이번 검사 token 사용량: 확인 불가
* 잔여 token: 확인 불가
* Codex usage/quota: 확인 불가

### 검사 상태

`완료`

### 다음 검사 기준

`5e6f58cdd80bfe02f22b530e83e95e56c8308900`

## 2026-10-14 03:25 KST

### 검사 범위

Baseline: `5e6f58cdd80bfe02f22b530e83e95e56c8308900` → checked HEAD: `8052825ff2f6fff7dc91b6b603b2cd7ec58ec793`

Baseline 이후 커밋된 문서와 working tree의 신규 제품 정책 및 연관 문서를 증분 검사했다. PRD·PF·PP 간 요구사항, 정책, 출시 기준의 추적성과 INDEX·README 탐색 경로를 함께 확인했다.

### 변경 감지

* 추가: 8개
* 수정: 6개
* 삭제: 0개
* 이동/파일명 변경: 0개

### 검사 대상

* M `DOCUMENT-CHECK-HISTORY.md`
* M `INDEX.md`
* M `MVP/poc/POC-003-수산물-가격-데이터-연계.md`
* M `MVP/product/decisions/PD-012-MVP-기능-우선순위.md`
* M `MVP/product/decisions/PD-013-가격-데이터-PoC-적용-원칙.md`
* A `MVP/product/PRD-001-MVP-제품-요구사항.md`
* A `MVP/product/features/PF-001-홈-화면.md`
* A `MVP/product/features/PF-002-수산물-가격-차트.md`
* A `MVP/product/features/PF-003-Price-Insight.md`
* A `MVP/product/features/PF-004-최근-이슈.md`
* A `MVP/product/features/PF-005-실시간-채팅.md`
* A `MVP/product/policies/PP-002-AI-분석-운영-정책.md` — working tree
* A `MVP/product/policies/PP-003-MVP-출시-인수-기준.md` — working tree
* M `README.md`

### 검사 결과

* 파일명: 자동 수정 — 기존 문서의 예약 번호 체계에 맞춰 제품 정책 번호 정리
* 디렉토리 구조: 정상
* 문서 구조: 자동 수정 — PP 문서 H1의 문서 ID 표기 통일
* 프로젝트 용어: 정상
* 링크: 자동 수정 — PP-002·PP-003 실제 문서 링크 및 탐색 경로 반영
* 요구사항 중복: 수정 — PRD는 상위 `CAP-*`, PF는 상세 `FR-*` 체계로 분리
* 요구사항 정합성: 정상 — 회원가입·로그인 제외, 실시간 채팅 포함, 초기 품목 3종 확정 유지
* Source of Truth: 정상 — Accepted PD와 신규 PP의 정책 의미가 일치함
* INDEX.md: 수정
* README.md: 수정

### 수행한 수정

* AI 분석 운영 정책을 `PP-002`, MVP 출시 인수 기준을 `PP-003`으로 정리해 기존 PP-001 예약 참조와 충돌 제거
* PP-003에 PF-005 실시간 채팅의 인수 기준, 운영 확인, 지표, 출시 차단 조건, 최종 체크리스트 추가
* PF-001~005의 실제 PP-002·PP-003 참조를 상대 링크로 연결
* PF 문서의 정합성 검토 상태 문구를 현재 상태로 갱신
* INDEX와 README에 제품 정책 디렉토리, 문서 역할, 관계, 권장 탐색 순서 추가
* PRD의 기능 영역을 `CAP-HOME`, `CAP-CHART`, `CAP-INSIGHT`, `CAP-ISSUE`, `CAP-CHAT`으로 식별하고 PF별 상위 기능 연결 및 INDEX·README 안내 추가

### 사용자 검토

발견된 문제:

* PRD와 PF가 동일한 요구사항 ID를 서로 다른 의미로 사용한다. 예를 들어 PRD의 `FR-INSIGHT-01`은 저장된 분석 조회를 뜻하지만 PF-003의 `FR-INSIGHT-01`은 요인 최대 3개 제한을 뜻한다.
* `FR-HOME-*`, `FR-CHART-*`, `FR-ISSUE-*`에서도 같은 형태의 추적성 충돌이 확인된다.

가능한 처리 방향:

* 권장: PRD는 `CAP-HOME`, `CAP-CHART`, `CAP-INSIGHT`, `CAP-ISSUE`, `CAP-CHAT` 같은 상위 기능 ID를 사용하고, PF는 상세 `FR-*` ID를 유지한다.
* PRD와 PF의 요구사항을 일대일로 재구성하고 동일한 `FR-*` ID 체계로 맞춘다.
* `PRD-FR-*`와 `PF-FR-*`처럼 문서 계층별 네임스페이스를 분리한다.

사용자 결정:

* PRD는 상위 `CAP-*` ID를 사용하고 PF는 상세 `FR-*` ID를 유지하는 권장안 승인

반영 결과:

* PRD와 PF에서 같은 `FR-*` ID가 다른 의미로 사용되던 충돌 제거
* PRD 기능 영역과 PF 상세 명세 사이의 일대일 추적 관계 명시

### 사용량

* 이번 검사 token 사용량: 확인 불가
* 잔여 token: 확인 불가
* Codex usage/quota: 확인 불가

### 검사 상태

`완료`

### 다음 검사 기준

* baseline_commit: `5e6f58cdd80bfe02f22b530e83e95e56c8308900` 유지 — working tree 커밋 후 갱신
* checked_head: `8052825ff2f6fff7dc91b6b603b2cd7ec58ec793`
* working_tree_dirty: `true`
* pending: `DOCUMENT-CHECK-HISTORY.md`, `INDEX.md`, `README.md`, `MVP/product/PRD-001`, `MVP/product/features/PF-001~005`, `MVP/product/policies/PP-002~003`

## 2026-10-14 18:57 KST

### 검사 범위

- Baseline: `24c2d0c098f95c63cc6a7a31dbb31bf8934d0f83`
- 검사 HEAD: `24c2d0c098f95c63cc6a7a31dbb31bf8934d0f83`
- Working tree: dirty
- 검사 방식: incremental

이전 검사에서 검증한 변경이 HEAD에 커밋된 것을 확인하고, 이후 working tree의 PRD·PF-005 수정과 신규 UX-001을 증분 검사했다.

### 변경 감지

- 추가: 1개
- 수정: 6개
- 삭제: 0개
- 이동/파일명 변경: 0개
- Untracked: 1개

### 검사 대상

- M `MVP/product/PRD-001-MVP-제품-요구사항.md`
- M `MVP/product/features/PF-005-실시간-채팅.md`
- M `MVP/product/policies/PP-003-MVP-출시-인수-기준.md`
- U `MVP/product/ux/UX-001-사용자-흐름-및-정보-구조.md`
- M `INDEX.md`
- M `README.md`
- M `DOCUMENT-CHECK-HISTORY.md` — 검사 메타데이터

관련 문서로 Accepted `PD-012`, `PP-003`, `INDEX.md`, `README.md` 및 HEAD의 기존 PF-005를 확인했다.

### 검사 결과

- 파일명: 정상
- 디렉토리 구조: 정상
- 문서 구조: 수정 — PF-005 전체 명세 복원·통합 및 PRD·UX H1 형식 통일
- 프로젝트 용어: 정상
- 내부 링크: 수정 — PRD·UX의 정책 번호와 상대 링크를 실제 PP-002·PP-003 경로로 정리
- 요구사항 중복: 정상
- 요구사항 정합성: 정상 — 기본 채팅 요구사항과 승인된 익명 식별·세션 정책을 PF-005에 통합
- Source of Truth: 정상 — 사용자 승인 내용을 PRD·PF·PP·UX와 검사 이력에 연결
- INDEX.md: 수정 — UX 디렉토리·UX-001과 갱신된 PF-005 역할·관계 등록
- README.md: 수정 — UX 문서 영역과 기본 탐색 순서 추가

### 발견된 문제

- 문제 ID: `PF005-STRUCT-001`
  - 관련 문서: PF-005, PRD-001, PP-003
  - 문제 내용: 기존 274줄 기능 명세가 109줄의 익명 식별·세션 정책으로 대체되어 문서 H1, 상태, 상위 문서, 채팅방 격리, 메시지 송수신, 입력 제한, 데이터 계약, QA, 출시 기준과 관련 문서가 삭제됐다.
  - 처리 상태: 해결 — 기존 전체 기능 명세 복원 후 신규 정책 통합
- 문제 ID: `CHAT-SOT-001`
  - 관련 문서: PRD-001, PF-005, UX-001, PD-012, PP-003
  - 문제 내용: 닉네임 500개×색상 20개, `localStorage`, 3분 예약, 조합 고갈 시 자동 재시도가 확정 정책으로 추가됐으나 Accepted PD와 기존 검사 이력에는 승인 근거가 없고 PP-003 출시 게이트에도 반영되지 않았다.
  - 처리 상태: 해결 — 사용자 승인 후 PP-003을 포함한 연관 문서에 반영
- 문제 ID: `PP-REF-001`
  - 관련 문서: PRD-001, UX-001, INDEX.md, README.md
  - 문제 내용: PRD·UX는 `PP-001-AI-분석-운영-정책.md`, `PP-002-MVP-출시-인수-기준.md`를 참조하지만 실제 문서는 PP-002·PP-003이다. 또한 PRD는 PP-001 가격 데이터 처리 정책을 폐기했다고 서술하지만 INDEX·README는 작성 예정으로 관리한다.
  - 처리 상태: 해결 — 기존 PP-001 작성 예정, PP-002 AI, PP-003 출시 기준 체계 유지
- 문제 ID: `UX-INDEX-001`
  - 관련 문서: UX-001, INDEX.md, README.md
  - 문제 내용: 신규 UX 디렉토리와 UX-001이 문서 탐색 구조에 등록되지 않았다.
  - 처리 상태: 해결 — INDEX·README 등록 완료

### 수행한 수정

- HEAD의 PF-005 기능 목적·범위·메시지 송수신·격리·입력 제한·데이터 계약·QA·출시 기준을 복원했다.
- PF-005에 500×20 익명 조합, 서버 검증, `localStorage` 복원 요청, 3분 예약, 조합 고갈 처리와 인수 조건을 통합했다.
- PP-003에 신규 채팅 인수 기준, 운영 검증, 지표와 출시 차단 조건을 추가했다.
- PRD와 UX의 정책 번호를 PP-002·PP-003 체계로 바로잡고 PP-001 가격 데이터 처리 정책을 작성 예정 상태로 통일했다.
- UX-001의 H1·상대 링크를 정리하고 INDEX·README에 UX 문서 영역과 관계를 등록했다.
- 검사 결과와 사용자 결정을 `DOCUMENT-CHECK-HISTORY.md`에 기록했다.

### 사용자 검토

권장 처리 방향:

- HEAD의 PF-005 전체 기능 명세를 복원한 뒤 신규 익명 식별·세션 정책을 해당 문서에 통합한다.
- 신규 채팅 수치 정책의 승인을 확인한 뒤 PP-003의 인수 기준·운영 검증·출시 차단 조건에 반영한다.
- 기존 정책 번호 체계인 PP-001 가격 데이터 처리 정책(작성 예정), PP-002 AI 분석 운영 정책, PP-003 MVP 출시 인수 기준을 유지하고 PRD·UX 참조를 바로잡는다.
- UX-001의 H1 형식과 링크를 정리하고 INDEX·README에 UX 문서 영역을 등록한다.

사용자 결정:

- 500×20 익명 조합, `localStorage` 복원 요청, 3분 재연결 예약, 조합 고갈 시 자동 재시도를 승인된 정책으로 확정
- 기존 PF-005 전체 명세를 복원한 뒤 신규 정책을 통합하고 PP-003·UX·INDEX·README까지 정리하는 권장안 승인

반영 결과:

- PRD의 `CAP-CHAT`, PF-005의 상세 `FR-CHAT-*`, UX-001의 사용자 흐름과 PP-003 출시 게이트가 같은 채팅 정책을 사용한다.
- 회원가입·로그인 제외와 채팅 장애 시 정보 조회 유지 원칙을 보존했다.

### 사용량

- 이번 검사 token 사용량: 확인 불가
- 잔여 token: 확인 불가
- Codex usage/quota: 확인 불가

### 검사 상태

`완료`

### 다음 검사 기준

- baseline_commit: `24c2d0c098f95c63cc6a7a31dbb31bf8934d0f83`
- checked_head: `24c2d0c098f95c63cc6a7a31dbb31bf8934d0f83`
- working_tree_dirty: `true`
- pending_uncommitted_changes: `DOCUMENT-CHECK-HISTORY.md`, `INDEX.md`, `README.md`, `MVP/product/PRD-001-MVP-제품-요구사항.md`, `MVP/product/features/PF-005-실시간-채팅.md`, `MVP/product/policies/PP-003-MVP-출시-인수-기준.md`, `MVP/product/ux/UX-001-사용자-흐름-및-정보-구조.md`

## 2026-10-14 20:11 KST

### 검사 범위

- Baseline: `e0044472ce9dab683b59b95a06f087751cef631a`
- 검사 HEAD: `e0044472ce9dab683b59b95a06f087751cef631a`
- Working tree: dirty
- 검사 방식: incremental

직전 검사 결과가 HEAD에 반영된 것을 확인하고, 이후 추가된 PRD·UX 흐름 이미지와 신규 UX-002 및 연관 문서를 증분 검사했다. 파일명·문서 구조·내부 링크·요구사항 정합성·Source of Truth·INDEX·README를 확인했다.

### 변경 감지

- 추가: 3개
- 수정: 5개
- 삭제: 0개
- 이동/파일명 변경: 0개
- Untracked: 3개

### 검사 대상

- M `MVP/product/PRD-001-MVP-제품-요구사항.md`
- M `MVP/product/ux/UX-001-사용자-흐름-및-정보-구조.md`
- U `MVP/product/ux/UX-002-화면-상태-및-인터랙션-설계.md`
- U `MVP/product/PRD-001-MVP-제품-요구사항.png`
- U `MVP/product/ux/UX-001-사용자-흐름.png`
- M `INDEX.md`
- M `README.md`
- M `DOCUMENT-CHECK-HISTORY.md` — 검사 메타데이터

### 검사 결과

- 파일명: 수정 — UX 흐름 이미지 제목을 한국어 파일명으로 통일
- 디렉토리 구조: 정상
- 문서 구조: 수정 — UX-002 H1 형식과 PRD·UX 이미지 설명 구조 정리
- 프로젝트 용어: 정상
- 내부 링크: 정상 — 로컬 링크·이미지 참조 0건 오류
- 요구사항 중복: 수정 — UX 미정 식별자 중복 제거
- 요구사항 정합성: 수정 — UX-002에서 확정한 검색·탭·채팅 패널·상태 전환을 PRD·UX-001에 동기화
- Source of Truth: 수정 — UX-001 흐름과 UX-002 상태·인터랙션의 책임 범위 분리
- INDEX.md: 수정 — UX-002 역할·주요 섹션·문서 관계 등록
- README.md: 수정 — UX-002 탐색 링크 추가

### 발견된 문제

- 문제 ID: `UX-SYNC-001`
  - 관련 문서: PRD-001, UX-001, UX-002
  - 문제 내용: UX-002에서 검색 방식, 상세 탭 구조, 채팅 패널과 오류·복구 동작을 확정했지만 PRD와 UX-001은 같은 항목을 후속 또는 미정으로 유지했다.
  - 처리 상태: 해결 — UX-002를 현재 상세 UX 기준으로 연결하고 기존 미정 표현을 갱신
- 문제 ID: `UX-ID-001`
  - 관련 문서: UX-001, UX-002
  - 문제 내용: 두 문서가 같은 `UX-OPEN-*` ID를 서로 다른 의미로 사용하고 해결된 ID와 결정의 대응도 일치하지 않았다.
  - 처리 상태: 해결 — 해결된 UX-001 목록을 제거하고 UX-002 잔여 항목을 `UX2-OPEN-*`로 분리
- 문제 ID: `UX-INDEX-002`
  - 관련 문서: UX-002, INDEX.md, README.md
  - 문제 내용: 신규 UX-002가 통합 목차와 기본 탐색 경로에 등록되지 않았다.
  - 처리 상태: 해결 — INDEX·README 및 문서 관계표에 등록
- 문제 ID: `UX-ASSET-001`
  - 관련 문서: PRD-001, UX-001, 두 PNG 이미지
  - 문제 내용: UX 이미지 파일명이 한국어 원칙과 맞지 않고, 이미지의 예시 가격·날짜·참여자 수가 확정 요구사항으로 오인될 수 있었다.
  - 처리 상태: 해결 — 파일명을 `UX-001-사용자-흐름.png`로 변경하고 예시 데이터 안내 추가

### 수행한 수정

- PRD의 UX-002 파일명·역할을 실제 문서와 일치시키고 해결된 `OPEN-15`를 제거했다.
- UX-001의 검색, 상세 탭, 채팅 패널, 재진입, 차트·오류 상태를 UX-002 결정과 동기화했다.
- UX-001의 해결된 `UX-OPEN-*` 목록을 후속 확인 사항 안내로 교체했다.
- UX-002 H1을 표준 형식으로 정리하고 잔여 UX 항목을 `UX2-OPEN-*`로 분리했다.
- PRD·UX 이미지에 예시 데이터 안내를 추가하고 UX 이미지 파일명을 한국어로 변경했다.
- INDEX와 README에 UX-002의 역할, 탐색 순서와 문서 관계를 등록했다.

### 사용자 검토

발견된 문서 동기화·식별자·목차·이미지 표기 문제의 수정 진행을 사용자가 승인했다.

### 사용량

- 이번 검사 token 사용량: 확인 불가
- 잔여 token: 확인 불가
- Codex usage/quota: 확인 불가

### 검사 상태

`완료`

### 다음 검사 기준

- baseline_commit: `e0044472ce9dab683b59b95a06f087751cef631a`
- checked_head: `e0044472ce9dab683b59b95a06f087751cef631a`
- working_tree_dirty: `true`
- pending_uncommitted_changes: `DOCUMENT-CHECK-HISTORY.md`, `INDEX.md`, `README.md`, `MVP/product/PRD-001-MVP-제품-요구사항.md`, `MVP/product/PRD-001-MVP-제품-요구사항.png`, `MVP/product/ux/UX-001-사용자-흐름-및-정보-구조.md`, `MVP/product/ux/UX-001-사용자-흐름.png`, `MVP/product/ux/UX-002-화면-상태-및-인터랙션-설계.md`

## 2026-10-15 03:00 KST

### 검사 기준 및 범위

- 기준 브랜치: `main`
- 기준 HEAD: `656841c9e99e7ede6b5c4f2432b353e19995b145`
- Working tree: 작업 시작 시 clean, 검사 이력 기록 시 dirty
- 사용자 승인 근거: 정합성 검토 1~8, `PD-012` 검색·채팅 부하 문구 최소 수정 승인, `UX-001` 차트 범위 최소 수정 승인
- Git 추적 Markdown: 30개
- 로컬 파일시스템 Markdown: 33개
- 차이 3개: Git 비추적·무시 파일인 `AGENTS.md`, `.codex/skills/docs-consistency-check/SKILL.md`, `env/ENV-001-카.md`
- 기계 검사는 로컬 33개 전체, 제품 정책 문맥 검사는 Git 추적 30개 전체를 대상으로 수행했다.
- 수정 범위: 승인된 14개 파일. 범위 밖 파일은 읽기 및 비교만 수행했다.

### 수정 대상

- `MVP/product/policies/PP-002-AI-분석-운영-정책.md`
- `MVP/product/features/PF-003-Price-Insight.md`
- `MVP/product/policies/PP-003-MVP-출시-인수-기준.md`
- `MVP/product/PRD-001-MVP-제품-요구사항.md`
- `MVP/product/features/PF-001-홈-화면.md`
- `MVP/product/features/PF-002-수산물-가격-차트.md`
- `MVP/product/features/PF-004-최근-이슈.md`
- `MVP/product/features/PF-005-실시간-채팅.md`
- `MVP/product/decisions/PD-012-MVP-범위.md`
- `MVP/product/decisions/PD-013-가격-데이터-PoC-적용-원칙.md`
- `MVP/product/ux/UX-001-사용자-흐름-및-정보-구조.md`
- `MVP/product/ux/UX-002-화면-상태-및-인터랙션-설계.md`
- `INDEX.md`
- `DOCUMENT-CHECK-HISTORY.md`

### 주요 수정 내용

- 게시된 과거 Insight를 고정 스냅샷으로 관리하고, 신규 근거·단순 가격 변경에 따른 자동 재분석을 제거했다. 명백한 오류는 개발자 수동 무효화·정정 대상으로 유지했다.
- 하루 1회 배치 실행 주기와 신규 완료 기간 입력 준비 후 2시간 이내 생성 목표를 서로 다른 운영 기준으로 명시했다.
- 출시 판정을 `PASS`, `CONDITIONAL_PASS`, `FAIL`, `PENDING`으로 구분하고 보안 심각도, 조건부 승인 기록, 운영 유사 환경 성능 증빙과 출시 차단 기준을 정리했다.
- 홈의 3종 즉시 검색, 고정 순서, 최근 완료 반월 가격, 직전 반월 변동률, 반올림, 카드별 오류·재시도와 갱신 시각을 동기화했다.
- 차트 범위를 최근 완료 반월 24개·완료 월 12개로 확정하고 미완료 기간을 제외했다. 중복·검증 오류·정상 극단값·등급 및 규격 보존 원칙과 `PFV-013` 보류를 정리했다.
- 최근 이슈의 KST 30개 달력 날짜, 출처 우선순위, 관련성, URL 정규화, 5개 단위 더보기, 원문 검증·재시도 및 메타데이터 1년 보존을 반영했다.
- 채팅의 300 Unicode 문자, 세션당 3초 1회·분당 20회, 최근 50개, 7일 보존, 서버 금칙어 검사, 다중 탭 세션, 재연결 백오프, 30일 이벤트 로그와 품목별 500명·p95 500ms를 동기화했다.
- `PD-012`는 초기 3종 검색 범위와 초당 5개 비정상 전송 제한 시험 해석만 최소 수정했다.
- `UX-001`과 `UX-002`의 차트 범위·Mermaid 흐름·UX-D05 표시 원칙 및 채팅 상태를 기능 문서와 맞췄다.
- 기능 요구사항, QA 시나리오, OPEN 상태와 출시 인수 기준을 함께 갱신했다.

### 전수검사 결과

| 번호 | 검사 항목 | 결과 |
|---:|---|---|
| 1 | Markdown 전체 목록과 수량 | PASS — 추적 30개, 로컬 33개를 구분 확인 |
| 2 | 파일 경로 및 상대 링크 | PASS — 로컬 33개 검사, 깨진 상대 링크 0건 |
| 3 | INDEX 등록 문서와 실제 파일 | PASS — 추적 문서 누락 0건, 비추적 대상 링크 0건 |
| 4 | README와 INDEX의 정책 번호·역할 | PASS — PP-001 작성 예정, PP-002 AI 운영, PP-003 출시 인수 체계 일치 |
| 5 | 제목·소제목 구조 | PASS — H1 누락 0건. 기존 11개 문서의 다중 H1 구조는 관찰 기록이며 이번 변경에서 새로 만들지 않음 |
| 6 | 요구사항 및 OPEN 식별자 중복 | PASS — 정의 중복 0건 |
| 7 | PRD–PD–PF–PP–UX 정책 충돌 | PASS — 승인 범위에서 잔여 충돌 0건 |
| 8 | 승인 정책 1~8 불일치 | PASS — 구 정책 잔존 검색 0건 |
| 9 | 해결된 미정 항목 잔존 | PASS — 기존 ID를 유지하고 확정·일부 확정·PoC/기술 보류로 구분 |
| 10 | QA·기능 명세·인수 기준 | PASS — 각 기능의 확정 정책을 QA와 인수 조건에 동기화 |
| 11 | 출시 차단·조건부 허용·보류 상태 | PASS — 실측 없는 필수 항목은 `PENDING`, `FAIL`·`PENDING` 필수 항목의 출시 금지 유지 |
| 12 | PoC 검증과 제품 목표 구분 | PASS — PoC 결과를 성능·출시 합격 증거로 사용하지 않음 |
| 13 | 미승인 기능·수치 생성 여부 | PASS — 승인 검토 1~8 외 새 정책·수치 없음 |
| 14 | 수정 범위 밖 파일 변경 | PASS — 승인된 14개만 변경 |
| 15 | INDEX와 검사 이력 최종 일치 | PASS — 역할·범위·검사 수량 동기화 |

검사 과정에서 처음 실행한 INDEX 비교 스크립트는 Git의 quoted path를 처리하지 못해 실패했다. 해당 결과는 폐기하고 `core.quotepath=false`를 적용해 재실행했으며, 위 표에는 정상 재실행 결과만 반영했다. ID·제목 구조 검사도 정규식 오류가 있던 최초 실행 결과를 폐기하고 수정 후 재실행한 결과만 반영했다.

### 남은 보류 및 검증 과제

- `PFV-013`: 서로 다른 등급·규격을 대표가격 하나에 혼합할지 여부
- `PFV-025`: 월간 AI 운영비 상한
- `PFV-026`: 기존 Insight 버전·오류 확인·무효화 이력의 구체적 보존 기간
- `PP-001 가격 데이터 처리 정책`: 작성 예정 상태 유지
- 최근 이슈 실제 제공처·이용약관, 원문 본문 보존과 장기 출처 추적: PoC·외부 권한 검증 대기
- 차트 라이브러리·정정 후 재집계, 채팅 대기 순서·서버 재시작 복원·세션 폐기: 기술 설계 보류
- AI 생성 성공률 목표: PFV 식별자와 연결하지 않은 별도 미정 상태 유지
- 하루 1회 AI 배치와 입력 준비 완료 후 2시간 생성 목표의 동시 충족 방식: 트리거·실행 시점 기술 설계 검증 대기
- 가격 수집 성공률의 정확한 분모·제외 조건과 부하 시험 표본·요청량·반복 횟수: 인프라 확인 및 별도 승인 대기
- 익명 KPI 식별·이벤트·개인정보 정책과 접근성 세부 기준: 후속 검토 대기

### 실측 및 출시 인수 상태

- 성능·수집·보안·채팅 부하·E2E 시험의 실제 원본 증빙은 이번 문서 검사에서 생성하거나 확인하지 않았다.
- 가격 차트·저장 Insight API, 모바일 LCP, 가격 반영·수집 성공률, 신규 Insight 생성, 채팅 전달·500명 동시 접속을 포함한 출시 인수 상태는 모두 `PENDING`이다.
- 현재 최종 출시 판정은 `PENDING`이며 `PASS` 또는 검증 완료로 기록한 실제 기능은 없다.

### 검사 상태 및 다음 기준

#### 2026-10-15 03:04 KST 커밋 전 추가 검증

- `PFV-025` 참조를 전체 Markdown에서 재검사해 의미를 **월간 AI 운영비 상한 보류**로 바로잡았다.
- AI 생성 성공률 목표는 PFV 식별자와 연결하지 않은 별도 미정·`PENDING` 항목으로 유지했다.
- 하루 1회 배치와 입력 준비 완료 후 2시간 생성 목표는 모두 유지하고, 두 조건의 동시 충족 가능성을 트리거·실행 시점 기술 설계 검증 과제로 등록했다.
- 추가 수정 파일: `PRD-001`, `PP-002`, `PF-003`, `DOCUMENT-CHECK-HISTORY.md` 4개
- 최종 재검사: `git diff --check` 통과, 로컬 Markdown 33개 상대 링크 오류 0건, ID 정의 중복 0건, 비용 보류 식별자와 생성 성공률 목표의 오연결 0건
- 정책 수치나 실행 주기는 변경하지 않았으며 커밋·푸시를 수행하지 않았다.

- 문서 정책 정합성: 완료
- 문서 구조·상대 링크·INDEX 검사: 완료
- 추가 사용자 검토 필요 정책 충돌: 없음
- 미승인 변경: 없음
- 커밋·푸시: 수행하지 않음
- token 사용량 및 잔여 token: 확인 불가
- 다음 baseline_commit: `656841c9e99e7ede6b5c4f2432b353e19995b145`
- checked_head: `656841c9e99e7ede6b5c4f2432b353e19995b145`
- working_tree_dirty: `true`
- pending_uncommitted_changes: 위 수정 대상 14개 파일

## 2026-10-16 03:20 KST

### 검사 기준 및 범위

- 기준 브랜치: `main`
- 기준 HEAD: `e628da8a2f31920d6c28c32716e538cb88b4ab68`
- 작업 시작 시 Working tree: clean
- 검사 대상: Git 추적 Markdown 30개
- 공식 문서 수에서 제외: `.gitignore` 대상 `AGENTS.md`, Codex `SKILL.md`, 환경변수 기록 Markdown
- 환경변수 기록 파일의 내용은 읽거나 검사 출력에 포함하지 않았다.
- 수정 범위: `MVP/product/features/PF-002-수산물-가격-차트.md`, 검사 기록용 `DOCUMENT-CHECK-HISTORY.md`

### 잔여 정합성 문제와 수정

- `CHART-OPEN-07`이 가격 표시 형식을 미정으로 남긴 문제를 해결했다.
- 확정 문구: 가격 원 단위 정수, 변동률 소수 첫째 자리 반올림 (`PFV-004·005`).
- `FR-CHART-04` 상세 조건·인수 조건, `CHART-TC-040~041`, 출시 인수 조건에 동일 표시 규칙을 반영했다.
- `CHART-OPEN-11~12`는 승인된 기술 설계 보류임을 명시했다.
- `CHART-OPEN-13`은 단순 가격 변경에 따른 과거 Insight 자동 재분석·무효화 금지와 `PP-002` 오류 처리 참조를 명시하고, 구현 상세는 확정하지 않았다.

### 전체 검사 결과

| 검사 항목 | 결과 |
|---|---|
| Git 추적 Markdown 수 | PASS — 30개 |
| 상대 링크 | PASS — 오류 0건 |
| INDEX 등록과 추적 파일 | PASS — 누락 0건, 비추적 대상 링크 0건 |
| H1 존재 여부 | PASS — 누락 0건 |
| 다중 H1 | 관찰 — 기존 11개, 신규 구조 결함으로 처리하지 않음 |
| 요구사항·QA·OPEN ID 정의 중복 | PASS — 0건 |
| 승인 정책 잔존 검색 | PASS — 잔여 충돌 0건 |
| `PFV-025`·`PFV-026` 의미 | PASS — 각각 월간 AI 운영비 상한·Insight 버전 이력 보존 기간 보류 |
| `PFV-013` | PASS — 등급·규격 혼합 기준 보류 유지 |
| AI 생성 성공률 | PASS — PFV 식별자와 분리된 별도 미정·`PENDING` 유지 |
| 수정 범위 | PASS — PF-002와 검사 이력만 변경 |

첫 승인 정책 잔존 검색은 `rg` 기본 정규식이 look-around를 지원하지 않아 종료 코드 오류가 발생했다. 해당 결과는 폐기하고 `--pcre2`로 수정해 정상 종료한 재실행 결과만 위 표에 반영했다.

### 남은 보류 및 출시 상태

- 차트 라이브러리와 가격 정정 후 재집계 시점·처리 상세는 기술 설계 보류다.
- `PFV-013`, `PFV-025`, `PFV-026`의 기존 보류 상태는 변경하지 않았다.
- AI 생성 성공률 목표와 배치 주기·생성 SLA 동시 충족 방식의 기존 보류 상태도 변경하지 않았다.
- `PP-001 가격 데이터 처리 정책`은 작성 예정 상태를 유지한다.
- 실제 데이터 수집·성능·보안 시험 증빙을 이번 검사에서 생성하거나 확인하지 않았다.
- 문서 정책 정합성 검사는 통과했지만 최종 출시 판정은 계속 `PENDING`이다.
- 새로 발견한 범위 밖 정책 충돌 및 사용자 검토 필요 항목: 없음
- 커밋·푸시: 수행하지 않음
- token 사용량 및 잔여 token: 확인 불가

### 다음 검사 기준

- baseline_commit: `e628da8a2f31920d6c28c32716e538cb88b4ab68`
- checked_head: `e628da8a2f31920d6c28c32716e538cb88b4ab68`
- working_tree_dirty: `true`
- pending_uncommitted_changes: `MVP/product/features/PF-002-수산물-가격-차트.md`, `DOCUMENT-CHECK-HISTORY.md`
