# 오늘의 수산 — 백엔드 ADR 모음

**기준일:** 2026-10-29  
**범위:** 이번 논의에서 합의된 백엔드 기술 선정 및 운영 원칙  
**작성 원칙:** 확정 결정과 후속 검증·미정 항목을 구분. 실제 코드·AWS 구성은 아직 검증 전.

## 문서 목차

| ADR | 주제 | 핵심 결정 |
|---|---|---|
| [BE-ADR-001](BE-ADR-001-백엔드-아키텍처.md) | 백엔드 아키텍처 | 가벼운 모듈형 모놀리스 |
| [BE-ADR-002](BE-ADR-002-런타임-및-웹-프레임워크.md) | 런타임/프레임워크 | Java 25 · Corretto 25 · Boot 4.1 · MVC/STOMP |
| [BE-ADR-003](BE-ADR-003-빌드-및-의존성-관리.md) | 빌드 도구 | Gradle 9.x · Kotlin DSL · Wrapper |
| [BE-ADR-004](BE-ADR-004-데이터-접근-및-영속성.md) | 데이터 접근 | Spring Data JPA + 선택적 Spring JDBC |
| [BE-ADR-005](BE-ADR-005-데이터베이스-및-AWS-인프라.md) | DB/인프라 | PostgreSQL · EC2 t2.micro · RDS db.t3.micro |
| [BE-ADR-006](BE-ADR-006-스키마-변경-및-백업.md) | 스키마/백업 | `ddl-auto=none`, 운영 전환 시 Flyway V1 |
| [BE-ADR-007](BE-ADR-007-가격수집-PDF-AI-파이프라인.md) | 수집/AI 파이프라인 | `@Scheduled` · 이중 원천 · 가격 필수 · PDF 조건부 |

## ADR 문서 구조

각 ADR은 **핵심 결론 → 배경/결정 → 검토한 대안(옵션별 장점·부담·선정 여부) → 선택 근거/운영 정책 → 재검토 조건** 순으로 작성했습니다. 확정된 기술과 조건부/미도입 대안을 표에서 구분합니다.

## 미정 의사결정

- **Q8 AI 실행 아키텍처:** Spring Boot 외부 LLM API 직접 호출, Python Worker, 관리형 워크플로 비교.
- JWT·CSRF·STOMP 통합 구현 및 Jackson 3·Hibernate 7 실호환 검증.
- 운영 배포에서 Flyway 실행 경로, DDL 계정·권한 분리, 백업 복구 훈련.
- EC2 t2.micro 500개 동시 WebSocket 연결 목표 성능 검증 및 AWS 실제 무료 사용 자격·월 비용 확인.
- KMI PDF 수집·가공 이용 조건과 PDF 기반 품목 가격 지표의 시간 단위 검증.

> **주의:** 이 문서들은 논의 내용을 반영한 신규 ADR 초안입니다. 기존 저장소의 ADR 번호 체계와 파일 경로에 맞춰 반영할 때 번호 충돌 여부를 확인하세요.
