# korea-law-mcp-public

> **[seunghan91/korea-law-mcp-public](https://github.com/seunghan91/korea-law-mcp-public)** · ⭐ 2 · TypeScript · 최근 푸시 2026-04-16 · 카테고리: 📜 Legal & Government

한국 법령·판례·자치법규를 하이브리드 검색(BM25 + 벡터)으로 조회하는 MCP 서버 (Korea Law Hub 오픈 코어).

## 개요

**Korea Law Hub**의 MIT 공개 코어로, 법제처·국회·대법원 공공 법률 데이터를 AI-ready 형태로 노출하는 오픈 데이터 허브다. 법제처 Open API + Elasticsearch 하이브리드 검색(BM25 nori 형태소 + 법률 동의어 120+ 사용자 사전 + Dense Vector 1024dim bbq_hnsw + RRF fusion) + BGE-M3 임베딩 기반 RAG 도구를 제공한다. 자치법규를 조문·별표 단위로 구조화 저장해 "제N조 제M항" 수준의 정확한 인용을 지원하며, 내부망(폐쇄망) 로컬 LLM 환경에서의 법률 자문·심사를 겨냥한 설계다. 전국 17개 광역 + 243개 기초 지자체 조례·규칙을 커버.

## 제공 도구

| 도구 | 기능 |
|------|------|
| `search_across_laws` | 국가법령 통합 검색 |
| `search_ordinances` | 자치법규(조례·규칙) 검색 |
| `search_precedents` | 판례 검색 |
| `search_constitutional_decisions` | 헌법재판소 결정 검색 |
| `search_legal_interpretations` | 법령해석례 검색 |
| `get_law_text` | 법령 본문 조회 |
| `get_ordinance_text` | 자치법규 본문 조회 |
| `get_ordinance_article` | 자치법규 조문 단위 조회 |
| `list_municipalities` | 지자체 목록 조회 |
| `compare_ordinances_across_municipalities` | 지자체 간 조례 비교 |
| `verify_case_exists` | 판례 실존 검증 |
| `chain_full_research` | 다단계 통합 리서치 chain |
| `chain_ordinance_compare` | 조례 비교 chain |

## 설치

```bash
# pnpm 9+ 모노레포
pnpm install
pnpm build
pnpm dev:mcp
# 샘플 동기화 예: pnpm sync:ordinances --municipality 노원구 --limit 5
```

## 필요 키 · 환경변수

| 환경변수 | 발급처 | 필수 |
|---------|--------|------|
| 법제처 OC | [open.law.go.kr](https://open.law.go.kr) | ✅ |
| Elasticsearch 엔드포인트 | 자체 ES 인스턴스(`ordinances_v1` 하이브리드 인덱스) | ✅(자치법규 검색) |

(구체 변수명은 저장소 `.env` 예시 참조 — README 기반 구성)

## 설정 예시

```
# pnpm dev:mcp 로 stdio MCP 서버 기동 후 클라이언트에 연결 (README 기반 구성)
```

## 비고

- MIT 라이선스. Node.js 22+, pnpm workspace 모노레포. 리포명은 레거시(`korea-law-mcp-public`)이나 브랜드는 Korea Law Hub로 통일 중.
- 본 리포는 `seunghan91/law` 모노레포의 공개 가능 부분(Core Adapter + Engine `korea-law`)만 발췌·sanitize한 코어. Hosted Gateway(`law-check.com/api/mcp`)는 별도 SaaS 래퍼.
- 성문법(civil law) 국가 구조를 인덱스에 인코딩해 로컬 LLM으로도 조문 단위 근거 제시를 지향.

---
*수집일: 2026-07-02 · 출처: 저장소 README*
