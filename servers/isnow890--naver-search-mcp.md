# naver-search-mcp

> **[isnow890/naver-search-mcp](https://github.com/isnow890/naver-search-mcp)** · ⭐ 77 · TypeScript · 최근 푸시 2026-05-12 · 카테고리: 🔎 Search & Trends

네이버 검색 API와 데이터랩 API를 연동해 종합 검색·트렌드 분석을 제공하는 MCP 서버.

## 개요

네이버 검색 API와 데이터랩(DataLab) API를 통합한 MCP 서버다. 웹·뉴스·블로그·카페·쇼핑·이미지·지식iN·책·백과사전·학술·지역 등 다양한 네이버 서비스 검색과, 검색어 트렌드·쇼핑 인사이트(카테고리/디바이스/성별/연령별) 분석을 제공한다. npm 패키지로 배포되고, API 키 없이 Kakao PlayMCP를 통해서도 사용 가능하다.

## 제공 도구

| 도구 | 기능 |
|------|------|
| `find_category` | 자연어로 카테고리 검색 (트렌드·쇼핑 인사이트용 카테고리 번호 자동 탐색) |
| `search_webkr` | 네이버 웹 문서 검색 |
| `search_news` | 네이버 뉴스 검색 |
| `search_blog` | 네이버 블로그 검색 |
| `search_cafearticle` | 네이버 카페 글 검색 |
| `search_shop` | 네이버 쇼핑 검색 |
| `search_image` | 네이버 이미지 검색 |
| `search_kin` | 네이버 지식iN 검색 |
| `search_book` | 네이버 책 검색 |
| `search_encyc` | 네이버 백과사전 검색 |
| `search_academic` | 네이버 학술 논문 검색 |
| `search_local` | 네이버 지역(장소) 검색 |
| `datalab_search` | 검색어 트렌드 분석 |
| `datalab_shopping_category` | 쇼핑 카테고리 트렌드 분석 |
| `datalab_shopping_by_device` | 디바이스별 쇼핑 트렌드 |
| `datalab_shopping_by_gender` | 성별 쇼핑 트렌드 |
| `datalab_shopping_by_age` | 연령별 쇼핑 트렌드 |
| `datalab_shopping_keywords` | 쇼핑 키워드 트렌드 |
| `datalab_shopping_keyword_by_device` | 키워드×디바이스 트렌드 |
| `datalab_shopping_keyword_by_gender` | 키워드×성별 트렌드 |
| `datalab_shopping_keyword_by_age` | 키워드×연령 트렌드 |

## 설치

```bash
npx -y @isnow890/naver-search-mcp
```

## 필요 키 · 환경변수

| 환경변수 | 발급처 | 필수 |
|---------|--------|------|
| `NAVER_CLIENT_ID` | [Naver Developers](https://developers.naver.com/apps/#/register) (검색 + 데이터랩 API 체크) | ✅ |
| `NAVER_CLIENT_SECRET` | Naver Developers | ✅ |

## 설정 예시

```json
{
  "mcpServers": {
    "naver-search": {
      "command": "npx",
      "args": ["-y", "@isnow890/naver-search-mcp"],
      "env": {
        "NAVER_CLIENT_ID": "your_client_id",
        "NAVER_CLIENT_SECRET": "your_client_secret"
      }
    }
  }
}
```

## 비고

- API 키 없이 [Kakao PlayMCP](https://playmcp.kakao.com/mcp/154)로 즉시 사용 가능. OpenClaw용 ClawHub 스킬(`openclaw skills install naver-search-mcp`)도 제공.
- 네이버 앱 등록 시 검색·데이터랩(검색어 트렌드)·쇼핑인사이트 API를 모두 체크해야 전체 도구 사용 가능. 라이선스: MIT.

---
*수집일: 2026-07-02 · 출처: 저장소 README*
