# 오늘의 수산 — 프론트엔드 ADR 모음

**기준일:** 2026-10-29

**범위:** 오늘의 수산 MVP 프론트엔드 기술 선정 및 운영 원칙

**작성 원칙:** 확정된 결정과 후속 검증·미정 항목을 구분하고, 제품 요구사항은 PRD·PF·UX 문서를 기준으로 한다.

## 문서 목차

| ADR | 주제 | 핵심 결정 |
| --- | --- | --- |
| [FE-ADR-001](./adr/FE-ADR-001-프레임워크-및-버전-선정.md) | 프레임워크 | Next.js 16.x · React 19.x · App Router |
| [FE-ADR-002](./adr/FE-ADR-002-렌더링-전략-선정.md) | 렌더링 | SSG + CSR |
| [FE-ADR-003](./adr/FE-ADR-003-데이터-캐싱-및-갱신-전략.md) | 데이터 캐싱 | TanStack Query + Fetch API · staleTime 30분 · gcTime 60분 |
| [FE-ADR-004](./adr/FE-ADR-004-스타일링-및-디자인-시스템-적용-전략.md) | 스타일링·디자인 시스템 | Tailwind CSS + CSS 변수 · `tokens.json`을 디자인 값의 기준으로 사용 |
| [FE-ADR-005](<./adr/FE-ADR-005. 클라이언트 상태 관리 전략.md>) | 클라이언트 상태 | React 기본 Hooks + URL Search Params · 전역 상태 라이브러리 미도입 |
| [FE-ADR-006](./adr/FE-ADR-006-가격-차트-라이브러리-선정.md) | 가격 차트 | Recharts |
| [FE-ADR-007](./adr/FE-ADR-007-백엔드-REST-API-연동-및-통신-전략.md) | REST API 통신 | TanStack Query → 기능별 API 함수 → 공통 Fetch 클라이언트 |
| [FE-ADR-008](./adr/FE-ADR-008-실시간-채팅-WebSocket-연결-전략.md) | 실시간 채팅 | WebSocket(WSS) + STOMP · 탭별 연결 · 최근 메시지 100개 메모리 보관 |
| [FE-ADR-009](./adr/FE-ADR-009-MVP-익명-사용자-식별-및-보안-토큰-관리-전략.md) | 익명 사용자·보안 토큰 | 7일 익명 JWT HttpOnly Cookie + 별도 CSRF API |
| [FE-ADR-010](./adr/FE-ADR-010-프론트엔드-배포-및-CI-CD-전략.md) | 배포·CI/CD | Cloudflare Pages 정적 배포 · GitHub Actions · 선택적 Staging |
| [FE-ADR-011](./adr/FE-ADR-011-프론트엔드-오류-처리-및-사용자-피드백-전략.md) | 오류 처리·사용자 피드백 | 공통 오류 분류 + 기능별 오류 UI · 핵심 오류 Sentry 수집 |

## ADR 문서 구조

각 ADR은 핵심 결론과 배경, 선택한 결정 및 대안, 근거와 트레이드오프, 후속 검증 또는 재검토 조건을 기록한다. 세부 항목은 결정 주제에 따라 달라질 수 있다.

## 미정 의사결정 및 후속 검증

- 백엔드 API 요청·응답 계약과 익명 JWT·CSRF의 서버 측 연동 세부 사항
- 운영 도메인, CORS·쿠키·WebSocket Origin 설정 및 Staging 인프라
- 품목별 WebSocket 500명 부하, Heartbeat·재연결 정책의 실측 검증
- 오류 문구·Skeleton UI, Sentry 수집량과 보관 설정

## 관련 제품 문서

- [PRD-001 MVP 제품 요구사항](../../product/PRD-001-MVP-제품-요구사항.md) — 통합 MVP 범위 및 기능·비기능 요구사항
- [PD-012 MVP 범위](../../product/decisions/PD-012-MVP-범위.md) — 제품 결정으로 확정한 MVP 범위
- [PP-003 MVP 출시 인수 기준](../../product/policies/PP-003-MVP-출시-인수-기준.md) — 출시 검증 기준

제품 범위, 초기 지원 품목 또는 성능 목표와 ADR 사이에 차이가 있으면 이 README의 목록 순서만으로 우선순위를 정하지 말고 관련 제품 결정 문서를 확인한다.
