# tossinvest-mcp

> **[scjang01/tossinvest-mcp](https://github.com/scjang01/tossinvest-mcp)** · ⭐ N/A (GitHub API rate-limit) · TypeScript · 카테고리: 🏦 Finance & Tax

토스증권 Open API로 현재가·호가·캔들·잔고·주문을 조회하는 한국 주식 MCP 서버입니다.

## 개요

토스증권 Open API(현재가·호가·체결·캔들·잔고·주문)를 MCP 도구로 노출하는 로컬 stdio 서버다. `npx tossinvest-mcp`로 실행하며 OAuth 토큰을 내부에서 자동 발급·갱신한다. 시세/잔고 조회는 기본 제공되지만, 주문 생성·정정·취소 도구(`toss_create_order`, `toss_modify_order`, `toss_cancel_order`)는 기본적으로 비활성화되며 가드레일(주문 한도·허용목록 등)을 환경변수로 켤 수 있다. 토스증권 Open API에는 모의투자 환경이 없어 거래 기능은 실계좌에 실주문을 낸다.

## 제공 도구

소스(`src/tools/*.ts`)에서 등록되는 도구 총 20개.

| 분류 | 도구 |
|------|------|
| 시세 (market) | `toss_get_prices`, `toss_get_orderbook`, `toss_get_trades`, `toss_get_candles`, `toss_get_price_limits`, `toss_get_stocks`, `toss_get_stock_warnings`, `toss_get_exchange_rate`, `toss_get_kr_market_calendar`, `toss_get_us_market_calendar` |
| 계좌 (account) | `toss_get_accounts`, `toss_get_holdings`, `toss_get_buying_power`, `toss_get_sellable_quantity`, `toss_get_commissions` |
| 주문 (orders) | `toss_get_orders`, `toss_get_order`, `toss_create_order`*, `toss_modify_order`*, `toss_cancel_order`* |

\* 주문 생성·정정·취소는 기본 비활성화(opt-in). 활성화해도 `confirmOrderAction` 확인값 없이는 호출되지 않는다.

## 설치

Node.js 20 이상 필요. 별도 설치 없이 npx로 실행한다. 토스증권 Open API는 허용 IP에서만 호출되므로 공인 IP 등록이 필요하다.

```bash
npx tossinvest-mcp
```

## 필요 키 · 환경변수

| 환경변수 | 발급처 | 필수 |
|---------|--------|------|
| `TOSSINVEST_API_KEY` | 토스증권 WTS → Open API 설정 | ✅ |
| `TOSSINVEST_SECRET_KEY` | 토스증권 WTS → Open API 설정 | ✅ |
| `TOSSINVEST_ACCOUNT` | 기본 계좌 지정 (미지정 시 `accountSeq` 1번) | ❌ |

## 설정 예시

```json
{
  "mcpServers": {
    "tossinvest": {
      "command": "npx",
      "args": ["tossinvest-mcp"],
      "env": {
        "TOSSINVEST_API_KEY": "발급받은-API-Key",
        "TOSSINVEST_SECRET_KEY": "발급받은-Secret-Key"
      }
    }
  }
}
```

## 비고

모의투자 환경 없음 — 거래 기능은 실계좌 실주문. 주문 도구는 기본 미등록. 도구명은 소스 코드에서 확인.

---
*수집일: 2026-07-03 · 출처: 저장소 README, 소스 코드(src/tools)*
