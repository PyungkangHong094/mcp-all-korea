# KIS_MCP_Server

> **[migusdn/KIS_MCP_Server](https://github.com/migusdn/KIS_MCP_Server)** · ⭐ 25 · Python · 최근 푸시 2026-06-15 · 카테고리: 🏦 Finance & Tax

한국투자증권(KIS) REST API를 MCP 도구로 호출하는 서버.

## 개요

한국투자증권 REST API(8개 그룹, 166개 API)를 카탈로그 기반 범용 도구와 자주 쓰는 편의 도구로 노출한다. 국내·해외 주식 시세/잔고/주문, 국내채권·선물옵션 조회를 지원하며, `stdio`/`sse`/`streamable-http` transport와 토큰 캐시·계좌정보 자동 보완을 갖췄다. 주문/정정/취소 등 상태 변경 API는 기본 차단(`KIS_ENABLE_TRADING=true` 명시 시에만 실행)이며, 컨텍스트 절약용 `catalog` 경량 모드를 제공한다. 비공식 오픈소스 프로젝트(한국투자증권과 제휴·승인 관계 없음).

## 제공 도구

카탈로그 도구 (`catalog` 모드에서 노출):

| 도구 | 기능 |
|------|------|
| `list-kis-api-specs` | API 그룹/검색어 기준 목록 조회 |
| `get-kis-api-spec` | 단일 API의 경로·TR_ID 후보·파라미터 확인 |
| `call-kis-api` | `group`, `api_type`, `params`로 카탈로그 API 호출 |

편의 도구 (`full` 모드에서 추가 노출):

| 도구 | 기능 |
|------|------|
| `inquery-stock-price` | 국내주식 현재가 조회 |
| `inquery-balance` | 국내주식 잔고 조회 |
| `inquery-order-list` | 국내주식 일별 주문/체결 조회 |
| `inquery-order-detail` | 국내주식 주문 상세 조회 |
| `inquery-stock-info` | 국내주식 일별 시세 조회 |
| `inquery-stock-history` | 국내주식 기간 시세 조회 |
| `inquery-stock-ask` | 국내주식 호가 조회 |
| `inquery-stock-market` | 국내 업종/지수 현재가 조회 |
| `inquery-stock-basic-info` | 국내주식 기본정보 조회 |
| `inquery-overseas-stock-price` | 해외주식 현재가 조회 |
| `order-stock` | 국내주식 매수/매도 주문 (거래 게이트 필요) |
| `order-overseas-stock` | 해외주식 매수/매도 주문 (거래 게이트 필요) |

## 설치

```bash
pip install uv
uv sync
cp .env.example .env
# .env에 KIS 키 설정 후
uv run python server.py
```

Python >= 3.13, uv 필요. 자세한 클라이언트별 등록은 저장소 `INSTALL.md` 참고.

## 필요 키 · 환경변수

| 환경변수 | 발급처 | 필수 |
|---------|--------|------|
| `KIS_APP_KEY` | [KIS Developers](https://apiportal.koreainvestment.com) 앱키 | ✅ |
| `KIS_APP_SECRET` | KIS Developers 시크릿키 | ✅ |
| `KIS_CANO` | 계좌번호 앞 8자리 | ✅ |
| `KIS_ACNT_PRDT_CD` | 계좌상품코드(예: `01`) | ✅ |
| `KIS_ACCOUNT_TYPE` | `REAL` 또는 `VIRTUAL` | ✅ |
| `KIS_ENABLE_TRADING` | 주문/정정/취소 API 활성화(`true`) | ❌ |
| `KIS_MCP_TOOLSET` | `catalog`(3개) 또는 `full`(15개) | ❌ |

## 설정 예시

```json
{
  "mcpServers": {
    "kis-mcp-server": {
      "command": "uv",
      "args": ["run", "python", "server.py"],
      "cwd": "<project-root>",
      "env": {
        "KIS_MCP_TOOLSET": "catalog",
        "KIS_MCP_LOG_LEVEL": "WARNING"
      }
    }
  }
}
```

## 비고

- 주문/정정/취소 도구는 `KIS_ENABLE_TRADING=true` 없이는 실행되지 않는다(안전 기본값).
- `catalog` 모드는 도구 스키마 로드량을 줄여 컨텍스트 사용을 낮춘다. 166개 API는 `call-kis-api`로 그대로 호출 가능.

---
*수집일: 2026-07-02 · 출처: 저장소 README*
