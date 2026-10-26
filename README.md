# 오늘의 수산 프로젝트 문서

이 저장소는 **오늘의 수산** 프로젝트의 기획, 제품 의사결정, UX, 기술 설계 및 검증 기준을 관리한다. 문서는 제품 범위와 의사결정의 근거를 기록해 사람과 AI Agent가 일관된 기준으로 제품을 설계하고 개발하도록 돕는다.

루트 README는 전체 문서 탐색의 단일 진입점이다. 하위 README는 해당 영역의 상세 안내를 제공하며, 별도의 전체 문서 INDEX는 운영하지 않는다. 요구사항과 의사결정은 각 원본 문서를 기준으로 한다.

## 문서 활용 방법

- 제품 범위와 필수 요구사항은 PRD, 확정된 제품 결정은 Accepted 상태의 PD에서 확인한다.
- 기능별 상세 동작은 PF, 공통 운영·출시 기준은 PP, 사용자 흐름과 화면 상태는 UX 문서를 확인한다.
- 기술 결정은 관련 ADR에서 확인한다. ADR과 제품 요구사항이 충돌하거나 최신 결정이 불명확하면 임의로 우선순위를 정하지 말고 결정권자에게 확인한다.
- PoC와 리서치는 검증·조사 근거로 사용하며, 그 결과만으로 제품 정책이 확정된 것으로 해석하지 않는다. 관련 PD와 PRD를 함께 확인한다.
- 문서 간 충돌을 검토할 때는 문서 상태와 결정 여부, 작성일, 상위 제품 결정, 근거 자료를 확인한다. 판단이 불명확하면 후속 결정 문서로 기록한다.

## 문서 목차

### `MVP/product/`

제품 전체의 MVP 범위와 필수 요구사항을 정의한다.

- [PRD-001-MVP-제품-요구사항.md](./MVP/product/PRD-001-MVP-제품-요구사항.md)

`decisions/`는 제품 방향과 정책에 관한 결정 및 근거를 기록한다.

- [PD-001-서비스-문제-정의.md](./MVP/product/decisions/PD-001-서비스-문제-정의.md)
- [PD-002-핵심-타깃-사용자.md](./MVP/product/decisions/PD-002-핵심-타깃-사용자.md)
- [PD-003-핵심-페르소나.md](./MVP/product/decisions/PD-003-핵심-페르소나.md)
- [PD-004-서비스-포지셔닝.md](./MVP/product/decisions/PD-004-서비스-포지셔닝.md)
- [PD-005-서비스-성장-전략.md](./MVP/product/decisions/PD-005-서비스-성장-전략.md)
- [PD-006-비즈니스-모델.md](./MVP/product/decisions/PD-006-비즈니스-모델.md)
- [PD-007-감성적-가치.md](./MVP/product/decisions/PD-007-감성적-가치.md)
- [PD-008-Price-Insight.md](./MVP/product/decisions/PD-008-Price-Insight.md)
- [PD-009-기준가격-정의.md](./MVP/product/decisions/PD-009-기준가격-정의.md)
- [PD-010-데이터-신뢰-정책.md](./MVP/product/decisions/PD-010-데이터-신뢰-정책.md)
- [PD-011-AI-역할-정의.md](./MVP/product/decisions/PD-011-AI-역할-정의.md)
- [PD-012-MVP-범위.md](./MVP/product/decisions/PD-012-MVP-범위.md)
- [PD-013-가격-데이터-PoC-적용-원칙.md](./MVP/product/decisions/PD-013-가격-데이터-PoC-적용-원칙.md)

`features/`는 화면과 기능별 동작, 예외 처리 및 인수 조건을 정의한다.

- [PF-001-홈-화면.md](./MVP/product/features/PF-001-홈-화면.md)
- [PF-002-수산물-가격-차트.md](./MVP/product/features/PF-002-수산물-가격-차트.md)
- [PF-003-Price-Insight.md](./MVP/product/features/PF-003-Price-Insight.md)
- [PF-004-최근-이슈.md](./MVP/product/features/PF-004-최근-이슈.md)
- [PF-005-실시간-채팅.md](./MVP/product/features/PF-005-실시간-채팅.md)

`policies/`는 기능 전반에 공통 적용되는 운영·출시 정책을 기록한다.

- [PP-002-AI-분석-운영-정책.md](./MVP/product/policies/PP-002-AI-분석-운영-정책.md)
- [PP-003-MVP-출시-인수-기준.md](./MVP/product/policies/PP-003-MVP-출시-인수-기준.md)

`ux/`는 사용자 흐름, 정보 구조, 화면 상태와 인터랙션을 정의한다.

- [UX-001-사용자-흐름-및-정보-구조.md](./MVP/product/ux/UX-001-사용자-흐름-및-정보-구조.md)
- [UX-002-화면-상태-및-인터랙션-설계.md](./MVP/product/ux/UX-002-화면-상태-및-인터랙션-설계.md)

### `MVP/research/user/`

사용자와 소비 흐름에 관한 조사 자료를 보관한다. 관찰된 사실과 제품 가설을 구분해 활용한다.

- [UR-001-제철-음식-소비-트렌드-리서치.md](./MVP/research/user/UR-001-제철-음식-소비-트렌드-리서치.md)

### `MVP/poc/`

가격 데이터의 출처, 연결 가능성 및 검증 결과를 기록한다. 제품 적용 범위는 관련 제품 결정 문서에서 확인한다.

- [POC-001-aT-공영도매시장-API-데이터.md](./MVP/poc/POC-001-aT-공영도매시장-API-데이터.md)
- [POC-002-외부-가격-데이터-검증-체크리스트.md](./MVP/poc/POC-002-외부-가격-데이터-검증-체크리스트.md)
- [POC-003-수산물-가격-데이터-연계.md](./MVP/poc/POC-003-수산물-가격-데이터-연계.md)

### `MVP/architecture/frontend/`

프론트엔드 아키텍처의 기술 선택과 구현 기준을 관리한다. 상세한 기술 결정의 관계와 사용 방법은 [README.md](./MVP/architecture/frontend/README.md)를 함께 확인한다.

- [README.md](./MVP/architecture/frontend/README.md)

`adr/`는 프론트엔드 기술 결정과 재검토 기준을 기록한다.

- [FE-ADR-001-프레임워크-및-버전-선정.md](./MVP/architecture/frontend/adr/FE-ADR-001-프레임워크-및-버전-선정.md)
- [FE-ADR-002-렌더링-전략-선정.md](./MVP/architecture/frontend/adr/FE-ADR-002-렌더링-전략-선정.md)
- [FE-ADR-003-데이터-캐싱-및-갱신-전략.md](./MVP/architecture/frontend/adr/FE-ADR-003-데이터-캐싱-및-갱신-전략.md)
- [FE-ADR-004-스타일링-및-디자인-시스템-적용-전략.md](./MVP/architecture/frontend/adr/FE-ADR-004-%EC%8A%A4%ED%83%80%EC%9D%BC%EB%A7%81-%EB%B0%8F-%EB%94%94%EC%9E%90%EC%9D%B8-%EC%8B%9C%EC%8A%A4%ED%85%9C-%EC%A0%81%EC%9A%A9-%EC%A0%84%EB%9E%B5.md)
- [FE-ADR-005. 클라이언트 상태 관리 전략.md](<./MVP/architecture/frontend/adr/FE-ADR-005. 클라이언트 상태 관리 전략.md>)
- [FE-ADR-006-가격-차트-라이브러리-선정.md](./MVP/architecture/frontend/adr/FE-ADR-006-가격-차트-라이브러리-선정.md)
- [FE-ADR-007-백엔드-REST-API-연동-및-통신-전략.md](./MVP/architecture/frontend/adr/FE-ADR-007-백엔드-REST-API-연동-및-통신-전략.md)
- [FE-ADR-008-실시간-채팅-WebSocket-연결-전략.md](./MVP/architecture/frontend/adr/FE-ADR-008-실시간-채팅-WebSocket-연결-전략.md)
- [FE-ADR-009-MVP-익명-사용자-식별-및-보안-토큰-관리-전략.md](./MVP/architecture/frontend/adr/FE-ADR-009-MVP-익명-사용자-식별-및-보안-토큰-관리-전략.md)

### `design-system/`

디자인 시스템 기준, Figma 설계 절차와 디자인 검증 문서를 관리한다. 승인된 토큰과 미리보기 자료는 함께 확인할 수 있다.

- [README.md](./design-system/README.md)
- [DS-001-디자인-시스템-현황.md](./design-system/DS-001-%EB%94%94%EC%9E%90%EC%9D%B8-%EC%8B%9C%EC%8A%A4%ED%85%9C-%ED%98%84%ED%99%A9.md)
- [tokens.json](./design-system/tokens/tokens.json)
- [index.html](./design-system/preview/index.html)

`figma/`는 Figma 설계 흐름과 토큰 동기화 정책을 담는다.

- [FG-001-Figma-설계-및-단계별-승인-기준.md](./design-system/figma/FG-001-Figma-%EC%84%A4%EA%B3%84-%EB%B0%8F-%EB%8B%A8%EA%B3%84%EB%B3%84-%EC%8A%B9%EC%9D%B8-%EA%B8%B0%EC%A4%80.md)
- [FG-002-컴포넌트-Variant-및-명명-규칙.md](./design-system/figma/FG-002-%EC%BB%B4%ED%8F%AC%EB%84%8C%ED%8A%B8-Variant-%EB%B0%8F-%EB%AA%85%EB%AA%85-%EA%B7%9C%EC%B9%99.md)
- [FG-003-화면-상태-프로토타입-설계.md](./design-system/figma/FG-003-%ED%99%94%EB%A9%B4-%EC%83%81%ED%83%9C-%ED%94%84%EB%A1%9C%ED%86%A0%ED%83%80%EC%9E%85-%EC%84%A4%EA%B3%84.md)
- [FG-004-디자인-토큰-동기화-정책.md](./design-system/figma/FG-004-%EB%94%94%EC%9E%90%EC%9D%B8-%ED%86%A0%ED%81%B0-%EB%8F%99%EA%B8%B0%ED%99%94-%EC%A0%95%EC%B1%85.md)

`verification/`는 디자인 요구사항의 추적, 의존성 및 검증 기준을 관리한다.

- [FV-001-요구사항-추적-및-검증-상태.md](./design-system/verification/FV-001-요구사항-추적-및-검증-상태.md)
- [FV-002-Override-및-의존성-관리.md](./design-system/verification/FV-002-Override-및-의존성-관리.md)
- [FV-003-접근성-반응형-E2E-검증-계획.md](./design-system/verification/FV-003-접근성-반응형-E2E-검증-계획.md)

### `env/`

개발 환경과 설정에 관한 프로젝트 문서를 보관한다.

- [ENV-001-카.md](./env/ENV-001-%EC%B9%B4.md)

### `.github/`

브랜치·커밋·PR 작성과 검토를 위한 저장소 운영 문서를 관리한다.

- [CONTRIBUTING.md](./.github/CONTRIBUTING.md)
- [PULL_REQUEST_TEMPLATE.md](./.github/PULL_REQUEST_TEMPLATE.md)
