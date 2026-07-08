# korean-law-mcp

> **[chrisryugj/korean-law-mcp](https://github.com/chrisryugj/korean-law-mcp)** · ⭐ 2152 · TypeScript · 최근 푸시 2026-07-07 · 카테고리: 📜 Legal & Government

법제처 국가법령정보 MCP — 법령·판례·조례 조회부터 인용 환각 검증까지 · Korean law MCP for LLMs

## 개요

법제처 Open API 42종을 소수의 상위 도구로 감싼 MCP 서버 겸 CLI다. 법령·판례·행정규칙·자치법규·조약·해석례(국세청 포함) 조회에 더해, LLM 환각 방지용 인용 검증(조문 실존 + 제목 내용 대조), 조문 영향 그래프, 시점 비교 자동 diff, 판례 생사 확인(Citator), 행위시법 판단, 조례 정비 레이더 같은 고급 분석 기능을 제공한다. Claude Desktop·Cursor·Windsurf·Zed·Claude.ai 등에서 바로 사용할 수 있다.

## 제공 도구

노출 도구를 통폐합(v4.4.0 기준 9개)하고, 세부 기능은 `discover_tools` → `execute_tool` 메타 패턴으로 필요할 때만 접근하는 구조다. README에서 확인된 주요 도구:

| 도구 | 기능 |
|------|------|
| `search_law` | 법령 검색 (시행예정·제명변경 감지 포함) |
| `get_law_text` | 법령 조문 본문 조회 |
| `search_decisions` | 판례·헌재·조세심판·공정위 등 17개 도메인 결정례 검색(`domain` 파라미터) |
| `get_decision_text` | 결정례 본문 조회(`domain` 파라미터) |
| `get_ordinance` | 자치법규(조례) 조회 |
| `get_annexes` | 별표·서식 조회 |
| `get_article_history` | 조문 개정 이력 조회 |
| `get_law_system_tree` | 법령 체계도 조회 |
| `legal_research` | 다단계 리서치 통합(`task`: full_research·law_system·action_basis·dispute_prep·amendment_track·ordinance_compare·procedure_detail·document_review) |
| `legal_analysis` | 킬러기능 통합(`mode`: verify_citations·cite_check·applicable_law·impact_map) |
| `ordinance_radar` | 조례 근거 상위법 개정 대조·정비 레이더 |
| `discover_tools` / `execute_tool` | 미노출 전문 도구 탐색·실행 메타 도구 |

## 설치

```bash
# npm 배포판 직접 실행
npx korean-law-mcp@latest
```

원격 HTTP 방식도 지원한다: `https://mcp.gomdori.app/law?oc=<인증키>`

## 필요 키 · 환경변수

| 환경변수 | 발급처 | 필수 |
|---------|--------|------|
| `OC` (인증키) | [국가법령정보센터 Open API](https://open.law.go.kr) | ✅ |

## 설정 예시

```json
{
  "mcpServers": {
    "korean-law": {
      "command": "npx",
      "args": ["-y", "mcp-remote", "https://mcp.gomdori.app/law?oc=honggildong"]
    }
  }
}
```

원격 HTTP 지원 클라이언트(Cursor, Windsurf 등)는 `{"url": "https://mcp.gomdori.app/law?oc=honggildong"}` 형태로 설정한다. `honggildong`을 본인 인증키(OC)로 교체한다.

## 비고

- MIT 라이선스, 활발히 유지보수 중(별점 2천 이상). 도구 수를 기능 수와 분리해 컨텍스트 소비를 줄이는 통폐합 설계가 특징.
- 클라우드 IP에서 법제처 안티봇(JS 리다이렉트) 자동 우회 로직 내장.

---
*수집일: 2026-07-02 · 출처: 저장소 README*
