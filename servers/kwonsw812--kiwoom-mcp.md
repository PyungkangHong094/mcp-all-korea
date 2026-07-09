# kiwoom-mcp

> **[kwonsw812/kiwoom-mcp](https://github.com/kwonsw812/kiwoom-mcp)** · ⭐ N/A (GitHub API rate-limit) · TypeScript · 카테고리: 🏦 Finance & Tax

키움증권 계좌를 자연어로 제어해 주가 조회·매매 주문을 수행하는 MCP 서버입니다.

## 개요

키움증권 REST API와 Claude Desktop을 MCP로 연결해 자연어로 주식 조회·매매를 수행하는 서버다. 잔고/포트폴리오, 시세 조회, 주문, 거래내역 분석의 4개 영역에 걸쳐 12개 도구를 제공한다. stdio 로컬 실행과 Docker HTTP 원격 배포를 모두 지원하며, 키움 API가 등록된 IP에서만 동작하므로 IP가 등록된 서버에 배포해 원격 연결할 수 있다. 모의투자(`KIWOOM_IS_MOCK=true`) 지원.

## 제공 도구

| 도구 | 기능 |
|------|------|
| `get_account_balance` | 보유 주식 목록, 평가금액, 수익률 |
| `get_portfolio_summary` | 종목별 비중/손익 분석 |
| `get_deposit_detail` | 예수금, 출금/주문 가능금액 |
| `get_stock_price` | 현재가, 등락률, 거래량, PER/PBR |
| `get_stock_chart` | 일봉 OHLCV 차트 (기간 지정) |
| `search_stock_code` | 종목명 → 종목코드 검색 |
| `place_buy_order` | 시장가/지정가 매수 |
| `place_sell_order` | 시장가/지정가 매도 |
| `get_unfilled_orders` | 미체결 주문 목록 |
| `cancel_order` | 주문 취소 |
| `get_trade_history` | 기간별 체결내역 |
| `analyze_profit_loss` | 종목별 실현손익, 승률 분석 |

## 설치

저장소 클론 후 빌드(stdio) 또는 Docker Compose(HTTP) 배포.

```bash
git clone https://github.com/kwonsw812/kiwoom-mcp.git
cd kiwoom-mcp
npm install
npm run build
```

## 필요 키 · 환경변수

| 환경변수 | 발급처 | 필수 |
|---------|--------|------|
| `KIWOOM_APP_KEY` | [키움 OpenAPI](https://openapi.kiwoom.com) | ✅ |
| `KIWOOM_SECRET_KEY` | 키움 OpenAPI | ✅ |
| `KIWOOM_ACCOUNT_NO` | 키움 계좌번호(10자리) | ✅ |
| `KIWOOM_IS_MOCK` | 모의투자 여부(`true`/`false`) | ✅ |
| `MCP_TRANSPORT` | 전송 방식(`stdio`/`http`) | ❌ |
| `MCP_PORT` | HTTP 포트(기본 3000) | ❌ |
| `MCP_AUTH_TOKEN` | HTTP 모드 Bearer 토큰 | HTTP 시 ✅ |

## 설정 예시

```json
{
  "mcpServers": {
    "kiwoom": {
      "command": "node",
      "args": ["/절대경로/kiwoom-mcp/dist/index.js"],
      "env": {
        "KIWOOM_APP_KEY": "...",
        "KIWOOM_SECRET_KEY": "...",
        "KIWOOM_ACCOUNT_NO": "계좌번호10자리",
        "KIWOOM_IS_MOCK": "true"
      }
    }
  }
}
```

## 비고

키움증권 공식 프로젝트 아님. 키움 REST API는 등록 IP에서만 동작. 모의투자 충분히 테스트 후 실전 전환 권고. 라이선스 MIT.

---
*수집일: 2026-07-03 · 출처: 저장소 README*
