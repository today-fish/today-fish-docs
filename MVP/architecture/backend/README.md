# 오늘의 수산 — 백엔드 ADR 모음

- **버전:** V1
- **상태:** 승인

**기준일:** 2026-10-29  
**범위:** 승인된 백엔드 기술 선정 및 운영 원칙
**작성 원칙:** 확정 결정과 후속 검증·미정 항목을 구분. 실제 코드·AWS 구성은 아직 검증 전.

## 문서 목차

| ADR                                                    | 주제               | 핵심 결정                                         |
| ------------------------------------------------------ | ------------------ | ------------------------------------------------- |
| [BE-ADR-001](BE-ADR-001-백엔드-아키텍처.md)            | 백엔드 아키텍처    | 가벼운 모듈형 모놀리스                            |
| [BE-ADR-002](BE-ADR-002-런타임-및-웹-프레임워크.md)    | 런타임/프레임워크  | Java 25 · Corretto 25 · Boot 4.1 · MVC/STOMP      |
| [BE-ADR-003](BE-ADR-003-빌드-및-의존성-관리.md)        | 빌드 도구          | Gradle 9.x · Kotlin DSL · Wrapper                 |
| [BE-ADR-004](BE-ADR-004-데이터-접근-및-영속성.md)      | 데이터 접근        | Spring Data JPA + 선택적 Spring JDBC              |
| [BE-ADR-005](BE-ADR-005-데이터베이스-및-AWS-인프라.md) | DB/인프라          | PostgreSQL · EC2 t2.micro · RDS db.t3.micro       |
| [BE-ADR-006](BE-ADR-006-스키마-변경-및-백업.md)        | 스키마/백업        | `ddl-auto=none`, 운영 전환 시 Flyway V1           |
| [BE-ADR-007](BE-ADR-007-가격수집-PDF-AI-파이프라인.md) | 수집/AI 파이프라인 | `@Scheduled` · 이중 원천 · 가격 필수 · PDF 조건부 |
| [BE-ADR-008](BE-ADR-008-AI-실행-아키텍처.md)           | AI 실행 아키텍처   | Spring Boot 직접 LLM 호출 · 백그라운드 작업       |

## Tech Spec 문서 목차

| 문서                                                                                       | 주제                         | 범위                                        |
| ------------------------------------------------------------------------------------------ | ---------------------------- | ------------------------------------------- |
| [BE-TECH-SPEC-001](tech-spec/BE-TECH-SPEC-001-데이터-수집-정규화-검증.md)                  | 데이터 수집·정규화·검증      | aT·KMI API 및 별도 발간물·기사 수집 경로    |
| [BE-TECH-SPEC-002](tech-spec/BE-TECH-SPEC-002-가격-데이터-모델링-및-산지-도매가격-산출.md) | 가격 데이터 모델링·산출      | 산지·도매 가격의 독립 집계와 기간 가격      |
| [BE-TECH-SPEC-003](tech-spec/BE-TECH-SPEC-003-PDF-기사-수집-및-정보-추출.md)               | PDF·기사 수집 및 정보 추출   | 원본 보존·Gemini 추출·Fact 및 Evidence 검증 |
| [BE-TECH-SPEC-004](tech-spec/BE-TECH-SPEC-004-Price-Insight-생성-검증-게시.md)             | Price Insight 생성·검증·게시 | 입력 선정·생성·검증·전체 원자적 게시        |
| [BE-TECH-SPEC-005](tech-spec/BE-TECH-SPEC-005-사용자-식별-인증-세션.md)                    | 익명 사용자 식별·인증        | JWT·CSRF·WebSocket Principal                |
| [BE-TECH-SPEC-006](tech-spec/BE-TECH-SPEC-006-실시간-채팅.md)                              | 실시간 채팅                  | 품목별 참여자 세션·3분 복구·STOMP 메시징    |

문서별 책임 경계와 병렬 입력 처리 흐름은 [tech-spec/README.md](tech-spec/README.md)를 단일 기준으로 따른다.

## 통합 데이터 모델

- [BE-ERD-001](erd/BE-ERD-001-통합-데이터-모델.md) — V1 승인, 18개 논리 테이블과 관계·키·제약의 통합 기준

## ADR 문서 구조

각 ADR은 **핵심 결론 → 배경/결정 → 검토한 대안(옵션별 장점·부담·선정 여부) → 선택 근거/운영 정책 → 재검토 조건** 순으로 작성했습니다. 확정된 기술과 조건부/미도입 대안을 표에서 구분합니다.

## 구현·운영 검증 항목

- JWT·CSRF·STOMP 통합 구현 및 Jackson 3·Hibernate 7 실호환 검증.
- 운영 배포에서 Flyway 실행 경로, DDL 계정·권한 분리, 백업 복구 훈련.
- EC2 t2.micro 500개 동시 WebSocket 연결 목표 성능 검증 및 AWS 실제 무료 사용 자격·월 비용 확인.
- KMI PDF 수집·가공 이용 조건과 PDF 기반 품목 가격 지표의 시간 단위 검증.

## 확정된 의사결정

- **Q8 AI 실행 아키텍처:** [BE-ADR-008](BE-ADR-008-AI-실행-아키텍처.md)에 따라 Spring Boot에서 외부 LLM API를 직접 호출한다.

> **주의:** 실제 코드·AWS 구성은 아직 검증 전이며, 미정 항목은 각 ADR의 상태와 후속 검증 항목을 확인하세요.
