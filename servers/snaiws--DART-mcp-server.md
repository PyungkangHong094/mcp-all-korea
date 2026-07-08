# DART-mcp-server

> **[snaiws/DART-mcp-server](https://github.com/snaiws/DART-mcp-server)** · ⭐ 11 · Python · 최근 푸시 2025-07-07 · 카테고리: 🏦 Finance & Tax

금융감독원 전자공시시스템(DART) API를 활용하는 MCP 서버.

## 개요

한국 전자공시시스템(DART) OpenAPI를 통해 상장기업의 공시검색·기업개황·고유번호·증자(감자) 현황·배당·자기주식·최대주주·임원 현황 등 공시/재무 정보를 조회한다. Docker 이미지(`snaiws/dart`)로 실행되며 `USECASE` 환경변수(예: `light`)로 노출 도구 집합을 필터링한다. XBRL 재무제표 파싱과 대용량 공시 XML의 구조/목차/내용 쿼리 도구를 갖췄다. 소스(`mcp_server/configs/tool.py`)의 `ToolDefine`에 84개 도구가 정의돼 있다.

## 제공 도구

전체 84개 도구(USECASE로 노출 범위 필터링). 주요 도구군:

| 도구군 | 대표 도구 |
|------|------|
| 파서·기업코드 | `get_corpcode`, `get_corp_candidates`, `update_corplist`, `xmlparser_get_table_csv` |
| 공시정보 | `get_disclosurelist`(공시검색), `get_corpinfo`(기업개황), `get_disclosure`(원본파일) |
| 정기보고서 주요정보 | `get_capitalstatus`(증자감자), `get_dividend_info`(배당), `get_treasury_stock`(자기주식), `get_major_shareholders`(최대주주), `get_executives`(임원), `get_employees`(직원), `get_board_total_compensation`, `get_total_shares` |
| 채권·증권 잔액 | `get_debt_securities_issuance`, `get_commercial_paper_balance`, `get_corporate_bond_balance`, `get_hybrid_securities_balance` 등 |
| 감사·지배구조 | `get_auditor_opinion`, `get_audit_service_contract`, `get_outside_directors`, `get_board_compensation_by_type` 등 |
| 재무제표 | `get_single_company_accounts`, `get_multi_company_accounts`, `get_xbrl_financial_statements`, `get_complete_financial_statements`, `get_single_company_key_indicators` |
| 지분공시 | `get_major_holding_reports`, `get_executive_major_shareholders_reports` |
| 주요사항 보고 | `get_paid_capital_increase`, `get_capital_reduction`, `get_merger_decision`, `get_split_decision`, `get_convertible_bond_issuance`, `get_treasury_stock_acquisition`, `get_litigation_filing`, `get_business_suspension` 등 |
| 증권신고·등록 | `get_equity_securities_registration`, `get_debt_securities_registration`, `get_merger_registration` 등 |

전체 84개 목록은 JSON 레코드(`_workspace/profiles/snaiws--DART-mcp-server.json`)에 수록.

## 설치

Smithery 자동 설치:

```bash
npx -y @smithery/cli install snaiws/dart-mcp-server --client claude
```

또는 Docker 수동 설정(아래 설정 예시). Docker Desktop 필요.

## 필요 키 · 환경변수

| 환경변수 | 발급처 | 필수 |
|---------|--------|------|
| `DART_API_KEY` | [금융감독원 전자공시시스템](https://opendart.fss.or.kr/uss/umt/EgovMberInsertView.do) 인증키 | ✅ |
| `USECASE` | 노출 도구 집합 필터(예: `light`) | ❌ |

## 설정 예시

```json
{
  "mcpServers": {
    "DART": {
      "command": "docker",
      "args": [
        "run", "--rm", "-i",
        "-v", ".:/app/data/mcp/DART",
        "-e", "DART_API_KEY=your-api-key",
        "-e", "USECASE=light",
        "snaiws/dart:latest"
      ]
    }
  }
}
```

## 비고

- 도구 식별자는 `ToolDefine` 키 기준이며, 실제 노출 도구는 `USECASE`에 지정된 목록으로 제한된다(`USECASE` 미지정 시 전체).
- 마지막 푸시 2025-07-07. Smithery 등록 서버.

---
*수집일: 2026-07-02 · 출처: 저장소 README, 소스 코드(mcp_server/configs/tool.py, run_server.py, Dockerfile)*
