# upbit-mcp-sse

> **[restful3/upbit-mcp-sse](https://github.com/restful3/upbit-mcp-sse)** · ⭐ (조회 실패) · Python · 최근 푸시 (조회 실패) · 카테고리: 🏦 Finance & Tax

업비트 OpenAPI를 SSE(Server-Sent Events)로 제공해 n8n 연동을 지원하는 MCP 서버입니다(solangii/upbit-mcp-server 기반).

## 개요

[solangii/upbit-mcp-server](https://github.com/solangii/upbit-mcp-server)를 기반으로, 원본의 stdio 통신 대신 SSE(Server-Sent Events) 방식을 지원하도록 개조한 포크다. n8n 같은 워크플로우 자동화 도구와의 연동을 목표로 하며 Docker/Docker Compose 배포를 기본으로 제공한다. FastMCP 1.0.0에 맞춰 에러 처리를 개선했고, 백테스팅 시스템과 차트 이미지 생성 기능이 추가되었다.

## 제공 도구

README의 "제공 툴(Tools)" 표에 명시된 도구:

| 도구 | 기능 |
|------|------|
| `get_ticker` | 특정 마켓의 현재 시세(가격·변동률) 조회 |
| `get_orderbook` | 실시간 매수/매도 호가 조회 |
| `get_trades` | 최근 체결 내역 조회 |
| `get_accounts` | 전체 계좌 잔고·보유 자산 조회 |
| `create_order` | 지정가/시장가 매수·매도 주문 생성 |
| `get_orders` | 미체결 주문 목록 조회 |
| `get_order` | 특정 주문 상세 조회 |
| `cancel_order` | 주문 취소 |
| `get_market_summary` | KRW 전체 마켓 상황 동적 요약 |
| `get_deposits_withdrawals` | 입출금 내역 조회 |
| `get_markets` | 거래 가능 전체 마켓 코드 목록 조회 |
| `get_candles` | 캔들(시고저종) 데이터 조회 |
| `create_withdraw` | 디지털 자산/원화 출금 요청 |
| `technical_analysis` | 기술적 지표·분석 신호 제공(MACD 등) |
| `backtesting` | SMA/RSI/볼린저밴드/MACD 전략 백테스팅 |
| `generate_chart_image` | 캔들스틱·라인·OHLC 차트 이미지 생성 및 웹 URL 반환 |

이 외에 `explain_ticker`, `analyze_portfolio` 등 프롬프트 템플릿과 `market://list` 리소스를 함께 제공한다.

## 설치

```bash
git clone https://github.com/restful3/upbit-mcp-sse.git
cd upbit-mcp-sse
# .env 파일에 UPBIT 키 저장 후
docker-compose up -d --build
```

`uv sync`로 로컬 실행도 가능하다. 기본 SSE 엔드포인트는 `http://<host>:8001/sse`이며 n8n 워크플로우에서 이 URL로 연결한다.

## 필요 키 · 환경변수

| 환경변수 | 발급처 | 필수 |
|---------|--------|------|
| `UPBIT_ACCESS_KEY` | [업비트 오픈API 관리](https://upbit.com/service_center/open_api_guide) | ✅ |
| `UPBIT_SECRET_KEY` | [업비트 오픈API 관리](https://upbit.com/service_center/open_api_guide) | ✅ |

`.env` 파일에 저장하며 `docker-compose.yml`의 `env_file`로 로드된다.

## 설정 예시

```yaml
# docker-compose.yml (README 기반 요약)
services:
  upbit_mcp_server:
    build: .
    ports:
      - "8001:8001"
    env_file:
      - .env
    networks:
      - nginx-n8n-net
```

## 비고

- SSE/Docker 기반이라 Claude Desktop stdio 방식보다는 n8n 등 외부 자동화 도구 연동에 초점이 맞춰져 있다.
- 실제 매매·출금 주문(`create_order`, `create_withdraw`)이 실행되므로 주의가 필요하다.
- 차트 이미지는 저자의 별도 서브도메인(`charts.resteful3.shop`)을 통해 서빙된다.

---
*수집일: 2026-07-03 · 출처: 저장소 README*
