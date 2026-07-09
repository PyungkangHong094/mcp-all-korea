# korean-patent-mcp

> **[Tech-curator/korean-patent-mcp](https://github.com/Tech-curator/korean-patent-mcp)** · ⭐ N/A (GitHub API 제한) · Python · 최근 푸시 N/A · 카테고리: 📊 Public Data

KIPRIS 특허정보 API로 출원인별 특허검색·상세조회·인용특허 분석을 제공하는 MCP 서버입니다.

## 개요

한국 특허정보 검색서비스(KIPRIS)의 KIPRIS Plus Open API(특허청 제공)에 연결하여, 자연어로 한국 특허를 검색·분석하는 MCP 서버다. 출원인명 검색, 출원번호 기반 상세 조회, 특정 특허를 인용한 후행 특허 조회를 지원한다. 모든 도구는 `response_format`(markdown/json) 파라미터를 제공한다.

## 제공 도구

| 도구 | 기능 |
|------|------|
| `kipris_search_patents` | 출원인명으로 특허 검색 |
| `kipris_get_patent_detail` | 출원번호로 특허 상세 정보 조회 |
| `kipris_get_citing_patents` | 특정 특허를 인용한 후행 특허 조회 |

> README에 `kipris_get_cpc_codes`, `kipris_get_inventors`, `kipris_check_rejection`, `kipris_analyze_rejection_reason`가 "향후 구현 예정(미구현)"으로 표기되어 있어 현재 도구에서 제외했다.

## 설치

```bash
# Smithery (권장)
npx -y @smithery/cli install korean-patent-mcp --client claude

# uv 로컬 설치
uv pip install git+https://github.com/Tech-curator/korean-patent-mcp.git
```

- 요구사항: Python 3.10+

## 필요 키 · 환경변수

| 환경변수 | 발급처 | 필수 |
|---------|--------|------|
| `KIPRIS_API_KEY` | [KIPRIS Plus](https://plus.kipris.or.kr) | ✅ |

## 설정 예시

```json
{
  "mcpServers": {
    "korean-patent": {
      "command": "uv",
      "args": ["run", "korean-patent-mcp"],
      "env": {
        "KIPRIS_API_KEY": "your_api_key_here"
      }
    }
  }
}
```

## 비고

- 라이선스: MIT.
- KIPRIS API 호출 제한이 있을 수 있어 대량 검색 시 페이지네이션 활용을 권장한다.

---
*수집일: 2026-07-03 · 출처: 저장소 README*
