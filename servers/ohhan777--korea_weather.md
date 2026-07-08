# korea_weather

> **[ohhan777/korea_weather](https://github.com/ohhan777/korea_weather)** · ⭐ - · Python · 카테고리: 🌦 Weather

기상청 단기예보 조회서비스 API 기반으로 한국 날씨 정보를 제공하는 MCP 서버.

## 개요

기상청 단기예보 API를 연동해 Claude·Cursor 등 MCP 클라이언트에 날씨 정보를 제공하는 FastMCP 서버다(한국항공우주연구원 제작). 위경도 좌표를 기상청 격자 좌표(Lambert Conformal Conic)로 변환해 현재 관측·초단기·단기 예보를 조회한다. Smithery(`@ohhan777/korea_weather`)로 배포되며 Smithery v4 `create_server()` 팩토리 패턴을 사용한다.

## 제공 도구

소스(`korea_weather.py`)에서 확인된 `@mcp.tool` 3개:

| 도구 | 기능 |
|------|------|
| `get_nowcast_observation` | 특정 좌표의 현재 관측 날씨 |
| `get_nowcast_forecast` | 특정 좌표의 초단기(6시간) 예보 |
| `get_short_term_forecast` | 특정 좌표의 단기(3~5일) 예보 |

## 설치

```bash
# Smithery 설치
npx -y @smithery/cli mcp add ohhan777/korea_weather --client claude
# 또는 소스
git clone https://github.com/ohhan777/korea_weather.git && cd korea_weather
uv sync && uv run korea_weather.py
```

## 필요 키 · 환경변수

| 환경변수 | 발급처 | 필수 |
|---------|--------|------|
| `KOREA_WEATHER_API_KEY` | [공공데이터포털 기상청 단기예보](https://www.data.go.kr) | ✅ |

## 설정 예시

```json
{
  "mcpServers": {
    "korea_weather": {
      "command": "uv",
      "args": ["--directory", "C:\\path\\to\\korea_weather", "run", "korea_weather.py"],
      "env": { "KOREA_WEATHER_API_KEY": "Input Your API Key Here!" }
    }
  }
}
```

## 비고

- `httpx`/`dotenv` 미설치 환경에서도 표준 라이브러리 HTTP fallback으로 동작.
- 내부 시험용 개발 — 별도 라이선스 규정 없이 자유 배포·수정 가능.

---
*수집일: 2026-07-02 · 출처: 저장소 README, 소스 코드(korea_weather.py)*
