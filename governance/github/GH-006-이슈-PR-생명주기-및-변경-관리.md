# GH-006 — 이슈·PR 생명주기 및 변경 관리

- **버전:** V1
- **상태:** 승인
- **적용 범위:** today-fish Docs·Backend·Frontend의 개발 작업과 완료 후 유지보수
- **관련 문서:** [GH-001 필드 정책](GH-001-이슈-분류-및-필드-정책.md), [GH-002 라벨 정책](GH-002-저장소별-라벨-정책.md), [GH-003 작업 분할 기준](GH-003-작업-계층-및-분할-기준.md), [GH-004 Issue 작성 가이드](GH-004-이슈-템플릿-및-작성-기준.md), [GH-005 Project 사용 가이드](GH-005-프로젝트-뷰-및-자동화-정책.md), [Docs 기여 규칙](../../.github/CONTRIBUTING.md)

## 핵심 요약

Issue에는 **할 일과 완료 조건**, PR에는 **바꾼 내용과 검증 근거**를 남긴다. 작업을 마쳤다면 PR 병합, Issue Closed, Project `Done`, L1 인수 조건을 각각 확인한다. 자동화가 일부를 처리할 수 있어도 결과를 직접 확인한다. Docs의 브랜치·PR 절차는 [Docs 기여 규칙](../../.github/CONTRIBUTING.md)을 따른다.

## 1. 새 작업은 어떤 순서로 진행하나요?

1. **할 일 확인:** 기준 문서와 기존 Issue를 찾는다. 같은 작업이 이미 있거나 선행 결과를 기다려야 하는지 확인한다.
2. **Issue 작성:** [GH-004 Issue 작성 가이드](GH-004-이슈-템플릿-및-작성-기준.md)에 따라 범위·완료 조건·검증 방법을 적는다. L1은 Docs, L2는 실제 변경 대상 Repository에 생성한다.
3. **필드와 라벨 지정:** [GH-001 필드 선택 가이드](GH-001-이슈-분류-및-필드-정책.md)로 Type·Level·`workstream`·Priority를, [GH-002 실제 라벨 목록](GH-002-저장소별-라벨-정책.md)으로 Label을 고른다. Priority 실제 옵션은 화면에서 확인한다.
4. **상위 목표 연결:** L2에 원본 L1과 기준 문서 링크를 남긴다. Parent/Sub-issue 연결을 사용할 수 있다면 추가하되, Repository 간 동작은 아직 `NOT VERIFIED`다.
5. **Project 등록 확인:** 통합 Project #1의 `All Task`에서 Issue를 찾는다. 없으면 권한 범위에서 등록하고 `Level`·`workstream`·`Status`를 확인한다.
6. **착수와 구현:** 선행 조건을 확인하고 `In Progress`로 바꾼다. 해당 Repository의 브랜치 규칙에 따라 구현한다. Docs는 [CONTRIBUTING](../../.github/CONTRIBUTING.md)의 `docs`→`main` 흐름을 따르며 이를 Backend·Frontend에 강제하지 않는다.
7. **검증과 PR:** 완료 조건에 맞는 테스트·문서 검사를 실행한 뒤 L2 Issue와 검증 결과를 PR에 연결한다. Docs PR은 [기존 PR 템플릿](../../.github/PULL_REQUEST_TEMPLATE.md)을 따른다. 실행하지 않은 검사를 PASS로 기록하지 않는다.
8. **리뷰와 병합:** 피드백을 반영하고 필요한 검증을 다시 한다. 리뷰 중인 Project Status는 `In Review`가 맞는지 확인한다.
9. **L2 종료 확인:** PR 병합, Issue Closed, Project `Done`을 각각 확인한다. 완료 조건이 남았다면 Issue를 닫지 않고 남은 일을 기록한다.
10. **L1 종료 확인:** 모든 필수 L2의 결과와 L1 자체의 사용자·운영 인수 조건을 확인한다. 충족한 경우에만 L1을 종료하고 `Done`으로 표시한다.

이 절은 실행 순서다. Type·Label 값의 상세 정의와 Status별 판단 기준은 각각 GH-001·002·005가 원본이다.

## 2. PR에 어떤 Issue를 연결하나요?

원칙은 **L2 Issue 하나당 PR 하나**다. PR에서 해당 L2의 URL과 완료 조건에 대한 검증 결과를 찾을 수 있어야 한다. 같은 Repository의 종료 키워드를 쓰더라도 자동 종료를 전제하지 않는다. 다른 Repository의 Issue는 전체 URL 또는 `owner/repo#번호` 형식으로 대상을 분명히 하고 실제 연결·종료 여부를 확인한다.

PR이 병합됐는데 Issue가 열려 있으면 먼저 남은 완료 조건을 확인한다. 모두 충족했다면 권한 범위에서 Issue를 닫고 Project Status도 확인한다. 일부만 끝났다면 Issue를 성급히 닫지 않고 남은 작업과 검증을 기록한다.

여러 PR이 필요한 예외가 생기면 하나의 목적을 단계적으로 완성하는지, 독립 결과를 가진 둘 이상의 L2인지 [GH-003](GH-003-작업-계층-및-분할-기준.md)의 크기 기준으로 판단한다. 같은 L2에 여러 PR을 연결해야 한다면 각 PR의 범위와 마지막 완료 조건을 Issue에 적는다. Docs PR 제목·본문·라벨·승인 절차는 CONTRIBUTING과 PR 템플릿을 따른다.

## 3. PR을 병합한 뒤 무엇을 확인하나요?

| 확인 대상 | 뜻 | 종료 전에 확인할 것 |
|---|---|---|
| PR merged | 변경이 대상 브랜치에 반영됨 | 리뷰와 필수 검증 결과 |
| Issue Closed | 해당 Issue의 할 일이 끝남 | 본문 완료 조건과 남은 작업 |
| Project `Done` | Project에서 완료 단계로 표시됨 | Issue 실제 종료 상태와 일치 여부 |
| L1 완료 | 상위 기능·기술 목표 달성 | 필수 L2와 L1 자체의 인수 기준 |

PR 병합 뒤에는 **Issue의 완료 조건 → Closed 여부 → Project Status** 순서로 확인한다. Issue가 열려 있거나 Project가 `Done`이 아니라면 먼저 실제로 남은 일이 있는지 확인한다. 일이 끝났다면 누락된 상태만 수동으로 바로잡는다. L2가 Done이 돼도 L1을 자동으로 Done으로 보지 않는다. 활성 Workflow 이름과 미검증 동작은 [GH-005 자동화 확인 가이드](GH-005-프로젝트-뷰-및-자동화-정책.md)에 있다.

## 4. 완료된 기능에서 Bug가 발생했다면?

최초 개발이 완료된 기능에 새 문제가 생기면 **새 Issue**를 만든다. 기존 L1을 유지하고 원본 L1·관련 PR을 링크로 연결한다. L2 성격의 작업이어도 완료된 L1의 새 Sub-issue로 넣지 않는다. Backend·Frontend Issue에는 `Maintenance` 라벨을, 필요하면 기존 `scope: *` 라벨도 적용한다. Docs에는 `Maintenance` 라벨이 없으므로 Docs 유지보수 PR에는 기존 Type/Area 분류를 사용한다.

| 상황 | 처리 |
|---|---|
| 원래 L1 인수 조건이 실제로 미충족이었거나 잘못 종료됨 | 기존 L1을 재오픈하고 미충족 조건과 관련 작업을 바로잡는다. |
| 최초 완료 후 새 Bug 발견 | 새 `Bug` Issue를 만들고 원본 L1을 관련 링크로 연결한다. |
| 새로운 개선 요구사항 | 범위와 독립 완료 기준을 판단해 새 Issue를 만든다. 큰 새 사용자 목표면 새 L1을 검토한다. |
| 리팩터링 | 동작 보존·검증 범위를 가진 새 `Task` Issue로 관리한다. |
| 요구사항·설계 변경 | 기준 문서의 승인 절차와 영향 범위를 먼저 확인한 뒤 새 작업을 분리한다. |

원래 Issue를 다시 여는 기준은 **원래 약속한 완료 조건의 실패**다. 완료 이후 생긴 요구를 원래 Issue의 진행률에 소급해 섞지 않는다.

## 5. 가격 차트 작업을 처음부터 끝까지 따라가기

다음은 실제 Issue·PR 기록이 아닌 **가상 업무 흐름**이다.

1. **L1 목표 등록:** Docs에 가격 차트 `Feature`·`L1`을 만든다. 기준 PRD·UX와 사용자 인수 조건을 적는다. 결과 확인: 기능 전체의 포함·제외 범위가 읽힌다.
2. **BE·FE L2 분할:** Backend에 가격 조회 API `Task`·`L2`·`BE`를, Frontend에 차트·기간 선택 `Task`·`L2`·`FE`를 만든다. 각 L2에 L1과 기준 문서 링크, 검증 방법을 적는다. 결과 확인: 두 작업을 독립적으로 리뷰할 수 있다.
3. **Project 등록:** 세 Issue를 통합 Project에서 찾는다. L1은 `MVP Roadmap`, L2는 각각 `Backend`·`Frontend` View의 필터 조건에 맞는지 확인한다. 안 보이면 [GH-005 문제 해결 순서](GH-005-프로젝트-뷰-및-자동화-정책.md)를 따른다.
4. **구현·PR·리뷰:** 각 Repository 규칙에 따라 작업하고 L2별 PR에 Issue와 검증 근거를 연결한다. 결과 확인: 리뷰 중 Status와 PR의 실제 상태가 맞는다.
5. **완료 판정:** PR 병합 후 각 L2의 Issue Closed·Project `Done`을 확인한다. 이어 가격 차트의 상위 인수 조건을 확인한 뒤 L1을 종료한다.
6. **후속 오류:** 완료 뒤 API 응답 오류가 발견되면 Backend에 새 `Bug` Issue를 만들고 `Maintenance`·`scope: API`를 검토한다. 원본 L1은 새 Sub-issue가 아니라 관련 링크로 남긴다.

다른 저장소 간 Parent/Sub-issue 연결과 자동 종료는 실제 작업에서 확인한다. 가능 여부가 확인되기 전에도 명시적 링크와 완료 조건으로 추적한다.

## 6. 관련 문서

- [GH-004 — Issue 본문을 쓰는 방법](GH-004-이슈-템플릿-및-작성-기준.md)
- [GH-005 — Project View·Status·자동화 확인](GH-005-프로젝트-뷰-및-자동화-정책.md)
- [Docs CONTRIBUTING — Docs 브랜치·PR 절차](../../.github/CONTRIBUTING.md)
