# k-targo-subway-mcp-server

> **[slicequeue/k-targo-subway-mcp-server](https://github.com/slicequeue/k-targo-subway-mcp-server)** · ⭐ N/A · TypeScript · 최근 푸시 N/A · 카테고리: 📊 Public Data

국토교통부 TAGO 지하철정보 API 기반으로 역 검색·시간표 조회를 제공하는 MCP 서버입니다.

## 개요

국토교통부_(TAGO)_지하철정보 API(`api.tago.go.kr`)를 감싼 MCP 서버. 역명으로 지하철역을 검색하고 특정 역의 열차 시간표를 조회한다. npm 패키지(`k-targo-subway-mcp-server`)로 배포되며 `npx`로 즉시 실행된다.

## 제공 도구

| 도구 | 기능 |
|------|------|
| `search_subway_station` | 역명(`stationName`)으로 지하철역 검색 |
| `get_station_timetable` | 역코드(`stationCode`)와 방향(`direction`, 상행/하행)으로 시간표 조회 |

## 설치

```bash
# npx 즉시 실행 (권장)
npx k-targo-subway-mcp-server

# Smithery 자동 설치
npx -y @smithery/cli install @slicequeue/k-targo-subway-mcp-server --client claude

# npm 설치
npm install -g k-targo-subway-mcp-server
```

## 필요 키 · 환경변수

| 환경변수 | 발급처 | 필수 |
|---------|--------|------|
| `GOV_API_KEY` | [공공데이터포털 국토교통부 TAGO 지하철정보](https://www.data.go.kr/data/15098554/openapi.do) | ✅ |

## 설정 예시

```json
{
  "mcpServers": {
    "k-targo-subway": {
      "command": "npx",
      "args": ["k-targo-subway-mcp-server"],
      "env": { "GOV_API_KEY": "your_targo_api_key_here" }
    }
  }
}
```

## 비고

Smithery 등재. 데이터 형식 JSON, 인증은 공공데이터 API 키(`GOV_API_KEY`) 기반.

---
*수집일: 2026-07-02 · 출처: 저장소 README*
