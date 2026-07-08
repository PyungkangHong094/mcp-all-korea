# naver-api-mcp

> **[dataartai/naver-api-mcp](https://github.com/dataartai/naver-api-mcp)** · ⭐ N/A · TypeScript · 최근 푸시 N/A · 카테고리: 🔎 Search & Trends

네이버 쇼핑인사이트(DataLab) API와 검색 API를 통합 제공하는 MCP 서버입니다.

## 개요

네이버 개발자센터의 두 가지 API를 하나의 MCP 서버로 묶었다. DataLab 쇼핑인사이트로 카테고리·키워드별 트렌드(기기/성별/연령 세분화)를 조회하고, 검색 API로 블로그·지식iN·쇼핑·백과사전을 검색한다. TypeScript로 작성되어 `npm run build` 후 Node로 실행한다.

## 제공 도구

| 도구 | 기능 |
|------|------|
| `get-category-trends` | 카테고리별 트렌드 (최대 3개 비교) |
| `get-category-by-device` | 카테고리 기기별 트렌드 |
| `get-category-by-gender` | 카테고리 성별 트렌드 |
| `get-category-by-age` | 카테고리 연령별 트렌드 |
| `get-keyword-trends` | 키워드별 트렌드 (최대 5개 비교) |
| `get-keyword-by-device` | 키워드 기기별 트렌드 |
| `get-keyword-by-gender` | 키워드 성별 트렌드 |
| `get-keyword-by-age` | 키워드 연령별 트렌드 |
| `search-blog` | 블로그 검색 |
| `search-kin` | 지식iN 검색 |
| `search-shopping` | 쇼핑 검색 (가격순·중고/렌탈/해외직구 필터) |
| `search-encyclopedia` | 백과사전 검색 |

## 설치

```bash
git clone https://github.com/dataartai/naver-api-mcp.git
cd naver-api-mcp
npm install
npm run build
```

## 필요 키 · 환경변수

| 환경변수 | 발급처 | 필수 |
|---------|--------|------|
| `NAVER_CLIENT_ID` | [네이버 개발자센터](https://developers.naver.com) | ✅ |
| `NAVER_CLIENT_SECRET` | [네이버 개발자센터](https://developers.naver.com) | ✅ |

쇼핑인사이트(DataLab)와 검색 API를 각각 사용 신청해야 한다.

## 설정 예시

```json
{
  "mcpServers": {
    "naver-api": {
      "command": "node",
      "args": ["path/to/naver-api-mcp/dist/index.js"],
      "env": {
        "NAVER_CLIENT_ID": "YOUR-CLIENT-ID",
        "NAVER_CLIENT_SECRET": "YOUR-CLIENT-SECRET"
      }
    }
  }
}
```

## 비고

API 호출 한도: 쇼핑인사이트 1,000회/일, 검색 25,000회/일. 카테고리 비교 최대 3개, 키워드 비교 최대 5개.

---
*수집일: 2026-07-02 · 출처: 저장소 README*
