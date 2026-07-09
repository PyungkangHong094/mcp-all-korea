# mcp-korean-stock

> **[ctk03272/mcp-korean-stock](https://github.com/ctk03272/mcp-korean-stock)** · ⭐ N/A · Python · 카테고리: 🏦 Finance & Tax

FinanceDataReader와 네이버 차트 API로 한국 주식 종목·일봉·10분봉과 기술지표를 제공하는 MCP 서버입니다.

## 개요

한국 주식 데이터를 제공하는 Python MCP 서버다. `FinanceDataReader`로 종목 리스트·프로필·일별 OHLCV를 조회하고, 네이버 차트 API(비공식 엔드포인트)로 10분봉 인트라데이 캔들을 수집한다. 기술지표는 로컬에서 계산한다. `STDIO`와 `HTTP/SSE` 두 가지 트랜스포트를 지원한다.

## 제공 도구

| 도구 | 기능 |
|------|------|
| `search_korean_stocks` | 종목명/키워드로 한국 주식 검색 |
| `get_korean_stock_profile` | 종목 프로필 정보 조회 |
| `get_korean_stock_daily_history` | 일별 OHLCV(일봉) 이력 조회 |
| `get_korean_stock_intraday_10m` | 10분봉 인트라데이 캔들 조회 (네이버 API) |
| `get_korean_stock_indicators` | 로컬 계산 기술지표 조회 |

## 설치

```bash
python3 -m venv .venv
source .venv/bin/activate
pip install -e .[dev]
```

실행(STDIO):

```bash
korean-stock-mcp
```

실행(HTTP):

```bash
MCP_TRANSPORT=http MCP_HOST=127.0.0.1 MCP_PORT=8000 korean-stock-mcp
```

## 필요 키 · 환경변수

API 키 불필요. 트랜스포트 관련 환경변수만 사용한다: `MCP_TRANSPORT`, `MCP_HOST`, `MCP_PORT` (HTTP 모드 시).

## 설정 예시

```json
{
  "mcpServers": {
    "korean-stock": {
      "command": "korean-stock-mcp"
    }
  }
}
```
*(README의 STDIO 실행 방법 기반 구성)*

## 비고

- 10분봉 데이터는 비공식 네이버 엔드포인트를 사용하므로 지연되거나 상위 스키마 변경에 영향받을 수 있다.
- 프로필 필드는 FinanceDataReader가 리스팅 데이터셋에서 노출하는 범위로 제한된다.
- Python 3.11+ 필요. 프로덕션 배포용 GitHub Actions/launchd 템플릿 포함.

---
*수집일: 2026-07-03 · 출처: 저장소 README*
