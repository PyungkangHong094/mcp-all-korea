# upbit-mcp-server

> **[solangii/upbit-mcp-server](https://github.com/solangii/upbit-mcp-server)** · ⭐ (조회 실패) · Python · 최근 푸시 (조회 실패) · 카테고리: 🏦 Finance & Tax

업비트(Upbit) 거래소 OpenAPI로 시세·계좌·주문·입출금·기술분석을 제공하는 MCP 서버입니다.

## 개요

업비트 암호화폐 거래소의 OpenAPI를 MCP 도구로 감싼 서버다. 시세·호가창·체결내역·캔들 등 시장 데이터 조회, 계좌 잔고·주문내역 확인, 지정가/시장가 주문 생성 및 취소, 입출금 관리, 기술적 분석 기능을 제공한다. FastMCP 기반 Python 구현이며 stdio 방식으로 Claude Desktop에 직접 연결한다.

## 제공 도구

README의 "수행가능한 기능 목록"에 명시된 도구:

| 도구 | 기능 |
|------|------|
| `get_ticker` | 현재 암호화폐 시세 조회 |
| `get_orderbook` | 호가창 정보 조회 |
| `get_trades` | 최근 체결 내역 조회 |
| `get_market_summary` | 주요 암호화폐 시장 요약 정보 확인 |
| `get_accounts` | 보유 자산 목록 및 잔고 확인 |
| `get_orders` | 주문 내역 조회 |
| `get_order` | 특정 주문 상세 정보 조회 |
| `get_deposits_withdrawals` | 입출금 내역 조회 |
| `create_order` | 지정가/시장가 매수·매도 주문 생성 |
| `cancel_order` | 주문 취소 |

## 설치

```bash
git clone https://github.com/solangii/upbit-mcp-server.git
cd upbit-mcp-server
uv sync
```

`.env` 파일에 API 키를 저장한 뒤 `uv run python main.py`로 실행하거나 `fastmcp install main.py`로 등록한다.

## 필요 키 · 환경변수

| 환경변수 | 발급처 | 필수 |
|---------|--------|------|
| `UPBIT_ACCESS_KEY` | [업비트 오픈API 관리](https://upbit.com/service_center/open_api_guide) | ✅ |
| `UPBIT_SECRET_KEY` | [업비트 오픈API 관리](https://upbit.com/service_center/open_api_guide) | ✅ |

## 설정 예시

```json
{
  "mcpServers": {
    "upbit-mcp-server": {
      "command": "/full/path/to/upbit-mcp-server/.venv/bin/python",
      "args": ["/full/path/to/upbit-mcp-server/main.py"]
    }
  }
}
```

## 비고

- 실제 매매·출금 주문이 실행되므로 API 키 권한 설정에 주의해야 한다. README도 "실거래가 발생하니 신중히 사용하라"고 경고한다.
- 라이선스: MIT.

---
*수집일: 2026-07-03 · 출처: 저장소 README*
