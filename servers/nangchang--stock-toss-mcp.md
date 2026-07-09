# stock-toss-mcp

> **[nangchang/stock-toss-mcp](https://github.com/nangchang/stock-toss-mcp)** · ⭐ (조회 실패) · Node.js/TypeScript · 최근 푸시 (조회 실패) · 카테고리: 🏦 Finance & Tax

토스증권 Open API로 주식 거래·시장 데이터·계좌 관리를 연동하는 MCP 서버입니다.

## 개요

토스증권 Open API를 MCP 도구로 감싼 Node.js/TypeScript 서버다. 국내외 주식의 시세·호가·체결·캔들 등 시장 데이터, 종목 기본정보·유의사항, 환율·장운영시간, 계좌·보유주식·매수가능금액 등 자산 정보를 조회하고, 실계좌 주문 생성·정정·취소까지 지원한다. 토스증권 WTS에서 발급받은 `client_id`/`client_secret`로 인증한다.

## 제공 도구

README의 "제공 도구" 표에 명시된 도구:

| 도구 | 기능 |
|------|------|
| `toss_get_orderbook` | 호가 조회 |
| `toss_get_prices` | 현재가 조회(최대 200개 종목) |
| `toss_get_trades` | 최근 체결 내역 조회 |
| `toss_get_price_limits` | 상/하한가 조회 |
| `toss_get_candles` | 캔들 차트 조회(1분봉/일봉) |
| `toss_get_stocks` | 종목 기본 정보 조회(최대 200개) |
| `toss_get_stock_warnings` | 종목 매수 유의사항 조회 |
| `toss_get_exchange_rate` | KRW↔USD 환율 조회 |
| `toss_get_kr_market_calendar` | 국내 장 운영 시간 조회 |
| `toss_get_us_market_calendar` | 미국 장 운영 시간 조회 |
| `toss_get_accounts` | 계좌 목록 조회 |
| `toss_get_holdings` | 보유 주식 조회 |
| `toss_get_buying_power` | 매수 가능 금액 조회 |
| `toss_get_sellable_quantity` | 판매 가능 수량 조회 |
| `toss_get_commissions` | 매매 수수료 조회 |
| `toss_get_orders` | 주문 목록 조회 |
| `toss_get_order` | 주문 상세 조회 |
| `toss_create_order` | 주문 생성(⚠️ 실거래) |
| `toss_modify_order` | 주문 정정(⚠️ 실거래) |
| `toss_cancel_order` | 주문 취소(⚠️ 실거래) |

## 설치

```bash
npm install
npm run build
```

Node.js 18+ 필요. 빌드 후 `dist/index.js`를 실행 파일로 사용한다.

## 필요 키 · 환경변수

| 환경변수 | 발급처 | 필수 |
|---------|--------|------|
| `TOSS_CLIENT_ID` | 토스증권 WTS Open API | ✅ |
| `TOSS_CLIENT_SECRET` | 토스증권 WTS Open API | ✅ |

## 설정 예시

```json
{
  "mcpServers": {
    "toss-invest": {
      "command": "node",
      "args": ["/path/to/stock-toss-mcp/dist/index.js"],
      "env": {
        "TOSS_CLIENT_ID": "여기에_client_id",
        "TOSS_CLIENT_SECRET": "여기에_client_secret"
      }
    }
  }
}
```

## 비고

- `toss_create_order`, `toss_modify_order`, `toss_cancel_order`는 실제 계좌에서 거래가 발생하므로 주의가 필요하다.

---
*수집일: 2026-07-03 · 출처: 저장소 README*
