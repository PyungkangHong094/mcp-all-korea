# korea-mcp-suite

> **[k08200/korea-mcp-suite](https://github.com/k08200/korea-mcp-suite)** · ⭐ 1 · Python · 최근 푸시 2026-05-17 · 카테고리: 📊 Public Data

기상청·서울시·국토교통부·행정안전부 공공데이터를 하나로 묶은 10개 도구 MCP 서버.

## 개요

한국 공공데이터를 Claude·Cursor·Windsurf 등 MCP 호환 AI에 연결하는 통합 서버다. 날씨(기상청 단기예보), 서울 지하철·버스 실시간 도착, 아파트 매매·전월세 실거래가(국토교통부), 도로명주소·좌표·우편번호(행정안전부) 등 4개 분류 10개 도구를 제공한다.

## 제공 도구

| 분류 | 도구 | 기능 |
|------|------|------|
| 날씨 | `get_current_weather` | 현재 날씨 요약(기온·하늘·강수·습도·풍속) |
| 날씨 | `get_weather_forecast` | 최대 72시간 단기 예보 |
| 교통 | `get_subway_arrival` | 서울 지하철 실시간 도착 |
| 교통 | `search_subway_station` | 역명 키워드 검색 |
| 교통 | `get_bus_arrival` | 서울 버스 정류소 실시간 도착 |
| 부동산 | `get_apartment_trade` | 아파트 매매 실거래가 |
| 부동산 | `get_apartment_rent` | 아파트 전월세 실거래 |
| 주소 | `search_address` | 도로명주소 검색 |
| 주소 | `get_address_coordinates` | 주소 → 위경도 변환 |
| 주소 | `get_zip_code` | 주소 → 우편번호 |

## 설치

```bash
git clone https://github.com/k08200/korea-mcp-suite
cd korea-mcp-suite
cp .env.example .env   # API 키 입력
uv sync
```

## 필요 키 · 환경변수

| API | 발급처 | 필수 |
|-----|--------|------|
| 기상청 단기예보 | [data.go.kr](https://www.data.go.kr) | ✅ |
| 서울 열린데이터(지하철·버스) | [data.seoul.go.kr](https://data.seoul.go.kr) | ✅ |
| 공공데이터포털(실거래가) | [data.go.kr](https://www.data.go.kr) | ✅ |
| 도로명주소 | [juso.go.kr](https://www.juso.go.kr/openIndexPage.do) | ✅ |

정확한 환경변수명은 README에 명시되지 않음(`.env.example` 참고). 모든 API 무료.

## 설정 예시

```json
{
  "mcpServers": {
    "korea-mcp-suite": {
      "command": "uv",
      "args": ["--directory", "/path/to/korea-mcp-suite", "run", "korea-mcp"]
    }
  }
}
```

## 비고

- 로드맵: 네이버 지도, 카카오 통합, 금융, 식약처 도구 예정.
- 라이선스: MIT.

---
*수집일: 2026-07-02 · 출처: 저장소 README*
