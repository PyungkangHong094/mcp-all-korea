# LexLink-ko-mcp

> **[rabqatab/LexLink-ko-mcp](https://github.com/rabqatab/LexLink-ko-mcp)** · ⭐ 1 · Python · 최근 푸시 2026-06-21 · 카테고리: 📜 Legal & Government

국가법령정보센터 Open API를 구조적으로 노출하고 시맨틱 검색(aiSearch)을 지원하는 MCP 서버.

## 개요

LexLink는 국가법령정보센터 Open API(open.law.go.kr)를 AI 에이전트·LLM 앱에 노출하는 MCP 서버로, **54개 도구 + 2개 리소스 + 9개 프롬프트**를 제공한다. 법령(시행일·공포일 기준)·영문법령·행정규칙·조문/항/호 조회, 법령-자치법규 연계, 위임법령에 더해 판례·헌재결정례·법령해석례·행정심판례(Phase 3), 조문 인용 추출(Phase 4), AI 시맨틱 검색 aiSearch·관련법령 발견(Phase 5), 다단계 리서치 chain 도구(Phase 9)까지 단계적으로 구현했다. korean-law-mcp에서 영감받은 지능형 캐싱·법령 약칭 자동 해소(52개 시드 별칭 + 동적 학습) 기능 포함. 카카오 PlayMCP 3위 수상.

## 제공 도구

54개 전체는 저장소 README에 Phase별로 정리되어 있다. Phase 1(핵심 법령 6개) 확인된 도구:

| 도구 | 기능 |
|------|------|
| `eflaw_search` | 시행일 기준 법령 검색 |
| `law_search` | 공포일 기준 법령 검색 |
| `eflaw_service` | 시행일 기준 법령 본문/조문 조회(`jo` 파라미터 권장) |
| `law_service` | 공포일 기준 법령 본문/조문 조회 |

Phase 2~9: 영문법령, 행정규칙, 법령-자치법규 연계, 위임법령, 판례·헌재·해석례·행정심판례, 조문 인용 추출, aiSearch 시맨틱 검색·관련법령, chain 리서치 도구 등. 리소스 2종(Law ID 캐시: 정적 1 + 템플릿 `lexlink://law/{name}` 1).

## 설치

```bash
uv sync
```

## 필요 키 · 환경변수

| 환경변수 | 발급처 | 필수 |
|---------|--------|------|
| `OC` | [open.law.go.kr](https://open.law.go.kr) — OC identifier | ✅ |

## 설정 예시

```bash
# stdio transport (Claude Code, Cursor 등)
OC=your_oc uv run stdio

# HTTP transport (Kakao PlayMCP)
OC=your_oc TRANSPORT=http uv run serve
```

각 도구 호출 시 `oc` 인자로 개별 오버라이드도 가능하다.

## 비고

- 라이선스 미표기. Python 3.10+. Smithery 배포 지원. API 커버리지 ~28%(191+ 엔드포인트 중 54개 도구), v2.1.0.
- 응답 포맷 JSON(기본)/HTML/XML 선택 가능.

---
*수집일: 2026-07-02 · 출처: 저장소 README*
