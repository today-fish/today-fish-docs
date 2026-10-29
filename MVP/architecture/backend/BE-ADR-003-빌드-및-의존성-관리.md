# BE-ADR-003 — 빌드 및 의존성 관리

- **상태:** 승인
- **결정:** 2026-10-29

## 핵심 결론

**Gradle 9.x + Kotlin DSL**을 사용하고, **Gradle Wrapper**로 실행 버전을 고정한다.

## 결정

- 빌드 스크립트: `build.gradle.kts`, `settings.gradle.kts`.
- Gradle은 Java 25 실행을 지원하는 **9.1 이상 9.x**를 사용한다. 정확한 릴리스는 Wrapper 설정에 고정한다.
- Java Toolchain을 **25**로 지정한다. Mac·CI 환경에 Corretto 25를 명시적으로 제공한다.
- Spring Boot 플러그인과 BOM 기반의 의존성 버전 관리를 우선한다.
- 라이브러리 저장소는 기본적으로 Maven Central을 사용한다.
- 로컬과 CI에서는 `./gradlew`를 사용한다.
- GitHub Actions에서 컴파일, 정적 검사(도입 시), 테스트, `bootJar` 생성 및 산출물 검증을 수행한다.

## 검토한 대안

| 대안 | 고려한 장점 | 주요 부담·제약 | 판단 |
|---|---|---|---|
| Maven 3.9.x | XML 선언형, 널리 알려진 표준 빌드 생명주기 | 설정이 길어질 수 있으며 Kotlin DSL의 타입 기반 편집 경험은 없음 | 미채택 |
| Gradle 9.x + Groovy DSL | 유연하고 간결한 빌드 스크립트, 다양한 기존 예제 | 동적 DSL 특성상 일부 설정 오류를 실행·평가 중 발견 | 미채택 |
| **Gradle 9.x + Kotlin DSL** | Gradle 빌드·캐시 활용, 정적 타입 검사·IDE 자동완성으로 설정 오류를 조기 발견 | Kotlin DSL 학습 비용 및 최초 스크립트 컴파일 비용 | **채택** |
| 전역 Gradle 설치 기반 실행 | 개인 PC에서 간단히 실행 | 로컬·CI 간 Gradle 버전 불일치 위험 | 미채택; Wrapper 사용 |

## 선택 근거

Kotlin DSL은 Gradle API의 타입 기반 검사·자동완성으로 빌드 설정 오류를 상대적으로 일찍 발견할 수 있다. Wrapper는 팀원과 CI 사이 빌드 도구 버전 차이를 줄인다.

## 한계와 운영 수칙

- Kotlin DSL이 런타임 호환성이나 의존성 충돌을 자동 해결하지는 않는다.
- 필요 시 `dependencies`, `dependencyInsight`로 실제 해석된 버전을 확인한다.
- 의존성 패치와 JDK·Gradle 자체 업데이트를 구분해 수행한다.
- 초기에는 단일 Gradle 프로젝트로 유지한다. 다중 모듈은 필요할 때만 도입한다.
