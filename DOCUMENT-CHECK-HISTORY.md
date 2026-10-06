# 문서 일관성 검사 이력

## 2026-10-07 02:23 KST

### 검사 범위

Baseline: 없음 → `44fff1ee81fa2437d259f5bd474cf71ee8152106`

최초 검사로 다음 범위를 전체 확인했다.

* Repository root의 README와 INDEX
* `MVP/product/decisions/`의 PD-001~PD-012
* `MVP/research/user/`의 UR-001
* 파일명, 문서 ID, H1/H2, 상태, 용어, 내부 링크
* MVP 범위, Price Insight, 데이터 신뢰 및 AI 역할의 문서 간 정합성

검사 시작 시 Git 변경사항:

* 문서 변경 없음
* `.codex/skills/docs-consistency-check/SKILL.md` 미추적

### 검사 결과

* 파일명 규칙: 자동 수정
* 디렉토리 구조: 정상
* 문서 구조: 비차단 이슈 확인
* 프로젝트 용어: 자동 수정
* 내부 링크: 정상
* 문서 정합성: 사용자 결정 후 반영
* INDEX.md: 수정
* README.md: 수정

### 수행한 수정

* `PD-010-data-trust-policy.md`를 `PD-010-데이터-신뢰-정책.md`로 변경
* `PD-11-ai-role.md`를 `PD-011-AI-역할-정의.md`로 변경
* `PD-012-mvp-scope.md`를 `PD-012-MVP-범위.md`로 변경
* PD-005에서 MVP 기본 품목별 채팅과 Phase 3 참여형 커뮤니티의 범위를 구분
* PD-005 Follow-up에 PD-012 연결 추가
* PD-010의 중복 heading을 `정책이 지향하는 사용자 경험`으로 변경
* `타겟` 표기를 `타깃`으로 통일
* INDEX에 PD-010~PD-012를 추가하고 개정된 PD-008 목차를 동기화
* README에 PD-010~PD-012와 검사 이력 링크를 추가

### 사용자 검토

발견된 문제:

* PD-005는 참여형 커뮤니티를 Phase 3으로 정의하지만 PD-012는 실시간 채팅을 MVP 핵심 기능으로 정의함

사용자 결정:

* PD-012를 최신 MVP 기준으로 사용
* MVP에서는 최소 품목별 채팅을 제공
* Phase 3에서는 사용자 역할, 인증, Moderation과 참여자별 정보 구조를 포함한 참여형 커뮤니티로 확장

반영 결과:

* PD-005에 두 단계의 범위 차이를 명시하고 PD-012와 연결함

### 확인된 문제

다음 항목은 제품 결정 충돌을 만들지 않는 비차단 정리 과제로 남겼다.

* PD-001과 UR-001에 문서 전체 Status가 없음
* PD-003 이후 다수 문서가 번호 섹션에 H1을 사용하여 한 파일에 H1이 여러 개 존재함
* PD-005의 전년 동기 비교가 Phase 1 가격 정보와 Phase 2 주요 기능에 함께 나타나 단계별 범위가 불명확함
* 작성일, 수정일, Owner가 없어 Accepted 문서 간 시간적 우선순위를 문서만으로 판별하기 어려움
* API, ERD, Data Flow, NFR을 구현 수준으로 정의한 Tech Spec 또는 ADR이 아직 없음

### 검사 사용량

* 이번 검사 사용량: 확인 불가
* 잔여 사용량: 확인 불가

### 검사 상태

`완료`

### 다음 검사 기준

`44fff1ee81fa2437d259f5bd474cf71ee8152106`

현재 검사 수정사항을 커밋한 뒤 다음 검사에서는 해당 커밋을 새로운 baseline으로 갱신한다.

## 2026-10-07 02:38 KST

### 검사 범위

Baseline: `44fff1ee81fa2437d259f5bd474cf71ee8152106` → `d3e4da390fbba27383fdc14a366217b8e991a231`

직전 검사 결과가 반영된 commit과 현재 working tree의 검사 skill 변경을 증분 검사했다.

### 변경 감지

* 추가: 2개
* 수정: 5개
* 삭제: 0개
* 이동/파일명 변경: 3개
* Working tree 수정: 1개

### 검사 대상

* A `.codex/skills/docs-consistency-check/SKILL.md`
* A `DOCUMENT-CHECK-HISTORY.md`
* M `INDEX.md`
* M `MVP/product/decisions/PD-002-핵심-타깃-사용자.md`
* M `MVP/product/decisions/PD-005-서비스-성장-전략.md`
* R `PD-010-data-trust-policy.md` → `PD-010-데이터-신뢰-정책.md`
* R `PD-11-ai-role.md` → `PD-011-AI-역할-정의.md`
* R `PD-012-mvp-scope.md` → `PD-012-MVP-범위.md`
* M `MVP/research/user/UR-001-제철-음식-소비-트렌드-리서치.md`
* M `README.md`
* Working tree M `.codex/skills/docs-consistency-check/SKILL.md`

### 검사 결과

* 파일명: 정상
* 디렉토리 구조: 정상
* 문서 구조: 정상; 이전 검사에서 기록한 비차단 과제는 유지
* 프로젝트 용어: 정상
* 링크: 정상
* 문서 정합성: 정상
* INDEX.md: 정상
* README.md: 정상

### 수행한 수정

* 검사 이력에 현재 증분 검사 결과와 새 baseline을 추가

### 사용자 검토

* 없음

### 사용량

* 이번 검사 token 사용량: 확인 불가
* 잔여 token: 확인 불가
* Codex usage/quota: 확인 불가

### 검사 상태

`완료`

### 다음 검사 기준

`d3e4da390fbba27383fdc14a366217b8e991a231`
