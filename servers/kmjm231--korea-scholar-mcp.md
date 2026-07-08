# korea-scholar-mcp

> **[kmjm231/korea-scholar-mcp](https://github.com/kmjm231/korea-scholar-mcp)** · ⭐ N/A · Python · 최근 푸시 N/A · 카테고리: 🧩 Miscellaneous

한국 학술지 논문을 검색하고 상세 정보를 조회하는 MCP 서버.

## 개요

FastAPI(SSE 방식) 기반 한국 학술 정보 MCP 서버로, 키워드(제목·저자·키워드)로 논문을 검색하고 특정 논문의 상세 정보(초록 원문 포함)를 조회한다. 최근 3년/5년 연도 필터, KCI 등재 여부 필터, 인용순 정렬을 지원한다. 서버는 기본 `http://localhost:8000`에서 SSE(`/sse`)로 통신한다.

## 제공 도구

| 도구 | 기능 |
|------|------|
| `search_papers` | 논문 검색 (query 필수, journal·keyword·date_from·date_to 선택) |
| `get_paper_detail` | 논문 상세 정보 조회 (article_id 필수, 초록 포함) |

## 설치

uv 기반 소스 구동.

```bash
# uv 설치 후
uv sync

# 실행
uv run uvicorn korea_scholar_mcp.main:app --reload --host 0.0.0.0 --port 8000
# 또는
uv run python -m korea_scholar_mcp.main
```

## 필요 키 · 환경변수

README에 API 키·환경변수 명시 없음. 현재 실제 KCI API 미연동 상태(모의 데이터 사용)로 외부 키가 필요 없다.

## 설정 예시

SSE 방식 원격 서버로, 로컬 실행 후 SSE 엔드포인트에 연결한다.

```json
{
  "mcpServers": {
    "korea-scholar": {
      "url": "http://localhost:8000/sse"
    }
  }
}
```
(README 기반 구성)

## 비고

- 도구 목록은 README에 명시(2개, 확인됨).
- **주의**: README TODO에 따르면 현재 실제 KCI API 미연동 — 모의 데이터를 사용하는 초기 단계.
- 엔드포인트: `GET /`(서버 정보), `POST /messages`, `GET /sse`.

---
*수집일: 2026-07-02 · 출처: 저장소 README*
