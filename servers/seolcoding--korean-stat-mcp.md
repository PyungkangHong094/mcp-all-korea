# korean-stat-mcp

> **[seolcoding/korean-stat-mcp](https://github.com/seolcoding/korean-stat-mcp)** · ⭐ (조회 실패) · Python · 최근 푸시 (조회 실패) · 카테고리: 📊 Public Data

KOSIS OpenAPI 통계 데이터를 검색·조회·분석할 수 있게 제공하는 Python MCP 서버입니다.

## 개요

통계청 국가통계포털 KOSIS OpenAPI를 MCP 도구로 감싼 Python 서버다. 통계표 키워드 검색, 기관/주제별 목록 탐색, 통계표 메타데이터(분류·항목·수록기간) 확인, 원천 데이터 조회·필터링·그룹 집계, 특정 수치와 원천 데이터 대조 검증까지 지원한다. PyPI로 배포되며(`pip install korean-stat-mcp`), stdio·Streamable HTTP 두 방식과 저자가 운영하는 원격 호스팅 엔드포인트(설치 불필요)를 함께 제공한다.

## 제공 도구

README의 "주요 도구" 표에 명시된 도구:

| 도구 | 기능 |
|------|------|
| `search_statistics` | 키워드로 통계표 찾기 |
| `browse_categories` | 기관/주제별 목록 탐색 |
| `get_table_metadata` | 통계표 분류·항목·기간 메타데이터 확인 |
| `get_available_values` | 사용 가능한 분류/항목 값 확인 |
| `get_statistics_data` | KOSIS 원천 데이터 조회 |
| `filter_statistics` | 데이터 필터링 |
| `aggregate_statistics` | 그룹 집계 |
| `read_stored_data` | 저장된 큰 결과를 나눠 읽기 |
| `list_stored_data` | 저장된 데이터 목록 조회 |
| `verify_statistics` | 특정 수치와 원천 데이터 대조 검증 |

전체 도구 목록과 이전 이름 매핑은 저장소의 `docs/TOOL_MIGRATION.md` 참고.

## 설치

```bash
pip install korean-stat-mcp
export KOSIS_API_KEY="<KOSIS_API_KEY>"
korean-stat-mcp          # stdio (Claude Desktop/Cursor용)
korean-stat-mcp --http   # Streamable HTTP (http://localhost:8000/mcp)
```

설치 없이 저자 호스팅 인스턴스를 Claude.ai 커넥터로 쓸 수도 있다:
`https://korean-stat-mcp.seolcoding.com/mcp?apiKey=<YOUR_KOSIS_KEY>`

## 필요 키 · 환경변수

| 환경변수 | 발급처 | 필수 |
|---------|--------|------|
| `KOSIS_API_KEY` | [KOSIS OpenAPI 신청](https://kosis.kr/openapi/) | ✅ |
| `KOSIS_ARTIFACTS_DIR` | 로컬 차트/리포트 저장 경로 | ⬜ |

## 설정 예시

```json
{
  "mcpServers": {
    "korean-stat": {
      "command": "korean-stat-mcp",
      "env": {
        "KOSIS_API_KEY": "<KOSIS_API_KEY>"
      }
    }
  }
}
```

## 비고

- Python 3.12+ 필요, 라이선스 MIT.
- 자체 호스팅(Docker/Fly.io/Render/Railway 등) 배포 가이드는 저장소 `deploy/README.md`에 있다.
- 호스팅 커넥터는 Claude Pro/Max/Team/Enterprise 요금제가 필요하다(Free는 커넥터 1개 제한).

---
*수집일: 2026-07-03 · 출처: 저장소 README*
