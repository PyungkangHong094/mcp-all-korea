# data4library-mcp

> **[isnow890/data4library-mcp](https://github.com/isnow890/data4library-mcp)** · ⭐ N/A · TypeScript · 최근 푸시 N/A · 카테고리: 📊 Public Data

도서관 정보나루(Data4Library) API로 공공도서관 검색·대출 현황·독서 통계를 제공하는 MCP 서버입니다.

## 개요

국립중앙도서관이 운영하는 도서관 정보나루(전국 1,000여 개 공공도서관 통합 정보)를 완전 활용하는 MCP 서버. 도서관/도서 검색, 인기도서·트렌드, 대출·독서 통계, 개인화 추천, GPS 기반 주변 도서관 검색까지 25개 도구를 제공한다. Smithery·npx·Docker로 설치할 수 있다.

## 제공 도구

총 25개 (주요 도구):

| 도구 | 기능 |
|------|------|
| `search_libraries` | 전국 공공도서관 검색 |
| `search_books` | 도서 통합 검색 |
| `search_libraries_by_book` | 특정 도서 소장 도서관 찾기 |
| `get_book_detail` | ISBN 상세정보 |
| `check_book_availability` | 실시간 대출 가능 여부 |
| `search_popular_books` | 인기 대출도서 |
| `search_popular_books_by_library` | 도서관별 인기도서 |
| `get_hot_trend` | 대출 급상승 도서 |
| `get_new_arrival_books` | 신착도서 |
| `get_monthly_keywords` | 이달의 키워드 |
| `get_usage_trend` | 대출반납 추이 |
| `get_reading_quantity` | 지역별 독서량 |
| `search_items` | 장서/대출 데이터 |
| `get_book_usage_analysis` | 도서 이용 분석 |
| `get_mania_recommendations` | 마니아 추천도서 |
| `get_reader_recommendations` | 다독자 추천도서 |
| `get_book_keywords` | 도서 키워드 분석 |
| `search_nearby_libraries` | GPS 기반 주변 도서관 검색 |
| `search_library_codes` | 도서관 코드 검색 |
| `get_region_codes` / `get_detailed_region_codes` | 지역코드 조회 |
| `get_subject_codes` / `get_detailed_subject_codes` | KDC 주제분류코드 |
| `get_library_info` / `get_popular_books_by_library` | 도서관별 종합 정보 |
| `session_stats` | 사용량 통계 |

## 설치

```bash
# Smithery 자동 설치
npx -y @smithery/cli install @isnow890/data4library-mcp
```

npx 직접 실행·Docker도 지원.

## 필요 키 · 환경변수

| 환경변수 | 발급처 | 필수 |
|---------|--------|------|
| `LIBRARY_API_KEY` | [도서관 정보나루](https://www.data4library.kr/) | ✅ |

## 설정 예시

```json
{
  "mcpServers": {
    "data4library": {
      "command": "npx",
      "args": ["-y", "@isnow890/data4library-mcp"],
      "env": { "LIBRARY_API_KEY": "your-api-key" }
    }
  }
}
```

## 비고

`search_nearby_libraries`(GPS 거리 계산)는 정보나루 API에 없는 독자 구현. 영문 문서(README-en.md) 별도 제공. Smithery·MseeP 보안 배지 등재.

---
*수집일: 2026-07-02 · 출처: 저장소 README*
