# korean-law-mcp

> **[SeoNaRu/korean-law-mcp](https://github.com/SeoNaRu/korean-law-mcp)** · ⭐ 67 · Python · 최근 푸시 2026-01-20 · 카테고리: 📜 Legal & Government

국가법령정보센터 Open API로 한국 법령·판례·행정규칙 검색을 제공하는 고성능 MCP 서버.

## 개요

국가법령정보센터 Open API를 활용해 AI 에이전트(Claude Desktop, Cursor 등)가 한국 법령·판례·행정규칙을 실시간 검색·조회할 수 있게 하는 FastMCP 기반 서버다. 법령 키워드 검색·상세 조회, 판례 검색(법원 필터링·판결요지·참조조문 포함), 행정규칙 검색을 지원하며, cachetools 기반 24시간 전략적 캐싱으로 API 호출을 최소화한다. Pydantic 검증 + asyncio 비동기 처리.

## 제공 도구

| 도구 | 기능 |
|------|------|
| `health` | 서비스 상태 및 API 키 설정 확인 |
| `search_law_tool` | 법령 키워드 검색 (법령명·소관부처·공포일자·시행일자) |
| `get_law_detail_tool` | 특정 법령 상세 정보 및 전문(조문) 조회 |
| `search_precedent_tool` | 판례 키워드 검색 (법원 필터 지원) |
| `get_precedent_detail_tool` | 판례 상세 조회 (판결요지·판시사항·전문) |
| `search_administrative_rule_tool` | 행정규칙 검색 (소관부처·제정/시행일자) |

## 설치

```bash
pip install -r requirements.txt   # 또는 uv sync
python -m src.law_main
```

Docker 실행도 지원:

```bash
docker build -t korean-law-mcp:latest .
docker run --rm -e LAW_API_KEY=your_key -p 8096:8096 korean-law-mcp:latest
```

## 필요 키 · 환경변수

| 환경변수 | 발급처 | 필수 |
|---------|--------|------|
| `LAW_API_KEY` | [국가법령정보센터 Open API](https://open.law.go.kr) — 인증키(OC) | ✅ |
| `LOG_LEVEL` / `PORT` | 기본값 INFO / 8096 | ❌ |

## 설정 예시

```env
# .env (env.law.example 복사)
LAW_API_KEY=your_law_api_key_here
LOG_LEVEL=INFO
PORT=8096
```

## 비고

- 라이선스 미표기. HTTP 서버(포트 8096) 방식으로도 구동 가능.
- 배치 내 Python 법령 서버 중 별점이 높은 편(67).

---
*수집일: 2026-07-02 · 출처: 저장소 README*
