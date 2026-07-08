# opendata-mcp

> **[ceami/opendata-mcp](https://github.com/ceami/opendata-mcp)** · ⭐ - · Node.js · 카테고리: 📊 Public Data

한국 공공데이터포털(OpenAPI)을 검색·표준문서화·호출하는 MCP 서버.

## 개요

공공데이터포털의 방대한 OpenAPI를 더 쉽게 탐색·호출하도록 돕는 MCP 서버다. 키워드로 API를 검색하고, 선택한 API의 표준 문서(markdown)를 병합해 받은 뒤, 그 메타데이터를 근거로 실제 엔드포인트를 호출하는 3단계 워크플로우를 제공한다. 검색·문서 도구는 내부적으로 `mcp.ezrnd.co.kr` 백엔드를 사용한다. Smithery(`@iosif2/opendata-mcp`)로 배포된다.

## 제공 도구

| 도구 | 기능 |
|------|------|
| `search_api` | 키워드 배열로 공공데이터 API 검색 (page/pageSize 지원) |
| `get_std_docs` | 검색 결과의 `listId[]`로 표준 문서(markdown) 병합 반환 |
| `fetch_data` | 표준문서/메타데이터 기반으로 실제 OpenAPI 엔드포인트 호출 (GET/POST, serviceKey/Authorization 자동 주입) |

## 설치

```bash
npm install
npm run dev   # Smithery CLI로 MCP 개발 서버 구동
```

요구: Node.js ≥ 18.17.

## 필요 키 · 환경변수

| 환경변수 | 발급처 | 필수 |
|---------|--------|------|
| `ODP_SERVICE_KEY` | [공공데이터포털](https://www.data.go.kr) | ✅(일부 API 호출 시) |

파라미터명에 `serviceKey`가 있으면 자동 주입, 헤더명에 `Authorization`이 있으면 `{Prefix} {키}` 형식으로 자동 주입.

## 설정 예시

```json
{
  "mcpServers": {
    "opendata": {
      "command": "npx",
      "args": ["-y", "@smithery/cli", "run", "@iosif2/opendata-mcp"]
    }
  }
}
```
(README 기반 구성 — Smithery 배포명 `@iosif2/opendata-mcp`)

## 비고

- 검색/문서 백엔드는 `mcp.ezrnd.co.kr`(HTTPS)에 의존.
- README 주: Smithery 테스트 환경에서는 `ODP_SERVICE_KEY` 주입 미지원(개선 예정).

---
*수집일: 2026-07-02 · 출처: 저장소 README*
