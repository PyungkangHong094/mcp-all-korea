# lawtutor-mcp

> **[seung23/lawtutor-mcp](https://github.com/seung23/lawtutor-mcp)** · ⭐ 0 · Python · 최근 푸시 2026-05-17 · 카테고리: 📜 Legal & Government

한국 7급 공무원시험(행정직) 행정법·헌법 학습용 RAG MCP 서버.

## 개요

국가법령정보센터 OPEN API에서 수집한 94만여 건(법령 조문 240,695 · 대법원 판례 579,012 · 헌재결정례 99,394 · 법령해석례 26,839)을 벡터 DB에 인덱싱한 RAG MCP 서버다. BGE-M3 dense(1024차원) + sparse 벡터를 RRF로 융합한 하이브리드 검색에 동의어 확장·N-gram 타이틀 부스트 리랭킹을 적용해 6개 도구를 제공한다. 단일 소스(국가법령정보센터) 기반 RAG로 존재하지 않는 조문·판례 생성을 막는 것이 핵심. 집 PC + Docker + Cloudflare Tunnel 셀프호스팅 구조.

## 제공 도구

| 도구 | 기능 |
|------|------|
| `search_law` | 법령 조문 검색 (하이브리드 검색 + 리랭킹) |
| `search_precedent` | 대법원 판례 검색 (기본 필터: 대법원) |
| `search_constitutional_decision` | 헌법재판소 결정례 검색 |
| `search_legal_interpretation` | 법제처·행안부 유권해석례 검색 |
| `fetch_article_by_number` | 법령명 + 조문번호로 정확한 조문 조회 |
| `fetch_case_by_number` | 사건번호로 판례·결정례 조회 |

모든 도구는 DB 미스 시 국가법령정보센터 API 실시간 폴백을 지원한다.

## 설치

```bash
git clone https://github.com/seung23/lawtutor-mcp.git
cd lawtutor-mcp
cp .env.example .env   # 값 채우기
uv sync
docker compose up -d
```

Python 3.11+, uv, Docker Desktop/Engine 필요.

## 필요 키 · 환경변수

| 환경변수 | 발급처 | 필수 |
|---------|--------|------|
| 국가법령정보센터 OC | [open.law.go.kr](https://open.law.go.kr) | ✅ |

(구체 변수명은 `.env.example` 참조 — README에 명시된 것은 국가법령정보센터 OPEN API OC)

## 설정 예시

```
# MCP Python SDK Streamable HTTP transport로 서버 기동 후
# Claude.ai 등 MCP 클라이언트에서 HTTP 엔드포인트 연결 (README 기반 구성)
```

## 비고

- 라이선스 미표기. Qdrant 벡터 DB + BGE-M3 임베딩 + FastAPI/uvicorn 스택.
- 검증 평가셋(102건) 기준 법령 검색 Recall@5 0.90, 정확 조회 1.00. 판례 의미검색은 대규모 컬렉션 특성상 Recall이 낮음(0.45/0.36).

---
*수집일: 2026-07-02 · 출처: 저장소 README*
