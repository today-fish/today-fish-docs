# 오늘의 수산 프로젝트 문서

- **버전:** V1
- **상태:** 승인

## 프로젝트와 저장소

오늘의 수산은 갈치·고등어·전복의 가격 차트, Price Insight, 최근 이슈와 품목별 실시간 채팅을 제공하는 모바일 웹 서비스다. 이 저장소는 제품 요구사항, 기술 설계와 검증 근거를 관리하는 Docs V1의 진입점이다.

V1 Baseline 기준일은 2026-11-12다. 문서 승인은 구현·테스트 완료를 의미하지 않는다. PoC·리서치의 실험 판정과 디자인 시안·토큰의 개별 승인 상태는 원본 기록을 따른다.

## 문서 구성과 책임

| 유형 | 책임 | 탐색 위치 |
|---|---|---|
| PRD | 서비스 목표와 상위 요구사항 | [PRD-001](MVP/product/PRD-001-MVP-제품-요구사항.md) |
| PF | 기능별 동작·예외·인수 기준 | [features/](MVP/product/features/) |
| PP | 공통 제품·운영 정책과 출시 기준 | [policies/](MVP/product/policies/) |
| PD | 제품 의사결정과 근거 | [decisions/](MVP/product/decisions/) |
| UX | 사용자 흐름·화면 상태·인터랙션 | [ux/](MVP/product/ux/) |
| FE-ADR | 프론트엔드 기술 결정 | [프론트엔드 안내](MVP/architecture/frontend/README.md) |
| BE-ADR | 백엔드 기술 결정 | [백엔드 안내](MVP/architecture/backend/README.md) |
| BE-TECH-SPEC | 백엔드 구현 계약 | [Tech Spec 책임표](MVP/architecture/backend/tech-spec/README.md) |
| BE-ERD | 영속 데이터 모델 | [BE-ERD-001](MVP/architecture/backend/erd/BE-ERD-001-통합-데이터-모델.md) — V1 승인, 18개 엔티티 |
| PoC | 기술 검증의 방법·결과·한계 | [poc/](MVP/poc/) |
| Research | 조사 결과와 제품 가설의 근거 | [research/](MVP/research/) |

## 문서 읽는 순서

| 목적 | 권장 순서 |
|---|---|
| 제품 전체 이해 | PRD → PF·PP·PD → UX |
| 백엔드 구현 | PRD·PF → BE-ADR → BE-TECH-SPEC → BE-ERD |
| 프론트엔드 구현 | PRD·PF·UX → FE-ADR → Design System |

위 순서는 탐색 경로이며 문서의 승인 우선순위를 새로 정의하지 않는다. 계약이 충돌하면 각 원본의 승인 범위·결정일·관련 근거를 대조하고, 최신 기준이 불분명하면 결정권자에게 확인한다.

GitHub Issue·Project·PR로 개발 작업을 관리하는 방법은 [GitHub 운영 가이드](governance/github/README.md)에서 시작한다. 제품·기술 설계의 상세 계약은 아래 원본 문서를 따른다.

## 제품 설계

| 문서 | 역할 |
|---|---|
| [PF-001](MVP/product/features/PF-001-홈-화면.md) | 홈·검색 |
| [PF-002](MVP/product/features/PF-002-수산물-가격-차트.md) | 가격 차트·기간 선택 |
| [PF-003](MVP/product/features/PF-003-Price-Insight.md) | Price Insight 표시·조회 |
| [PF-004](MVP/product/features/PF-004-최근-이슈.md) | 최근 이슈 목록·출처 |
| [PF-005](MVP/product/features/PF-005-실시간-채팅.md) | 품목별 실시간 채팅 |
| [PP-002](MVP/product/policies/PP-002-AI-분석-운영-정책.md) | AI 분석 운영 정책 |
| [PP-003](MVP/product/policies/PP-003-MVP-출시-인수-기준.md) | MVP 출시 인수 기준 |
| [UX-001](MVP/product/ux/UX-001-사용자-흐름-및-정보-구조.md) | 사용자 흐름·정보 구조 |
| [UX-002](MVP/product/ux/UX-002-화면-상태-및-인터랙션-설계.md) | 화면 상태·인터랙션 |

제품 결정의 상세 근거는 decisions/에서 확인한다. 핵심 기능의 요구사항과 화면 동작을 함께 읽고, 기술 구현 값은 해당 ADR·Tech Spec을 따른다.

## 기술·디자인 문서

프론트엔드·백엔드 문서 목록은 각 영역 안내에서 관리한다. API·STOMP·JWT·Snapshot 게시·테이블 제약의 상세 내용은 원본 Tech Spec과 ERD에 둔다.

| 문서 | 역할 |
|---|---|
| [Design System](design-system/README.md) | 디자인 문서·미리보기·토큰과 검증 기준 |

## 검증 근거와 운영 참고

PoC·리서치는 관측 결과와 한계를 기록한다. PASS·FAIL·REVIEW를 문서 승인 상태나 전체 서비스의 검증 완료로 해석하지 않는다.

| 문서 | 역할 |
|---|---|
| [POC-005](MVP/poc/POC-005-Gemini-PDF-분석-성능-및-정확도-검증.md) | Gemini PDF 추출의 성능·정확도 검증 결과와 한계 |
| [UR-001](MVP/research/user/UR-001-제철-음식-소비-트렌드-리서치.md) | 제철 음식 소비 트렌드 조사 |
| [env/](env) | 환경·설정 참고 자료; 설계 승인 문서와 구분 |

## 문서 관리 원칙

- 요구사항·정책·구현 계약은 담당 원본 문서에서 관리하고 README에는 탐색 정보만 둔다.
- 문서 경로와 ID를 유지하고, 문서 변경 시 관련 링크·참조·승인 상태를 확인한다.
- 실험 결과, 미채택 대안, 기술·정책 버전과 과거 변경 이력은 문서 버전과 구분해 보존한다.
- 저장소 운영 규칙은 [AGENTS.md](AGENTS.md), Git·PR 작성 규칙은 [CONTRIBUTING.md](.github/CONTRIBUTING.md), PR 양식은 [PULL_REQUEST_TEMPLATE.md](.github/PULL_REQUEST_TEMPLATE.md)를 따른다.
