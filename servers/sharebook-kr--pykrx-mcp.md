# pykrx-mcp

> **[sharebook-kr/pykrx-mcp](https://github.com/sharebook-kr/pykrx-mcp)** · ⭐ 3 · Python · 최근 푸시 2026-02-01 · 카테고리: 🏦 Finance & Tax

pykrx 라이브러리 기반으로 한국 주식시장 데이터를 제공하는 MCP 서버.

## 개요

[pykrx](https://github.com/sharebook-kr/pykrx) 라이브러리를 통해 KOSPI·KOSDAQ·KONEX 시장의 주가(OHLCV), 시가총액, 재무지표(PER/PBR/EPS/DIV/BPS/DPS), 투자자별 수급, 공매도, 외국인 투자, 지수, ETF 데이터를 자연어로 조회한다. FastMCP 기반이며 별도 API 키 없이 KRX 공개 데이터를 사용한다. 총 23개 도구 제공.

## 제공 도구

| 도구 | 기능 |
|------|------|
| `get_market_ticker_list` | 시장별 종목 코드 조회 |
| `get_market_ticker_name` | 종목 코드로 종목명 조회 |
| `get_stock_ohlcv` | 개별 종목 OHLCV |
| `get_market_ohlcv_by_date` | 특정 일자 전종목 시세 |
| `get_market_price_change` | 기간별 전종목 가격 변동 |
| `get_market_cap_by_date` | 개별 종목 시가총액 |
| `get_market_fundamental_by_date` | PER/PBR/EPS/DIV/BPS/DPS |
| `get_market_trading_value_by_date` | 종목별 투자자 수급(거래대금) |
| `get_market_trading_volume_by_investor` | 투자자별 거래량 |
| `get_market_trading_value_by_investor` | 투자자별 거래대금 |
| `get_market_net_purchases_of_equities` | 투자자별 순매수 상위 종목 |
| `get_index_ticker_list` | 지수 티커 목록 |
| `get_index_ticker_name` | 지수 이름 조회 |
| `get_index_portfolio_deposit_file` | 지수 구성 종목 |
| `get_index_ohlcv` | 지수 OHLCV |
| `get_index_fundamental` | 지수 PER/PBR/배당수익률 |
| `get_shorting_status_by_date` | 종목별 공매도 현황 |
| `get_shorting_volume_by_ticker` | 전종목 공매도 거래량 |
| `get_shorting_balance_top50` | 공매도 잔고 상위 50 |
| `get_shorting_volume_top50` | 공매도 거래 비중 상위 50 |
| `get_exhaustion_rates_of_foreign_investment` | 외국인 보유량·한도소진률 |
| `get_etf_ticker_list` | ETF 종목 리스트 |
| `get_etf_ohlcv_by_date` | ETF OHLCV |

## 설치

```bash
uvx pykrx-mcp
```

PyPI 패키지 `pykrx-mcp`. Python 3.10+ 필요.

## 필요 키 · 환경변수

API 키 불필요 (KRX 공개 데이터).

## 설정 예시

```json
{
  "mcpServers": {
    "pykrx": {
      "command": "uvx",
      "args": ["pykrx-mcp"]
    }
  }
}
```

## 비고

- 데이터 출처는 KRX(한국거래소)이며 pykrx 라이브러리의 조회 능력에 종속된다.
- 기술 스택: pykrx + FastMCP.

---
*수집일: 2026-07-02 · 출처: 저장소 README*
