# mcp-kr-legislation

> **[ChangooLee/mcp-kr-legislation](https://github.com/ChangooLee/mcp-kr-legislation)** · ⭐ 5 · Python · 최근 푸시 2026-04-28 · 카테고리: 📜 Legal & Government

한국 법제처 OPEN API를 통합한 Model Context Protocol(MCP) 서버 — 191개 API 중 132개 도구 구현.

## 개요

법제처 OPEN API 191종 중 132개를 도구로 구현한 대규모 통합 서버다. 법령, 부가서비스, 행정규칙, 자치법규, 판례, 위원회결정문, 조약, 별표서식, 학칙공단, 법령용어, 맞춤형, 지식베이스, 특별행정심판, 중앙부처해석(30개 부처) 등 거의 모든 법률 정보 카테고리를 커버한다. FastMCP 기반이며 각 응답에 실제 API URL을 포함해 직접 검증이 가능하다.

## 제공 도구

README에 카테고리별 전체 목록(132개)이 표로 정리되어 있다. 주요 카테고리와 대표 도구:

| 카테고리 | 도구 수 | 대표 도구 |
|------|------|------|
| 법령 관련 | 45 | `search_law`, `search_english_law`, `search_effective_law`, `search_law_articles`, `get_law_summary`, `search_old_and_new_law`, `search_law_appendix` |
| 행정규칙/자치법규 | 8 | `search_administrative_rule`, `get_administrative_rule_detail`, `search_local_ordinance`, `search_linked_ordinance`, `get_local_ordinance_detail` |
| 판례·위원회결정문·조약·해석 등 | 나머지 | 위원회결정문·조약·별표서식·법령용어·중앙부처해석(30개 부처) 등 |

전체 도구명·테스트 질문은 저장소 README "지원 도구 전체 목록(카테고리별)" 섹션 참조.

## 설치

```bash
git clone https://github.com/ChangooLee/mcp-kr-legislation.git
cd mcp-kr-legislation
# 방법 1: uv
uv pip install -e .
# 방법 2: pip (Python 3.10+)
python3.10 -m venv .venv
pip install -e .
```

## 필요 키 · 환경변수

| 환경변수 | 발급처 | 필수 |
|---------|--------|------|
| `LEGISLATION_API_KEY` | [법제처 OPEN API](https://open.law.go.kr) — 본인 이메일 주소(OC) 입력 | ✅ |
| `LEGISLATION_SEARCH_URL` / `LEGISLATION_SERVICE_URL` | 기본값 사용 권장 | ❌ |

## 설정 예시

```bash
# .env
LEGISLATION_API_KEY=your_email@example.com
LEGISLATION_SEARCH_URL=http://www.law.go.kr/DRF/lawSearch.do
LEGISLATION_SERVICE_URL=http://www.law.go.kr/DRF/lawService.do
```

## 비고

- Python 3.10 이상 필수. 라이선스는 GitHub상 "Other(NOASSERTION)"로 표기.
- 도구 수가 132개로 매우 많아 컨텍스트 소비가 클 수 있음 — 클라이언트에 따라 필요한 카테고리만 선택 사용 권장.

---
*수집일: 2026-07-02 · 출처: 저장소 README*
