# korean-news-mcp

> **[SongT-50/korean-news-mcp](https://github.com/SongT-50/korean-news-mcp)** · ⭐ 0 · Python · 최근 푸시 2026-03-08 · 카테고리: 🔎 Search & Trends

네이버 RSS와 Google News 기반 한국 뉴스·글로벌 테크 뉴스를 API 키 없이 무료로 제공하는 MCP 서버입니다.

## 개요

한국 뉴스와 글로벌 AI/테크 뉴스를 API 키 없이 조회하는 FastMCP 기반 서버다. 한국 뉴스는 네이버 뉴스 RSS(8개 카테고리)와 Google News 한국판에서, 글로벌 테크 뉴스는 Hacker News·TechCrunch·The Verge·Ars Technica·GeekNews 등에서 가져온다. 카테고리별 조회, 키워드 검색, 실시간 트렌딩, 기사 본문 읽기, 종합 브리핑을 제공한다. `feedparser`로 RSS를, `beautifulsoup4`+`httpx`로 본문을 파싱한다.

## 제공 도구

| 도구 | 기능 |
|------|------|
| `korean_news` | 한국 뉴스 카테고리별 조회 (속보/정치/경제/사회/IT/세계/연예/스포츠) |
| `tech_news` | 글로벌 AI/테크 뉴스 (AI/Claude/OpenAI/MCP/스타트업/개발/클라우드) |
| `news_search` | 키워드 뉴스 검색 (한국어/영어) |
| `trending` | 실시간 트렌딩 뉴스 (한국/글로벌테크) |
| `read_article` | 기사 URL 본문 읽기 |
| `daily_briefing` | 종합 뉴스 브리핑 (한국 + AI + Claude) |

## 설치

```bash
git clone https://github.com/SongT-50/korean-news-mcp.git
cd korean-news-mcp
pip install -r requirements.txt
claude mcp add korean-news -- python server.py
```

원격 접속(설치 없이): Render 배포 서버를 streamable-http로 사용 가능.
```bash
claude mcp add korean-news --transport streamable-http https://korean-news-mcp.onrender.com/mcp
```

## 필요 키 · 환경변수

API 키 불필요 (공개 RSS·뉴스 소스만 사용).

## 설정 예시

```json
{
  "mcpServers": {
    "korean-news": {
      "command": "python",
      "args": ["/path/to/korean-news-mcp/server.py"]
    }
  }
}
```

## 비고

- 무료 Render 인스턴스는 비활성 시 슬립되어 첫 요청에 30~60초 걸릴 수 있음.
- 전송: stdio / streamable-http. 라이선스: MIT.

---
*수집일: 2026-07-02 · 출처: 저장소 README*
