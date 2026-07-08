# koreainvestment-mcp

> **[koreainvestment/koreainvestment-mcp](https://github.com/koreainvestment/koreainvestment-mcp)** · ⭐ 17 · Python · 최근 푸시 2025-08-27 · 카테고리: 🏦 Finance & Tax

한국투자증권 API를 자연어로 검색해 필요한 금융 API를 찾는 MCP 서버.

## 개요

한국투자증권의 334개 API(국내주식 156·해외주식 50·국내선물옵션 43·해외선물옵션 35·ELW 24·국내채권 18·ETF/ETN 6·인증 2)를 자연어 질문으로 검색하는 서비스다. 로컬 `data.csv`에 저장된 API 명세를 카테고리·부분 매칭으로 조회하고 JSON 구조화 결과를 반환한다. **실제 API 호출은 구현되지 않았으며, 원하는 기능을 빠르게 찾는 검색 용도**다.

## 제공 도구

소스(`server.py`)의 `@mcp.tool` 등록에서 확인:

| 도구 | 기능 |
|------|------|
| `search_auth_api` | 인증 관련 API 검색 |
| `search_domestic_stock_api` | 국내주식 API 검색 |
| `search_domestic_bond_api` | 국내채권 API 검색 |
| `search_domestic_futureoption_api` | 국내선물옵션 API 검색 |
| `search_overseas_stock_api` | 해외주식 API 검색 |
| `search_overseas_futureoption_api` | 해외선물옵션 API 검색 |
| `search_elw_api` | ELW API 검색 |
| `search_etfetn_api` | ETF/ETN API 검색 |
| `fetch_api_code` | GitHub README URL에서 API 코드/설정 정보 추출 |

## 설치

```bash
uv sync
uv run server.py
```

## 필요 키 · 환경변수

API 키 불필요 (로컬 `data.csv` 검색만 수행).

## 설정 예시

```json
{
  "mcpServers": {
    "kis-api-search": {
      "command": "{uv 경로}/uv",
      "args": ["run", "--project", "{프로젝트 경로}", "python", "{프로젝트 경로}/server.py"],
      "env": {
        "PYTHONPATH": "{프로젝트 경로}"
      }
    }
  }
}
```

## 비고

- API 검색 서비스이며 실제 시세 조회·주문 호출은 별도 구현이 필요하다(한계사항 명시).
- DXT(Desktop Extension) 패키징(`npx @anthropic-ai/dxt pack`)으로 Claude Desktop 원클릭 설치 지원.
- 저장소에 라이선스 파일 없음. 마지막 푸시 2025-08-27.

---
*수집일: 2026-07-02 · 출처: 저장소 README, 소스 코드(server.py)*
