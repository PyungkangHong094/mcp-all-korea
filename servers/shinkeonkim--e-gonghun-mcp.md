# e-gonghun-mcp

> **[shinkeonkim/e-gonghun-mcp](https://github.com/shinkeonkim/e-gonghun-mcp)** · ⭐ N/A · Python · 최근 푸시 미상 · 카테고리: 📜 Legal & Government

독립유공자 공적조서·포상 기록을 조회하는 e-공훈 MCP 서버입니다.

## 개요

국가보훈부 공훈전자사료관의 독립유공자 공훈록 및 공적조서를 조회하는 MCP 서버다. 이름·생년월일·훈격·운동계열 등으로 공훈록 목록을 검색하고, 공적조서와 훈격·운동계열 코드 정보를 조회할 수 있다. Python + uv로 로컬 stdio 서버로 실행되며 Claude Desktop과 연동한다.

## 제공 도구

| 도구 | 기능 |
|------|------|
| `get_merit_list` | 독립유공자 공훈록 목록 조회(이름·생년월일·훈격·운동계열 등으로 검색) |
| `get_public_report` | 독립유공자 공적조서 조회 |
| `get_hunkuk_codes` | 훈격 코드 정보 조회 |
| `get_workout_affil_codes` | 운동계열 코드 정보 조회 |
| `clear_cache` | 캐시된 데이터 초기화 |

## 설치

```bash
git clone https://github.com/<owner>/e-gonghun-mcp.git
cd e-gonghun-mcp
uv pip install -e .

# .env 설정
cp .env.sample .env
```

요구: macOS 또는 Windows, Claude Desktop 최신 버전, uv 0.4.18 이상.

## 필요 키 · 환경변수

`.env.sample`을 `.env`로 복사해 설정(구체적 키 항목은 README에 명시되지 않음). API 키 요구 여부는 README에 명시 없음.

## 설정 예시

```json
{
  "mcpServers": {
    "e_gonghun_mcp": {
      "command": "uv",
      "args": [
        "--directory",
        "C:\\Users\\사용자이름\\projects\\e-gonghun-mcp",
        "run",
        "gonghun-mcp"
      ]
    }
  }
}
```

## 비고

- 라이선스 MIT.
- `.env.sample` → `.env` 복사가 필요하나 README에 구체 환경변수명은 명시되지 않음.

---
*수집일: 2026-07-03 · 출처: 저장소 README*
