# opendart-mcp

> **[RealYoungk/opendart-mcp](https://github.com/RealYoungk/opendart-mcp)** · ⭐ (rate limit) · Python · 최근 푸시 (rate limit) · 카테고리: 🏦 Finance & Tax

금감원 DART 전자공시 Open API 83종을 자연어로 조회하는 MCP 서버입니다.

## 개요

금융감독원 [DART 전자공시시스템](https://opendart.fss.or.kr) Open API를 MCP 서버로 제공한다. OpenDART의 83개 API를 1:1로 도구화해, Claude/ChatGPT 등에서 한국 상장기업의 공시정보·재무제표·지분공시·주요사항보고서·정기보고서를 자연어로 조회할 수 있다. uvx·Docker·SSE(원격) 실행을 지원한다.

## 제공 도구

83개 도구를 카테고리별 제공 (README 도구 표 기준). 소분류는 전체 열거, 대규모 분류는 대표 도구만 표기.

| 카테고리 | 개수 | 대표 도구 |
|---------|------|----------|
| 공시정보 | 4 | `search_disclosure`, `get_company_info`, `get_document`, `get_corp_code` |
| 정기보고서 주요정보 | 28 | `get_dividend_info`, `get_treasury_stock_status`, `get_largest_shareholder`, `get_executive_status`, `get_auditor_opinion`, `get_total_compensation` 등 |
| 재무정보 | 7 | `get_single_company_accounts`, `get_multi_company_accounts`, `get_xbrl_document`, `get_full_financial_statement`, `get_single_financial_index` 등 |
| 지분공시 | 2 | `get_major_stockholding`, `get_executive_stockholding` |
| 주요사항보고서 | 36 | `get_paid_capital_increase`, `get_convertible_bond_decision`, `get_treasury_stock_acquisition_decision`, `get_lawsuit_filing`, `get_rehabilitation_filing` 등 |

> 개별 도구 83개 전체 이름은 저장소 README의 "제공 도구 (83개)" 섹션 참조.

## 설치

```bash
# uvx
claude mcp add opendart -- uvx opendart-mcp
# Docker
docker build -t opendart-mcp . && docker run -e OPENDART_API_KEY="<KEY>" -p 8000:8000 opendart-mcp
```

## 필요 키 · 환경변수

| 환경변수 | 발급처 | 필수 |
|---------|--------|------|
| `OPENDART_API_KEY` | [OpenDART](https://opendart.fss.or.kr) | ✅ |

## 설정 예시

```json
{
  "mcpServers": {
    "opendart": {
      "command": "uvx",
      "args": ["opendart-mcp"],
      "env": { "OPENDART_API_KEY": "<YOUR_API_KEY>" }
    }
  }
}
```

## 비고

- SSE 원격 모드: `uvx opendart-mcp --transport sse --host 0.0.0.0 --port 8000`.
- OpenDART 엔드포인트 1:1 커버리지가 목표라 도구 수가 많다(83종).

---
*수집일: 2026-07-03 · 출처: 저장소 README*
