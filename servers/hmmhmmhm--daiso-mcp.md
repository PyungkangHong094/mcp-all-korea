# daiso-mcp

> **[hmmhmmhm/daiso-mcp](https://github.com/hmmhmmhm/daiso-mcp)** · ⭐ 309 · TypeScript · 최근 푸시 2026-07-07 · 카테고리: 🛒 Commerce & Retail

한국 로컬 리테일·생활정보·영화관 조회를 MCP·CLI·Codex Skill로 연결하는 다중 서비스 서버.

## 개요

Cloudflare Workers에서 실행되는 플러그인 기반 원격 MCP 서버로, 14개 서비스(다이소·올리브영·롯데마트·GS25·세븐일레븐·CU·이마트24·CGV·메가박스·롯데시네마·네이버 지역검색·오피넷·가격비교·개발자피드백)를 하나로 묶는다. 사용자는 별도 API 키 없이 호스팅된 엔드포인트(`https://mcp.aka.page`)로 바로 사용할 수 있고, `npx daiso` CLI 및 Codex Skill로도 제공된다. 각 서비스는 `{service}_*` 네이밍의 도구를 등록한다.

## 제공 도구

소스(`src/services/*`)에서 확인된 도구 및 서비스별 도구군:

| 도구 / 도구군 | 기능 |
|------|------|
| `daiso_search_products` · `daiso_find_stores` · `daiso_check_inventory` · `daiso_find_inventory_by_name` · `daiso_get_price_info` · `daiso_get_display_location` | 다이소 상품·매장·재고·가격·진열위치 조회 |
| `opinet_get_average_prices` · `opinet_get_lowest_price_stations` · `opinet_search_stations_around` · `opinet_get_station_detail` | 오피넷 전국 평균유가·최저가·반경 주유소·주유소 상세 |
| `places_search_nearby` | 네이버 지역검색 기반 주변 음식점/카페/장소 |
| `compare_products` | 다이소·GS25·세븐일레븐·이마트24 통합 상품 가격 비교 |
| `submit_developer_request` | MCP 오류·개선·신규기능 요청을 개발자에게 제출(Supabase 저장) |
| 편의점 서비스 (`gs25_*`, `seveneleven_*`, `cu_*`, `emart24_*`) | 상품·매장·재고·인기검색어·카탈로그 조회 |
| 리테일 서비스 (`oliveyoung_*`, `lottemart_*`) | 상품·매장·재고 조회 |
| 영화관 서비스 (`cgv_*`, `megabox_*`, `lottecinema_*`) | 극장·영화·시간표·잔여좌석 조회 |

각 서비스별 세부 도구 전체 목록은 `src/services/{service}/tools/`에 정의된다.

## 설치

원격 MCP(권장, 키 불필요):

```
https://mcp.aka.page
```

CLI:

```bash
npx daiso
```

## 필요 키 · 환경변수

호스팅된 `mcp.aka.page` 사용 시 **API 키 불필요**.

직접 배포(self-host) 시에만 필요:

| 환경변수 | 발급처 | 필수 |
|---------|--------|------|
| `NAVER_CLIENT_ID` · `NAVER_CLIENT_SECRET` | [네이버 개발자센터](https://developers.naver.com) | 지역검색 사용 시 |
| `OPINET_API_KEY` | [오피넷](https://www.opinet.co.kr) 유가정보 API 인증키 | 유가 조회 시 |
| `GOOGLE_MAPS_API_KEY` | Google Cloud | 오피넷 location 검색 시 |
| `SUPABASE_URL` · `SUPABASE_SERVICE_ROLE_KEY` | Supabase | 개발자 요청 저장 시 |

## 설정 예시

```json
{
  "mcpServers": {
    "daiso": {
      "type": "http",
      "url": "https://mcp.aka.page"
    }
  }
}
```

## 비고

- 오피넷 무료 API는 1일 1,500 call 한도 기준으로 운영되며 Cloudflare Edge Cache로 원본 호출을 줄인다.
- 다이소 진열위치 도구는 외부 기여(@thecats1105), CGV 서비스는 @betterthanhajin 기여로 추가됐다.
- 실시간 서비스 상태: [Daiso MCP Status](https://aka-page.betteruptime.com/).

---
*수집일: 2026-07-02 · 출처: 저장소 README, 소스 코드(src/index.ts, src/services/*)*
