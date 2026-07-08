# dooray-mcp

> **[mskim8717/dooray-mcp](https://github.com/mskim8717/dooray-mcp)** · ⭐ N/A (API rate limit) · Python · 최근 푸시 N/A · 카테고리: 🤝 Collaboration & Communication

Dooray API를 활용해 일정 추가 및 관리를 지원하는 MCP 서버입니다.

## 개요

Dooray API로 캘린더 일정을 조회·등록하는 경량 Python MCP 서버다. 일정 추가 시 시작/종료 시간 자동 설정, 위치·설명 정보를 지원한다. Smithery로 자동 설치하거나 소스에서 직접 설치할 수 있다.

## 제공 도구

| 도구 | 기능 |
|------|------|
| `get_schedule` | 지정 기간의 일정을 조회 |
| `add_schedule` | 새 일정을 추가 (시작/종료 시간, 위치, 설명 지원) |

## 설치

```bash
# Smithery 자동 설치
npx -y @smithery/cli install @mskim8717/dooray-mcp --client claude

# 또는 소스
git clone https://github.com/mskim8717/dooray-mcp.git
cd dooray-mcp && pip install -e .
```

## 필요 키 · 환경변수

| 환경변수 | 발급처 | 필수 |
|---------|--------|------|
| `DOORAY_API_KEY` | Dooray! 개인 인증 토큰 | ✅ |
| `DOORAY_MEMBER_ID` | Dooray 멤버 ID | ✅ |
| `DOORAY_CALENDAR_ID` | Dooray 캘린더 ID | ✅ |

`.env` 파일로 설정한다.

## 설정 예시

```json
{
  "mcpServers": {
    "dooray-mcp": {
      "command": "/Users/yourname/project/.venv/bin/python",
      "args": ["/Users/yourname/project/src/dooray-mcp-server.py"]
    }
  }
}
```

## 비고

- 라이선스: MIT.
- GitHub 메타데이터는 수집 시점 API rate limit으로 별점·푸시일 미확보.

---
*수집일: 2026-07-02 · 출처: 저장소 README, 소스 코드(src/dooray-mcp-server.py)*
