# 오늘의 수산 프로젝트 문서 목차

이 문서는 오늘의 수산 프로젝트 전체 문서를 탐색하기 위한 통합 목차다. 상세 요구사항과 의사결정의 최종 기준은 각 원본 문서이며, 이 문서는 필요한 정보를 빠르게 찾기 위한 문서 지도다.

## 이 문서의 사용 방법

새로운 제품 기획, 설계 또는 개발 검토를 시작할 때 이 목차를 먼저 확인한다. 관련 문서를 찾은 후 반드시 원본 문서를 읽고 판단한다.

여러 문서의 내용이 충돌하면 임의로 해석하지 말고 다음 순서로 확인한다.

1. 문서 상태와 결정·가설의 구분
2. 작성일 또는 수정일
3. 상위 문제·제품 결정 문서
4. 관련 사용자 리서치와 근거
5. 최신 `Accepted` 결정

현재 문서에는 작성일·수정일이 없으므로, 충돌을 발견하면 결정권자에게 확인하고 후속 결정 문서로 기록한다.

## Repository 구조

### Repository root

* [`README.md`](./README.md) — **오늘의 수산 프로젝트 문서**: 저장소 첫 화면과 `INDEX.md` 진입 링크
* [`DOCUMENT-CHECK-HISTORY.md`](./DOCUMENT-CHECK-HISTORY.md) — **문서 일관성 검사 이력**: 검사 결과와 다음 baseline 기록
* `AGENTS.md` — **Repository Guidelines**: 로컬 AI Agent용 언어 규칙이며 Git에서는 제외한다.
* `INDEX.md`: 전체 문서의 위치, 역할, 관계를 안내하는 통합 목차

### `MVP/product/decisions/`

현재 `PD-NNN` 문서가 위치한다. `PD-NNN`은 변경하지 않는 문서 식별자다.

### `MVP/product/`

제품 전체 요구사항을 정의하는 `PRD-NNN` 문서가 위치한다.

### `MVP/product/features/`

화면과 기능별 상세 요구사항을 정의하는 `PF-NNN` 문서가 위치한다.

### `MVP/product/policies/`

여러 기능에 공통 적용되는 운영·출시 정책을 정의하는 `PP-NNN` 문서가 위치한다. `PP-001 가격 데이터 처리 정책`은 작성 예정이다.

### `MVP/research/user/`

현재 `UR-NNN` 문서가 위치한다. 문서를 읽을 때 관찰된 사실과 제품 가설을 구분한다.

### `MVP/poc/`

현재 `POC-NNN` 문서가 위치한다. `POC-NNN`은 변경하지 않는 문서 식별자다.

## 프로젝트 문서 흐름

### 1. 사용자와 문제 이해

1. [UR-001 제철 음식 소비 트렌드 리서치](./MVP/research/user/UR-001-제철-음식-소비-트렌드-리서치.md)에서 계절 경험 가설의 근거를 확인한다.
2. [PD-001 서비스 문제 정의](./MVP/product/decisions/PD-001-서비스-문제-정의.md)에서 해결할 정보 비대칭과 Price Insight의 출발점을 확인한다.
3. [PD-002 핵심 타깃 사용자](./MVP/product/decisions/PD-002-핵심-타깃-사용자.md)와 [PD-003 핵심 페르소나](./MVP/product/decisions/PD-003-핵심-페르소나.md)에서 누구를 위해 설계하는지 확인한다.

### 2. 제품 정의와 경험

1. [PD-004 서비스 포지셔닝](./MVP/product/decisions/PD-004-서비스-포지셔닝.md)에서 Primary Flow와 제품 경계를 확인한다.
2. [PD-007 감성적 가치](./MVP/product/decisions/PD-007-감성적-가치.md)에서 기능적 가치와 계절 경험의 연결 원칙을 확인한다.

### 3. MVP 기능 기준

1. [PD-012 MVP 범위](./MVP/product/decisions/PD-012-MVP-범위.md)에서 현재 구현 범위와 우선순위를 확인한다.
2. [PD-009 기준가격 정의](./MVP/product/decisions/PD-009-기준가격-정의.md)에서 차트와 분석의 기준값을 확인한다.
3. [PD-008 Price Insight](./MVP/product/decisions/PD-008-Price-Insight.md)에서 핵심 기능의 데이터 범위와 표현 정책을 확인한다.
4. [PD-010 데이터 신뢰 정책](./MVP/product/decisions/PD-010-데이터-신뢰-정책.md)에서 출처와 Evidence 사용 원칙을 확인한다.
5. [PD-011 AI 역할 정의](./MVP/product/decisions/PD-011-AI-역할-정의.md)에서 MVP AI 범위와 후속 신뢰성 로드맵을 확인한다.
6. [PD-013 가격 데이터 PoC 적용 원칙](./MVP/product/decisions/PD-013-가격-데이터-PoC-적용-원칙.md)에서 PoC 결과를 제품 정책에 반영하는 경계와 후속 검증 조건을 확인한다.
7. [PRD-001 MVP 제품 요구사항](./MVP/product/PRD-001-MVP-제품-요구사항.md)에서 확정 MVP 범위와 기능 간 사용자 여정을 확인한다.
8. [PF-001 홈 화면](./MVP/product/features/PF-001-홈-화면.md), [PF-002 수산물 가격 차트](./MVP/product/features/PF-002-수산물-가격-차트.md), [PF-003 Price Insight](./MVP/product/features/PF-003-Price-Insight.md), [PF-004 최근 이슈](./MVP/product/features/PF-004-최근-이슈.md), [PF-005 실시간 채팅](./MVP/product/features/PF-005-실시간-채팅.md)에서 기능별 요구사항과 인수 기준을 확인한다.
9. [PP-002 AI 분석 운영 정책](./MVP/product/policies/PP-002-AI-분석-운영-정책.md)과 [PP-003 MVP 출시 인수 기준](./MVP/product/policies/PP-003-MVP-출시-인수-기준.md)에서 공통 운영 정책과 출시 게이트를 확인한다.
10. [POC-001 aT 공영도매시장 API 데이터 PoC](./MVP/poc/POC-001-aT-공영도매시장-API-데이터.md), [POC-002 외부 가격 데이터 검증 체크리스트](./MVP/poc/POC-002-외부-가격-데이터-검증-체크리스트.md), [POC-003 수산물 가격 데이터 연계 PoC](./MVP/poc/POC-003-수산물-가격-데이터-연계.md)에서 데이터 소스와 가격 차트의 실제 사용 가능성을 확인한다.

### 4. 성장과 운영

1. [PD-005 서비스 성장 전략](./MVP/product/decisions/PD-005-서비스-성장-전략.md)에서 Phase 2·3 확장 순서를 확인한다.
2. [PD-006 비즈니스 모델](./MVP/product/decisions/PD-006-비즈니스-모델.md)에서 비영리 MVP, 비용 원칙, 수익화 검토 조건을 확인한다.

제품 수준의 기술 원칙은 정의되어 있지만 API, 데이터 모델, NFR, 보안·운영 정책을 구현 가능한 수준으로 구체화한 Tech Spec 또는 ADR은 아직 존재하지 않는다.

## 제품 요구사항 문서

### [`MVP/product/PRD-001-MVP-제품-요구사항.md`](./MVP/product/PRD-001-MVP-제품-요구사항.md)

**문서 제목:** PRD-001 오늘의 수산 MVP 제품 요구사항

**상태:** DRAFT; 기존 문서 정합성 검토 및 확정 범위 반영 완료

**역할:** 갈치·고등어·전복을 대상으로 홈, 검색, 가격 차트, Price Insight, 최근 이슈, 비로그인 실시간 채팅의 통합 MVP 요구사항과 상위 `CAP-*` 기능 영역을 정의한다.

**주요 섹션:** 목적과 해결할 문제, MVP 범위, 핵심 사용자 여정, 기능 요구사항, 데이터 및 정책 요구사항, 데이터 흐름 및 운영 요구사항, 측정 지표, 비기능 요구사항과 출시 기준, 추적 가능성 및 후속 문서, 미정·승인 필요 항목

**관련 문서:** PD-012와 PD-013의 확정 범위를 상위 `CAP-*` 기능 영역으로 정리하고 PF-001~005의 상세 `FR-*` 요구사항으로 연결한다.

## 제품 기능 문서

### [`MVP/product/features/PF-001-홈-화면.md`](./MVP/product/features/PF-001-홈-화면.md)

**문서 제목:** PF-001 홈 화면

**상태:** DRAFT

**역할:** 초기 품목 3종의 검색·목록·최근 확정 평균가격·변동률·상세 이동과 데이터 상태 처리를 정의한다.

**주요 섹션:** 기능 목적, 화면 구성, 사용자 흐름, 기능 요구사항, 데이터 요구사항, 화면 상태별 동작, 비기능 요구사항, QA 테스트 시나리오, MVP 제외 기능, 미정 사항, 출시 인수 기준, 관련 문서

### [`MVP/product/features/PF-002-수산물-가격-차트.md`](./MVP/product/features/PF-002-수산물-가격-차트.md)

**문서 제목:** PF-002 수산물 가격 차트

**상태:** DRAFT

**역할:** 최근 1년 가격의 15일·월별 집계, 기간 선택, 결측 표현, 품질 상태와 Price Insight 연동을 정의한다.

**주요 섹션:** 기능 목적, 기능 범위, 화면 구성, 가격 데이터 정의, 가격 집계 규칙, 기간 집계 정책, 사용자 상호작용, 차트 상태 관리, 데이터 조회 계약, 경계 조건과 예외 처리, QA 테스트 시나리오, 비기능 요구사항, 미정 사항, 출시 인수 기준

### [`MVP/product/features/PF-003-Price-Insight.md`](./MVP/product/features/PF-003-Price-Insight.md)

**문서 제목:** PF-003 Price Insight

**상태:** DRAFT

**역할:** 선택 가격 기간의 확인된 사실·가능한 해석·파악 중 상태, 출처 추적, 일 1회 분석과 실패 처리를 정의한다.

**주요 섹션:** 기능 목적, MVP 기능 범위, Price Insight 구성, 분석 대상, 분석 데이터, 정보 신뢰 수준, 가격 변동 가능 요인, 분석 생성 및 저장, 사용자 상호작용, AI 역할 분리, 분석 결과 데이터 계약, 예외 및 실패 처리, QA 테스트 시나리오, 비기능 요구사항, 미정 사항, 출시 인수 기준

### [`MVP/product/features/PF-004-최근-이슈.md`](./MVP/product/features/PF-004-최근-이슈.md)

**문서 제목:** PF-004 최근 이슈

**상태:** DRAFT

**역할:** 품목별 최근 30일 뉴스·공공기관 자료의 수집, 정렬, 중복 제거, 더보기와 원문 이동을 정의한다.

**주요 섹션:** 기능 목적, MVP 기능 범위, 화면 구성, 사용자 흐름, 기능 요구사항, Price Insight와의 관계, 자료 수집 정책, 최근 30일 조회 정책, 상태 관리, 데이터 조회 계약, 경계 조건 및 예외 처리, QA 테스트 시나리오, 비기능 요구사항, 미정 사항, 출시 인수 기준

### [`MVP/product/features/PF-005-실시간-채팅.md`](./MVP/product/features/PF-005-실시간-채팅.md)

**문서 제목:** PF-005 실시간 채팅

**상태:** DRAFT

**역할:** 회원가입·로그인 없는 품목별 채팅방, 메시지 송수신, 임시 표시 이름, 연결·재연결과 기본 이용 제한을 정의한다.

**주요 섹션:** 기능 목적, MVP 기능 범위, 화면 구성, 사용자 흐름, 기능 요구사항, 채팅 데이터 계약, 상태 및 오류 처리, 비기능 요구사항, QA 테스트 시나리오, 미정 사항, 출시 인수 기준, 관련 문서

## 제품 정책 문서

### [`MVP/product/policies/PP-002-AI-분석-운영-정책.md`](./MVP/product/policies/PP-002-AI-분석-운영-정책.md)

**문서 제목:** PP-002 AI 분석 운영 정책

**상태:** DRAFT

**역할:** Price Insight의 일 1회 배치 분석, 사실·해석 구분, 출처 추적, 결과 버전과 실패·재분석 원칙을 공통 정책으로 정의한다.

**주요 섹션:** AI 역할, 분석 실행 정책, 분석 신뢰 정책, 분석 결과 관리, 장애 및 예외 처리, 운영 및 비용, 출시 인수 조건, 미정 사항

**관련 문서:** PD-008·PD-010·PD-011의 AI 원칙을 PRD-001, PF-003, PF-004의 공통 운영 기준으로 연결한다.

### [`MVP/product/policies/PP-003-MVP-출시-인수-기준.md`](./MVP/product/policies/PP-003-MVP-출시-인수-기준.md)

**문서 제목:** PP-003 MVP 출시 인수 기준

**상태:** DRAFT; 최종 출시 판정 `PENDING`

**역할:** PF-001~005의 핵심 기능, 데이터 신뢰성, AI·채팅 운영 안정성, 성능과 KPI 준비 상태를 통합 출시 게이트로 정의한다.

**주요 섹션:** 출시 판정 원칙, 핵심 기능 인수 기준, 데이터 신뢰성 인수 기준, 운영 안정성 인수 기준, 성능 및 운영 지표, KPI 측정 준비, 출시 차단 기준, 최종 출시 점검표, 미정 사항, 관련 문서

**관련 문서:** PRD-001과 PF-001~005의 출시 필수 조건을 통합하고 PP-002의 AI 분석 운영 정책을 검증 기준으로 사용한다.

## 제품 결정 문서

### [`MVP/product/decisions/PD-001-서비스-문제-정의.md`](./MVP/product/decisions/PD-001-서비스-문제-정의.md)

**문서 제목:** PD-001 서비스 문제 정의

**상태:** 미표기

**역할:** 수산물 가격 정보 비대칭을 정의하고, 가격 인텔리전스 서비스와 Price Insight를 핵심 해결 방향으로 결정한다.

**주요 섹션:** 개요, 문제 인식, 어떤 서비스를 지향할 것인가, Decision, Rationale, 결론, 제약사항, Follow-up Decisions

**관련 문서:** PD-002가 사용자를 구체화하고, PD-004가 포지셔닝과 흐름을, PD-008과 PD-009가 핵심 기능과 가격 기준을 구체화한다.

### [`MVP/product/decisions/PD-002-핵심-타깃-사용자.md`](./MVP/product/decisions/PD-002-핵심-타깃-사용자.md)

**문서 제목:** PD-002 핵심 타깃 사용자

**상태:** Accepted

**역할:** 시장 흐름에 관심 있는 일반 소비자를 Primary Target으로 정하고 사용자 확장 순서를 정의한다.

**주요 섹션:** Status, 개요, 유저 후보, 최종 결정, Target User Mix, 결정 이유, Consequences, Follow-up

**중요 H3:** Candidate A·B·C, Primary Target, Secondary Target, Long-term Target

**관련 문서:** PD-003의 페르소나와 PD-005의 단계별 사용자 확장 기준이 된다.

### [`MVP/product/decisions/PD-003-핵심-페르소나.md`](./MVP/product/decisions/PD-003-핵심-페르소나.md)

**문서 제목:** PD-003 Primary Persona

**상태:** Accepted

**역할:** 제철·트렌드, 시장·가격, 가족·합리적 소비 동기를 대표하는 세 페르소나와 제품 설계 질문을 정의한다.

**주요 섹션:** 핵심 요약, 페르소나 구성, Persona 1 이서연, Persona 2 김민수, Persona 3 박성호, 세 페르소나 비교, 공통 사용자 특성, Emotional Value, 제품 설계 기준, 결정, Follow-up

**중요 H3:** 이서연, 27세 직장인; 김민수, 35세 직장인; 박성호, 48세 직장인; 각 페르소나의 핵심 동기와 주요 Pain Point

**관련 문서:** PD-002의 타깃을 구체화하며, UR-001과 PD-007의 계절 경험 근거·원칙을 제품 설계 관점으로 연결한다.

### [`MVP/product/decisions/PD-004-서비스-포지셔닝.md`](./MVP/product/decisions/PD-004-서비스-포지셔닝.md)

**문서 제목:** PD-004 서비스 포지셔닝

**상태:** Accepted

**역할:** 오늘의 수산을 수산물 시장 정보 탐색 서비스로 정의하고 Primary Flow, Secondary Flow, MVP에서 지양할 범위를 정한다.

**주요 섹션:** 핵심 요약, 개요, 검토한 포지셔닝, 결정, 사용자 진입 동기, 핵심 사용자 탐색 흐름, Primary Flow, Secondary Flow, 기능적 포지셔닝, 감성적 포지셔닝, 핵심 메시지, 초기 MVP에서 지양하는 방향, 결정 근거, Consequences, Follow-up

**관련 문서:** PD-001의 문제를 사용자 흐름으로 전환하고, PD-007의 감성 가치와 PD-008의 Price Insight 역할을 배치한다.

### [`MVP/product/decisions/PD-005-서비스-성장-전략.md`](./MVP/product/decisions/PD-005-서비스-성장-전략.md)

**문서 제목:** PD-005 서비스 성장 전략

**상태:** Accepted

**역할:** 시장 이해, 개인화된 탐색, 참여형 커뮤니티의 3단계 성장 순서와 단계별 사용자·기능 원칙을 정하고, MVP 기본 채팅과 Phase 3 커뮤니티를 구분한다.

**주요 섹션:** 성장 전략 개요, Phase 1 — 시장 이해, Phase 1 성공 기준, Phase 2 — 개인화된 시장 탐색, Phase 2 주요 기능, 가격 판단 원칙, Phase 2 개인화 기능, Phase 3 — 참여형 수산물 시장 커뮤니티, 사용자 유형, Role Badge, 공식 정보와 사용자 정보의 결합, 인증 정책, B2B 서비스 여부, 단계별 성장 구조, 성장 원칙, 장기 비전, Follow-up

**중요 H3:** 가격 정보, Price Insight, 근거 확인, 계절 정보, 품목별 실시간 채팅

**관련 문서:** PD-004의 제품 경계를 시간 순서로 확장하며, PD-006의 수익화 단계, PD-007의 재방문 경험, PD-012의 확정 MVP 범위에 연결된다.

### [`MVP/product/decisions/PD-006-비즈니스-모델.md`](./MVP/product/decisions/PD-006-비즈니스-모델.md)

**문서 제목:** PD-006 비즈니스 모델

**상태:** Accepted

**역할:** 비영리 MVP, MAU 3,000 수익화 검토 Trigger, 광고·Premium 원칙, 비용 Guardrail을 정의한다.

**주요 섹션:** BM 목적, 비즈니스 모델 기본 원칙, MVP 수익화 정책, 수익화 Trigger, 1차 수익화 — Google Ads, 2차 수익화 — 개인화 Premium, 관심 수산물 Premium, Premium 가격 가설, 예상 Premium 매출 시나리오, 비용 최소화 전략, 주요 운영 비용, 주요 비용 리스크, Cost Guardrail, 수익성 판단, BM 단계, 현재 BM Decision, 추가 보완 필요 영역, 최종 결론

**관련 문서:** PD-005의 성장 단계에 운영·수익 조건을 추가하며, Price Insight와 핵심 정보의 무료 제공 원칙을 정한다.

### [`MVP/product/decisions/PD-007-감성적-가치.md`](./MVP/product/decisions/PD-007-감성적-가치.md)

**문서 제목:** PD-007 감성적 가치

**상태:** Accepted

**역할:** 계절을 잘 살아가고 있다는 만족감을 제품 가설로 정의하고 제철 경험의 순환과 UX 원칙을 설명한다.

**주요 섹션:** 감성적 가치의 정의, 개발자가 정의하는 감성적 가치, 핵심 제품 문장, 핵심 감성 가치 — 계절을 잘 살아가고 있다는 만족감, 제철의 의미, 제철 경험의 순환, 트렌드에서 기억으로, 변화하는 수산물 문화, 기능적 가치와 감성적 가치, 제품 경험 원칙, 제품 경험의 핵심 구조, Primary Flow와의 관계, Secondary Discovery, UI/UX 적용 원칙, 검증이 필요한 가설, Decision, 최종 제품 메시지, Follow-up

**관련 문서:** UR-001을 근거로 삼고, PD-003의 사용자 동기와 PD-004의 Secondary Flow를 감성 경험으로 구체화한다.

### [`MVP/product/decisions/PD-008-Price-Insight.md`](./MVP/product/decisions/PD-008-Price-Insight.md)

**문서 제목:** PD-008 Price Insight

**상태:** Accepted

**역할:** 핵심 기능의 정의, 데이터 범위, Chart First 원칙, 일 1회 생성 정책, 근거·표현 정책을 정한다.

**주요 섹션:** Price Insight의 목적, Price Insight 정의, 핵심 원칙, 고려하는 데이터 범위, 품목마다 중요 요인은 다르다, 정형 데이터 수집, 비정형 데이터 수집, MVP Collector AI, MVP Price Insight 생성 주기, 변경이 없는 경우, 가격 차트, 시점별 Price Insight, 주요 시장 요인은 최대 3개, Historical Insight Snapshot, 최근 시장 이슈, 출처 공개, 분석 상태, 파악 중, 실시간 채팅 연계, 표현 원칙, 직접적인 설명이 존재하는 경우, MVP AI 범위, 성공 기준, 현재 Decision, 후속 기술 결정, 최종 결론

**중요 H3:** 사실, 시장 배경 설명

**관련 문서:** PD-001의 해결책을 기능 정책으로 구체화하고, PD-009의 기준가격을 분석 기준점으로 사용한다.

### [`MVP/product/decisions/PD-009-기준가격-정의.md`](./MVP/product/decisions/PD-009-기준가격-정의.md)

**문서 제목:** PD-009 기준가격 정의

**상태:** Accepted

**역할:** 주요 도매시장 평균을 대표 기준가격으로 정하고 분포, 추정 소비자가, 최신성, 누락·이상치 처리 원칙을 정의한다.

**주요 섹션:** 기준가격이 필요한 이유, 대표 기준가격, 도매가를 선택한 이유, 여러 시장의 가격 처리, 가격 분포 함께 제공, 시장별 상세 가격, 소매가격의 역할, 예상 소비자가, 실측가격과 추정가격 구분, 초기 가격 구분 기준, 추가 구분 후보, 데이터 최신성, 데이터 Freshness, 데이터 없는 날의 처리, 가격 데이터 품질 검증, 이상치 처리, Price Quality Status, Price Insight와의 관계, 가격 표시 원칙, 초기 MVP 범위, 현재 Decision, 후속 결정, 최종 결론

**관련 문서:** PD-008의 가격 차트와 Price Insight가 사용하는 수치 기준을 제공하며, 후속 Data Quality·정규화 기술 문서의 상위 결정이다.

### [`MVP/product/decisions/PD-010-데이터-신뢰-정책.md`](./MVP/product/decisions/PD-010-데이터-신뢰-정책.md)

**문서 제목:** PD-010 데이터 신뢰 정책

**상태:** Accepted

**역할:** 출처를 Official, Market, Verified Media, Community로 구분하고 Signal·Evidence·원 출처·근거 부족 처리 원칙을 정의한다.

**주요 섹션:** 데이터 신뢰 정책의 목적, 핵심 원칙, 데이터 출처 분류, Level A — Official, Level B — Market, Level C — Verified Media, Level D — Community, 출처 Level의 의미, Signal과 Evidence, 뉴스 사용 원칙, 원 출처 우선, 출처 충돌, 정형 데이터 검증, 데이터 정규화, 데이터 최신성, 추정값과 관측값 분리, AI 생성 정보의 위치, Source Traceability, MVP AI 신뢰성 관리, MVP에서 구현하지 않는 신뢰성 기능, Harness Engineering, 근거 부족, Community Insight, 정책이 지향하는 사용자 경험, 현재 Decision, 최종 결론

**관련 문서:** PD-008의 근거·표현 정책과 PD-011의 AI 검증 범위를 구체화한다.

### [`MVP/product/decisions/PD-011-AI-역할-정의.md`](./MVP/product/decisions/PD-011-AI-역할-정의.md)

**문서 제목:** PD-011 AI 역할 정의

**상태:** Accepted

**역할:** MVP에서 Collector AI만 사용하고 정형 데이터는 API·Batch로 처리하는 원칙과 이후 신뢰성 고도화 단계를 정의한다.

**주요 섹션:** AI를 사용하는 이유, AI의 기본 역할, AI는 데이터의 원 출처가 아니다, 정형 데이터 수집, 비정형 데이터, MVP Collector AI, Collector AI 역할, Collector AI 출력 예시, Collector AI의 제한, MVP Price Insight 생성, MVP에서 복수 AI Agent를 사용하지 않는다, MVP 신뢰성 관리, Human-in-the-loop, AI가 하면 안 되는 일, AI 비용 원칙, 향후 신뢰성 개선, Evidence 구조화, Atomic Claim, Verifier AI, Model Routing, Harness Engineering, Evidence Binding, 자동 Fallback, AI Evaluation, AI 고도화 로드맵, MVP에서 하지 않는 것, 현재 Decision, 후속 기술 결정, 최종 결론

**관련 문서:** PD-008의 Price Insight 생성 방식과 PD-010의 데이터 신뢰 정책을 구현 관점에서 제한한다.

### [`MVP/product/decisions/PD-012-MVP-범위.md`](./MVP/product/decisions/PD-012-MVP-범위.md)

**문서 제목:** PD-012 MVP Scope

**상태:** Accepted

**역할:** MVP의 핵심 흐름, 필수·선택·제외 기능, 초기 품목 선정 기준, 기술·비용 원칙과 개발 시작 조건을 확정한다.

**주요 섹션:** MVP 목적, MVP 개발 원칙, MVP 핵심 사용자 흐름, MVP 필수 기능, 수산물 상세 페이지, 대표 기준가격, 가격 차트, Chart First, Price Insight, Price Insight 갱신, Collector AI, 정형 데이터 수집, 출처 공개, 근거 부족 처리, 시점별 시장 요인, 시장 이슈 영역, 인증 정책, 실시간 채팅, 채팅 기본 경험, 채팅 MVP 범위, 채팅 성능 목표, 관심 수산물, 초기 지원 품목, MVP에서 제외하는 기능, MVP 기능 우선순위, MVP 기술 원칙, MVP 비용 원칙, MVP 성공 판단, MVP가 검증해야 하는 핵심 가설, MVP 개발 시작 조건, MVP 이후, 현재 Decision, 최종 결론

**관련 문서:** PD-005의 Phase 1, PD-006의 비영리 정책, PD-008~011의 기능·가격·데이터·AI 결정을 하나의 구현 범위로 통합한다.

### [`MVP/product/decisions/PD-013-가격-데이터-PoC-적용-원칙.md`](./MVP/product/decisions/PD-013-가격-데이터-PoC-적용-원칙.md)

**문서 제목:** PD-013 가격 데이터 PoC 적용 원칙

**상태:** Accepted

**역할:** 가격 데이터 PoC의 기술 검증 결과와 제품 결정을 분리하고, 초기 제공 품목·대표가격 집계·추정 분류·결측값의 적용 원칙을 정한다.

**주요 섹션:** Status, 배경, Decision, PoC와 제품 결정의 역할, 초기 제공 품목, 대표가격 집계, 원산지와 상품 상태 추정, 결측값, Consequences, Follow-up, 관련 문서

**관련 문서:** PD-009·PD-010·PD-012를 Source of Truth로 유지하면서 POC-003의 결과를 개발 검증과 후속 제품 결정에 연결한다.

## 사용자 리서치 문서

### [`MVP/research/user/UR-001-제철-음식-소비-트렌드-리서치.md`](./MVP/research/user/UR-001-제철-음식-소비-트렌드-리서치.md)

**문서 제목:** UR-001 제철 음식 소비 트렌드 리서치

**상태:** 문서 상태 미표기; 기후변화와 계절감 가설은 `Needs Validation`

**역할:** 제철 음식의 검색 관심, 소비 동기, 연령대별 관심과 수산물 계절성을 조사하고 제품 가설과 적용 방향을 도출한다.

**주요 섹션:** 리서치 목적, Research Questions, 검색 관심 증가, 제철코어 트렌드, 소비 동기, 연령대별 관심, 수산물에서 나타나는 계절성, 산업 반응, 관찰된 사실, 제품 해석, 제품 가설, 기후변화와 계절감 가설, 제품 적용 방향, 결론, Follow-up

**중요 H3:** 20대·30대·40~50대, 겨울 방어, 가을 전어·새우, Hypothesis 1·2·3, 가설 상태

**관련 문서:** PD-003의 페르소나, PD-004의 감성적 포지셔닝, PD-007의 계절 경험 가설에 근거를 제공한다.

## PoC 문서

### [`MVP/poc/POC-001-aT-공영도매시장-API-데이터.md`](./MVP/poc/POC-001-aT-공영도매시장-API-데이터.md)

**문서 제목:** POC-001 aT 공영도매시장 API 데이터 PoC

**상태:** 문서 상태 미표기; Primary Price Source는 `NO-GO`

**역할:** aT 공영도매시장 API의 우럭·주요 어류 거래량, 최신성, 연속성을 검증하고 핵심 가격 데이터 소스 사용 여부를 판단한다.

**주요 섹션:** 핵심 결론, 왜 검증했는가, 검증한 데이터, PoC 진행 과정, 최종 판단, 이번 PoC에서 얻은 핵심 인사이트, 관련 문서

**중요 H3:** 전국 공영도매시장 실시간 경매정보, 농축수산물 표준코드, Step 1~5, API 존재 ≠ 서비스 사용 가능, 표준코드 존재 ≠ 실제 데이터 존재, 외부기관의 품목코드에 종속되면 안 된다

**관련 문서:** PD-009의 데이터 Source 선정, PD-010의 정형 데이터 검증·정규화, PD-012의 Data PoC 개발 시작 조건에 근거를 제공한다.

### [`MVP/poc/POC-002-외부-가격-데이터-검증-체크리스트.md`](./MVP/poc/POC-002-외부-가격-데이터-검증-체크리스트.md)

**문서 제목:** POC-002 외부 가격 데이터 PoC 공통 체크리스트

**상태:** 문서 상태 미표기

**역할:** 새로운 외부 가격 데이터 소스를 검증할 때 확인할 공통 기준을 제공한다.

**주요 섹션:** 관련 문서

**주요 내용:** API 접근, 품목, 실제 데이터, 최신성, 연속성, 데이터량, 과거 데이터, 단위, 품목 Mapping, 시장 정보, 자동수집, 출처

**관련 문서:** POC-001의 검증 결과를 재사용 가능한 점검 기준으로 일반화하고 PD-009·PD-010·PD-012의 데이터 원칙에 연결한다.

### [`MVP/poc/POC-003-수산물-가격-데이터-연계.md`](./MVP/poc/POC-003-수산물-가격-데이터-연계.md)

**문서 제목:** POC-003 수산물 가격 데이터 연계 PoC 최종 보고서

**상태:** 가격 차트 기술 검증 완료; 갈치·고등어·전복을 초기 제공 품목으로 확정

**역할:** KAMIS 가격과 공공데이터포털 정산정보를 이용해 갈치·고등어·전복의 가격 차트, 결측 처리, 품목 코드 매핑 구현 가능성을 검증한다.

**주요 섹션:** PoC 목적과 진행 과정, 개발 검증 품목 선정 결과, 대표 가격의 기준, 15일 단위 가격, API, 품목 코드 매핑, 결측값, 검증 결과와 결론, 관련 문서

**관련 문서:** PD-013의 적용 원칙에 따라 기술 검증 근거로 사용하며, PD-009·PD-010·PD-012의 제품 결정을 변경하지 않는다.

## 핵심 문서 관계

| 출발 문서 | 연결 문서 | 관계 |
| --- | --- | --- |
| UR-001 | PD-003, PD-004, PD-007 | 제철·계절 경험에 대한 사용자 및 시장 근거 |
| PD-001 | PD-002, PD-004, PD-008 | 문제 정의 → 사용자·포지셔닝·핵심 기능 |
| PD-002 | PD-003, PD-005 | 타깃 정의 → 페르소나·단계별 사용자 확장 |
| PD-004 | PD-007, PD-008 | 서비스 포지셔닝 → 감성 가치·Price Insight |
| PD-005 | PD-006, PD-012 | 성장 단계 → 운영·수익화 조건과 확정 MVP 범위 |
| PD-009 | PD-008 | 기준가격 → 차트와 Price Insight 분석 기준 |
| PD-008 | PD-010, PD-011 | Price Insight → 데이터 신뢰 정책과 AI 역할 |
| PD-008~PD-011 | PD-012 | 기능·가격·신뢰·AI 결정 → 통합 MVP 범위 |
| POC-003 | PD-013 | 가격 데이터 기술 검증 → 제품 정책 적용 경계와 후속 검증 조건 |
| POC-001, POC-002 | PD-009, PD-010, PD-012 | 데이터 소스 검증 → 가격·신뢰 정책과 MVP 개발 시작 조건 |
| PD-012, PD-013 | PRD-001 | Accepted 제품 범위와 초기 품목 → 통합 요구사항 |
| PRD-001 | PF-001~PF-005 | 통합 MVP 요구사항 → 화면·기능별 명세와 인수 기준 |
| PD-008, PD-010, PD-011 | PP-002 | AI·신뢰 결정 → 공통 분석 운영 정책 |
| PRD-001, PF-001~PF-005, PP-002 | PP-003 | 기능·운영 요구사항 → 통합 출시 게이트 |

## 목차 유지 규칙

다음 상황에서는 이 목차도 함께 업데이트한다.

* 새로운 Markdown 문서 추가 또는 기존 문서 삭제
* 문서 파일명 변경 또는 이동
* H1이나 주요 섹션 구조 변경
* 문서 역할 또는 상태 변경
* 문서 간 상위·근거·후속 관계 변경

목차는 원본 문서 내용을 복제하지 않는다. 항상 “어떤 정보가 어디에 있는가”를 빠르게 찾을 수 있는 수준으로 유지한다. 파일명은 `PREFIX-NNN-한국어-문서명.md` 형식을 사용하되 `Price Insight`, `MVP`, `API` 같은 프로젝트 고유 영어 명사는 유지한다.
