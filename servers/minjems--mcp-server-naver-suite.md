# mcp-server-naver-suite

> **[minjems/mcp-server-naver-suite](https://github.com/minjems/mcp-server-naver-suite)** · ⭐ 0 · TypeScript · 최근 푸시 2026-04-12 · 카테고리: 🔎 Search & Trends

네이버 검색·파파고 번역·지도 지오코딩을 하나로 통합한 올인원 네이버 API MCP 서버입니다.

## 개요

Claude 등 AI 어시스턴트용 올인원 네이버 API MCP 서버(TypeScript)다. 네이버 검색(웹·뉴스·블로그·쇼핑) 4종, 파파고 번역·언어감지 2종, 지도 지오코딩·역지오코딩 2종을 합쳐 총 10개 도구를 제공한다. npx로 바로 실행할 수 있다.

## 제공 도구

| 도구 | 기능 |
|------|------|
| `naver-web-search` | 한국어 웹 검색 |
| `naver-news-search` | 뉴스 검색 (날짜 정렬) |
| `naver-blog-search` | 블로그 글 검색 |
| `naver-shopping-search` | 쇼핑 상품·가격 검색 |
| `papago-translate` | 텍스트 번역 (13개 언어) |
| `papago-detect-language` | 언어 감지 |
| `naver-geocode` | 주소 → 좌표 |
| `naver-reverse-geocode` | 좌표 → 주소 |

## 설치

```bash
npx -y mcp-server-naver-suite
```

## 필요 키 · 환경변수

| 환경변수 | 발급처 | 필수 |
|---------|--------|------|
| `NAVER_CLIENT_ID` | [네이버 개발자센터](https://developers.naver.com/apps/) (검색·파파고·지도 활성화) | ✅ |
| `NAVER_CLIENT_SECRET` | 네이버 개발자센터 | ✅ |

## 설정 예시

```json
{
  "mcpServers": {
    "naver": {
      "command": "npx",
      "args": ["-y", "mcp-server-naver-suite"],
      "env": {
        "NAVER_CLIENT_ID": "YOUR_CLIENT_ID",
        "NAVER_CLIENT_SECRET": "YOUR_CLIENT_SECRET"
      }
    }
  }
}
```

## 비고

- 무료 한도: 검색 25,000건/일, 파파고 10,000자/일, 지도 30,000건/월.
- 애플리케이션 등록 시 검색·파파고 번역·지도(지오코딩) 3개 API를 모두 활성화해야 한다. 라이선스: MIT.
- README 제목은 "10 tools"로 표기하나 표에는 8개만 명시되어 위 목록은 표에 명시된 8개만 기재.

---
*수집일: 2026-07-02 · 출처: 저장소 README*
