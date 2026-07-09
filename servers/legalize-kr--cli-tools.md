# cli-tools

> **[legalize-kr/cli-tools](https://github.com/legalize-kr/cli-tools)** · ⭐ N/A (GitHub API 제한) · Python · 최근 푸시 N/A · 카테고리: 📜 Legal & Government

GitHub REST API로 미러링된 한국 법령·판례·행정규칙·자치법규를 클론·인증 없이 조회하는 CLI 겸 로컬 stdio MCP 서버(legalize-mcp)입니다.

## 개요

legalize-kr 미러 저장소(법령·판례·행정규칙·자치법규)를 GitHub REST API로 직접 조회하는 도구다. `legalize` CLI와, MCP 지원 클라이언트에 등록 가능한 로컬 stdio MCP 서버 `legalize-mcp`를 함께 제공한다(`mcp` extra 필요). LLM/에이전트 소비를 위한 `--json` 출력, 시점 기준 조회(`--date`), 두 시점 비교(diff), 오프라인 캐시 조회를 지원한다. GitHub 토큰 없이도 동작하나(시간당 60회), 토큰 사용 시 5,000회로 늘어난다.

## 제공 도구

MCP 서버(`legalize-mcp`)가 제공하는 Tool:

| 도구 | 기능 |
|------|------|
| `laws_list` | 법령 목록 조회 (카테고리·페이지 필터) |
| `laws_get` | 법령 전문 조회 (날짜 기준) |
| `laws_article` | 특정 조문 조회 (제839조 등) |
| `search` | 법령·판례·행정규칙·자치법규 키워드 검색 |
| `precedents_list` | 판례 목록 조회 (법원·사건종류 필터) |
| `precedents_get` | 판례 전문 조회 (사건번호·판례일련번호) |
| `admrules_list` | 행정규칙 목록 조회 (종류·기관 필터) |
| `admrules_get` | 행정규칙 전문 조회 |
| `ordinances_list` | 자치법규 목록 조회 (종류·지자체 필터) |
| `ordinances_get` | 자치법규 전문 조회 |

## 설치

```bash
# MCP 서버 설치 없이 실행
uvx --from legalize-cli[mcp] legalize-mcp

# 또는 설치
pipx install 'legalize-cli[mcp]'
legalize-mcp
```

- 요구사항: Python 3.10+

## 필요 키 · 환경변수

| 환경변수 | 발급처 | 필수 |
|---------|--------|------|
| `GITHUB_TOKEN` | [GitHub PAT](https://github.com/settings/tokens) (`public_repo` 스코프) | 선택(Rate limit 완화) |

> 토큰 없이도 동작하나 시간당 60회 제한이 있으며, 토큰 사용 시 5,000회로 늘어난다.

## 설정 예시

```json
{
  "mcpServers": {
    "legalize-kr": {
      "command": "uvx",
      "args": ["--from", "legalize-cli[mcp]", "legalize-mcp"],
      "env": {
        "GITHUB_TOKEN": "ghp_xxxxxxxxxxxxxxxxxxxx"
      }
    }
  }
}
```

## 비고

- 라이선스: 법령 텍스트는 공개 도메인(정부 저작물), 도구 자체는 MIT.
- 미러 저장소는 이력 재구성으로 force-push될 수 있어, 캐시는 커밋 SHA가 아닌 `(path, author_date)` 기준으로 무효화한다.
- AI Agent 스킬/플러그인은 별도 저장소 [legalize-kr/agent-skills](https://github.com/legalize-kr/agent-skills)에서 제공된다.

---
*수집일: 2026-07-03 · 출처: 저장소 README*
