# korea-trip-concierge

> **[bb4rjfl/korea-trip-concierge](https://github.com/bb4rjfl/korea-trip-concierge)** · ⭐ N/A · TypeScript · 최근 푸시 N/A · 카테고리: 🌏 Tourism & Travel

방한 외국인의 장소탐색·외국인 친화 매장·교통·결제를 영어로 구조화해 돕는 MCP 서버입니다.

## 개요

카카오 Agentic Player 10 공모전 출품작. 방한 외국인이 겪는 마찰(장소 검색, 외국카드 결제 가능 매장, 대중교통, 결제 관습)을 영어로 해결한다. TypeScript + Node 22, MCP SDK 1.29, Streamable HTTP(stateless)로 동작한다. 도구는 한국관광공사 TourAPI(영문)·ODsay·기상청·에어코리아·VisitJeju 등을 데이터 소스로 쓰며, 큐레이션(자체 지식) 도구 3종은 API 키 없이도 동작한다.

## 제공 도구

11개 도구 (출처: `docs/00_service_overview.md`):

| 도구 | 기능 | 데이터 소스 |
|------|------|------------|
| `searchPlaceForeigner` | 장소 검색 | TourAPI 영문(EngService2) |
| `findForeignerFriendlyStore` | 외국인 친화(외국카드) 매장 | TourAPI |
| `getTransitRoute` | 대중교통 경로 | ODsay + TourAPI 지오코딩 |
| `trackBusArrival` | 실시간 버스 도착 (조회형) | 실시간 API |
| `trackSubwayArrival` | 서울 지하철 실시간 (조회형) | 실시간 API |
| `explainPayment` | 결제 안내 (큐레이션, 키 불필요) | 자체 지식 |
| `getAreaGuide` | 동네 가이드 (큐레이션, 키 불필요) | 자체 지식 |
| `translateMenuContext` | 메뉴 맥락 해석 (큐레이션, 키 불필요) | 자체 지식 |
| `getNowInfo` | 지금 갈 만한지 (영업시간 등) | TourAPI |
| `getJejuInfo` | 제주 특화 정보 | VisitJeju |
| `getWeatherAndAir` | 날씨 + 미세먼지 | 기상청 + 에어코리아 |

## 설치

```bash
npm install
npm run build   # 네이밍 린트 + tsc
npm start       # node dist/server.js
# 개발: npm run dev (POST /mcp)
```

## 필요 키 · 환경변수

`.env.example`를 `.env`로 복사해 설정. 발급법은 `docs/08_api_key_issuance.md` 참조. 외부 API 키(TourAPI, ODsay, 기상청, 에어코리아 등)가 필요하나 README에 개별 환경변수명은 명시되지 않음. **키 없이도 큐레이션 도구 3종(`explainPayment`, `getAreaGuide`, `translateMenuContext`)은 동작.**

## 설정 예시

```json
{
  "mcpServers": {
    "korea-trip-concierge": {
      "url": "http://localhost:PORT/mcp"
    }
  }
}
```
(README 기반 구성 — Remote/Streamable HTTP stateless 서버로 POST /mcp 사용)

## 비고

카카오 PlayMCP 심사 제약 준수: 서버·툴명에 `kakao` 금지, Streamable HTTP·Remote·Stateless, 응답 Markdown ≤24k, 푸시 불가. 개별 API 환경변수명은 `.env.example`/`docs`에서 확인 필요.

---
*수집일: 2026-07-02 · 출처: 저장소 README, docs/00_service_overview.md*
