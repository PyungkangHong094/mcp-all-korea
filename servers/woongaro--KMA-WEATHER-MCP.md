# KMA-WEATHER-MCP

> **[woongaro/KMA-WEATHER-MCP](https://github.com/woongaro/KMA-WEATHER-MCP)** · ⭐ - · Python · 카테고리: 🌦 Weather

기상청(KMA) 단기예보 Open API로 현재 날씨와 예보 도구·리소스를 제공하는 MCP 서버.

## 개요

대한민국 기상청 단기예보 Open API를 연결하는 FastMCP 기반 MCP 서버다. 서울 및 임의 위경도의 현재 날씨를 리소스로 노출하고, 초단기(6시간)·단기 예보를 도구로 제공한다.

## 제공 도구

| 도구 | 기능 |
|------|------|
| `get_ultra_short_term_forecast` | 향후 6시간 초단기 예보(강수확률·하늘상태 등) |
| `get_village_forecast` | 오늘~모레 단기 예보 |

리소스: `weather://seoul/now`(서울시청 현재 날씨), `weather://{latitude}/{longitude}/now`(임의 좌표 현재 날씨).

## 설치

```bash
# uv로 실행 (README의 Claude Desktop 설정 참조)
uv run -q --with "mcp[cli]" --with httpx --with fastmcp --with python-dotenv src/server.py
# 개발: npx @modelcontextprotocol/inspector uv run src/server.py
```

## 필요 키 · 환경변수

| 환경변수 | 발급처 | 필수 |
|---------|--------|------|
| `KMA_API_KEY_DECODED` | [공공데이터포털 기상청 단기예보](https://www.data.go.kr/data/15084084/openapi.do) (일반 인증키 Decoding) | ✅ |

## 설정 예시

```json
{
  "mcpServers": {
    "kma-weather": {
      "command": "uv",
      "args": ["run", "-q", "--with", "mcp[cli]", "--with", "httpx", "--with", "fastmcp", "--with", "python-dotenv", "/ABSOLUTE/PATH/TO/kma-weather-mcp/src/server.py"],
      "env": { "KMA_API_KEY_DECODED": "YOUR_KEY_HERE" }
    }
  }
}
```

## 비고

- 인증키는 반드시 Decoding(디코딩) 버전 사용.

---
*수집일: 2026-07-02 · 출처: 저장소 README*
