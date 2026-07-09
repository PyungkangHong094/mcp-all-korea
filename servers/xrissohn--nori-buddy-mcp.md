# nori-buddy-mcp

> **[xrissohn/nori-buddy-mcp](https://github.com/xrissohn/nori-buddy-mcp)** · ⭐ N/A · Node.js · 최근 푸시 미상 · 카테고리: 🧩 Miscellaneous

카카오톡 안에서 대화하는 성장형 AI 캐릭터 친구(카카오 PlayMCP 제출작) MCP 서버입니다.

## 개요

카카오 Agentic Player 10 / PlayMCP in KC 제출용 성장형 AI 캐릭터("노리톡 버디") MCP 서버다. 카카오톡 안에서 대화하는 AI 캐릭터로, 사용자의 기분·목표·관심사를 바탕으로 오늘의 작은 미션과 응원 메시지를 제공하고 미션 완료에 따라 캐릭터가 성장하는 Agentic 경험을 제공한다. HTTP 서버(`POST /mcp`)로 동작하며 감정 체크·미션 생성·캐릭터 성장 도구를 노출한다. 샘플 서버로 사용자 정보를 저장하지 않으며 모든 결과는 요청 단위로 계산된다.

## 제공 도구

| 도구 | 기능 |
|------|------|
| `talkWithCharacter` | 사용자 메시지에 공감하고 오늘 할 수 있는 작은 행동 제안 (입력: `message`, `userNickname`, `characterName`, `mood`, `goal`, `tone`) |
| `checkMood` | 감정 상태·에너지 점수 분석 및 대화 방향 제공 (입력: `message`, `energyLevel`, `context`) |
| `createDailyMission` | 기분·목표·가용 시간 기반 실행 가능한 미션 3개 생성 (입력: `mood`, `goal`, `availableMinutes`, `intensity`) |
| `growCharacter` | 완료 미션 기반 성장 포인트·레벨업·다음 미션 반환 (입력: `completedMission`, `currentLevel`, `currentPoints`, `streakDays`) |

## 설치

```bash
npm install
npm start
```

로컬 실행 후 health check: `GET http://localhost:3000/health`, MCP 엔드포인트: `POST /mcp`.

## 필요 키 · 환경변수

API 키 불필요 (README에 환경변수 명시 없음).

## 설정 예시

README는 클라이언트 설정 JSON 대신 HTTP 엔드포인트 방식을 안내한다. PlayMCP in KC Git 소스 빌드(Dockerfile 경로 `Dockerfile`, 브랜치 `main`)로 배포한다.

```bash
# tools/list 확인
curl -X POST http://localhost:3000/mcp \
  -H "Content-Type: application/json" \
  -d '{"jsonrpc":"2.0","id":1,"method":"tools/list"}'
```
(README 기반 구성 — 표준 stdio 클라이언트 설정 예시는 없음)

## 비고

- 카카오 PlayMCP 제출용 샘플 서버 — HTTP(`/mcp`) 기반, 테스트용 엔드포인트(`/test/*`) 별도 제공.
- 사용자 정보 미저장. 실서비스화 시 이용자 동의·보관기간·삭제 기능 별도 구현 필요(README 명시).

---
*수집일: 2026-07-03 · 출처: 저장소 README*
