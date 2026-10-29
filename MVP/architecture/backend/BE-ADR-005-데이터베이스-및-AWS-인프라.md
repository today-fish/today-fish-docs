# BE-ADR-005 — 데이터베이스 및 AWS 운영 인프라

- **상태:** 승인(성능·무료 사용 자격 검증 조건)
- **결정:** 2026-10-29

## 핵심 결론

**PostgreSQL을 AWS RDS Single-AZ `db.t3.micro`에서 운영하고, 백엔드는 EC2 `t2.micro`에서 별도로 실행한다.** NoSQL과 Redis는 초기 도입하지 않는다.

## 배경

가격·시장·품목·기간별 정형 데이터를 관계형으로 저장하고, 향후 KMI PDF에서 추출한 가격·수급 정보와 AI 결과를 연결해야 한다. 1인 개발과 낮은 운영 복잡도를 우선한다.

## 결정

- DBMS: **PostgreSQL**. 구체적 DB 메이저 버전은 RDS 지원 버전·패치 정책을 확인해 구축 시 고정한다.
- 운영: **Amazon RDS PostgreSQL Single-AZ, `db.t3.micro`**.
- 애플리케이션: **EC2 `t2.micro`**, Spring Boot 및 STOMP 단일 서버.
- DB는 외부 공개하지 않고, 가능한 한 같은 리전·VPC의 EC2에서만 DB 포트 접근을 허용한다.
- NoSQL/Redis/별도 분석 DB는 MVP에서 도입하지 않는다.
- PDF 원본 보관 필요 시 S3를 별도로 검토한다. 정형 추출 데이터와 출처 메타데이터는 PostgreSQL에 저장하고, 유연한 부가 정보는 필요 시 JSONB를 사용한다.
- DB 정기 백업은 RDS 자동 백업과 PITR을 중심으로 구성하고, 위험한 변경 전에는 수동 스냅샷을 검토한다.

## 검토한 대안

**DBMS 선정**

| 대안 | 고려한 장점 | 주요 부담·제약 | 판단 |
|---|---|---|---|
| **PostgreSQL** | 관계형 무결성·집계 SQL·JSONB·향후 문서/벡터 검색 확장 선택지 | 운영 지식 필요, 검색 확장은 현재 잠재적 이점 | **채택** |
| MySQL | JPA/JDBC·집계 쿼리 충분, 익숙한 CRUD 운영 | PostgreSQL의 일부 인덱스·확장 선택지와 차이 | 미채택; MVP 기능 충족 가능 |
| Firebase Firestore/Realtime Database | 실시간 동기화·관리형 BaaS 기능 | 기존 JPA·STOMP 설계와 중복, 관계형 집계·클라우드 이원화 부담 | 미채택 |
| MongoDB 등 문서형 NoSQL | 유연한 문서 스키마 | 가격·시장·품목 관계와 집계, 복수 저장소 운영 비용 | 초기 미채택 |

**AWS 배치 및 운영 방식**

| 대안 | 고려한 장점 | 주요 부담·제약 | 판단 |
|---|---|---|---|
| EC2 `t2.micro`에 앱+PostgreSQL 함께 설치 | 별도 DB 인스턴스 비용 감소 가능 | 1 GiB 메모리 경합, 백업·패치·장애 복구 직접 운영 | 미채택 |
| EC2 + 별도 EC2 PostgreSQL | 앱과 DB 자원 격리 | DB 서버의 OS·백업·복구 관리 책임 지속 | 미채택 |
| **EC2 `t2.micro` + RDS `db.t3.micro` Single-AZ** | JVM/DB 리소스 분리, 관리형 백업·유지보수, 단순한 운영 책임 | RDS 추가 요금·Single-AZ 장애 위험·소형 인스턴스 성능 제한 | **채택(성능·비용 검증 조건)** |
| RDS Multi-AZ | 장애 대응 가용성 향상 | 초기 월 운영비 증가 | MVP 미채택 |

## 기술 선정 근거

- PostgreSQL·MySQL 모두 핵심 가격 집계와 JPA를 충족한다. PostgreSQL은 JSONB, 고급 인덱스 및 향후 문서/벡터 검색 확장 선택지를 고려해 선택했다. **일반적인 JOIN/CRUD가 무조건 더 빠르다는 주장은 근거로 사용하지 않는다.**
- Firebase Firestore/Realtime Database는 현재 JPA 중심 관계형 가격 집계와 STOMP 아키텍처의 이점이 크지 않아 채택하지 않는다.
- RDS는 EC2의 제한된 메모리를 DB와 경쟁시키지 않고 백업·유지보수 부담을 줄인다.

## 주의·검증 사항

- `t2.micro`: 1 vCPU / 1 GiB 메모리. 500개 동시 STOMP 연결 목표 달성은 **미검증**이며 실제 부하 테스트 필수.
- `db.t3.micro`: 2 vCPU / 1 GiB 메모리. DB 연결 풀, 쿼리·인덱스, CPU 크레딧을 측정한다.
- 계정 생성 시점 및 AWS 정책에 따라 `t2.micro`와 RDS의 무료 크레딧·Free Tier 적용 여부가 달라질 수 있다. **무료 운영을 보장하지 않는다.**
- 무료 크레딧 종료 후 서울 리전 기준 EC2·RDS·스토리지·백업·네트워크 비용을 확인한다.
- Single-AZ는 관리형 DB이지만 고가용성을 보장하는 Multi-AZ 구성은 아니다.

## 재검토 조건

메모리·CPU·DB 연결 병목, 실제 청구 비용 초과, 가용성 요구 증가, 검색 기능 확대.
