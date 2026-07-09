# serper-discover-mcp

> **[leeyseo/serper-discover-mcp](https://github.com/leeyseo/serper-discover-mcp)** · ⭐ N/A · 미상 (Docker 배포) · 최근 푸시 미상 · 카테고리: 🔎 Search & Trends

Serper 구글검색에 네이버 블로그·카페 검색과 장소 발굴(discover_places)을 더한 한국 특화 검색 MCP 서버입니다.

## 개요

[Serper](https://serper.dev) Google Search API 위에 구축된 한국어 특화 검색·장소 발굴 MCP 서버다. 일반 Serper 래퍼가 `search(query)`만 노출하는 것과 달리, 한국 지역명(성수동·잠실·강남 등)과 카테고리(attraction/restaurant/cafe 등)로 여러 구글 쿼리를 생성하고 스니펫·제목에서 접미사 기반 정규식(공원/박물관/카페/식당 등)으로 한국 장소명을 추출하는 `discover_places`를 제공한다. 네이버 블로그·카페 도메인 한정 검색과 페이지 본문 추출도 지원하며, 결과는 기본적으로 한국어 우선(`gl=kr`, `hl=ko`)이고 5분 인메모리 캐시를 둔다. 한국 여행 일정 플래너 Daypath를 위해 만들어졌다.

## 제공 도구

| 도구 | 기능 |
|------|------|
| `web_search` | 구글 검색, 선택적 `site` 필터 |
| `naver_blog_search` | 네이버 블로그 사이트 한정 검색 |
| `naver_cafe_search` | 네이버 카페(커뮤니티) 검색 |
| `discover_places` | (area, place_type)로 한국 장소 발굴 |
| `fetch_page` | 페이지 본문 텍스트 추출(HTML/스크립트 제거) |

## 설치

Smithery로 설치:

```bash
npx -y @smithery/cli install serper-discover --client claude
```

또는 Docker로 수동 설정.

## 필요 키 · 환경변수

| 환경변수 | 발급처 | 필수 |
|---------|--------|------|
| `SERPER_API_KEY` | [Serper](https://serper.dev) (월 2,500회 무료) | ✅ |

## 설정 예시

```json
{
  "mcpServers": {
    "serper-discover": {
      "command": "docker",
      "args": ["run", "-i", "--rm", "-e", "SERPER_API_KEY", "leeyseo/serper-discover-mcp"],
      "env": { "SERPER_API_KEY": "your-key-here" }
    }
  }
}
```

## 비고

- 라이선스 MIT.
- `discover_places`는 후보 장소를 반환하는 발굴 도구로, 권위 있는 소스로의 검증을 전제로 설계됨.

---
*수집일: 2026-07-03 · 출처: 저장소 README*
