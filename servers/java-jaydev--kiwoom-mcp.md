# kiwoom-mcp

> **[java-jaydev/kiwoom-mcp](https://github.com/java-jaydev/kiwoom-mcp)** · ⭐ 2 · TypeScript · 최근 푸시 2026-03-06 · 카테고리: 🏦 Finance & Tax

키움증권 REST API를 MCP 도구로 래핑한 서버 — Claude Code 등 LLM 클라이언트에서 한국 주식 정보를 직접 조회.

## 개요

키움증권 OpenAPI(REST)를 Model Context Protocol 도구로 감싸, LLM에서 국내 주식의 현재가·호가·일봉·투자자 동향과 계좌/예수금/체결 내역을 조회한다. **조회 전용**이며 주문(매수/매도/취소) 기능은 포함되지 않는다. TypeScript + Node.js(ES Module), `@modelcontextprotocol/sdk` + Zod, Stdio Transport 기반.

## 제공 도구

| 도구 | 기능 |
|------|------|
| `get_stock_price` | 현재가 조회 (종목명, 등락률, PER, PBR 등) — `stockCode` |
| `get_orderbook` | 호가 조회 (매도/매수 1~10호가, 잔량) — `stockCode` |
| `get_daily_chart` | 일봉 차트 (시/고/저/종가, 거래량) — `stockCode`, `baseDate?` |
| `get_investor_trend` | 투자자별 매매동향 (외국인/기관/개인 순매수) — `stockCode` |
| `get_account_balance` | 계좌평가현황 (예수금, 보유종목, 손익률) |
| `get_deposit` | 예수금 상세 (출금가능, 주문가능금액) |
| `get_unfilled_orders` | 미체결 주문 조회 |
| `get_filled_orders` | 체결 내역 조회 — `stockCode?` (미입력 시 전체) |

## 설치

```bash
git clone https://github.com/java-jaydev/kiwoom-mcp.git
cd kiwoom-mcp
pnpm install   # 또는 npm install
pnpm run build # 또는 npm run build
```

## 필요 키 · 환경변수

| 환경변수 | 발급처 | 필수 |
|---------|--------|------|
| `KIWOOM_APP_KEY` | [키움 OpenAPI 포털](https://openapi.kiwoom.com/) | ✅ |
| `KIWOOM_SECRET_KEY` | [키움 OpenAPI 포털](https://openapi.kiwoom.com/) | ✅ |
| `KIWOOM_API_BASE_URL` | 기본값 `https://api.kiwoom.com` | ❌ |

## 설정 예시

```json
{
  "mcpServers": {
    "kiwoom": {
      "type": "stdio",
      "command": "node",
      "args": ["/path/to/kiwoom-mcp/dist/index.js"],
      "env": {
        "KIWOOM_APP_KEY": "<your-app-key>",
        "KIWOOM_SECRET_KEY": "<your-secret-key>"
      }
    }
  }
}
```

## 비고

- **IP 제한**: 키움 API 토큰은 발급된 IP에서만 유효 — 서버·클라이언트가 같은 IP여야 함.
- 토큰 유효기간 24시간, 만료 1시간 전 자동 갱신.
- 장 마감 후에는 시/고/저가가 0으로 반환될 수 있음.

---
*수집일: 2026-07-02 · 출처: 저장소 README*
