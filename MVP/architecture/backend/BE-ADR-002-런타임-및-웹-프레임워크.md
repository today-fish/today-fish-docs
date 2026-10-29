# BE-ADR-002 — Java 런타임 및 Spring Boot

- **상태:** 승인
- **결정:** 2026-10-29

## 핵심 결론

**Java 25 LTS / Amazon Corretto 25 / Spring Boot 4.1.x / Spring MVC**를 채택한다. 실시간 채팅은 Spring WebSocket + STOMP + Simple Broker를 사용한다.

## 배경

신규 프로젝트이며, AWS 기반 운영과 향후 상업화 가능성, 보안 패치, 1인 개발자의 업데이트 부담을 고려한다.

## 결정

- Java 메이저 버전: **25 LTS**. 런타임 배포판은 **Amazon Corretto 25**.
- Spring Boot **4.1.x**의 유지보수 중인 패치 릴리스를 사용한다. 정확한 패치 번호는 프로젝트 생성·업데이트 시 고정한다.
- 웹 API는 **Spring MVC**. WebFlux 전면 도입은 하지 않는다.
- 채팅은 기존 FE 계약에 맞춰 **WebSocket/STOMP + Spring Simple Broker**를 사용한다.
- Virtual Threads는 **초기 비활성화**하고 블로킹 작업·성능 측정 결과에 따라 재평가한다.
- 개발/CI/운영 환경은 동일 Java 메이저와 가능하면 동일 Corretto 배포판을 사용한다.
- Spring Boot OSS와 Corretto의 무료 상업적 사용을 전제로 하며, 유료 Spring Enterprise는 도입하지 않는다.

## 검토한 대안

**Java 런타임 및 JDK 배포판**

| 대안 | 고려한 장점 | 주요 부담·제약 | 판단 |
|---|---|---|---|
| Java 21 LTS | 검증된 런타임과 축적된 실무 사례 | Java 25보다 지원 기간이 짧고 최신 Virtual Threads 개선이 없음 | 미채택 |
| **Java 25 LTS** | 더 긴 지원 경로, Virtual Threads 관련 JVM 개선 | 상대적으로 새로운 런타임이므로 실제 의존성·성능 검증 필요 | **채택** |
| Oracle JDK 25 | Oracle의 정식 JDK 배포판 | 업데이트 시점에 따른 라이선스 조건 확인 필요 | 미채택 |
| **Amazon Corretto 25** | 무료 상업 사용, 장기 보안 패치, AWS 운영 환경과 일관성 | JDK 보안 패치는 운영자가 반영·재배포해야 함 | **채택** |

**Spring Boot 및 웹 모델**

| 대안 | 고려한 장점 | 주요 부담·제약 | 판단 |
|---|---|---|---|
| Spring Boot 3.5.x | 기존 Jackson 2·Security 6 생태계와 축적된 사례 | 신규 프로젝트의 4.x 전환 부담, OSS 지원 수명 | 미채택 |
| Spring Boot 4.0.x | Framework 7·Security 7·Jackson 3로 신규 개발 가능 | 4.1보다 앞선 마이너 릴리스, 지원 주기상 불리 | 미채택 |
| **Spring Boot 4.1.x** | Java 25 지원, 4.x 생태계에 바로 진입, 신규 유지보수 경로 | Jakarta EE 11·Jackson 3·Security 7 및 서드파티 호환성 검증 필요 | **채택** |
| **Spring MVC + STOMP** | JPA/JDBC 블로킹 모델, 기존 채팅 계약에 부합 | 스레드·Executor와 웹소켓 부하 관리 필요 | **채택** |
| Spring WebFlux 전면 적용 | 논블로킹 I/O 중심의 높은 동시성 모델 | Reactor 학습·디버깅 부담, JPA의 블로킹 경계 처리 필요 | 미채택 |
| Virtual Threads 초기 활성화 | 블로킹 대기 많은 워크로드에서 확장 가능성 | 현 STOMP 부하에서 이점 미검증; DB 풀 등 자원 제한 필요 | **활성화 보류** |

## 선택 근거

- Corretto 25는 장기 업데이트 경로를 제공하며 AWS 운영 환경에 일관되게 적용할 수 있다.
- Boot 4.1은 신규 코드에 Spring Framework 7, Security 7, Jackson 3, Jakarta EE 11 계열을 적용해 Boot 3→4 전환 비용을 피한다.
- 현재의 JPA/REST/STOMP에 WebFlux가 요구되지 않는다. Virtual Threads도 WebSocket 연결 수 자체를 줄이지 않는다.

## 호환성·보안 검증

- Jakarta Persistence/Validation/Servlet 및 내장 Tomcat 조합 검증.
- Jackson 3 기반 REST·STOMP JSON 계약(날짜·단위·필드명 등) 검증.
- 익명 JWT 쿠키, CSRF, STOMP CONNECT, Origin/구독 권한 검증.
- JPA/Hibernate, DB 드라이버, 외부 JWT 라이브러리의 실제 통합 테스트.
- JDK 패치·Spring Boot 패치·서드파티 취약점은 각각 추적하고 정기 업데이트한다.

## 재검토 조건

지원 종료, 주요 호환성 문제, 부하 테스트 결과 또는 라이선스·보안 정책 변경.
