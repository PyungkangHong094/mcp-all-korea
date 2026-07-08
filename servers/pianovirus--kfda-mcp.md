# kfda-mcp

> **[pianovirus/kfda-mcp](https://github.com/pianovirus/kfda-mcp)** · ⭐ - · Python · 카테고리: 📊 Public Data

식약처(MFDS) 공공 OpenAPI로 의약품 검색·병용금기(DUR) 확인·건강기능식품 조회를 제공하는 MCP 서버.

## 개요

한국 의료 AI 생태계를 위한 식약처 OpenAPI MCP 서버로, LLM 에이전트가 의약품 마스터, DUR(의약품 안전사용서비스) 규칙, 건강기능식품 DB를 표준 MCP 프로토콜로 질의할 수 있다. 와파린+자몽 병용 확인 같은 다단계 안전성 판단을 도구 체이닝으로 수행한다. Zenodo DOI 발급.

## 제공 도구

| 도구 | 기능 | KFDA OpenAPI |
|------|------|--------------|
| `search_drug` | 의약품 마스터 검색(제품명·성분·제조사·ATC) | 의약품 제품 허가정보 |
| `check_dur_interaction` | 두 약물 병용금기·연령금기·임부금기 확인 | DUR 안전사용서비스 |
| `search_supplement` | 건강기능식품 인허가 검색 | 식품안전나라 건기식 |
| `get_drug_easy_info` | e약은요(환자용 쉬운 약물 정보) 조회 | e약은요 |
| `lookup_atc_code` | ATC 코드 → 약물군 분류 | 내장 매핑 |

## 설치

```bash
pip install kfda-mcp
# 또는 소스: git clone https://github.com/pianovirus/kfda-mcp && cd kfda-mcp && pip install -e .
kfda-mcp   # MCP 서버 실행
```

## 필요 키 · 환경변수

| 환경변수 | 발급처 | 필수 |
|---------|--------|------|
| `MFDS_API_KEY` | [공공데이터포털](https://www.data.go.kr) 식약처 OpenAPI | ✅ |

## 설정 예시

```json
{
  "mcpServers": {
    "kfda": {
      "command": "kfda-mcp",
      "env": { "MFDS_API_KEY": "your_api_key_here" }
    }
  }
}
```

## 비고

- Transport: stdio / SSE.
- 라이선스: MIT · Zenodo DOI 10.5281/zenodo.21063208.

---
*수집일: 2026-07-02 · 출처: 저장소 README*
