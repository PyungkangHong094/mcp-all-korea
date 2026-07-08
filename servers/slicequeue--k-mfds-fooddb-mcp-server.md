# k-mfds-fooddb-mcp-server

> **[slicequeue/k-mfds-fooddb-mcp-server](https://github.com/slicequeue/k-mfds-fooddb-mcp-server)** · ⭐ N/A · TypeScript · 최근 푸시 N/A · 카테고리: 📊 Public Data

식품의약품안전처(K-MFDS) 식품영양성분 DB OpenAPI를 검색·조회하는 MCP 서버입니다.

## 개요

식약처 식품영양성분DB를 MCP 도구로 노출한다. 식품명·제조사·카테고리·품목제조보고번호 등 다양한 조건으로 영양성분 정보를 검색한다. npm 패키지(`k-mfds-fooddb-mcp-server`)로 배포되며 `npx`로 즉시 실행되고 STDIO 기반으로 동작한다.

## 제공 도구

| 도구 | 기능 |
|------|------|
| `searchFoodNutrition` | 식품 영양성분 검색. `foodNameKr`(식품명), `makerName`(제조사), `foodCategory1Name`(대분류), `itemReportNo`(품목제조보고번호), `pageNo`, `numOfRows` 등으로 조회 |

## 설치

```bash
# npx 즉시 실행
npx k-mfds-fooddb-mcp-server

# Smithery 자동 설치
npx -y @smithery/cli install @slicequeue/k-mfds-fooddb-mcp-server --client claude

# npm 전역 설치
npm install -g k-mfds-fooddb-mcp-server
```

## 필요 키 · 환경변수

| 환경변수 | 발급처 | 필수 |
|---------|--------|------|
| `GOV_API_KEY` | [공공데이터포털 식약처 식품영양성분DB](https://www.data.go.kr/data/15000161/openapi.do) | ✅ |

## 설정 예시

```json
{
  "mcpServers": {
    "k-mfds-fooddb": {
      "command": "npx",
      "args": ["k-mfds-fooddb-mcp-server"],
      "env": { "GOV_API_KEY": "발급받은_식약처_API_키" }
    }
  }
}
```

## 비고

Gemini(AI Studio)·Cursor·Continue·ModelContext 등 다양한 클라이언트 설정 예시 제공. Smithery 등재.

---
*수집일: 2026-07-02 · 출처: 저장소 README*
