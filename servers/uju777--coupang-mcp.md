# coupang-mcp

> **[uju777/coupang-mcp](https://github.com/uju777/coupang-mcp)** · ⭐ (조회 실패) · Python · 최근 푸시 (조회 실패) · 카테고리: 🛒 Commerce & Retail

쿠팡 상품을 검색하고 다나와에서 실시간 최저가를 확인하는(로켓배송·중고 포함) MCP 서버입니다.

> ⚠️ README 상단 안내에 따르면 **현재 내부 보수·업데이트 중(Under Maintenance)**으로, 모든 API 호출이 HTTP 503 점검 응답을 반환한다(수집 시점 기준).

## 개요

Claude Desktop에서 쿠팡 상품을 검색하고 최저가를 확인하는 FastMCP 기반 Python 서버다. README는 다나와 실시간 가격 조회, 로켓/일반배송 구분, 가격 포맷팅, 폴백 지원을 특징으로 소개한다. Docker(HuggingFace Space) 기반으로 배포되며 소스는 쿠팡 파트너스 API(HMAC 서명 인증)를 사용한다.

## 제공 도구

README에는 도구 표가 없어 소스(`server.py`)의 `@mcp.tool()` 등록부에서 확인:

| 도구 | 기능 |
|------|------|
| `search_coupang_products` | 키워드로 쿠팡 상품 검색(`keyword`, `limit`) |
| `get_coupang_best_products` | 카테고리별 베스트 상품 조회(`category_id`, `limit`) |
| `generate_coupang_deeplink` | 상품 URL을 파트너스 딥링크로 변환(`original_url`) |
| `get_coupang_goldbox` | 골드박스(특가) 상품 조회(`limit`) |

## 설치

Docker 기반(HuggingFace Space). `Dockerfile`은 `http_server.py`를 7860 포트로 실행한다. 로컬 stdio MCP는 `server.py`를 사용한다.

```bash
git clone https://github.com/uju777/coupang-mcp.git
cd coupang-mcp
pip install -r requirements.txt
# .env에 COUPANG_ACCESS_KEY / COUPANG_SECRET_KEY 설정 후
python server.py
```

## 필요 키 · 환경변수

| 환경변수 | 발급처 | 필수 |
|---------|--------|------|
| `COUPANG_ACCESS_KEY` | [쿠팡 파트너스](https://partners.coupang.com) | ✅ |
| `COUPANG_SECRET_KEY` | [쿠팡 파트너스](https://partners.coupang.com) | ✅ |

`server.py`는 두 키가 없으면 `ValueError`를 발생시키며 종료한다.

## 설정 예시

```json
{
  "mcpServers": {
    "coupang": {
      "command": "python",
      "args": ["/path/to/coupang-mcp/server.py"],
      "env": {
        "COUPANG_ACCESS_KEY": "여기에_access_key",
        "COUPANG_SECRET_KEY": "여기에_secret_key"
      }
    }
  }
}
```
*(README 기반 구성 — README의 "빠른 시작"은 설정 파일 위치 안내에서 잘려 있어 소스 기준으로 구성)*

## 비고

- **API 키 관련 불일치**: 카탈로그 설명은 "API 키 불필요"라고 하지만, 소스(`server.py`)는 `COUPANG_ACCESS_KEY`·`COUPANG_SECRET_KEY`(쿠팡 파트너스 API HMAC 인증)를 필수로 요구한다. 배포된 HuggingFace Space 버전은 서버가 키를 보유해 사용자가 키 없이 호출하는 구조일 수 있으나, 저장소 코드 기준으로는 키가 필요하다.
- 수집 시점 기준 서비스가 점검 중(HTTP 503)이다.

---
*수집일: 2026-07-03 · 출처: 저장소 README, 소스 코드*
