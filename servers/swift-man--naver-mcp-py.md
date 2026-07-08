# naver-mcp-py

> **[swift-man/naver-mcp-py](https://github.com/swift-man/naver-mcp-py)** · ⭐ 0 · Python · 최근 푸시 2026-03-18 · 카테고리: 🔎 Search & Trends

네이버 검색 API 15+ 도구와 데이터랩 트렌드 분석 10개 도구를 제공하는 Python FastMCP 서버입니다.

## 개요

네이버 오픈 검색 API와 데이터랩을 MCP 도구로 노출하는 Python FastMCP 서버이자 재사용 가능한 클라이언트 라이브러리다. 표준 라이브러리 HTTP 스택을 사용하며 Python 3.9+ Linux 서버에서 돌아가도록 설계됐다. 재시도·타임아웃·캐시·검증, HTML 태그 제거와 정규화된 응답 스키마를 저장소 안에서 처리한다. MCP 서버 모드와 직접 Python 라이브러리 모드를 모두 지원한다.

## 제공 도구

검색 도구 (15개):

| 도구 | 도구 |
|------|------|
| `search_local` | `search_blog` |
| `search_web` | `search_news` |
| `search_cafearticle` | `search_image` |
| `search_book` | `search_book_advanced` |
| `search_encyc` | `search_kin` |
| `search_shop` | `search_doc` |
| `spell_check` | `detect_adult_query` |
| `search_naver_auto` | |

데이터랩 도구 (10개):

| 도구 | 도구 |
|------|------|
| `datalab_search_trends` | `datalab_shopping_category_trends` |
| `datalab_shopping_category_device_trends` | `datalab_shopping_category_gender_trends` |
| `datalab_shopping_category_age_trends` | `datalab_shopping_keyword_trends` |
| `datalab_shopping_keyword_device_trends` | `datalab_shopping_keyword_gender_trends` |
| `datalab_shopping_keyword_age_trends` | `datalab_shopping_device_trends` |

`datalab_shopping_device_trends`는 `datalab_shopping_category_device_trends`의 하위 호환 별칭이다.

## 설치

```bash
python3 -m venv .venv && source .venv/bin/activate
pip install -U pip
pip install -e ".[server]"
python3 -m naver_mcp.server
```

## 필요 키 · 환경변수

| 환경변수 | 발급처 | 필수 |
|---------|--------|------|
| `NAVER_CLIENT_ID` | [네이버 개발자센터](https://developers.naver.com) | ✅ |
| `NAVER_CLIENT_SECRET` | 네이버 개발자센터 | ✅ |
| `NAVER_MCP_HOST` / `NAVER_MCP_PORT` / `NAVER_MCP_PATH` / `NAVER_MCP_TRANSPORT` | 서버 바인딩·전송 설정 (기본 127.0.0.1:8100/mcp, streamable-http) | ⬜ |
| `NAVER_HTTP_TIMEOUT_SEC` / `NAVER_CACHE_TTL_SEC` | 타임아웃·캐시 TTL | ⬜ |

## 설정 예시

streamable-http 전송으로 서버를 띄운 뒤 `http://127.0.0.1:8100/mcp`로 접속한다 (README 기반 구성). 환경변수는 셸 export 또는 `systemd EnvironmentFile`로 주입한다.

```bash
export NAVER_CLIENT_ID="your_client_id"
export NAVER_CLIENT_SECRET="your_client_secret"
export NAVER_MCP_TRANSPORT="streamable-http"
python3 -m naver_mcp.server
```

## 비고

- 현재 코드는 `.env`를 자동 로드하지 않는다 — 환경변수를 명시적으로 export하거나 프로세스 매니저로 주입해야 한다.
- Linux 서버 장기 실행에 최적화(systemd 배포 예시 제공). `healthz()` 헬퍼 노출.

---
*수집일: 2026-07-02 · 출처: 저장소 README*
