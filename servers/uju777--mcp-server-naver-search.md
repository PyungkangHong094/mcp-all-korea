# mcp-server-naver-search

> **[uju777/mcp-server-naver-search](https://github.com/uju777/mcp-server-naver-search)** · ⭐ N/A · Python · 최근 푸시 N/A · 카테고리: 🔎 Search & Trends

네이버 검색 API로 쇼핑 최저가·카페 후기·실시간 뉴스·블로그를 조회하는 MCP 서버입니다.

## 개요

Brave/Google이 잘 못 가져오는 한국 로컬 정보(가격, 카페 글, 뉴스)를 네이버 검색 DB로 보완하기 위한 브리지. Python 3.10+ 기반으로 `uv`와 `mcp[cli]`·`httpx`·`python-dotenv`를 사용해 실행한다. 단일 도구 `search_naver`에 `category` 파라미터(blog/shopping/cafe/news 등)로 검색 대상을 전환한다.

## 제공 도구

| 도구 | 기능 |
|------|------|
| `search_naver` | 네이버 통합 검색. `query`, `category`(blog/shopping/cafe/news 등), `display` 파라미터로 쇼핑 최저가·카페 후기·뉴스·블로그를 조회 |

(도구 목록 출처: `server.py` 소스 — `@mcp.tool` `search_naver` 확인)

## 설치

```bash
git clone https://github.com/uju777/mcp-server-naver-search.git
# uv 로 실행 (아래 설정 예시 참고)
```

## 필요 키 · 환경변수

| 환경변수 | 발급처 | 필수 |
|---------|--------|------|
| `NAVER_CLIENT_ID` | [네이버 개발자센터](https://developers.naver.com/apps/#/register) | ✅ |
| `NAVER_CLIENT_SECRET` | [네이버 개발자센터](https://developers.naver.com/apps/#/register) | ✅ |

무료 한도 25,000 req/일.

## 설정 예시

```json
{
  "mcpServers": {
    "naver-search": {
      "command": "uv",
      "args": [
        "run", "--with", "mcp[cli]", "--with", "httpx", "--with", "python-dotenv",
        "/YOUR/PATH/TO/mcp-server-naver-search/server.py"
      ],
      "env": {
        "NAVER_CLIENT_ID": "YOUR_ID",
        "NAVER_CLIENT_SECRET": "YOUR_SECRET"
      }
    }
  }
}
```

## 비고

MIT License. Claude Desktop·Claude Code(CLI)·Cursor 설정 예시가 README에 제공됨. Claude Code는 `sh -c` + PATH export가 필요.

---
*수집일: 2026-07-02 · 출처: 저장소 README, 소스 코드(server.py)*
