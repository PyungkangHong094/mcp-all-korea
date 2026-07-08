# taxfood-mcp

> **[man2service/taxfood-mcp](https://github.com/man2service/taxfood-mcp)** · ⭐ N/A · Python · 최근 푸시 N/A · 카테고리: 🧩 Miscellaneous

전국 공공기관이 업무추진비(세금)로 식사한 식당 데이터를 검색·지역별·랭킹으로 조회하는 MCP 서버.

## 개요

공공기관 업무추진비 지출 식당 데이터를 AI 에이전트용 MCP 도구로 노출하는 정보공개·투명성 서비스다. 데이터는 런타임에 공개 CDN(`https://taxfood.kr/data/*.json`)에서 fetch + 인메모리 캐시하며, 공개 레포에는 데이터·개인정보·시크릿이 포함되지 않는다. 모든 응답에 공식 정보공개 출처 링크와 카카오맵 딥링크가 붙는다. Streamable HTTP · 스테이트리스 원격 MCP(단일 `POST /mcp/`)로, 카카오 PlayMCP / AGENTIC PLAYER 10 출품용이다.

## 제공 도구

| 도구 | 기능 |
|------|------|
| `search_tax_restaurants` | 이름/지역/구 검색 + 정렬 |
| `find_nearby_tax_restaurants` | 좌표 기반 주변 검색(카톡 위치공유) |
| `rank_tax_restaurants_in_area` | 시/도·구 지출 랭킹 |
| `get_agency_dining_summary` | 기관별 지출 집계 |
| `get_place_spending_detail` | 근거 원장(날짜·부서·금액·목적) |
| `get_spend_source_records` | 공식 출처 링크만 반환(검증) |
| `list_regions_overview` | 지역 커버리지/총계 |

## 설치

pip 소스 구동.

```bash
pip install -e ".[dev]"
python -m taxmatjip_mcp          # http://0.0.0.0:8080/mcp/
```

카카오 클라우드(PlayMCP in KC)에는 Git 소스 + Dockerfile 빌드로 배포한다.

## 필요 키 · 환경변수

| 환경변수 | 발급처 | 필수 |
|---------|--------|------|
| `PORT` | (기본 8080) | ❌ |
| `TAXMATJIP_DATA_BASE_URL` | (기본 `https://taxfood.kr/data`) | ❌ |

API 키 불필요.

## 설정 예시

원격 Streamable HTTP MCP로, 발급된 엔드포인트의 `/mcp/`에 연결한다.

```json
{
  "mcpServers": {
    "taxfood": {
      "url": "http://localhost:8080/mcp/"
    }
  }
}
```
(README 기반 구성)

## 비고

- 도구 목록은 README에 명시(7개, 확인됨).
- 응답 단계 PII 스크럽(이름+직함 패턴 제거) 적용.
- 라이선스: MIT(코드). 데이터는 각 공공기관 정보공개 자료가 원본.
- 데이터 원본/지도: https://taxfood.kr

---
*수집일: 2026-07-02 · 출처: 저장소 README*
