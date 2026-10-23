# 프론트엔드 아키텍처

이 디렉토리는 오늘의 수산 MVP 프론트엔드의 기술 선택과 구현 기준을 기록한다. 제품 범위와 사용자 요구사항은 PRD·PF·UX 문서를 기준으로 하고, 이 문서의 ADR은 해당 요구사항을 만족하기 위한 프론트엔드 기술 결정을 설명한다.

## ADR 읽기 순서

1. [FE-ADR-001 프레임워크 및 버전 선정](./adr/FE-ADR-001-프레임워크-및-버전-선정.md) — Next.js, React, App Router
2. [FE-ADR-002 렌더링 전략 선정](./adr/FE-ADR-002-렌더링-전략-선정.md) — SSG + CSR
3. [FE-ADR-003 데이터 캐싱 및 갱신 전략](./adr/FE-ADR-003-데이터-캐싱-및-갱신-전략.md) — TanStack Query, Fetch API, 캐시·오류 정책
4. [FE-ADR-004 스타일링 및 디자인 시스템 적용 전략](./adr/FE-ADR-004-스타일링-및-디자인-시스템-적용-전략.md)
5. [FE-ADR-005 클라이언트 상태 관리 전략](<./adr/FE-ADR-005. 클라이언트 상태 관리 전략.md>)
6. [FE-ADR-006 가격 차트 라이브러리 선정](./adr/FE-ADR-006-가격-차트-라이브러리-선정.md)
7. [FE-ADR-007 백엔드 REST API 연동 및 통신 전략](./adr/FE-ADR-007-백엔드-REST-API-연동-및-통신-전략.md)
8. [FE-ADR-008 실시간 채팅 WebSocket 연결 전략](./adr/FE-ADR-008-실시간-채팅-WebSocket-연결-전략.md)

## 관련 제품 문서

- [PRD-001 MVP 제품 요구사항](../../product/PRD-001-MVP-제품-요구사항.md) — 통합 MVP 범위 및 기능·비기능 요구사항
- [PD-012 MVP 범위](../../product/decisions/PD-012-MVP-범위.md) — 제품 결정으로 확정한 MVP 범위
- [PP-003 MVP 출시 인수 기준](../../product/policies/PP-003-MVP-출시-인수-기준.md) — 출시 검증 기준

제품 범위, 초기 지원 품목 또는 성능 목표와 ADR 사이에 차이가 있으면 이 README의 읽기 순서만으로 우선순위를 정하지 말고 관련 제품 결정 문서를 확인한다.
