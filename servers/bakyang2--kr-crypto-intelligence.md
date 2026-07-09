# kr-crypto-intelligence

> **[bakyang2/kr-crypto-intelligence](https://github.com/bakyang2/kr-crypto-intelligence)** · ⭐ N/A (GitHub API 제한) · 언어 미상(호스팅 HTTP API) · 최근 푸시 N/A · 카테고리: 🏦 Finance & Tax

180+ 토큰 김치프리미엄·Upbit/Bithumb 시세·한국어 감성분석을 제공하는 크립토 인텔리전스 MCP 서버입니다.

## 개요

한국 암호화폐 시장 데이터와 AI 분석을 AI 에이전트에 제공하는 원격 호스팅 서비스다. Upbit·Bithumb·Binance·CoinGecko 등을 데이터 소스로 삼아 180+ 토큰 김치프리미엄, 한국→영어 크립토 감성분석(세계 최초 표방), 글로벌 vs 한국 가격 괴리, AI 시장 분석(Claude 기반)을 제공한다. MCP 서버는 `https://mcp.printmoneylab.com/mcp`로 호스팅되며, 결제는 x402 프로토콜(Base/Polygon/Solana의 USDC) 기반 종량제로 API 키·구독·가입이 필요 없다.

## 제공 도구

> README는 MCP 도구명을 별도로 열거하지 않고, 서비스의 **15개 유료 REST 엔드포인트**로 기능을 설명한다 (호스팅 MCP가 이를 래핑). 아래는 그 엔드포인트 기준 기능 요약이며, 실제 MCP 도구명은 저장소에 명시 없음.

| 엔드포인트 | 기능 |
|------|------|
| `/api/v1/kr-news/kpop`, `/kpop-summary` | K-pop 뉴스 영역 번역 및 AI 감성 요약 |
| `/api/v1/kr-news/semiconductor`, `/semiconductor-summary` | 반도체 산업 뉴스 및 AI 시장 신호 |
| `/api/v1/kr-sentiment` | 한국 시장 감성(영문) — 거래소+뉴스 결합 |
| `/api/v1/global-vs-korea-divergence`, `-deep` | 글로벌 vs 한국 가격 괴리 (light/deep) |
| `/api/v1/arbitrage-scanner` | 180+ 토큰 김치프리미엄·역프·거래소 가격차 |
| `/api/v1/exchange-alerts` | 신규 상장/폐지·투자유의·주의 플래그 |
| `/api/v1/market-movers` | 1분 급등락·거래량 급증·상위 20 토큰 |
| `/api/v1/market-read` | 12+ 데이터소스 AI 시장 분석 (토큰별 시그널) |
| `/api/v1/kimchi-premium` | BTC 김치프리미엄 (공식 USD/KRW + USDT 실거래 이중 기준) |
| `/api/v1/stablecoin-premium` | 국내 거래소 USDT/USDC 프리미엄 |
| `/api/v1/kr-prices` | 국내 거래소(Upbit/Bithumb) 시세 |
| `/api/v1/fx-rate` | USD/KRW 환율 |

## 설치

설치 불필요 — 원격 호스팅 MCP 서버(`https://mcp.printmoneylab.com/mcp`)에 URL로 연결한다.

## 필요 키 · 환경변수

API 키 불필요. x402 프로토콜 기반 종량제 결제(Base/Polygon/Solana의 USDC)를 사용한다. 무료 엔드포인트로 `/api/v1/symbols`, `/api/v1/stats`, `/health` 등이 제공된다.

## 설정 예시

```json
{
  "mcpServers": {
    "kr-crypto-intelligence": {
      "url": "https://mcp.printmoneylab.com/mcp"
    }
  }
}
```

## 비고

- 라이선스: MIT.
- AWS Bedrock AgentCore Payments와 x402-native 연동을 지원하며 `.well-known/x402`로 서비스 디스커버리가 가능하다.
- 저장소는 서비스 문서(README) 중심이며 서버 구현 언어는 명시되어 있지 않다.

---
*수집일: 2026-07-03 · 출처: 저장소 README*
