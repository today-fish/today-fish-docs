# 오늘의 수산 docs 기여 및 Git 운영 규칙

> **핵심 결론:** `main`은 검토된 문서의 기준선이며 `docs`는 문서 변경을 준비하는 작업 브랜치다. 변경 사유와 검증 결과는 GitHub PR에 기록하고, 과거 상태는 Git 커밋으로 복원한다.

## 1. 브랜치 전략

| 브랜치 | 역할                                             |
| ------ | ------------------------------------------------ |
| `main` | 검토·병합된 문서 기준선                          |
| `docs` | 문서 작성·검사·PR 준비를 위한 재사용 작업 브랜치 |

1. 변경 전 `main` 기준 상태와 작업 트리의 미커밋 변경을 확인한다.
2. `docs`에서 변경하고, 검증·사용자 검토 후 `docs` → `main` PR을 생성한다.
3. PR 병합 후 다음 작업을 시작하기 전에 `docs`를 최신 `main`과 동기화한다.
4. **Squash Merge**로 병합한 경우 커밋 그래프가 달라질 수 있다. `--ff-only`가 실패하면 미병합 변경을 확인한 후 재생성·리셋 방법을 사용자와 결정한다. 미확인 작업을 `reset --hard`로 삭제하지 않는다.
5. `main` 직접 푸시는 피하고 PR 검토를 기본으로 한다.

## 2. PR 분류 — Type + Area

PR 분류의 기준은 **주된 변경 목적(Type)**과 **변경 영역(Area)**이다. 폴더나 파일 확장자만으로 Type을 정하지 않는다.

### Type — 변경 목적

| Label | 의미 |
|---|---|
| `type:decision` | ADR 및 제품·기술 의사결정 |
| `type:feature` | 기능 또는 요구사항 추가·변경 |
| `type:docs` | 문서 작성·구조·운영 규칙 변경 |
| `type:fix` | 오류, 모순, 잘못된 내용 수정 |
| `type:chore` | 설정, 유지보수, 자동화 작업 |

### Area — 변경 영역

| Label | 의미 |
|---|---|
| `area:frontend` | 프론트엔드 아키텍처 및 FE-ADR |
| `area:backend` | 백엔드 아키텍처 및 BE-ADR |
| `area:product` | PRD, 기능 명세, 제품 정책 |
| `area:ux` | UX 문서, 사용자 흐름, 정보 구조 |
| `area:design-system` | 디자인 시스템, 디자인 토큰 및 컴포넌트 |
| `area:docs` | README, 템플릿, 공통 문서 구조 및 운영 체계 |

총 11개 라벨을 기준으로 한다. `type:adr`, `area:architecture`, `area:infra` 등 추가 세분화 라벨은 사용하지 않는다.

### 적용 규칙

1. PR에는 주된 변경 목적에 맞는 Type 라벨을 원칙적으로 하나 지정한다.
2. 주요 변경 영역에 해당하는 Area 라벨을 하나 이상 지정한다. 실질적인 변경이 여러 영역에 걸치면 복수 지정할 수 있다.
3. README 목차 갱신이나 링크 수정처럼 부수적인 변경에는 별도 Area 라벨을 추가하지 않는다.
4. ADR은 `type:decision`을 사용하고, FE-ADR은 `area:frontend`, BE-ADR은 `area:backend`를 적용한다.
5. Type은 단순 파일 확장자나 폴더 위치보다 PR의 주된 변경 목적을 기준으로 정한다.
6. 서로 독립적인 변경은 하나의 PR에 묶기보다 분리하는 것을 우선한다.

### 적용 예시

| 변경 내용 | Type | Area |
|---|---|---|
| FE-ADR 신규 추가 | `type:decision` | `area:frontend` |
| BE-ADR 신규 추가 | `type:decision` | `area:backend` |
| 가격지수 산정 정책 결정 | `type:decision` | `area:product` |
| 백엔드 API 요구사항 추가 | `type:feature` | `area:backend` |
| 사용자 흐름 개선 | `type:feature` | `area:ux` |
| 디자인 토큰 변경 | `type:feature` | `area:design-system` |
| 문서 운영 규칙 개편 | `type:docs` | `area:docs` |
| 기술 ADR의 잘못된 설명 수정 | `type:fix` | 해당 기술 영역 |

### 기존 라벨 전환

현재 등록된 라벨 6개는 다음과 같이 **삭제하지 않고 이름을 변경**한다.

| 기존 라벨 | 변경 라벨 | 처리 |
|---|---|---|
| `Decision` | `type:decision` | 이름 변경 |
| `Design-System` | `area:design-system` | 이름 변경 |
| `docs` | `area:docs` | 이름 변경 |
| `frontend` | `area:frontend` | 이름 변경 |
| `Product` | `area:product` | 이름 변경 |
| `UX` | `area:ux` | 이름 변경 |

다음 5개는 신규 생성 대상으로 둔다.

- `type:feature`
- `type:docs`
- `type:fix`
- `type:chore`
- `area:backend`

이름 변경으로 기존 색상과 Issue·PR 연결 관계를 가능한 한 유지한다. 실제 이름 변경·신규 생성 전 현재 사용 현황과 연결 상태를 확인하고 사용자 승인을 받는다. 기존 라벨은 삭제하지 않는다. 실제 라벨 작업은 별도 실행 단계에서 수행한다.

## 3. PR 작성 및 검증

- `.github/PULL_REQUEST_TEMPLATE.md`에 따라 변경 목적과 주요 변경 사항을 작성하고, 필요하면 영향 범위·검증 결과·미정 항목을 참고 사항에 기록한다.
- 관련 PRD/PF/PP/UX/PD/DS 문서를 확인하고 **승인된 결정과 Draft·미정 제안**을 구분한다.
- 링크·경로·`README.md` 목차와 관련 문서 간 정합성을 확인한다.
- 기존 Codex 문서 일관성 검사 Skill을 사용하되 **전체 검사 전에 사용자 승인을 받는다**. 충돌·오류 발견 시 무단 수정하지 않고 검토를 요청한다.
- 검사 결과는 PR에 요약한다. `DOCUMENT-CHECK-HISTORY.md`에 새 검사 결과를 누적하지 않는다. 기존 파일 정리·삭제는 별도 검토 사항이다.
- 실행하지 않은 검사에 `PASS`를 쓰지 않는다. `NOT RUN`과 사유를 남긴다.
- 사용자 승인 없이 커밋·PR 생성·병합·강제 푸시·파괴적 Git 명령을 실행하지 않는다.

## 4. 디자인 시스템 관리

- `design-system/preview/index.html`과 `design-system/tokens/tokens.json`을 최신 미리보기·토큰으로 관리하며, 승인 상태는 `DS-001`을 확인한다.
- 과거 버전 HTML은 누적하지 않는다. 변경 추적은 PR과 Git 기록을 사용한다.
- 디자인 시안이 제품 정책과 충돌하면 원본 요구사항을 임의 변경하지 않고 검토한다.

## 5. Restore / Reimplement

- **Restore:** Git 이력에서 지정한 파일·커밋 상태를 복구한다. 공유 이력을 변경하는 방법은 사전 승인받는다.
- **Reimplement:** 지정한 `docs` 커밋의 승인된 요구사항·디자인·정책을 기준으로 새 구현을 검증한다. 동일한 AI 출력이나 바이트 동일성을 약속하지 않는다.
- 중요 구현 PR에는 사용한 docs 기준 커밋과 검증 증빙을 링크하는 방식을 권장한다.

## 6. 현재 범위

- 자동 CI 또는 브랜치 보호 규칙은 별도로 설정할 때까지 도입된 것으로 간주하지 않는다.

## PR 제목 및 본문

### 제목

PR 제목은 접두사 없이 변경 목적과 내용을 간결하게 작성한다. `[Decision]`, `[Product]`, `[UX]`, `[Design System]`, `[Docs]` 등의 유형 접두사는 사용하지 않는다. 기존 PR 제목은 일괄 수정하지 않는다.

예시:

- `백엔드 아키텍처 ADR 문서 추가`
- `프론트엔드 렌더링 전략 ADR 수정`
- `Price Insight 사용자 흐름 개선`
- `디자인 시스템 토큰 갱신`
- `문서 운영 규칙 및 라벨 분류 체계 개편`

### 본문

- `.github/PULL_REQUEST_TEMPLATE.md`를 기준으로 작성한다.
- 변경 목적은 1~2문장, 주요 변경 사항은 3~5개 이내로 작성한다.
- 영향 범위, 검증 결과, 미정 사항 등 필요한 참고 사항을 기록한다.
- PR 본문에 적용한 라벨 목록을 반복해서 작성하지 않는다.
