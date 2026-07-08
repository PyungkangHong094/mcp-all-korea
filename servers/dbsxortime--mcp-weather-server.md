# mcp-weather-server

> **[dbsxortime/mcp-weather-server](https://github.com/dbsxortime/mcp-weather-server)** · ⭐ 0 · TypeScript · 최근 푸시 2025-04-22 · 카테고리: 🌦 Weather

한국 기상청 API를 활용해 위치 기반 현재 날씨와 예보를 제공하는 MCP 서버입니다.

## 개요

한국 기상청 API를 사용하는 TypeScript 기반 MCP 서버로, npm 패키지(`@dbsxortime/mcp-weather-server`)로 배포된다. 위도·경도를 입력받아 현재 날씨(온도·습도·풍속), 초단기예보, 단기예보를 한 번에 조회한다. AI가 지명을 위경도로 변환해 전달하는 사용 흐름을 가정한다.

## 제공 도구

| 도구 | 기능 |
|------|------|
| `get-weather` | 위도·경도를 받아 현재 날씨 + 초단기예보 + 단기예보를 조회 |

## 설치

```bash
npx -y @dbsxortime/mcp-weather-server
```

## 필요 키 · 환경변수

| 환경변수 | 발급처 | 필수 |
|---------|--------|------|
| `WEATHER_API_KEY` | [공공데이터포털](https://www.data.go.kr) 기상청 API 서비스 키 | ✅ |

## 설정 예시

```json
{
  "mcpServers": {
    "weather": {
      "command": "npx",
      "args": ["-y", "@dbsxortime/mcp-weather-server"],
      "env": {
        "WEATHER_API_KEY": "<YOUR_WEATHER_API_KEY>"
      }
    }
  }
}
```

## 비고

- 라이선스: MIT (README 명시).
- 입력 파라미터는 `latitude`, `longitude`.

---
*수집일: 2026-07-02 · 출처: 저장소 README, 소스 코드(src/index.ts)*
