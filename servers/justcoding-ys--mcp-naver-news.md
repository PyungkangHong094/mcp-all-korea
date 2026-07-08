# mcp-naver-news

> **[justcoding-ys/mcp-naver-news](https://github.com/justcoding-ys/mcp-naver-news)** · ⭐ 0 · (언어 미상) · 최근 푸시 2025-06-26 · 카테고리: 🔎 Search & Trends

네이버 뉴스 API로 뉴스 검색·정렬·필터링을 제공하는 MCP 서버입니다.

## 개요

네이버 뉴스 검색 API를 위한 MCP 서버다. 키워드로 뉴스 기사를 검색하고 날짜/관련도 정렬, 날짜 범위 필터링을 지원한다. 2단계 워크플로우를 권장한다: `search_news`로 기사 후보를 빠르게 리서치·필터링한 뒤, 심층 분석이 필요할 때만 `search_news_detail`로 실제 기사 본문을 추출한다.

## 제공 도구

| 도구 | 기능 |
|------|------|
| `search_news` | 네이버 뉴스 API 결과(제목·요약·링크) 빠른 반환. 본문 미추출 — 먼저 사용 |
| `search_news_detail` | 실제 기사 페이지에서 본문 추출 (정밀 분석용) |

`search_news` 파라미터: `query`(검색 키워드), `display`(표시 결과 수) 등.

## 설치

```bash
git clone https://github.com/ChangooLee/mcp-naver-news.git
cd mcp-naver-news
python3.10 -m venv .venv
source .venv/bin/activate
python3 -m pip install --upgrade pip
pip install -e .
```

Python 3.10 이상 필수.

## 필요 키 · 환경변수

| 환경변수 | 발급처 | 필수 |
|---------|--------|------|
| `X_NAVER_CLIENT_ID` | [네이버 개발자센터](https://developers.naver.com/) (뉴스 검색 API) | ✅ |
| `X_NAVER_CLIENT_SECRET` | 네이버 개발자센터 | ✅ |
| `MCP_SERVER_NAME` / `MCP_HOST` / `MCP_PORT` / `TRANSPORT` / `LOG_LEVEL` | 서버 설정 (기본: mcp-naver-news / 0.0.0.0 / 8000 / stdio / INFO) | ⬜ |

## 설정 예시

```json
{
  "mcpServers": {
    "mcp-naver-news": {
      "command": "YOUR_LOCATION/.venv/bin/mcp-naver-news",
      "env": {
        "X_NAVER_CLIENT_ID": "YOUR_CLIENT_ID",
        "X_NAVER_CLIENT_SECRET": "YOUR_CLIENT_SECRET",
        "MCP_SERVER_NAME": "mcp-naver-news",
        "MCP_HOST": "0.0.0.0",
        "MCP_PORT": "8000",
        "TRANSPORT": "stdio",
        "LOG_LEVEL": "INFO"
      }
    }
  }
}
```

## 비고

- 이 저장소는 `ChangooLee/mcp-naver-news`의 포크로, README의 배지·클론 URL·PyPI 패키지(`mcp-naver-news`)가 모두 원본을 가리킨다.
- 환경변수 접두사가 `X_NAVER_`로 일반 네이버 MCP와 다르니 주의.

---
*수집일: 2026-07-02 · 출처: 저장소 README*
