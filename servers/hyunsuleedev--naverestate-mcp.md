# naverestate-mcp

> **[hyunsuleedev/naverestate-mcp](https://github.com/hyunsuleedev/naverestate-mcp)** · ⭐ N/A (GitHub API rate-limit) · TypeScript · 카테고리: 🏠 Real Estate

Playwright로 네이버 부동산 아파트 매물 데이터를 수집하는 MCP 서버입니다.

## 개요

네이버 부동산 페이지를 실제 브라우저(Playwright)로 열어 public 흐름으로 접근하고, UI 상호작용(필터·스크롤·중복매물 펼치기) 과정에서 발생하는 내부 네트워크 응답을 **passive capture**해 정규화하는 MCP 서버다. 단지명 자동완성으로 후보를 찾아 `complexNo`로 resolve한 뒤 대표매물·중복매물을 수집한다. anti-detection 보정으로 기본 persistent 프로필 실행이 가능하며, 기존 Chrome에 CDP attach하는 경로도 지원한다. TypeScript workspace(collector-core / playwright-driver / mcp-server)로 구성.

## 제공 도구

소스 기준 stdio MCP 서버가 제공하는 도구 4개.

| 도구 | 기능 |
|------|------|
| `naver_search_complex` | 키워드로 단지 자동완성 후보 검색 |
| `naver_resolve_complex` | 후보를 `complexNo`로 resolve하고 캐시 저장 |
| `naver_collect_complex` | 단지 상세에서 대표매물 + 중복매물 수집 |
| `naver_get_last_result` | 마지막 수집 JSON 다시 가져오기 |

## 설치

저장소 클론 후 빌드하고 `packages/mcp-server/dist/index.js`를 실행한다.

```bash
npm run build
node packages/mcp-server/dist/index.js
```

## 필요 키 · 환경변수

API 키 불필요 (로그인 없는 public 흐름 기본). 선택적으로 CDP attach 모드에서 아래 변수 사용.

| 환경변수 | 용도 | 필수 |
|---------|------|------|
| `NAVER_CDP_ENDPOINT_URL` | 기존 Chrome 디버깅 엔드포인트에 attach (예: `http://127.0.0.1:9222`) | ❌ |

## 설정 예시

```json
{
  "mcpServers": {
    "naverestate": {
      "command": "node",
      "args": ["/path/to/naverestate-mcp/packages/mcp-server/dist/index.js"],
      "env": {}
    }
  }
}
```
*(README에 클라이언트 설정 JSON 예시가 없어 실행 방법 기반으로 구성)*

## 비고

Playwright 기반 스크래핑 서버 — 네이버 부동산이 새 Playwright 컨텍스트를 차단할 수 있어 CDP attach 경로 제공. 검색 기본 정렬은 최신순(`dateDesc`) 고정. 도구 목록은 README 표에 명시.

---
*수집일: 2026-07-03 · 출처: 저장소 README*
