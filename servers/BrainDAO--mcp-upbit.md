# mcp-upbit

> **[BrainDAO/mcp-upbit](https://github.com/BrainDAO/mcp-upbit)** · ⭐ (rate limit) · TypeScript/Node · 최근 푸시 (rate limit) · 카테고리: 🏦 Finance & Tax

업비트 거래소의 공개 시세 조회와 선택적 사설 거래 도구를 제공하는 MCP 서버입니다.

## 개요

한국 최대 암호화폐 거래소 [Upbit](https://upbit.com)를 위한 FastMCP 서버. 실시간 시세(ticker), 오더북, 최근 체결 등 공개 시장 데이터에 API 키 없이 접근할 수 있고, API 키를 설정하면 잔고 조회·주문 생성/취소·입출금 등 사설 거래 도구가 활성화된다. npm 패키지 `@iqai/mcp-upbit`로 배포된다.

## 제공 도구

19개 도구 (README "MCP Tools" 자동생성 목록 기준).

| 도구 | 기능 | API 키 |
|------|------|--------|
| `GET_TICKER` | 시세 조회 | 불필요 |
| `GET_ORDERBOOK` | 오더북 조회 | 불필요 |
| `GET_TRADES` | 최근 체결 조회 | 불필요 |
| `GET_ACCOUNTS` | 잔고·포지션 조회 | 필요 |
| `CREATE_ORDER` | 주문 생성 (limit/market/price) | 필요 |
| `CANCEL_ORDER` | 주문 취소 | 필요 |
| `GET_ORDER` / `GET_ORDERS` | 주문 조회/목록 | 필요 |
| `GET_DEPOSIT` / `LIST_DEPOSITS` | 입금 조회/목록 | 필요 |
| `GET_DEPOSIT_CHANCE` | 입금 가능 정보 | 필요 |
| `CREATE_DEPOSIT_ADDRESS` / `GET_DEPOSIT_ADDRESS` / `LIST_DEPOSIT_ADDRESSES` | 입금 주소 생성/조회/목록 | 필요 |
| `CREATE_WITHDRAWAL` / `CANCEL_WITHDRAWAL` | 출금 생성/취소 | 필요 |
| `GET_WITHDRAWAL` / `LIST_WITHDRAWALS` | 출금 조회/목록 | 필요 |
| `LIST_WITHDRAWAL_ADDRESSES` | 출금 주소 목록 | 필요 |

## 설치

```bash
npx @iqai/mcp-upbit
# 소스 빌드
git clone https://github.com/IQAIcom/mcp-upbit.git && cd mcp-upbit && pnpm install && pnpm run build
```

## 필요 키 · 환경변수

| 환경변수 | 필수 | 설명 |
|---------|------|------|
| `UPBIT_SERVER_URL` | 선택 | 기본 `https://api.upbit.com` |
| `UPBIT_ACCESS_KEY` | 거래 시 | [Upbit Developer Center](https://upbit.com/service_center/open_api_guide) 발급 |
| `UPBIT_SECRET_KEY` | 거래 시 | 시크릿 키 |
| `UPBIT_ENABLE_TRADING` | 거래 시 | `true`면 사설 거래 도구 활성화 (기본 `false`) |

## 설정 예시

```json
{
  "mcpServers": {
    "upbit": {
      "command": "npx",
      "args": ["-y", "@iqai/mcp-upbit"],
      "env": {
        "UPBIT_SERVER_URL": "https://api.upbit.com",
        "UPBIT_ACCESS_KEY": "your_access_key_here",
        "UPBIT_SECRET_KEY": "your_secret_key_here",
        "UPBIT_ENABLE_TRADING": "true"
      }
    }
  }
}
```

## 비고

- npm 스코프·소스 저장소는 `IQAIcom/mcp-upbit`이며, 카탈로그의 `BrainDAO/mcp-upbit`는 관련/미러 저장소로 보인다.
- 시크릿 키는 비공개 유지 + IP allowlist 권장. `UPBIT_ENABLE_TRADING`은 실제 주문/출금 의도가 있을 때만 활성화.

---
*수집일: 2026-07-03 · 출처: 저장소 README*
