# korean-rnd-regs-mcp

> **[smilemin07/korean-rnd-regs-mcp](https://github.com/smilemin07/korean-rnd-regs-mcp)** · ⭐ 4 · Python · 최근 푸시 2026-07-07 · 카테고리: 📜 Legal & Government

연구행정 규정 검토용 MCP 서버. 국가법령정보센터 OpenAPI로 국가 R&D 관련 규정을 검색·검토한다.

## 개요

국가법령정보센터([open.law.go.kr](https://open.law.go.kr)) OpenAPI를 활용해 국가 R&D 관련 규정(혁신법·성과평가법 등 법률 > 시행령 > 시행규칙 > 행정규칙 위계)을 조회하고, 특정 사례에 대한 다층적 규정 검토를 지원한다. AI가 검토에 필요한 조문을 자동으로 식별·인용하도록 설계됐으며, 규정에 명시되지 않은 해석·추측을 배제하는 검토 프롬프트를 내장한다. 산업기술·중소기업·보건의료·학술진흥·산학협력·연구산업 등 부문별 R&D 특별법 family를 포함한 52개 규정을 다룬다.

## 제공 도구

| 도구 | 기능 |
|------|------|
| `health` | 서버 상태 점검 (status=ok 확인) |
| `search_provision` | 규정 조문 검색 |
| `suggest_review_sources` | 검토 상황에 필요한 규정 조문 후보 제안 (검색 키워드 배열 입력) |
| `get_provision_detail` | 조문·별표 상세 원문 조회 |
| `list_rule_sets` | 지원 규정 세트 목록 조회 |

## 설치

원격(권장) — Claude Code 플러그인 마켓플레이스:

```
/plugin marketplace add smilemin07/korean-rnd-regs-mcp
/plugin install korean-rnd-regs@korean-rnd-regs-marketplace
/reload-plugins
```

또는 원격 MCP URL 직접 등록(oc 파라미터에 API 키 삽입):

```
https://mcp.rndmanagers.org/mcp?oc=<국가법령정보센터_API키>
```

로컬 실행은 `uv` 필요. PyPI 패키지 `korean-rnd-regs-mcp`로 배포된다.

## 필요 키 · 환경변수

| 환경변수 | 발급처 | 필수 |
|---------|--------|------|
| `LAW_API_KEY` | [국가법령정보센터](https://open.law.go.kr) 마이페이지 → API 신청 → "법령" 카테고리 (OC 인증값) | ✅ |

## 설정 예시

```json
{
  "mcpServers": {
    "korean-rnd-regs": {
      "url": "https://mcp.rndmanagers.org/mcp?oc=<국가법령정보센터_API키>"
    }
  }
}
```

## 비고

- 국가법령정보센터 "법령" 카테고리 API 신청 후 '승인' 대기가 필요하다.
- 조문 원문은 `get_provision_detail` 반환 content로만 인용하도록 설계됐다(외부 웹 열람으로 대체 금지).
- 클로드 사용 시 Sonnet 4.6 이상, Effort High 이상 권장(README).

---
*수집일: 2026-07-02 · 출처: 저장소 README, 소스 코드(src/korean_rnd_regs_mcp/main.py)*
