# kr-movie-tv-mcp

> **[carasjung/kr-movie-tv-mcp](https://github.com/carasjung/kr-movie-tv-mcp)** · ⭐ N/A · Python · 최근 푸시 N/A · 카테고리: 🧩 Miscellaneous

한국 영화·드라마의 박스오피스, 시청률, 수상 이력, 스트리밍 제공 여부, 출연진 정보를 통합 조회하는 MCP 서버.

## 개요

한국 영화·TV 데이터를 10개 소스(TMDB, KOBIS, MyDramaList, HanCinema, Naver Movies/TV, JustWatch, Wikipedia 등)에서 수집해 하나의 Supabase(PostgreSQL) DB로 통합하고, FastMCP로 17개 도구를 노출한다. 국내외 평점(닐슨코리아·네이버·MDL·TMDB·Rotten Tomatoes), 회차별 시청률, JustWatch 스트리밍 가용성(US/UK/CA/AU), KOBIS 공식 박스오피스, 5개 시상식 수상 이력, OST 앨범 등을 제공한다. Railway에 상시 호스팅되며 Descope 기반 OAuth 2.1 인증을 사용하는 원격 MCP다.

## 제공 도구

| 도구 | 기능 |
|------|------|
| `search_titles` | 영어/한글 제목으로 영화·드라마 검색 |
| `get_trending_dramas` | 방영 중 드라마를 MDL 평점순 정렬 |
| `get_top_dramas` | 역대 최고 완결 드라마(장르 필터) |
| `get_top_movies` | 최고 한국 영화(장르/연도/평점 필터) |
| `browse_by_genre` | 장르별 영화·드라마 필터 |
| `browse_by_tag` | MDL 커뮤니티 태그로 드라마 필터 |
| `get_movie` | 영화 상세(5개 평점 소스 포함) |
| `get_drama` | 드라마 상세(전체 평점 소스 포함) |
| `get_cast` | 배역·역할 유형 포함 출연진 목록 |
| `get_episode_ratings` | 닐슨코리아 회차별 시청률(%) |
| `get_ost_albums` | OST 앨범(네이버 바이브 스트리밍 링크) |
| `find_where_to_watch` | 제목·지역별 스트리밍 가용성 |
| `find_by_provider` | 지역 내 특정 제공사(Netflix/Viki 등) 콘텐츠 |
| `get_weekly_boxoffice` | KOBIS 주간 박스오피스 순위 |
| `get_actor_filmography` | 배우·감독 전체 필모그래피 |
| `get_awards` | 제목·시상식 연도별 수상 이력 |
| `compare_ratings` | 전 소스 평점 나란히 비교 |

## 설치

원격 호스팅 서버로, 별도 설치 없이 엔드포인트에 연결한다(Descope OAuth 2.1 인증).

```
Live endpoint: https://kr-movie-tv-mcp-production.up.railway.app/mcp
```

소스 직접 구동 시 `server.py`(FastMCP)와 Supabase 연결이 필요하다.

## 필요 키 · 환경변수

원격 엔드포인트 이용 시 Descope OAuth 2.1 인증 흐름을 따른다(별도 API 키 없이 OAuth). 소스 자체 구동 시 각 데이터 소스 API 키(TMDB, KOBIS 등)와 Supabase 연결 정보가 필요하나 README에 환경변수명 명시는 없음.

## 설정 예시

```json
{
  "mcpServers": {
    "kr-movie-tv": {
      "url": "https://kr-movie-tv-mcp-production.up.railway.app/mcp"
    }
  }
}
```
(README 기반 구성 — OAuth 2.1 인증 필요)

## 비고

- 도구 목록은 README에 명시(17개, 확인됨).
- Supabase 무료 티어 기반, GitHub Actions + Prefect로 야간 동기화.
- KMDb 소스는 API 승인 대기 중(pending).

---
*수집일: 2026-07-02 · 출처: 저장소 README*
