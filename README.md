# 오늘의 수산 프로젝트 문서

이 저장소는 **오늘의 수산** 프로젝트의 기획과 제품 의사결정을 관리하는 문서 저장소다. 사용자 리서치부터 문제 정의, 타깃 사용자, 서비스 포지셔닝, 핵심 기능, 가격 정책, 성장 및 비즈니스 모델까지 실제 개발 판단에 필요한 기준을 기록한다.

사람과 AI Agent는 먼저 [INDEX.md](./INDEX.md)에서 문서의 역할과 관계를 확인한 뒤 각 원본 문서를 읽는다. 요구사항과 의사결정의 최종 기준은 원본 문서다.

## 문서 목차

### 프로젝트 안내

1. [INDEX.md — 통합 문서 목차](./INDEX.md)
   - 전체 문서의 역할, 주요 섹션, 읽기 순서와 문서 관계를 안내한다.
2. [DOCUMENT-CHECK-HISTORY.md — 문서 일관성 검사 이력](./DOCUMENT-CHECK-HISTORY.md)
   - 문서 검사 범위, 수정 결과와 다음 검사 기준을 기록한다.

### `MVP/product/decisions/`

1. [PD-001-서비스-문제-정의.md](./MVP/product/decisions/PD-001-서비스-문제-정의.md)
2. [PD-002-핵심-타깃-사용자.md](./MVP/product/decisions/PD-002-핵심-타깃-사용자.md)
3. [PD-003-핵심-페르소나.md](./MVP/product/decisions/PD-003-핵심-페르소나.md)
4. [PD-004-서비스-포지셔닝.md](./MVP/product/decisions/PD-004-서비스-포지셔닝.md)
5. [PD-005-서비스-성장-전략.md](./MVP/product/decisions/PD-005-서비스-성장-전략.md)
6. [PD-006-비즈니스-모델.md](./MVP/product/decisions/PD-006-비즈니스-모델.md)
7. [PD-007-감성적-가치.md](./MVP/product/decisions/PD-007-감성적-가치.md)
8. [PD-008-Price-Insight.md](./MVP/product/decisions/PD-008-Price-Insight.md)
9. [PD-009-기준가격-정의.md](./MVP/product/decisions/PD-009-기준가격-정의.md)
10. [PD-010-데이터-신뢰-정책.md](./MVP/product/decisions/PD-010-데이터-신뢰-정책.md)
11. [PD-011-AI-역할-정의.md](./MVP/product/decisions/PD-011-AI-역할-정의.md)
12. [PD-012-MVP-범위.md](./MVP/product/decisions/PD-012-MVP-범위.md)
13. [PD-013-가격-데이터-PoC-적용-원칙.md](./MVP/product/decisions/PD-013-가격-데이터-PoC-적용-원칙.md)

### `MVP/product/`

1. [PRD-001-MVP-제품-요구사항.md](./MVP/product/PRD-001-MVP-제품-요구사항.md)

### `MVP/product/features/`

1. [PF-001-홈-화면.md](./MVP/product/features/PF-001-홈-화면.md)
2. [PF-002-수산물-가격-차트.md](./MVP/product/features/PF-002-수산물-가격-차트.md)
3. [PF-003-Price-Insight.md](./MVP/product/features/PF-003-Price-Insight.md)
4. [PF-004-최근-이슈.md](./MVP/product/features/PF-004-최근-이슈.md)
5. [PF-005-실시간-채팅.md](./MVP/product/features/PF-005-실시간-채팅.md)

### `MVP/product/ux/`

1. [UX-001-사용자-흐름-및-정보-구조.md](./MVP/product/ux/UX-001-사용자-흐름-및-정보-구조.md)

### `MVP/product/policies/`

1. `PP-001-가격-데이터-처리-정책.md` — 작성 예정
2. [PP-002-AI-분석-운영-정책.md](./MVP/product/policies/PP-002-AI-분석-운영-정책.md)
3. [PP-003-MVP-출시-인수-기준.md](./MVP/product/policies/PP-003-MVP-출시-인수-기준.md)

### `MVP/research/user/`

1. [UR-001-제철-음식-소비-트렌드-리서치.md](./MVP/research/user/UR-001-제철-음식-소비-트렌드-리서치.md)

### `MVP/poc/`

1. [POC-001-aT-공영도매시장-API-데이터.md](./MVP/poc/POC-001-aT-공영도매시장-API-데이터.md)
2. [POC-002-외부-가격-데이터-검증-체크리스트.md](./MVP/poc/POC-002-외부-가격-데이터-검증-체크리스트.md)
3. [POC-003-수산물-가격-데이터-연계.md](./MVP/poc/POC-003-수산물-가격-데이터-연계.md)

## 기본 탐색 순서

1. 사용자 리서치와 서비스 문제를 이해한다.
2. 타깃 사용자와 페르소나를 확인한다.
3. 서비스 포지셔닝과 감성적 가치를 확인한다.
4. 성장 전략과 MVP 범위에서 현재 구현 대상을 확인한다.
5. 기준가격, Price Insight, 데이터 신뢰 및 AI 역할 문서를 구현 기준으로 사용한다.
6. PRD에서 통합 MVP 범위와 상위 `CAP-*` 기능 영역을 확인하고 PF 문서에서 상세 `FR-*` 요구사항과 인수 기준을 확인한다.
7. UX 문서에서 기능 간 사용자 흐름, 정보 구조와 화면 상태를 확인한다.
8. PP 문서에서 공통 운영 정책과 출시 인수 기준을 확인한다.
9. PoC 문서에서 데이터 소스와 가격 차트의 실제 사용 가능성을 확인하고, PD-013에서 제품 정책에 적용하는 기준을 확인한다.
10. 비즈니스 모델에서 운영 및 수익화 원칙을 확인한다.
