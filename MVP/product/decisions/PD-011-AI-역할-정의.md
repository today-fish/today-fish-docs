# PD-011 AI 역할 정의

## Status

Accepted

## 핵심 요약

* 오늘의 수산에서 AI는 **새로운 사실을 만들어내는 주체가 아니라, 데이터를 수집·정리·요약하는 도구**로 사용한다.
* MVP에서는 복수 AI Agent 구조를 사용하지 않고 **Collector AI를 중심으로 최소한의 AI 기능만 구현**한다.
* 정형 데이터는 AI가 아닌 API와 Batch 작업으로 수집한다.
* 뉴스, 정책, 연구자료, 트렌드 등 비정형 데이터는 Collector AI가 검색·분류·요약한다.
* Collector AI가 수집한 정보에는 반드시 출처와 원문 링크를 함께 저장한다.
* AI가 가격의 직접적인 원인을 근거 없이 생성하거나 데이터 공백을 임의로 추정해서는 안 된다.
* MVP에서는 AI 신뢰성 문제를 완전 자동화하지 않고 **간단한 규칙 검증 + 개발자 검수**를 활용한다.
* Verifier AI, Atomic Claim, Evidence Binding, 자동 Reject/Fallback 등의 신뢰성 시스템은 후속 개선 단계에서 도입한다.
* 하네스 엔지니어링은 MVP 필수 기능이 아니라 **AI 신뢰성과 자동화 수준을 높이기 위한 성능·품질 개선 과제**로 관리한다.
* AI 구현은 정확도뿐 아니라 비용, 개발 복잡도, 운영 가능성을 함께 고려한다.

---

# 1. AI를 사용하는 이유

오늘의 수산은 다음과 같이 서로 다른 형태의 데이터를 활용한다.

* 가격
* 생산량
* 출하량
* 수입·수출
* 수온
* 환경 데이터
* 정책
* 정부 보도자료
* 뉴스
* 트렌드
* 국제정세

이 중 정형 데이터는 API나 통계 형태로 비교적 쉽게 수집할 수 있다.

반면 뉴스, 정책, 연구자료와 같은 비정형 데이터는 사람이 지속적으로 탐색하고 정리하기 어렵다.

AI는 이러한 정보 탐색과 정리 비용을 줄이기 위해 사용한다.

---

# 2. AI의 기본 역할

오늘의 수산에서 AI의 역할은 다음과 같다.

> **사용 가능한 데이터를 찾고, 정리하고, 사용자가 이해할 수 있는 형태로 요약하는 것**

AI 자체가 새로운 시장 정보를 만들어내지 않는다.

---

# 3. AI는 데이터의 원 출처가 아니다

다음 구조를 기본 원칙으로 한다.

**원본 데이터 / 원문**

↓

AI

↓

요약 및 분류

AI가 생성한 문장은 원본 데이터보다 높은 신뢰 수준을 가지지 않는다.

AI Summary는 언제든 다시 생성할 수 있는 가공 정보다.

---

# 4. 정형 데이터 수집

정형 데이터는 AI를 사용하지 않는다.

예:

* 가격 API
* 생산량 API
* 출하량 API
* 수입·수출 API
* 수온 API
* 통계 API

수집 구조:

**External API**

↓

**Batch**

↓

**Normalize**

↓

**Database**

---

# 5. AI를 사용하지 않는 이유

정형 데이터를 AI를 통해 검색하면 다음 문제가 발생한다.

* 불필요한 AI 비용
* 최신성 문제
* 잘못된 숫자 생성 가능성
* 재현성 저하

따라서 제공 가능한 API나 공식 데이터가 존재한다면 직접 수집한다.

---

# 6. 비정형 데이터

AI는 다음과 같은 비정형 데이터 탐색에 활용한다.

* 뉴스
* 정부 보도자료
* 정책
* 연구자료
* 시장 이슈
* 소비 트렌드
* 국제정세

---

# 7. MVP Collector AI

MVP에서 구현하는 AI의 중심 역할을 `Collector AI`로 정의한다.

Collector AI는 오늘의 수산에 필요한 비정형 시장 정보를 찾고 정리한다.

---

# 8. Collector AI 역할

Collector AI는 다음 작업을 수행한다.

## Search

수산물과 관련된 새로운 자료를 탐색한다.

## Classification

수집된 자료가 어떤 품목과 관련되는지 분류한다.

## Category

자료의 성격을 분류한다.

예:

* 생산
* 환경
* 정책
* 수입
* 국제
* 트렌드

## Summary

사용자가 이해할 수 있도록 핵심 내용을 요약한다.

## Source

원 출처와 원문 링크를 함께 기록한다.

---

# 9. Collector AI 출력 예시

### 원문

남해안 일부 지역에서 고수온으로 조피볼락 양식장 피해가 보고되었다.

### Collector 결과

**관련 품목**

우럭

**Category**

환경 / 생산

**Summary**

남해안 일부 조피볼락 양식장에서 고수온 피해가 확인됨.

**Source**

원 기관 또는 언론사

**Original URL**

원문 링크

**Published At**

자료 게시일

---

# 10. Collector AI의 제한

Collector AI는 다음 판단을 임의로 수행하지 않는다.

> 고수온 때문에 우럭 가격이 상승했다.

원문에 가격과의 직접적인 인과관계가 없다면 이를 생성하지 않는다.

Collector AI의 주요 목적은

> **무슨 일이 있었는가?**

를 정리하는 것이다.

---

# 11. MVP Price Insight 생성

MVP에서는 Collector AI와 정형 데이터를 활용해 Price Insight에 필요한 시장 배경을 구성한다.

개념적 흐름:

**정형 데이터**

가격 / 생산 / 출하 / 수입 / 환경

*

**Collector AI**

뉴스 / 정책 / 트렌드 / 공식자료

↓

시장 배경 정리

↓

Price Insight

---

# 12. MVP에서 복수 AI Agent를 사용하지 않는다

초기에는 다음 구조를 구현하지 않는다.

**Collector AI**

↓

**Verifier AI**

↓

**Insight AI**

↓

**Output Validator**

이 구조는 높은 신뢰성을 제공할 수 있지만 초기 MVP에서 다음 비용이 발생한다.

* AI 호출 증가
* 개발 복잡도 증가
* 토큰 비용 증가
* 테스트 범위 증가
* 운영 난이도 증가

---

# 13. MVP Trade-off

오늘의 수산은 MVP에서

> **완전 자동화보다 낮은 비용과 구현 단순성을 우선한다.**

이는 AI 신뢰성의 중요성을 낮게 평가하기 때문이 아니다.

초기 사용자와 데이터 규모에서는 복잡한 자동 검증 시스템보다 개발자가 일부 검수하는 것이 비용과 개발시간 측면에서 현실적이라고 판단한다.

---

# 14. MVP 신뢰성 관리

MVP에서는 다음 수준의 검증을 수행한다.

## Source 제한

신뢰할 수 있는 출처를 우선 검색한다.

## 원문 링크 저장

Collector AI가 사용한 자료의 원문 URL을 저장한다.

## 수집 시점 저장

언제 발견하고 수집했는지 기록한다.

## 기본 구조 검증

필수 데이터가 존재하는지 확인한다.

예:

* Source
* URL
* Published Date
* Related Species
* Category

## 개발자 검수

필요한 경우 Price Insight 게시 전 개발자가 실제 근거를 확인한다.

---

# 15. Human-in-the-loop

MVP에서는 개발자가 AI 검증 과정의 일부를 담당할 수 있다.

개념적 구조:

**Collector AI**

↓

**기본 자동 검증**

↓

**Human Review**

↓

**Price Insight**

---

# 16. Human Review를 선택한 이유

초기에는 수집되는 데이터량이 제한적일 가능성이 높다.

이 단계에서 복잡한 Verifier AI를 개발하고 지속적으로 호출하는 것보다 중요한 Insight를 사람이 직접 검토하는 방식이 효율적일 수 있다.

---

# 17. AI가 하면 안 되는 일

## 출처 없는 사실 생성

AI가 확인되지 않은 새로운 사실을 생성해서는 안 된다.

---

## 직접적인 인과관계 생성

근거가 없는 경우 다음과 같이 표현하지 않는다.

> 고수온 때문에 우럭 가격이 상승했다.

---

## 가격 생성

실제 가격 데이터가 없는 시점의 가격을 AI가 임의로 생성하지 않는다.

---

## 데이터 공백 보정

데이터가 없다는 이유로 AI가 예상값을 만들어 실제 데이터처럼 제공하지 않는다.

---

## 존재하지 않는 출처 생성

원문 링크나 기관명을 AI가 임의로 생성하지 않는다.

---

## 근거 부족 상태 은폐

설명 가능한 근거가 없다면 다음 상태를 허용한다.

> 파악 중

---

# 18. AI 비용 원칙

AI 호출은 서비스 비용에 직접적인 영향을 준다.

따라서 다음 원칙을 적용한다.

## 불필요한 AI 호출 금지

코드 또는 API로 처리할 수 있는 작업에 AI를 사용하지 않는다.

## 동일 결과 재사용

동일한 시장 데이터를 여러 사용자가 조회하더라도 AI를 매번 호출하지 않는다.

## Batch 기반 처리

사용자 요청 시점보다 데이터 갱신 시점에 AI 분석을 수행하는 방향을 우선한다.

## Cache

생성된 결과를 저장하고 재사용한다.

---

# 19. 사용자 수와 AI 비용 분리

오늘의 수산은 다음 구조를 지향한다.

**데이터 변경**

↓

AI 분석

↓

결과 저장

↓

사용자 A

사용자 B

사용자 C

↓

동일 결과 조회

이를 통해 사용자 수가 증가하더라도 AI 호출량이 동일한 비율로 증가하지 않도록 한다.

---

# 20. 향후 신뢰성 개선

서비스 규모와 데이터량이 증가하면 개발자 검수만으로 운영하기 어려워질 수 있다.

이 시점부터 AI 신뢰성 자동화를 단계적으로 도입한다.

---

# 21. Reliability Phase 1 — Evidence 구조화

수집된 정보를 단순 요약문보다 구조화된 Evidence 형태로 관리한다.

예:

* Source
* Document
* Species
* Category
* Date
* Summary
* Original URL

---

# 22. Reliability Phase 2 — Atomic Claim

문서 안의 주요 사실을 작은 Claim 단위로 분리한다.

예:

### Claim A

고수온이 발생했다.

### Claim B

조피볼락 피해가 확인되었다.

### Claim C

생산량이 감소했다.

### Claim D

생산량 감소가 가격 상승을 발생시켰다.

각 Claim은 서로 다른 근거 수준을 가질 수 있다.

---

# 23. Reliability Phase 3 — Verifier AI

Verifier AI를 도입하여

> Claim이 실제 원문에 의해 뒷받침되는가?

를 검사할 수 있다.

예:

* SUPPORTED
* PARTIALLY_SUPPORTED
* UNSUPPORTED
* CONTRADICTED

---

# 24. Verifier AI 비용 문제

Verifier AI를 모든 문서와 Claim에 사용하면 AI 비용이 크게 증가할 수 있다.

따라서 향후 도입 시에도 모든 데이터에 동일한 검증을 적용하지 않는다.

---

# 25. 단계적 검증

우선 저비용 검증을 수행하고 필요한 데이터만 높은 비용의 검증으로 전달한다.

예:

**100개 자료**

↓

코드 필터

↓

중복 제거

↓

관련성 필터

↓

중요 Evidence 후보

↓

필요한 자료만 Verifier AI

---

# 26. Model Routing

모든 작업에 동일한 AI 모델을 사용하지 않는다.

향후 다음 구조를 검토한다.

## 저비용 모델

* 문서 분류
* 품목 태깅
* 카테고리 분류

## 정밀 모델

* Claim 검증
* 복잡한 시장 정보 해석

이를 통해 정확성과 비용 사이의 균형을 맞춘다.

---

# 27. Harness Engineering

AI 신뢰성을 자동화하는 단계에서 Harness Engineering을 도입한다.

Harness Engineering은 AI를 더 똑똑하게 만드는 것이 아니라

> **AI가 실수해도 검증되지 않은 결과가 사용자에게 전달되지 않도록 주변 시스템을 설계하는 것**

을 목표로 한다.

---

# 28. Harness Engineering 후보

향후 다음 기능을 검토한다.

* Tool 제한
* Context 제한
* Structured Output
* Evidence Binding
* Claim Verification
* Source Deduplication
* Conflict Detection
* Automatic Reject
* Fallback
* AI Evaluation
* Regression Test
* Model Routing

---

# 29. Evidence Binding

향후 Price Insight의 각 주요 주장에 Evidence ID를 연결하는 구조를 검토한다.

예:

**주요 요인**

출하량 감소

**Evidence**

E103

근거가 없는 요인은 사용자에게 노출하지 않는다.

---

# 30. 자동 Fallback

향후 검증 실패 시 AI에게 계속 답을 생성하도록 하지 않는다.

예:

Evidence 부족

↓

Validation 실패

↓

> **파악 중**

상태로 종료한다.

---

# 31. AI Evaluation

AI 시스템이 고도화되면 실제 시장 사례를 기반으로 평가셋을 구축한다.

예:

### Case A

고수온과 가격 상승이 동시에 발생했지만 직접 인과근거 없음.

Expected:

직접 원인으로 단정하지 않음.

### Case B

공식기관이 가격 상승 원인을 직접 설명.

Expected:

출처와 함께 원인 표현 가능.

### Case C

관련 Evidence 없음.

Expected:

파악 중.

---

# 32. AI 고도화 로드맵

## MVP

**Collector AI**

*

기본 Source 저장

*

간단한 규칙 검증

*

Human Review

↓

## Reliability Improvement

Evidence 구조화

Atomic Claim

Verifier AI

Source Deduplication

Conflict Detection

↓

## Harness Engineering

Evidence Binding

Structured Output

Automatic Reject

Fallback

AI Evaluation

Regression Test

Model Routing

---

# 33. MVP에서 하지 않는 것

초기 버전에서는 다음을 구현하지 않는다.

* 모든 Claim 자동 검증
* 복수 AI Agent Pipeline
* 고비용 AI Cross Validation
* 자동 인과관계 검증
* 복잡한 신뢰 점수
* 완전 자동화된 AI Harness

이들은 명시적인 향후 개선사항으로 관리한다.

---

# 34. 기술 부채가 아닌 계획된 확장

MVP에서 AI 검증 시스템을 단순화하는 것을 무계획한 기술 부채로 보지 않는다.

현재 프로젝트의

* 1인 개발
* 비용 최소화
* 제한된 초기 사용자
* 제한된 MVP 범위

를 고려한 의도적인 선택이다.

서비스 규모가 커지면 신뢰성 시스템을 단계적으로 추가한다.

---

# 35. 현재 Decision

오늘의 수산 MVP에서는

> **Collector AI를 중심으로 비정형 데이터를 수집·분류·요약한다.**

정형 데이터는 API와 Batch Pipeline으로 관리한다.

AI 결과에는 반드시 가능한 범위에서 원 출처를 연결한다.

초기 검증은 기본적인 시스템 검증과 Human Review를 활용한다.

---

# 36. 후속 기술 결정

다음 내용은 Product Decision에서 결정하지 않는다.

별도 Tech Spec 및 ADR에서 설계한다.

* LLM Provider
* AI Model
* 검색 도구
* 웹 수집 방식
* Prompt
* Collector 실행 주기
* Batch 주기
* Cache TTL
* AI 호출 제한
* Evidence Schema
* Admin Review UI
* 향후 Verifier AI 구조
* Harness 구현 방식

---

# 37. 최종 결론

오늘의 수산은 AI를 서비스의 주인공으로 만들지 않는다.

AI는

> **시장을 이해하는 데 필요한 정보를 빠르게 수집하고 정리하기 위한 도구**

다.

MVP에서는 Collector AI를 중심으로 최소한의 구조를 구현하고,

신뢰성 문제는

> **Source 관리 + 기본 검증 + Human Review**

를 통해 관리한다.

서비스가 성장하고 자동화 필요성이 증가하면

> **Verifier AI → Evidence 구조화 → Harness Engineering**

순서로 신뢰성 시스템을 고도화한다.

이를 통해 AI 정확성뿐 아니라 **개발 복잡도와 운영 비용까지 고려한 현실적인 AI 아키텍처**를 지향한다.
