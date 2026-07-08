# dooray_mcp

> **[dooray-go/dooray_mcp](https://github.com/dooray-go/dooray_mcp)** · ⭐ N/A (API rate limit) · Go · 최근 푸시 N/A · 카테고리: 🤝 Collaboration & Communication

Dooray! 메신저 보내기, 캘린더 조회 및 일정 등록 기능을 제공하는 MCP 서버입니다.

## 개요

Dooray!를 Claude 등 MCP 호환 클라이언트에서 자연어로 다루게 해 주는 Go 기반 MCP 서버다. 메신저 DM 전송, 캘린더 조회·일정 등록(종일/반복일정 지원), 업무(프로젝트 포스트) 검색, 멤버 검색을 지원한다. Homebrew·릴리즈 바이너리·소스 빌드로 설치한다.

## 제공 도구

| 도구 | 기능 |
|------|------|
| `dooray_messenger` | 다른 멤버에게 DM 전송 |
| `dooray_calendar_calendars` | 내 캘린더 목록 조회 |
| `dooray_calendar_events` | 기간별 일정 조회 |
| `dooray_calendar_post_event` | 일정 등록 (종일/반복일정 지원) |
| `dooray_account_members` | 이름/userCode로 멤버 검색 |
| `dooray_account_member` | 멤버 상세정보 조회 |
| `dooray_project` | 참여 중인 프로젝트 조회 |
| `dooray_posts` | 업무(포스트) 검색 (담당자/상태/기한 필터) |
| `os` | 현재 시각 조회 |

## 설치

```bash
brew tap dooray-go/tap
brew install dooray-mcp
```

또는 소스 빌드(Go 1.26+): `go build -o dist/dooray-mcp .`

## 필요 키 · 환경변수

| 환경변수 | 발급처 | 필수 |
|---------|--------|------|
| (CLI 인자 `--token`) | Dooray! 개인설정 > API > 개인 인증 토큰 | ✅ |

API 키는 환경변수가 아니라 `--token` 실행 인자로 전달한다.

## 설정 예시

```json
{
  "mcpServers": {
    "dooray": {
      "command": "dooray-mcp",
      "args": ["--token", "{개인토큰}"]
    }
  }
}
```

## 비고

- 반복 일정은 daily/weekly/monthly/yearly 주기, interval, 종료일, 요일/일자 지정을 지원.
- GitHub 메타데이터는 수집 시점 API rate limit으로 별점·푸시일 미확보.

---
*수집일: 2026-07-02 · 출처: 저장소 README*
