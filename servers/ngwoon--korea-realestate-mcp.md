# korea-realestate-mcp

> **[ngwoon/korea-realestate-mcp](https://github.com/ngwoon/korea-realestate-mcp)** · ⭐ 0 · TypeScript · 최근 푸시 2026-02-08 · 카테고리: 🏠 Real Estate

네이버부동산·직방·다방·KB부동산 등 여러 플랫폼의 매물 정보를 통합 조회하는 MCP 서버.

## 개요

여러 부동산 플랫폼(네이버부동산·직방·다방·KB부동산)을 provider 추상화로 묶어, 좌표 또는 지역 키워드로 매물을 통합 검색하고 상세 정보를 조회한다. 네이버부동산 기준의 지역 코드 탐색도 제공. TypeScript, `@modelcontextprotocol/sdk` + Zod, axios, express(HTTP 서버), ngeohash. README가 없어 도구 목록은 소스(`src/server/tools/`)에서 확인.

## 제공 도구

| 도구 | 기능 |
|------|------|
| `search_articles` | 네이버부동산·직방·다방·KB부동산 통합 매물 검색 (좌표 `lat`/`lng` 또는 지역 키워드 `region`, 거래유형·가격·면적·방 수 필터) |
| `get_article_detail` | 특정 매물 상세 조회 (`search_articles`의 `source`·`id` 사용) |
| `get_regions` | 네이버부동산 기준 지역 코드 조회 (전국=`0000000000`, 서울=`1100000000`, 경기=`4100000000`) |

## 설치

```bash
git clone https://github.com/ngwoon/korea-realestate-mcp.git
cd korea-realestate-mcp
npm install
npm run build   # dist/server/index.js 생성
```
*(README 없음 — package.json 기준 구성. bin: `korean-realstate-mcp` → `dist/server/index.js`)*

## 필요 키 · 환경변수

API 키 불필요 (각 플랫폼의 비공식/공개 조회 API 사용). 소스에서 별도 필수 환경변수는 확인되지 않음.

## 설정 예시

```json
{
  "mcpServers": {
    "korea-realestate": {
      "command": "node",
      "args": ["/path/to/korea-realestate-mcp/dist/server/index.js"]
    }
  }
}
```
*(README 기반 아님 — package.json bin 경로 기준 표준형 구성)*

## 비고

- **README 파일이 저장소에 없음** — 도구·구성 정보는 소스 코드(`src/server/index.ts`, `src/server/tools/*.ts`, `package.json`)에서 추출.
- providers: naver / zigbang / dabang / kb. 라이선스: MIT.
- HTTP 서버 모드(express) 포함(`src/server/http-server.ts`).

---
*수집일: 2026-07-02 · 출처: 소스 코드(src/server, package.json)*
