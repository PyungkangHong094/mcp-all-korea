# bithumb-mcp

> **[zereight/bithumb-mcp](https://github.com/zereight/bithumb-mcp)** · ⭐ N/A (GitHub API 제한) · TypeScript/JavaScript · 최근 푸시 N/A · 카테고리: 🏦 Finance & Tax

빗썸(Bithumb) 거래소 API로 시세·호가·캔들·잔고 조회 및 주문·출금을 처리하는 18개 도구 MCP 서버입니다.

## 개요

빗썸(Bithumb) 거래소 공개/인증 API에 연동하여 암호화폐 시세 정보 조회와 거래를 수행하는 MCP 서버다. 공개 API(시세·호가·체결·캔들)와 인증 API(잔고·주문·출금)를 모두 커버하며, npm 패키지 `@zereight/bithumb-mcp`로 배포된다. 모든 도구는 JSON 문자열을 반환한다.

## 제공 도구

| 도구 | 기능 |
|------|------|
| `get_ticker` | 코인 티커(시세) 정보 조회 |
| `get_orderbook` | 호가 정보 조회 |
| `get_transaction_history` | 최근 체결 내역 조회 |
| `get_assets_status` | 자산 입출금 상태 조회 |
| `get_candlestick` | 캔들스틱 데이터 조회 |
| `post_account` | 회원 계정 정보·수수료 조회 |
| `get_balance` | 계정 잔고 조회 |
| `post_wallet_address` | 코인 입금 지갑 주소 조회 |
| `post_ticker_user` | 회원 최근 거래 정보 조회 |
| `post_orders` | 회원 주문 내역 조회 |
| `post_order_detail` | 특정 주문 상세 조회 |
| `post_user_transactions` | 거래 완료 내역 조회 |
| `post_place` | 지정가 주문(매수/매도) |
| `post_cancel` | 주문 취소 |
| `post_market_buy` | 시장가 매수 |
| `post_market_sell` | 시장가 매도 |
| `post_withdrawal_coin` | 코인 출금 요청 |
| `post_withdrawal_krw` | 원화 출금 요청 (빗썸에서 Deprecated) |

## 설치

```bash
# Smithery (권장)
npx -y @smithery/cli install @zereight/bithumb-mcp --client claude

# 직접 실행
npx @zereight/bithumb-mcp
```

## 필요 키 · 환경변수

| 환경변수 | 발급처 | 필수 |
|---------|--------|------|
| `BITHUMB_API_KEY` | [빗썸 API 관리](https://www.bithumb.com) | ✅ |
| `BITHUMB_SECRET_KEY` | [빗썸 API 관리](https://www.bithumb.com) | ✅ |

## 설정 예시

```json
{
  "mcpServers": {
    "bithumb-mcp": {
      "command": "npx",
      "args": ["-y", "@zereight/bithumb-mcp@latest"],
      "env": {
        "BITHUMB_API_KEY": "YOUR_BITHUMB_API_KEY",
        "BITHUMB_SECRET_KEY": "YOUR_BITHUMB_SECRET_KEY"
      },
      "disabled": false
    }
  }
}
```

## 비고

- 라이선스: MIT.
- 주문·출금 도구는 실제 자산을 이동시키므로 API 키 권한 설정에 주의가 필요하다.
- `post_withdrawal_krw`는 빗썸 정책상 폐기(Deprecated)된 기능이다.

---
*수집일: 2026-07-03 · 출처: 저장소 README*
