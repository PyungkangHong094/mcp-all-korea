---
name: korea-mcp-catalog
description: mcp-all-korea 카탈로그 하네스의 오케스트레이터. README의 모든 MCP 서버 링크를 방문해 상세 문서(servers/*.md)를 생성·검증·게시하는 전체 파이프라인 실행. "카탈로그 만들어/갱신해", "서버 상세 전부 수집해", "새 서버 추가하고 상세 문서도", "카탈로그 다시 실행", "QA만 다시", "특정 카테고리만 재수집", "게시/푸시해줘" 등 카탈로그 구축·재실행·부분 갱신 요청 시 반드시 이 스킬 사용.
---

# Korea MCP Catalog — 오케스트레이터

README에 큐레이션된 전체 MCP 서버의 상세 카탈로그를 수집(팬아웃) → 검증 → 게시하는 파이프라인.

**실행 모드: 서브 에이전트** (수집기 간 통신 불필요 — 산출물이 파일로 독립적이며, 팀 조율 오버헤드가 이득보다 크다. 수집기들은 `run_in_background`로 병렬 실행.)

## 팀 구성

| 에이전트 | 정의 파일 | 역할 | 사용 스킬 |
|---------|----------|------|----------|
| mcp-profiler ×N | `.claude/agents/mcp-profiler.md` | 배치별 저장소 프로파일링 | mcp-server-profiling |
| mcp-catalog-qa | `.claude/agents/mcp-catalog-qa.md` | 산출물 정합성 검증 | mcp-server-profiling (템플릿 기준) |
| mcp-catalog-publisher | `.claude/agents/mcp-catalog-publisher.md` | 인덱스·README 연결·커밋·푸시 | — |

모든 Agent 호출에 `model: "opus"` 명시.

## Phase 0: 컨텍스트 확인

1. `_workspace/profiles/`와 `servers/` 존재 여부 확인:
   - 둘 다 없음 → **초기 실행** (Phase 1부터)
   - 존재 + 부분 수정 요청("이 카테고리만", "QA만", "실패분만") → **부분 재실행** (해당 Phase/배치만)
   - 존재 + 전체 재수집 요청 → 기존 `_workspace/`를 `_workspace_prev/`로 이동 후 초기 실행
2. `_workspace/profiles/*.json`에서 `status != ok`인 항목이 있으면 우선 재수집 대상으로 분류

## Phase 1: 서버 목록 추출 (오케스트레이터 직접)

README에서 GitHub 링크 + 카테고리 + 설명을 추출해 `_workspace/00_server_list.json`으로 저장한다. 스크립트로 처리:

- 정규식: `\*\*\[([^\]]+)\]\((https://github\.com/[^)]+)\)\*\* – (.+)` 를 카테고리 헤더(`### `)와 함께 스캔
- 레코드: `{owner, repo, category, description}`
- 추출 수가 README의 `github.com` 링크 수와 다르면 원인 파악 후 진행 (badge 링크 등 제외 대상 확인)

## Phase 2: 팬아웃 수집 (서브 에이전트 병렬)

1. 서버 목록을 **10개 내외 배치**로 분할 (82개 → 8~9배치)
2. 배치마다 mcp-profiler를 `run_in_background: true`로 스폰. 프롬프트에 포함할 것:
   - 배정 저장소 JSON 배열 전체 (owner/repo/category/description)
   - "`.claude/skills/mcp-server-profiling/SKILL.md`를 먼저 읽고 그 템플릿·절차를 따르라"
   - 출력 경로: `servers/`, `_workspace/profiles/`
   - GitHub API rate limit 주의 — 메타데이터 API는 배치당 총 10회 이하, 실패 시 생략하고 진행
3. 전 배치 완료 대기 → 반환 메시지에서 실패 목록 수합
4. 실패 저장소는 1회 재시도 배치로 재스폰 → 재실패 시 `status` 기록만 남기고 진행 (QA 보고서에 누락 명시)

## Phase 3: QA 검증 (서브 에이전트 1)

mcp-catalog-qa 스폰 → `_workspace/02_qa_report.md` 생성. 수정 필요 항목이 있으면:
- 수집 오류 → 해당 저장소만 mcp-profiler 재스폰 (부분 재실행)
- 경미한 오탈자 → QA가 직접 수정 완료했는지 확인

QA 통과(미해결 치명 항목 0건) 전에는 Phase 4로 넘어가지 않는다.

## Phase 4: 게시 (서브 에이전트 1)

mcp-catalog-publisher 스폰:
1. `servers/README.md` 카테고리별 인덱스 생성
2. 메인 README 각 항목에 상세 링크 삽입 (스크립트 일괄 처리)
3. 커밋 (+ 사용자가 게시 요청한 경우 푸시)

## 데이터 전달

파일 기반 + 반환값 기반:

```
_workspace/
├── 00_server_list.json        # Phase 1 산출
├── profiles/{owner}--{repo}.json  # Phase 2 산출 (구조화)
├── 02_qa_report.md            # Phase 3 산출
└── 03_publish_report.md       # Phase 4 산출
servers/
├── README.md                  # 인덱스 (Phase 4)
└── {owner}--{repo}.md         # 상세 문서 (Phase 2)
```

`_workspace/`는 커밋하지 않는다 (.gitignore 등록). `servers/`만 게시 대상.

## 에러 핸들링

| 상황 | 대응 |
|------|------|
| 프로파일러 배치 무응답/죽음 | 해당 배치 1회 재스폰 → 재실패 시 배치를 반으로 쪼개 재시도 |
| GitHub rate limit | 메타데이터 생략 모드로 진행 (문서에 별점 없이) |
| 저장소 삭제/404 | `status: gone` 기록, 메인 README에서 제거는 사용자 확인 후 |
| QA 치명 실패 반복 | 2회 재수집 후에도 실패하면 해당 서버 제외하고 게시, 보고서에 명시 |

## 테스트 시나리오

**정상 흐름**: "카탈로그 만들어줘" → Phase 1(82개 추출) → 9개 배치 병렬 수집 → QA 통과 → servers/ 83개 파일 + README 링크 → 커밋·푸시 → 사용자에게 커버리지 보고 (82/82).

**에러 흐름**: 배치 3에서 저장소 2개 404 → profiles에 `gone` 기록 → QA 보고서 "80/82 수집, 2개 소멸" → 게시는 80개만 링크, 최종 보고에 소멸 저장소 목록 + README 제거 여부 질문.

## 후속 작업

- "새 서버 N개 추가해줘" → Phase 1에서 신규분만 목록화 → 배치 1개 수집 → QA(신규분) → 게시(증분)
- "상세 문서 갱신해줘" → 전체 재수집 (기존 문서를 읽고 갱신하도록 프로파일러에 지시)
- "QA만 다시" → Phase 3만 실행
