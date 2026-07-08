# korea-realestate-mcp

> **[ohkyuetaek/korea-realestate-mcp](https://github.com/ohkyuetaek/korea-realestate-mcp)** · ⭐ 0 · Python · 최근 푸시 2026-03-09 · 카테고리: 🏠 Real Estate

공공데이터포털 국토부 API로 아파트 매매·전월세 시세 조회, 가격 추이·지역 비교 등 8가지 도구를 제공하는 MCP 서버.

## 개요

국토교통부 아파트 매매·전월세 실거래가 공공 API를 활용해 자연어로 시세 조회·분석을 수행하는 MCP 서버. 지역명→법정동코드 퍼지 매칭, 월별 시세 추이 분석, 2~5개 지역 비교, 전세가율(갭투자) 분석, 단지 종합 요약을 제공한다. Python 3.10+, FastMCP, httpx, SQLite 캐시(aiosqlite), pandas. `uvx`로 바로 실행 가능.

## 제공 도구

| 도구 | 기능 |
|------|------|
| `realestate_search_apt_trade` | 아파트 매매 실거래가 조회 |
| `realestate_search_apt_rent` | 아파트 전월세 실거래가 조회 |
| `realestate_get_region_code` | 지역명 → 법정동 코드 (퍼지 매칭) |
| `realestate_analyze_price_trend` | 시세 추이 분석 (월별 통계, 변동률) |
| `realestate_compare_regions` | 2~5개 지역 시세 비교 |
| `realestate_analyze_rent_ratio` | 매매가 대비 전세가율 분석 |
| `realestate_get_apt_summary` | 특정 아파트 단지 종합 요약 |

> README 표에는 7개 도구가 명시됨 (설명의 "8가지"와 차이 — 표 기준 기록).

## 설치

```bash
uvx korea-realestate-mcp
# 또는
pip install korea-realestate-mcp
```

## 필요 키 · 환경변수

| 환경변수 | 발급처 | 필수 |
|---------|--------|------|
| `PUBLIC_DATA_API_KEY` | [공공데이터포털](https://www.data.go.kr) (아파트 매매/전월세 자료, 서비스키 Decoding) | ✅ |

## 설정 예시

```json
{
  "mcpServers": {
    "korea-realestate": {
      "command": "uvx",
      "args": ["korea-realestate-mcp"],
      "env": { "PUBLIC_DATA_API_KEY": "<발급받은 서비스 키>" }
    }
  }
}
```

## 비고

- 라이선스: MIT. PyPI 배포(`uvx korea-realestate-mcp`).
- 결과를 Markdown 테이블로 반환. 데이터 출처: 국토부 실거래가 공개시스템, 공공데이터포털.

---
*수집일: 2026-07-02 · 출처: 저장소 README*
