# stock-news-mcp

> **[navyjeongs/stock-news-mcp](https://github.com/navyjeongs/stock-news-mcp)** · ⭐ N/A (GitHub API 제한) · JavaScript/TypeScript · 최근 푸시 N/A · 카테고리: 🏦 Finance & Tax

주식 뉴스·종목 분석·포트폴리오 관리를 제공하며 국내 뉴스를 네이버 검색 API로 가져오는 MCP 서버입니다.

## 개요

주식 뉴스, 종목 분석, 포트폴리오 관리를 위한 MCP 서버다. 종목 정보·분석은 Yahoo Finance(yahoo-finance2), 국내 뉴스는 네이버 검색 API(키 설정 시) 또는 Google News RSS, 해외 뉴스는 Google News RSS를 사용한다. 기술적 지표(SMA/RSI/MACD/볼린저)와 펀더멘털(PER/PBR/ROE 등), 애널리스트 의견을 종합한 종목 분석과 포트폴리오·스크리닝을 지원한다. 뉴스 도구는 `sentiment`(positive/negative) 필터를 제공한다. npm 패키지 `stock-news-mcp`로 배포된다.

## 제공 도구

| 도구 | 기능 |
|------|------|
| `get_korean_stock_news` | 국내 주식 뉴스 조회 |
| `get_us_stock_news` | 미국 주식 뉴스 조회 |
| `get_stock_news` | 특정 종목 관련 뉴스 검색 |
| `get_stock_info` | 특정 종목 정보 조회 (현재가·등락률·시가총액 등) |
| `get_market_news` | 글로벌 시장 이슈 뉴스 (전쟁·금리·유가 등) |
| `get_stock_analysis` | 종목 종합 분석 (기술적+펀더멘털+애널리스트) |
| `search_stock` | 종목명으로 티커 심볼 검색 (한/영) |
| `get_market_summary` | 증시 자동 요약 (시간대별 한국/미국) |
| `compare_stocks` | 여러 종목 비교 (PER·PBR·ROE 등) |
| `get_sector_performance` | 업종/섹터별 대표 종목 성과 분석 |
| `analyze_portfolio` | 보유 종목 포트폴리오 종합 분석 |
| `get_exchange_rate` | 주요 환율 정보 조회 (USD/KRW 등) |
| `screen_stocks` | 조건 기반 종목 스크리닝 (PER·ROE·배당률 등) |

## 설치

```bash
npm install -g stock-news-mcp
# 또는
npx stock-news-mcp
```

## 필요 키 · 환경변수

| 환경변수 | 발급처 | 필수 |
|---------|--------|------|
| `NAVER_CLIENT_ID` | [네이버 개발자센터](https://developers.naver.com) | 선택 |
| `NAVER_CLIENT_SECRET` | [네이버 개발자센터](https://developers.naver.com) | 선택 |

> 네이버 키 미설정 시 국내 뉴스는 Google News RSS로 대체된다.

## 설정 예시

```json
{
  "mcpServers": {
    "stock-news-mcp": {
      "command": "npx",
      "args": ["-y", "stock-news-mcp"],
      "env": {
        "NAVER_CLIENT_ID": "발급받은_ID",
        "NAVER_CLIENT_SECRET": "발급받은_SECRET"
      }
    }
  }
}
```

## 비고

- 라이선스: MIT.
- 종목 데이터는 Yahoo Finance 기준이며, 한국 종목은 `005930.KS` 형식의 티커를 사용한다.

---
*수집일: 2026-07-03 · 출처: 저장소 README*
