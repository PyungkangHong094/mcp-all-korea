# naver-search-mcp-fixed

> **[floatingcloud/naver-search-mcp-fixed](https://github.com/floatingcloud/naver-search-mcp-fixed)** · ⭐ N/A · Node.js/TypeScript · 최근 푸시 미상 · 카테고리: 🔎 Search & Trends

네이버 검색·데이터랩 트렌드를 제공하는 isnow890/naver-search-mcp의 프로토콜 오류 수정 포크입니다.

## 개요

원본 [@isnow890/naver-search-mcp](https://github.com/isnow890/naver-search-mcp)의 수정 포크로, 원본에 누락되어 있던 MCP 프로토콜 메서드(`prompts/list`, `resources/list`)를 추가해 Cursor·Claude Desktop 등에서 발생하던 "Method not found" 오류를 해결했다. 네이버 검색 API와 데이터랩 API를 감싸 웹·뉴스·블로그·쇼핑 등 11종 검색과 검색어/쇼핑 트렌드 분석 도구를 제공한다. npm 패키지 `@d429/naver-search-mcp-fixed`로 배포된다.

## 제공 도구

**검색 도구 (11)**

| 도구 | 기능 |
|------|------|
| `search_webkr` | 네이버 웹문서 검색 |
| `search_news` | 뉴스 검색 |
| `search_blog` | 블로그 검색 |
| `search_cafearticle` | 카페글 검색 |
| `search_shop` | 쇼핑 검색 |
| `search_image` | 이미지 검색 |
| `search_kin` | 지식iN 검색 |
| `search_book` | 책 검색 |
| `search_encyc` | 백과사전 검색 |
| `search_academic` | 학술논문 검색 |
| `search_local` | 지역 장소 검색 |

**데이터랩 도구 (9)**

| 도구 | 기능 |
|------|------|
| `datalab_search` | 검색어 트렌드 분석 |
| `datalab_shopping_category` | 쇼핑 카테고리 트렌드 |
| `datalab_shopping_by_device` | 쇼핑 트렌드(기기별) |
| `datalab_shopping_by_gender` | 쇼핑 트렌드(성별) |
| `datalab_shopping_by_age` | 쇼핑 트렌드(연령별) |
| `datalab_shopping_keywords` | 쇼핑 키워드 트렌드 |
| `datalab_shopping_keyword_by_device` | 쇼핑 키워드 트렌드(기기별) |
| `datalab_shopping_keyword_by_gender` | 쇼핑 키워드 트렌드(성별) |
| `datalab_shopping_keyword_by_age` | 쇼핑 키워드 트렌드(연령별) |

## 설치

```bash
npx @d429/naver-search-mcp-fixed
```

## 필요 키 · 환경변수

| 환경변수 | 발급처 | 필수 |
|---------|--------|------|
| `NAVER_CLIENT_ID` | [네이버 개발자센터](https://developers.naver.com/apps/#/register) | ✅ |
| `NAVER_CLIENT_SECRET` | [네이버 개발자센터](https://developers.naver.com/apps/#/register) | ✅ |

애플리케이션 등록 시 검색·데이터랩(검색어 트렌드)·데이터랩(쇼핑인사이트) API를 모두 선택해야 함.

## 설정 예시

```json
{
  "mcpServers": {
    "naver-search": {
      "command": "npx",
      "args": ["-y", "@d429/naver-search-mcp-fixed"],
      "env": {
        "NAVER_CLIENT_ID": "your_client_id",
        "NAVER_CLIENT_SECRET": "your_client_secret"
      }
    }
  }
}
```

## 비고

- 원본 isnow890/naver-search-mcp의 포크. 라이선스 MIT(원본과 동일).
- 요구사항: Node.js 18+, NPM 8+.

---
*수집일: 2026-07-03 · 출처: 저장소 README*
