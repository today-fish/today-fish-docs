# BE-TECH-SPEC-006 실시간 채팅

- **버전:** V1
- **상태:** 승인
- **기준일:** 2026-11-11
- **대상:** 오늘의 수산 백엔드 MVP
- **관련 문서:** [BE-ADR-001](../BE-ADR-001-백엔드-아키텍처.md), [BE-ADR-002](../BE-ADR-002-런타임-및-웹-프레임워크.md), [BE-TECH-SPEC-005](BE-TECH-SPEC-005-사용자-식별-인증-세션.md), [PF-005](../../../product/features/PF-005-실시간-채팅.md), [FE-ADR-008](../../frontend/adr/FE-ADR-008-실시간-채팅-WebSocket-연결-전략.md), [통합 ERD](../erd/BE-ERD-001-통합-데이터-모델.md)

## Summary

갈치·고등어·전복 상세 화면에 품목별 실시간 채팅을 제공한다. Spring WebSocket, STOMP, Simple Broker를 사용하며, 메시지는 영구 저장하지 않는다.

사용자 인증은 005의 JWT 및 Principal을 사용한다. 채팅 참여자 세션은 어종별로 서버 메모리에서 관리하고, 닉네임·색상 할당과 연결 단절 후 3분 복구를 담당한다.

동일 사용자의 같은 품목 다중 탭은 하나의 참여자 세션을 공유하되 WebSocket 연결은 탭별로 관리한다.

## 1. 범위와 불변 조건

1. 갈치·고등어·전복은 독립된 채팅방을 사용한다.
2. 로그인 없이 익명 채팅에 참여한다.
3. 닉네임 500개와 색상 20개의 조합을 서버에서 무작위 할당한다.
4. 동일 품목의 활성·예약 참여자 간 같은 조합을 중복 할당하지 않는다.
5. 마지막 연결 종료 후 3분 동안 기존 조합을 예약한다.
6. 메시지는 최대 300 Unicode 문자, 사용자당 초당 최대 5개로 제한한다.
7. 정규화된 금칙어 목록을 서버에서 검사한다.
8. 메시지는 실시간 전달만 수행하며 서버에 영구 저장하지 않는다.
9. 연결·참여자 상태는 단일 Spring 서버 메모리에서 관리한다.
10. 외부 Broker, Redis, HTTP Session, 채팅 메시지 테이블은 도입하지 않는다.

사용자 신고·차단, 메시지 삭제·검색, 1:1 채팅, 첨부파일, 과거 대화 조회는 MVP 범위에서 제외한다.

## 2. 구성과 상태 모델

### 2.1 구성

```text
Next.js / STOMP.js
       |
       | WSS
       v
Spring Boot
       |
       +-- 005 WebSocket Authentication
       |     JWT / Principal / Origin / CSRF
       |
       +-- ChatController
       |     참여 / 전송 / 오류 응답
       |
       +-- ChatService
       |     권한 / 내용 / 전송 빈도 검증
       |
       +-- ChatSessionRegistry
       |     참여자 / 연결 / 조합 / 3분 예약
       |
       +-- Simple Broker
             어종별 메시지 전달
```

005의 인증 로직을 채팅 모듈에서 중복 구현하지 않는다.

### 2.2 채팅방

기존 내부 `SPECIES.id`를 채팅방 식별자로 사용하며 외부 API 품목 코드와 구분한다.

초기에는 갈치·고등어·전복에 해당하는 어종만 허용한다. 지원 대상은 애플리케이션 설정으로 관리하며 실제 `SPECIES`와 일치하는지 검증한다.

별도 `CHAT_ROOM` 테이블을 생성하지 않는다.

### 2.3 참여자 세션

참여자 세션은 영구 엔티티가 아닌 서버 메모리 상태다.

| 필드                   | 의미                               |
| ---------------------- | ---------------------------------- |
| `participantSessionId` | 서버가 발급한 임시 세션 ID         |
| `speciesId`            | 소속 어종                          |
| `ownerUserId`          | 005에서 인증한 사용자 ID           |
| `nicknameId`           | 닉네임 풀 인덱스                   |
| `colorId`              | 색상 풀 인덱스                     |
| `connectionIds`        | 현재 참여 중인 WebSocket 연결 집합 |
| `state`                | ACTIVE / RESERVED                  |
| `reservationExpiresAt` | 예약 만료 시각                     |

하나의 참여자 세션은 같은 품목의 여러 WebSocket 연결을 가질 수 있다.

서버는 세션 ID만으로 소유권을 승인하지 않는다. 인증된 Principal, 품목, 서버에 보존한 세션 소유 정보를 함께 검증한다.

단일 서버 재시작 시 메모리 참여자 상태는 소멸하며 3분 복원을 보장하지 않는다.

`(userId, speciesId)`와 `participantSessionId`로 각각 조회한다. 표준 Java 동시성 컬렉션을 고려하되 복합 상태 변경과 조합 점유는 어종별 동기화 또는 명시적 락으로 원자적으로 처리한다.

## 3. 참여·닉네임 및 복구

### 3.1 최초 참여

1. 005의 익명 JWT와 CSRF 준비를 완료한다.
2. WebSocket 핸드셰이크 및 STOMP CONNECT를 수행한다.
3. 서버가 어종과 인증된 사용자 ID를 확인한다.
4. 같은 사용자 ID와 품목의 ACTIVE 또는 유효한 RESERVED 세션이 있으면 재사용하고 현재 연결을 추가한다.
5. 없으면 해당 어종에서 사용 가능한 닉네임·색상 조합을 원자적으로 할당한다.
6. 참여자 세션을 ACTIVE로 등록하고 연결을 연결 집합에 추가한다.
7. 클라이언트에 세션 ID와 닉네임·색상을 전달한다.

닉네임과 색상은 클라이언트가 직접 선택하거나 변경할 수 없다.

### 3.2 조합 할당

가능한 조합은 500 × 20 = 10,000개다.

동일 품목의 ACTIVE 및 RESERVED 세션에서 사용 중인 조합은 신규 할당 대상에서 제외한다. 서로 다른 품목에서 동일 조합을 사용하는 것은 허용한다.

원자적 할당은 어종별 동기화 경계를 두어 구현한다. 다중 스레드가 동시에 참여해도 같은 조합을 중복 확보할 수 없어야 한다.

조합이 모두 점유되면 참여를 대기 상태로 처리한다. 여유 발생 시 클라이언트가 제한된 간격으로 자동 재시도하며, 무한 고빈도 요청은 허용하지 않는다.

### 3.3 연결 종료와 3분 예약

- 하나의 탭만 종료되고 같은 참여자 세션의 다른 연결이 남았다면 ACTIVE를 유지한다.
- 마지막 연결이 종료되면 RESERVED로 전환한다.
- 예약 만료 시각은 마지막 유효 연결 종료를 서버가 확인한 시점부터 3분이다.
- 예약 중에는 닉네임·색상 조합을 다른 참여자에게 할당하지 않는다.
- 기한 내 정당한 복원 요청은 기존 세션을 ACTIVE로 전환한다.
- 기한이 지나면 세션을 정리하고 조합을 다시 사용할 수 있게 한다.

중복 연결 종료 이벤트와 비정상 네트워크 종료에도 상태 전이가 중복 실행되지 않도록 처리한다.

### 3.4 복원 자격정보

클라이언트는 서버가 발급한 참여자 세션 식별 정보를 `localStorage`에 보존할 수 있다.

서버는 세션 ID와 함께 현재 JWT Principal 및 품목별 소유권을 확인한다. 클라이언트가 전달한 닉네임·색상은 신뢰하지 않는다.

복원은 유효한 JWT Principal의 사용자 ID와 기존 소유자 ID, 품목이 일치하고 서버에 ACTIVE 또는 만료 전 RESERVED 세션이 존재할 때 허용한다. JWT 만료나 쿠키 삭제로 새 사용자 ID가 발급되면 기존 세션을 복원하지 않는다.

별도 복원 토큰은 발급하지 않는다. 소유권 또는 품목이 다르면 기존 세션 정보를 노출하지 않고 거부한다. 이후 세션 ID를 정리하고 신규 참여하되, 같은 사용자·품목의 유효 세션이 있으면 먼저 재사용한다.

## 4. STOMP 계약

### 4.1 Destination과 연결 순서

| 동작                 | 경로                         |
| -------------------- | ---------------------------- |
| WebSocket 핸드셰이크 | `/ws/chat`                   |
| 참여·복원 요청       | `/app/chat/{speciesId}/join` |
| 메시지 전송          | `/app/chat/{speciesId}/send` |
| 메시지 수신          | `/topic/chat/{speciesId}`    |
| 개인 참여 결과       | `/user/queue/chat/session`   |
| 전송 오류            | `/user/queue/chat/error`     |

위 경로는 정식 STOMP 계약이다. `{speciesId}`는 내부 `SPECIES.id BIGINT`이며 외부 API 품목 코드가 아니다. `/ws/chat`은 HTTP WebSocket Handshake 경로이며 나머지는 STOMP Destination이다.

FAB 최초 클릭 → 005 인증 준비 → Handshake → CONNECT → 개인 `session`·`error` 구독 처리 확인 → JOIN → 참여 성공 → 해당 품목 Topic 구독 → 메시지 송수신 순서로 진행한다.

구독의 서버 처리 완료 여부는 단순 SUBSCRIBE 전송만으로 단정하지 않으며 STOMP RECEIPT 연동은 구현 시 검증한다. 참여 전 Topic SUBSCRIBE·메시지 SEND는 거부한다.

같은 Principal의 다른 탭에 결과가 전달되지 않도록 요청 WebSocket 세션 ID로 개인 응답을 한정한다. Spring의 `@SendToUser(broadcast = false)` 또는 동등한 세션 지정 전달을 적용하고 실제 라우팅은 통합 검증한다.

`APP_USER.id`·`speciesId`는 BIGINT, `participantSessionId`·`requestId`·`clientMessageId`·`messageId`는 UUID다. `requestId`는 JOIN 요청을, `clientMessageId`는 SEND 요청을 식별한다.

### 4.2 참여 요청

```json
{"requestId":"a6b49f84-7cd2-4bb7-94e4-20d77836c8e1"}
```

신규 요청은 `participantSessionId`를 생략한다. 기존 세션 복원은 `{"requestId":"c9bd7b28-cf47-4f24-9b8a-688fe722a520","participantSessionId":"550e8400-e29b-41d4-a716-446655440000"}`을 보낸다.

`-1`이나 잘못된 UUID는 신규 참여 표시로 취급하지 않고 `CHAT_CONTENT_INVALID`로 거부한다. Java DTO의 선택적 UUID가 null로 매핑되더라도 외부 JSON은 필드 생략을 기본으로 한다.

서버는 요청 Destination의 어종, JWT Principal, 서버에 보관한 세션의 소유자·품목·ACTIVE 또는 유효한 RESERVED 상태를 검증한다. 세션 ID가 없어도 같은 사용자·품목의 유효 세션이 있으면 재사용한다.

명시한 세션 ID의 복원이 실패하면 `CHAT_SESSION_NOT_RESTORABLE`을 반환한다. 클라이언트는 오래된 ID를 지우고 신규 JOIN을 요청하며 서버는 같은 사용자·품목의 유효 세션을 먼저 재사용한다.

참여 성공 시 다음 형태의 상태를 반환한다.

```json
{
  "requestId": "a6b49f84-7cd2-4bb7-94e4-20d77836c8e1",
  "speciesId": 1,
  "participantSessionId": "550e8400-e29b-41d4-a716-446655440000",
  "nickname": "푸른갈매기",
  "colorId": 4,
  "restored": false
}
```

`/user/queue/chat/session` 응답은 요청 `requestId`를 그대로 돌려준다. `speciesId`(BIGINT), `participantSessionId`(UUID), `nickname`(문자열), `colorId`(정수), `restored`(boolean)는 필수다.

`restored=true`는 ACTIVE 재사용 또는 RESERVED 복원을, `false`는 신규 세션 생성을 뜻한다. 실제 어종 ID·닉네임 값은 서버 데이터에 따른다. 사용자 ID와 JWT 원문은 보내지 않는다.

### 4.3 메시지 계약

클라이언트는 메시지 본문과 중복 식별용 요청 ID를 보낸다.

```json
{
  "clientMessageId": "1f25cf07-3326-4b64-a032-6625b46bd36b",
  "content": "오늘 갈치 가격이 많이 올랐네요."
}
```

서버는 인증된 참여자 세션을 기준으로 메시지를 구성한다.

```json
{
  "messageId": "de992ecc-6ca1-42d1-b34d-08f43e682b1b",
  "clientMessageId": "1f25cf07-3326-4b64-a032-6625b46bd36b",
  "speciesId": 1,
  "participantSessionId": "550e8400-e29b-41d4-a716-446655440000",
  "nickname": "푸른갈매기",
  "colorId": 4,
  "content": "오늘 갈치 가격이 많이 올랐네요.",
  "createdAt": "2026-11-12T04:00:00Z"
}
```

SEND의 `clientMessageId`(UUID)와 `content`(문자열)는 필수다. 브로드캐스트의 `messageId`는 서버 생성 UUID, `createdAt`은 서버 UTC ISO 8601 시각이며 나머지 필드는 검증된 세션 상태에서 생성한다.

`clientMessageId`는 요청 값을 그대로 전달한다. `messageId`는 일시적 식별에만 사용한다. `speciesId`가 채팅방을, `participantSessionId`가 비영구 참여자를 식별한다.

전송 성공 후에도 실제 수신자의 전달·확인까지 보장하지 않는다.

### 4.4 채팅 오류와 DTO

애플리케이션 오류는 요청한 WebSocket 세션의 `/user/queue/chat/error`로 전송한다. JSON `code`는 다음 Java Enum 이름을 문자열로 직렬화한다.

```java
enum ChatErrorCode {
    CHAT_SESSION_NOT_RESTORABLE, CHAT_ROOM_NOT_SUPPORTED, CHAT_ROOM_FULL,
    CHAT_NOT_JOINED, CHAT_CONTENT_INVALID, CHAT_CONTENT_TOO_LONG,
    CHAT_RATE_LIMITED, CHAT_FORBIDDEN_WORD
}

record ChatJoinRequest(UUID requestId, UUID participantSessionId) {}
record ChatJoinResponse(UUID requestId, Long speciesId, UUID participantSessionId,
                        String nickname, Integer colorId, boolean restored) {}
record ChatSendRequest(UUID clientMessageId, String content) {}
record ChatErrorResponse(UUID requestId, UUID clientMessageId,
                         ChatErrorCode code, String message, Long retryAfterMs) {}
```

신규 JOIN JSON은 `participantSessionId`를 생략한다. 오류 응답에서 JOIN은 `requestId`, SEND는 `clientMessageId`만 포함하며 다른 상관관계 필드는 생략한다.

식별자 자체가 누락·파싱 불가하면 값을 만들어 돌려주지 않는다. `code`와 사용자 안내용 `message`는 필수이며 `retryAfterMs`는 서버가 지연값을 산정한 경우에만 포함한다. 클라이언트는 `message` 문구 대신 `code`로 분기한다.

```json
{"requestId":"a6b49f84-7cd2-4bb7-94e4-20d77836c8e1","code":"CHAT_ROOM_FULL","message":"현재 채팅방이 가득 찼습니다."}
```

```json
{"clientMessageId":"1f25cf07-3326-4b64-a032-6625b46bd36b","code":"CHAT_RATE_LIMITED","message":"메시지를 너무 빠르게 보내고 있습니다.","retryAfterMs":1000}
```

| 코드 | 조건·처리 |
|---|---|
| `CHAT_SESSION_NOT_RESTORABLE` | 세션 없음·소유자/품목 불일치·예약 만료; 존재 여부를 구별해 노출하지 않고 오래된 ID를 정리한 뒤 신규 JOIN |
| `CHAT_ROOM_NOT_SUPPORTED` | 미지원 `speciesId`; 참여 불가 안내 |
| `CHAT_ROOM_FULL` | 조합 고갈; 참여 대기 및 제한적 자동 재시도. 지연·횟수의 세부 값은 미확정 |
| `CHAT_NOT_JOINED` | 참여 전 메시지 SEND; 전송 비활성화 |
| `CHAT_CONTENT_INVALID` | 빈 본문·형식 오류 또는 JOIN/SEND 필수 UUID 누락·잘못된 형식; 입력 수정 |
| `CHAT_CONTENT_TOO_LONG` | 300 Unicode 코드 포인트 초과; 길이 안내 |
| `CHAT_RATE_LIMITED` | 같은 사용자 ID의 모든 탭·품목 합산 초당 5개 초과; 재전송 제한 |
| `CHAT_FORBIDDEN_WORD` | 서버 금칙어 포함; 내용 수정 |

Handshake JWT·Origin 및 CONNECT CSRF 실패, 임의 Destination 접근, 인증되지 않은 SUBSCRIBE/SEND는 005의 인증·프로토콜 단계에서 거부한다. HTTP 상태 코드를 채팅 STOMP 오류 Payload로 변환하지 않는다. 요청별 응답 라우팅과 구독 처리 확인은 Spring 통합 검증 대상이다.

## 5. 메시지 검증 및 권한

### 5.1 검증 순서

1. 인증된 Principal 존재 확인
2. 허용된 어종·Destination 확인
3. 현재 연결의 참여자 세션 및 품목 권한 확인
4. 메시지 본문 형식·길이 검증
5. 사용자 단위 전송 빈도 검증
6. 정규화 금칙어 검사
7. 서버 메시지 구성 및 브로드캐스트

### 5.2 메시지 제한

- 본문은 공백만 있는 메시지를 허용하지 않는다.
- 최대 길이는 **Unicode 코드 포인트 300개**이며 Java와 JavaScript에서 동일하게 계산한다.
- 사용자당 최근 1초 구간에서 최대 5개 메시지 전송을 허용한다.
- 같은 사용자 ID의 여러 탭·연결·품목 요청은 전송 제한을 공유한다.
- 클라이언트가 지정한 발신자 ID, 닉네임, 색상은 사용하지 않는다.

Unicode 문자 수의 Java·JavaScript 처리 방식은 통합 테스트로 일치시킨다.

금칙어는 서버 관리 목록을 사용하며 금칙어가 포함된 사용자 입력 원문은 영구 저장하지 않는다. Unicode 정규화와 대소문자·공백 처리 규칙을 고정해 검사하며, 거부 시 클라이언트에 오류 코드를 전달한다.

### 5.3 STOMP 권한

- `CONNECT`: 005의 인증 및 CSRF 검증 필수
- `SUBSCRIBE`: 개인 session/error 경로 또는 참여가 완료된 어종 Topic만 허용; 다른 어종과 참여 전 Topic은 거부
- `SEND`: 참여·복원 JOIN과 참여 완료된 어종의 메시지 SEND만 허용
- 클라이언트의 `/topic/**` 직접 전송 차단
- 다른 참여자 세션 가장 및 임의 Destination 차단

모든 메시지마다 PostgreSQL에서 사용자 정보를 재조회하지 않는다.

## 6. 동시성 및 메모리 관리

### 6.1 상태 변경

다음 작업은 중복·경합에 안전해야 한다.

- 참여자 세션 최초 생성
- 닉네임·색상 조합 할당
- 다중 탭 연결 추가·제거
- ACTIVE → RESERVED 전환
- RESERVED → ACTIVE 복구
- 예약 만료 및 조합 반환

동일 사용자·품목에 대한 중복 참여 요청은 서버 메모리에서 기존 참여자 세션을 확인한 뒤 처리한다.

### 6.2 정리

- 연결 종료 이벤트가 중복 발생해도 연결 집합을 정확히 갱신한다.
- Heartbeat와 타임아웃으로 비정상 연결을 감지한다.
- RESERVED 만료 상태는 주기적 정리 또는 접근 시 정리한다.
- 전송 제한 카운터와 사용하지 않는 세션 상태도 정리한다.

PostgreSQL, Redis, 별도 세션 복구 테이블은 사용하지 않는다.

## 7. 프론트엔드 연결 정책

FE-ADR-008의 다음 계약을 유지한다.

| 항목                | 정책                            |
| ------------------- | ------------------------------- |
| 클라이언트          | `@stomp/stompjs`                |
| 탭당 연결           | 최대 1개                        |
| 패널 닫기·내부 이동 | 연결 유지                       |
| 수신 메시지         | 최근 100개 브라우저 메모리 보관 |
| 자동 재연결         | 약 2초·5초 후 최대 2회          |
| 자동 재연결 실패    | 수동 재시도                     |
| Heartbeat 희망 간격 | 송·수신 각 10초                 |
| 누락 메시지         | 복구하지 않음                   |

재연결 시 005의 JWT 인증을 다시 준비하고, 참여자 세션을 복구한 후 STOMP 구독을 복원한다.

CONNECT 후 개인 session/error 구독의 처리 확인을 거쳐 JOIN한다. JOIN 성공 응답의 `requestId`로 요청을 대응시키고 그 뒤 품목 Topic을 구독한다. 같은 Principal의 탭마다 응답은 요청 WebSocket 세션에만 전달된다. 구독 처리 확인에 사용할 STOMP RECEIPT의 Spring 지원과 실제 순서는 통합 검증한다.

최초 채팅 FAB 클릭 시 인증과 연결을 시작한다. 상세 페이지 진입만으로 연결하지 않으며 패널 닫기와 앱 내부 이동 시 기존 연결을 유지한다.

## 8. 장애·성능 및 운영

| 상황                       | 처리                            |
| -------------------------- | ------------------------------- |
| JWT·CSRF·Origin 오류       | 연결 거부                       |
| 참여자 소유권 불일치       | `CHAT_SESSION_NOT_RESTORABLE` |
| 미지원 어종                | `CHAT_ROOM_NOT_SUPPORTED`    |
| 조합 10,000개 고갈         | `CHAT_ROOM_FULL`, 제한적 재시도 |
| 본문·금칙어·전송 제한 위반 | §4.4 코드로 요청 연결에 오류 응답, 메시지 미전달 |
| 네트워크 단절              | 연결 정리·3분 예약·재연결       |
| 서버 재시작                | 메모리 연결·참여자 상태 소멸    |
| 메시지 전달 실패           | 영구 큐·과거 조회·복원 없음     |

운영 이벤트는 연결·해제·연결 오류·재연결 실패·채팅 서비스 장애 및 운영 오류만 최대 30일 보존한다.

메시지 본문, 개별 메시지 전송·수신 이벤트, 메시지별 발신자·수신자·시각, JWT·CSRF 토큰은 운영 로그에 기록하지 않는다.

출시 검증 목표는 **품목별 500명 동시 접속과 정상 메시지 전달 p95 500ms 이하**다. 이는 실측으로 검증해야 하며 Simple Broker 사용만으로 충족을 보장하지 않는다.

## 9. 문서 연계 및 구현 검증

### 확정된 책임 경계

| 문서 | 책임                                                   |
| ---- | ------------------------------------------------------ |
| 005  | APP_USER, JWT, CSRF, 인증 Principal                    |
| 006  | 품목별 참여자 세션, 닉네임·색상, 3분 예약, 메시지 전달 |
| ERD  | 영구 데이터 모델 및 관계                               |

현재 권장 구조에서는 ERD에 `APP_USER`만 추가한다. 채팅방은 기존 `SPECIES`를 참조하고, 참여자 세션·메시지는 별도 영속 테이블로 저장하지 않는다.

### 확정된 예외 및 구현 검증

최초 JWT 동시 발급으로 서로 다른 사용자 ID를 받은 탭은 다른 참여자로 처리될 수 있다. 동일 사용자·품목 세션 생성은 원자적으로 처리한다. 쿠키가 하나로 수렴해도 기존 연결의 Principal은 바꾸지 않는다. JWT 만료 또는 쿠키 삭제로 새 ID를 받으면 신규 참여한다. 기존 세션은 다른 연결이 남거나 예약이 만료되기 전까지 유지한다. 연결 중 JWT 만료만으로 연결을 종료하지 않는다.

Spring Security와 CSRF·STOMP 연계, 배포 도메인과 쿠키 전송, 500명 및 p95 500ms 목표는 구현 후 검증한다.
