# mcp-weather

> **[jikime/mcp-weather](https://github.com/jikime/mcp-weather)** · ⭐ 0 · Python · 최근 푸시 2025-04-16 · 카테고리: 🌦 Weather

기상청 단기예보 API로 지역 검색 기반 한국 날씨 정보를 제공하는 MCP 서버입니다.

## 개요

공공데이터포털 기상청 단기예보(구 동네예보) API를 활용하는 Python(FastMCP) 기반 MCP 서버다. 시·구·동 이름으로 기상청 격자좌표를 조회한 뒤 해당 지역의 금일 날씨 예보(하늘상태, 온도, 강수량, 습도, 풍속, 풍향 등)를 제공한다.

## 제공 도구

| 도구 | 기능 |
|------|------|
| `get_grid_location` | 시·구·동 이름으로 기상청 격자좌표(nx/ny)를 조회 |
| `get_forecast` | 좌표 기반으로 해당 지역의 단기예보 날씨 정보를 조회 |

## 설치

```bash
git clone https://github.com/jikime/mcp-weather.git
cd mcp-weather
uv venv
source .venv/bin/activate
uv add "mcp[cli]"
```

## 필요 키 · 환경변수

| 환경변수 | 발급처 | 필수 |
|---------|--------|------|
| `OPEN_DATA_API_KEY` | [공공데이터포털 기상청 단기예보 조회서비스](https://www.data.go.kr/data/15084084/openapi.do) | ✅ |

프로젝트 루트에 `.env` 파일로 설정한다.

## 설정 예시

```json
{
  "mcpServers": {
    "Korea Weather": {
      "command": "/path/bin/uv",
      "args": [
        "--directory",
        "/Users/Dev/mcp/mcp-weather",
        "run",
        "src/server.py"
      ]
    }
  }
}
```

## 비고

- README의 실행 예시는 `ko_weather.py`를 언급하나 실제 진입점은 `src/server.py`다.

---
*수집일: 2026-07-02 · 출처: 저장소 README, 소스 코드(src/server.py)*
