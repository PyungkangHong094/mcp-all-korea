---
name: mcp-server-profiling
description: MCP 서버 GitHub 저장소 1개를 프로파일링하는 표준 절차. 도구 목록·설치 방법·필요 API 키·설정 예시 추출, 서버 상세 문서(servers/*.md) 생성, JSON 레코드 작성 시 반드시 사용. "서버 상세 문서 만들어", "이 MCP 저장소 분석해", "프로파일 갱신해" 요청 및 mcp-profiler/mcp-catalog-qa 에이전트 작업 시 트리거.
---

# MCP 서버 프로파일링

MCP 서버 저장소 1개를 방문해 표준 상세 문서를 만드는 절차. 목표는 **사용자가 이 문서만 보고 해당 MCP를 설치·설정할 수 있는 수준**의 정보다.

## 수집 절차

### 1단계: 메타데이터 (GitHub API)

```bash
curl -s "https://api.github.com/repos/{owner}/{repo}" | python -c "
import json,sys; d=json.load(sys.stdin)
print(json.dumps({k: d.get(k) for k in ['full_name','description','stargazers_count','pushed_at','language','license','archived','fork']}, ensure_ascii=False))"
```

API rate limit(비인증 60회/시간)에 걸리면 이 단계는 건너뛰고 README에서 얻은 정보만 기록한다. 별점 없이도 문서는 성립한다.

### 2단계: README 원문

HTML 페이지 대신 raw를 우선 사용한다 (빠르고 rate limit 없음):

```bash
curl -sL "https://raw.githubusercontent.com/{owner}/{repo}/HEAD/README.md"
```

실패 시 `README.ko.md`, `readme.md` 시도 → 그래도 없으면 WebFetch로 GitHub 페이지 조회.

### 3단계: 도구 목록 확보

우선순위:
1. README에 도구 표/목록이 있으면 그대로 사용
2. 없으면 소스에서 도구 등록 코드를 찾는다:
   - Python: `@mcp.tool` / `Tool(name=` / `list_tools`
   - TS/JS: `server.tool(` / `ListToolsRequestSchema` / `tools:`
   - GitHub code search 페이지 또는 raw 소스 파일 fetch로 확인
3. 소스도 확인 불가하면 "도구 목록: 저장소에 명시 없음"으로 기록 — **추측 금지.** 확인 안 된 도구명을 쓰면 QA에서 환각으로 걸린다.

### 4단계: 설치·인증·설정 추출

- 설치: npm/pip/uvx/docker/소스 빌드 중 README에 명시된 방법
- 필요 키: 환경변수명과 발급처(네이버 개발자센터, 공공데이터포털 등)를 짝으로 기록
- 설정 예시: README의 `claude_desktop_config.json` 예시를 그대로 인용. 없으면 설치 방법에서 표준형을 구성하되 `"(README 기반 구성)"` 표기.

## 문서 템플릿 — `servers/{owner}--{repo}.md`

````markdown
# {repo}

> **[{owner}/{repo}](https://github.com/{owner}/{repo})** · ⭐ {stars} · {language} · 최근 푸시 {pushed_at:10} · 카테고리: {category}

{한 줄 설명 — 메인 README의 설명과 동일하게}

## 개요

{2-4문장: 무엇을 하는 서버인지, 어떤 API/데이터 소스를 쓰는지}

## 제공 도구

| 도구 | 기능 |
|------|------|
| `tool_name` | 설명 |

{또는: "도구 목록: 저장소에 명시 없음 (소스 확인 불가)"}

## 설치

```bash
{설치 명령}
```

## 필요 키 · 환경변수

| 환경변수 | 발급처 | 필수 |
|---------|--------|------|
| `NAVER_CLIENT_ID` | [네이버 개발자센터](https://developers.naver.com) | ✅ |

{키가 필요 없으면: "API 키 불필요"}

## 설정 예시

```json
{claude_desktop_config.json 스니펫}
```

## 비고

{제약사항, 아카이브 여부, MCP가 아닌 경우 경고, 특이사항. 없으면 섹션 생략}

---
*수집일: {YYYY-MM-DD} · 출처: 저장소 README{, 소스 코드}*
````

## JSON 레코드 — `_workspace/profiles/{owner}--{repo}.json`

```json
{
  "owner": "", "repo": "", "category": "",
  "status": "ok | gone | fetch_failed | not_mcp",
  "stars": 0, "language": "", "pushed_at": "",
  "tools": ["tool_name"], "tools_source": "readme | source | unknown",
  "install": "npm | pip | uvx | docker | source | unknown",
  "env_keys": ["NAVER_CLIENT_ID"],
  "api_key_required": true,
  "collected_at": "YYYY-MM-DD"
}
```

## 품질 기준

- 문서 하나당 목표 분량 40~80줄. 원 README를 통째로 복사하지 않는다 — 요약·추출한다.
- 한국어로 작성하되 도구명·환경변수·명령은 원문 유지.
- 모든 사실에는 근거가 있어야 한다: README에서 왔는지, 소스에서 왔는지 하단 출처 라인에 표기.
- 파일명의 owner/repo는 소문자 변환 없이 GitHub 표기 그대로, 구분자는 `--`.
