# naramarketmcp

> **[alphago2580/naramarketmcp](https://github.com/alphago2580/naramarketmcp)** · ⭐ N/A · Python · 최근 푸시 미상 · 카테고리: 📊 Public Data

조달청 나라장터(G2B) OPEN API로 입찰공고·낙찰·계약·조달통계·쇼핑몰 상품을 조회하는 15개 도구 MCP 서버입니다.

## 개요

한국 공공조달(G2B) 데이터를 MCP로 제공하는 FastMCP 2.0 서버다. 공공데이터포털(data.go.kr)의 나라장터 주요 API를 통합해 입찰공고·낙찰정보·계약정보·조달통계·물품목록·종합쇼핑몰 데이터를 AI 에이전트가 바로 사용할 수 있게 한다. stdio·http·sse 전송을 지원하며 도구 15종, 리소스 3종, 프롬프트 3종을 제공한다.

## 제공 도구

**기본 도구 (3)**

| 도구 | 기능 |
|------|------|
| `crawl_list` | 나라장터 상품 목록 조회 |
| `get_detailed_attributes` | 상품 상세 속성 조회 |
| `server_info` | 서버 정보 및 사용 가능한 도구 목록 |

**정부조달 API (4)**

| 도구 | 기능 |
|------|------|
| `call_public_data_standard_api` | 공공데이터개방표준 API (입찰공고·낙찰·계약) |
| `call_procurement_statistics_api` | 조달통계 API (14개 오퍼레이션) |
| `call_product_list_api` | 물품목록 API (12개 오퍼레이션) |
| `call_shopping_mall_api` | 종합쇼핑몰 API (MAS·납품요구·벤처나라, 9개 오퍼레이션) |

**AI 친화 간편 도구 (4)**

| 도구 | 기능 |
|------|------|
| `get_recent_bid_announcements` | 최근 입찰공고 조회(기간 자동 계산) |
| `get_successful_bids_by_business_type` | 업무구분별 낙찰정보(한글→코드 자동 변환) |
| `get_procurement_statistics_by_year` | 연도별 조달통계 |
| `search_shopping_mall_products` | 쇼핑몰 제품 검색(제품명/업체명) |

**탐색 도구 (4)**

| 도구 | 기능 |
|------|------|
| `get_all_api_services_info` | 전체 서비스·오퍼레이션 목록 |
| `get_api_operations` | 서비스별 세부 오퍼레이션 조회 |
| `call_api_with_pagination_support` | 페이징 지원 대량 데이터 탐색 |
| `get_data_exploration_guide` | 데이터 탐색 전략 가이드 |

리소스 3종(API 파라미터 가이드·값 예시·검색 패턴), 프롬프트 3종(워크플로우·파라미터 선택·쿼리 예제).

## 설치

```bash
git clone https://github.com/alphago2580/naramarketmcp.git
cd naramarketmcp
cp .env.example .env   # NARAMARKET_SERVICE_KEY 설정
pip install -r requirements.txt

# 실행 (stdio)
python -m src.main
# 또는 패키지 설치 후
pip install . && naramarket-mcp
```

Docker: `docker run --rm -e NARAMARKET_SERVICE_KEY=your-key -p 8000:8000 naramarket-mcp`. 요구: Python 3.10+.

## 필요 키 · 환경변수

| 환경변수 | 발급처 | 필수 |
|---------|--------|------|
| `NARAMARKET_SERVICE_KEY` | [공공데이터포털](https://www.data.go.kr/) | ✅ |
| `FASTMCP_TRANSPORT` | 전송 모드(`stdio`/`http`/`sse`, 기본 `stdio`) | ❌ |
| `FASTMCP_HOST` | HTTP/SSE 바인딩 호스트(기본 `127.0.0.1`) | ❌ |
| `FASTMCP_PORT` | HTTP/SSE 포트(기본 `8081`) | ❌ |
| `LOG_LEVEL` | 로깅 레벨(기본 `INFO`) | ❌ |

## 설정 예시

```json
{
  "mcpServers": {
    "naramarket": {
      "command": "naramarket-mcp",
      "env": {
        "NARAMARKET_SERVICE_KEY": "your-key"
      }
    }
  }
}
```
(README 기반 구성 — README에는 명시적 클라이언트 설정 JSON 없음)

## 비고

- FastMCP 2.0 기반, Smithery.ai 클라우드 호스팅 설정(`smithery.yaml`) 포함.
- 라이선스 Apache 2.0.

---
*수집일: 2026-07-03 · 출처: 저장소 README*
