# asia-filings-mcp-server

> **[openpharma-org/asia-filings-mcp-server](https://github.com/openpharma-org/asia-filings-mcp-server)** · ⭐ (rate limit) · TypeScript/Node · 최근 푸시 (rate limit) · 카테고리: 🏦 Finance & Tax

일본 EDINET과 한국 DART로 아시아 7,700개 기업 재무공시를 검색·분석하는 MCP 서버입니다(한·일 다국가).

## 개요

일본 EDINET(5,000+ 기업)과 한국 DART(2,700+ 기업)를 통해 아시아 7,700개 이상 기업의 재무공시에 접근하는 비공식 MCP 서버. 공시 이력 조회, iXBRL/XBRL-JSON 파싱(J-GAAP/K-GAAP 택소노미), 세그먼트·지역·제품별 차원 분석, 다기간 시계열 분석(Phase 2), BI용 fact table 생성을 제공한다. Cursor·Claude Desktop 등 MCP 클라이언트와 호환.

## 제공 도구

단일 `asia-filings` 도구가 19개 메서드를 제공 (README "Complete API Reference" 기준).

| # | 메서드 | 대상 |
|---|--------|------|
| 1 | `search_japan_companies` | 일본 EDINET |
| 2 | `get_japan_company_by_code` | 일본 EDINET |
| 3 | `get_japan_company_filings` | 일본 EDINET |
| 4 | `get_japan_filing_document` | 일본 EDINET |
| 5 | `get_japan_documents_by_date` | 일본 EDINET |
| 6 | `get_japan_filing_facts` | 일본 EDINET (XBRL) |
| 7 | `get_japan_dimensional_facts` | 일본 EDINET (차원) |
| 8 | `search_korea_companies` | 한국 DART |
| 9 | `get_korea_company_by_code` | 한국 DART |
| 10 | `get_korea_company_filings` | 한국 DART |
| 11 | `get_korea_financial_statements` | 한국 DART (XBRL) |
| 12 | `get_korea_dimensional_facts` | 한국 DART (차원) |
| 13 | `get_korea_major_shareholders` | 한국 DART |
| 14 | `get_korea_executive_info` | 한국 DART |
| 15 | `get_korea_dividend_info` | 한국 DART |
| 16 | `filter_filings` | 공통 |
| 17 | `build_fact_table` | 공통 (Phase 2) |
| 18 | `search_facts_by_value` | 공통 (Phase 2) |
| 19 | `time_series_analysis` | 공통 (Phase 2) |

## 설치

소스 빌드 후 `build/index.js` 실행 (README 기준).

## 필요 키 · 환경변수

| 환경변수 | 발급처 | 필수 |
|---------|--------|------|
| `EDINET_API_KEY` | [EDINET](https://disclosure.edinet-fsa.go.jp/) (무료) | ✅ |
| `DART_API_KEY` | [Open DART](https://opendart.fss.or.kr/) (무료, 1,000 req/min) | ✅ |

## 설정 예시

```json
{
  "mcpServers": {
    "asia-filings": {
      "command": "node",
      "args": ["/path/to/asia-filings-mcp-server/build/index.js"],
      "env": {
        "EDINET_API_KEY": "your-edinet-api-key-here",
        "DART_API_KEY": "your-dart-api-key-here"
      }
    }
  }
}
```

## 비고

- 비공식(Unofficial) 서버. 한·일 두 개 API 키가 모두 필요.
- 도구 인터페이스는 단일 도구 + `method` 파라미터 라우팅 방식.

---
*수집일: 2026-07-03 · 출처: 저장소 README*
