---
name: docs-consistency-check
description: 마지막 문서 검사 이후 변경된 docs만 증분 검사하고 INDEX.md와 DOCUMENT-CHECK-HISTORY.md를 동기화한다.
---

# Docs Consistency Check

## Files

- Index: `<repo-root>/INDEX.md`
- History: `<repo-root>/DOCUMENT-CHECK-HISTORY.md`
- Repository rules: `<repo-root>/AGENTS.md`

`AGENTS.md`는 repository의 기본 문서 규칙을 정의한다. 이 Skill에서는 해당 규칙을 중복 작성하지 않고 참조한다.

## Workflow

1. `DOCUMENT-CHECK-HISTORY.md`에서 마지막 정상 검사 baseline commit을 확인한다.
2. baseline 이후 Git 변경사항과 현재 working tree 변경사항을 확인한다.
3. 추가·수정·삭제·이동된 Markdown 문서를 식별한다.
4. 변경된 문서만 우선 검사한다.
5. 정합성 판단에 필요한 관련 기존 문서만 추가로 읽는다.
6. `AGENTS.md`의 repository 규칙을 기준으로 다음을 검사한다.
   - 파일명
   - 디렉토리 위치
   - 문서 구조
   - 프로젝트 용어
   - 내부 링크
   - 문서 간 정합성
7. 변경 내용에 맞게 `INDEX.md`를 증분 갱신한다.
8. README에 영향을 주는 경우에만 `README.md`를 갱신한다.
9. 검사 결과를 `DOCUMENT-CHECK-HISTORY.md`에 기록한다.
10. 검사가 정상 완료된 경우 현재 HEAD를 다음 baseline으로 기록한다.

## Change Detection

기본적으로 다음 명령을 활용한다.

```sh
git status --short
git rev-parse HEAD
git diff --name-status <baseline>..HEAD
git diff --name-status
git diff --cached --name-status
```

변경 유형:

- `A`: 추가
- `M`: 수정
- `D`: 삭제
- `R`: 이동 또는 파일명 변경

committed 변경과 아직 commit되지 않은 변경을 모두 검사 범위에 포함한다.

## Incremental Check

전체 repository를 매번 다시 읽지 않는다.

먼저 변경된 문서를 검사하고, 필요한 경우에만 다음 관련 문서를 추가로 읽는다.

- 변경 문서가 직접 참조하는 문서
- 변경 문서를 직접 참조하는 문서
- 동일 기능 또는 개념을 정의하는 문서
- 관련 사용자 리서치
- 상위 제품 의사결정
- 관련 기술 설계

관련성을 설명할 수 없는 문서는 불필요하게 읽지 않는다.

## Full Scan

다음 경우 전체 검사가 필요할 수 있다.

- 검사 이력이 없음
- 유효한 baseline이 없음
- baseline이 Git history에서 유효하지 않음
- 문서 디렉토리 구조가 대규모로 변경됨
- 문서 관리 규칙이 크게 변경됨
- INDEX.md와 실제 repository가 광범위하게 불일치함
- 사용자가 전체 검사를 요청함

전체 검사를 수행하기 전에 반드시 사용자에게 다음을 알려 검토를 요청한다.

- 전체 검사가 필요한 이유
- 검사 대상 범위
- 예상되는 주요 작업

사용자의 승인을 받은 후에만 전체 검사를 수행한다.

## Conflict Handling

검사 중 제품 의미나 문서 정합성과 관련된 문제가 발견되면 임의로 수정하지 않는다.

예:

- Accepted decision 간 충돌
- MVP 범위 차이
- 타깃 사용자 정의 차이
- Price Insight 정의 차이
- 데이터 기준 변경
- 기능 포함/제외 정책 충돌
- Business Model 또는 주요 기술 설계 변경
- 어떤 문서가 최신 Source of Truth인지 판단할 수 없음

문제가 발견되면 다음을 사용자에게 보고한다.

- 변경 문서
- 관련 기존 문서
- 충돌 내용
- 가능한 처리 방향

사용자의 검토와 판단을 받은 뒤 수정하거나 다음 관련 작업을 수행한다.

이미 완료한 검사는 불필요하게 다시 수행하지 않는다.

## Automatic Fixes

제품 판단이 필요하지 않은 명백한 문제는 자동 수정할 수 있다.

예:

- 깨진 Markdown 상대 링크
- 파일 이동에 따른 링크 수정
- INDEX.md의 오래된 경로
- 삭제 문서 INDEX 항목 제거
- 신규 문서 INDEX 등록
- 변경된 H1/H2의 INDEX 반영
- 명백한 Markdown formatting 오류
- 프로젝트 고유명사의 단순 오타

자동 수정한 내용은 최종 보고와 검사 이력에 기록한다.

## INDEX.md

`INDEX.md`는 repository 전체의 상세 문서 목차다.

다음 변경이 발생하면 반드시 동기화한다.

- 문서 추가
- 문서 삭제
- 파일명 변경
- 문서 이동
- H1 변경
- 주요 H2 변경
- 문서 역할 변경
- 디렉토리 구조 변경

다음을 확인한다.

- 실제 파일 경로
- Markdown 링크
- 파일명
- 문서 제목
- 주요 H2
- 디렉토리 분류
- 중복 문서
- 문서 ID 순서

증분 검사에서는 INDEX 전체를 다시 만들지 않는다.

변경된 문서가 속한 영역만 수정한다.

INDEX 전체 검사가 필요하다면 전체 검사와 동일하게 사용자 승인을 받는다.

## README.md

README는 repository의 대표 진입점이다.

다음을 중심으로 유지한다.

- 프로젝트 설명
- repository 목적
- 주요 디렉토리
- 주요 문서 영역
- 추천 읽기 순서
- INDEX 및 주요 문서 링크

모든 개별 문서를 README에 추가하지 않는다.

변경사항이 README의 주요 구조에 영향을 줄 때만 수정한다.

## History

검사 이력은 반드시 다음 위치에 기록한다.

```text
<repo-root>/DOCUMENT-CHECK-HISTORY.md
```

기존 이력을 덮어쓰지 않고 누적한다.

각 검사에는 최소한 다음을 기록한다.

```md
## YYYY-MM-DD HH:mm

### 검사 범위

Baseline:
`이전 commit` → `현재 HEAD`

### 변경 감지

- 추가: N개
- 수정: N개
- 삭제: N개
- 이동/파일명 변경: N개

### 검사 대상

- A `경로`
- M `경로`
- D `경로`
- R `기존 경로` → `새 경로`

### 검사 결과

- 파일명: 정상 / 자동 수정 / 검토 필요
- 디렉토리 구조: 정상 / 자동 수정 / 검토 필요
- 문서 구조: 정상 / 자동 수정 / 검토 필요
- 프로젝트 용어: 정상 / 자동 수정 / 검토 필요
- 링크: 정상 / 자동 수정 / 검토 필요
- 문서 정합성: 정상 / 검토 필요 / 충돌
- INDEX.md: 정상 / 수정 / 검토 필요
- README.md: 정상 / 수정 / 검토 필요

### 수행한 수정

- 수정 내용

없으면:

- 없음

### 사용자 검토

없으면:

- 없음

사용자 판단이 있었으면:
- 발견된 문제
- 사용자 결정
- 반영 결과

### 사용량

- 이번 검사 token 사용량: `<확인 가능한 값 또는 확인 불가>`
- 잔여 token: `<확인 가능한 값 또는 확인 불가>`
- Codex usage/quota: `<확인 가능한 값 또는 확인 불가>`

### 검사 상태

`완료`

또는:

`검토 필요`

### 다음 검사 기준

`<현재 HEAD commit>`
```

## Usage

검사 과정에서 실제 token 또는 Codex 사용량 정보를 실행 환경이 제공하는 경우 표시한다.

가능하면 검사 시작 시점과 종료 시점을 비교한다.

단, 정확한 값을 확인할 수 없는 경우 추정하지 않는다.

다음과 같이 표시한다.

```text
이번 검사 token 사용량: 확인 불가
잔여 token: 확인 불가
Codex usage/quota: 확인 불가
```

token 수와 ChatGPT/Codex의 5시간·주간 사용량은 서로 다른 개념이므로 혼용하지 않는다.

## Baseline

정상적인 작업 순서는 다음과 같다.

```text
이전 baseline 확인
→ Git 변경 감지
→ 변경 문서 검사
→ 관련 문서 검사
→ 정합성 검사
→ 필요 시 사용자 검토
→ 승인된 수정
→ INDEX.md 동기화
→ 필요 시 README.md 동기화
→ 링크/Markdown 검증
→ DOCUMENT-CHECK-HISTORY.md 기록
→ 최종 검증
→ 다음 baseline 기록
```

중요한 정합성 문제가 해결되지 않은 경우 baseline을 갱신하지 않는다.

이 경우 history에 다음과 같이 기록한다.

```text
검사 상태: 검토 필요
baseline 갱신: 보류
```

## Validation

작업 완료 전 가능한 범위에서 다음을 실행한다.

```sh
rg --files
git status
git diff --check
```

필요한 경우:

```sh
git diff --word-diff
git diff --name-status <baseline>..HEAD
rg "검색 대상"
```

을 사용한다.

## Final Report

정상 완료 시 다음 형식으로 간결하게 보고한다.

```text
문서 일관성 검사를 완료했습니다.

변경 감지
- 추가: N개
- 수정: N개
- 삭제: N개
- 이동/파일명 변경: N개

검사 결과
- 파일명: 정상
- 디렉토리 구조: 정상
- 문서 구조: 정상
- 프로젝트 용어: 정상
- 링크: 1건 수정
- 문서 정합성: 정상

INDEX.md
- 신규 문서 1건 추가
- H2 목차 1건 갱신

README.md
- 변경 없음

검사 이력
- ./DOCUMENT-CHECK-HISTORY.md 갱신

사용량
- 이번 검사 token 사용량: <값 또는 확인 불가>
- 잔여 token: <값 또는 확인 불가>
- Codex usage/quota: <값 또는 확인 불가>

다음 검사 기준
- <commit hash>
```

판단이 필요한 문제가 발생하면 수정하지 않고 해당 문제를 먼저 사용자에게 보고한다.

# Goal

이 Skill의 목표는 docs repository를 하나의 일관된 프로젝트 문서 시스템으로 유지하는 것이다.

전체 repository를 매번 읽지 않고 Git 변경 이력과 기존 검사 이력을 활용하여 필요한 문서만 검사한다.

`INDEX.md`는 실제 문서 구조와 지속적으로 동기화하고, 모든 검사 결과는 repository root의 `DOCUMENT-CHECK-HISTORY.md`에 남긴다.