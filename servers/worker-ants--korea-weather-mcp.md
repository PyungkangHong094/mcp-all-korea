# korea-weather-mcp

> **[worker-ants/korea-weather-mcp](https://github.com/worker-ants/korea-weather-mcp)** · ⭐ - · TypeScript · 카테고리: 🌦 Weather

기상청 API 허브의 단기·중기예보, 기상특보, 영향예보, 구역정보를 래핑한 MCP 서버.

## 개요

기상청 [API 허브](https://apihub.kma.go.kr/)의 5개 카테고리(단기예보·중기예보·기상특보·영향예보·구역정보)를 래핑한 Node.js(TypeScript, ESM) MCP 서버다. 위경도 좌표 또는 구역코드(`regId`)/발표관서(`stnId`)를 입력하면 데이터를 한국어 텍스트로 정리해 반환한다. 발표 시각을 호출 시점에 자동 보정하고, 위경도→격자 좌표 변환을 내장한다. stdio·Streamable HTTP 두 transport 지원.

## 제공 도구

README 명시 12개:

| 분류 | 도구 |
|------|------|
| 좌표(위경도) | `get_nowcast_observation`, `get_nowcast_forecast`, `get_short_term_forecast` |
| 구역/관서 | `get_short_term_land_forecast`, `get_short_term_sea_forecast`, `get_weather_situation`, `get_mid_term_forecast`, `get_mid_term_temperature` |
| 전국/영향예보 | `get_active_warnings`, `get_impact_forecast` |
| 구역코드 검색 | `lookup_forecast_zone`, `lookup_warning_zone` |

## 설치

```bash
npm install
npm run build      # tsc → dist/
node dist/index.js --stdio
# 개발: npm run dev (tsx src/index.ts)
```

## 필요 키 · 환경변수

| 환경변수 | 발급처 | 필수 |
|---------|--------|------|
| `KOREA_WEATHER_API_KEY` | [기상청 API 허브](https://apihub.kma.go.kr) | ✅ |
| `MCP_API_KEY` | HTTP 모드 `x-api-key` 인증값 | ⛔(HTTP 모드에서만) |
| `HOST` / `PORT` / `TRANSPORT` | 서버 바인딩·전송방식(기본 127.0.0.1/8081/http) | ❌ |

## 설정 예시

```json
{
  "mcpServers": {
    "korea_weather": {
      "command": "node",
      "args": ["/absolute/path/to/dist/index.js", "--stdio"],
      "env": { "KOREA_WEATHER_API_KEY": "발급받은-기상청-API-허브-인증키" }
    }
  }
}
```

## 비고

- 단기 육상 `regId`와 중기 육상 `regId` 체계가 다름 → `lookup_forecast_zone` 먼저 호출 권장.
- HTTP `/mcp` 엔드포인트는 `x-api-key` 필수(`crypto.timingSafeEqual` 비교).

---
*수집일: 2026-07-02 · 출처: 저장소 README*
