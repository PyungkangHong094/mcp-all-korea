# hwpx-mcp-server

> **[airmang/hwpx-mcp-server](https://github.com/airmang/hwpx-mcp-server)** · ⭐ N/A · Python · 최근 푸시 미상 · 카테고리: 🔤 Korean NLP & Language

한글(HWPX) 문서를 한컴오피스 없이 순수 파이썬으로 읽기·검색·편집·양식채움·생성·검증하는 MCP 서버입니다.

## 개요

[python-hwpx](https://github.com/airmang/python-hwpx) 코어 위에 구축된 MCP 표준 서버로, HWPX 문서의 열람·검색·편집·양식채움·생성·추출을 AI 클라이언트(Claude Desktop, VS Code, Gemini CLI 등)에서 직접 수행하게 한다. 한글 워드프로세서 없이 순수 파이썬으로 처리하며 Windows·macOS·Linux에서 동작한다. 모든 쓰기는 python-hwpx의 단일 SavePipeline 게이트(무결성·XML·레이아웃·시각 검증)를 통과하고, raw XML 편집 표면은 노출하지 않는다. 기본 모드 도구에 더해 고급 모드(`HWPX_MCP_ADVANCED=1`)에서 점검·검증 도구가 추가된다.

## 제공 도구

README는 테마별 대표 도구를 나열하며, **전체 도구 목록·시그니처는 [`docs/use-cases.md`](https://github.com/airmang/hwpx-mcp-server/blob/main/docs/use-cases.md)와 [`docs/skill-first-workflows.md`](https://github.com/airmang/hwpx-mcp-server/blob/main/docs/skill-first-workflows.md)를 참고하도록 안내한다.** 아래는 README에 명시된 대표 도구다.

| 테마 | 도구(README 명시분) |
|------|------|
| 읽기·탐색 | `get_document_info`, `get_document_text`, `get_document_outline`, `find_text`, `get_table_text`, `get_table_map`, `find_cell_by_label`, `list_styles`, `get_document_map` |
| 로컬 문서 ingest | `document_to_markdown`, `document_extract_json`, `markdown_to_document_plan` |
| 검색·치환 | `search_and_replace`, `batch_replace`, `replace_in_paragraph`, `replace_by_anchor` |
| 편집·트랜잭션 | `add_heading`, `add_paragraph`, `insert_paragraph`, `delete_paragraph`, `add_page_break`, `add_memo`, `apply_edits`, `undo_last_edit`, `byte_preserving_patch`, `add_tracked_edit` |
| 표·양식채움 | `add_table`, `set_table_cell_text`, `merge_table_cells`, `split_table_cell`, `format_table`, `table_compute`, `fill_by_path`, `verify_fill`, `analyze_template_formfit`, `apply_template_formfit` |
| 누름틀 양식 | `list_form_fields`, `fill_form_field`, `analyze_form_fill` |
| 선언형 생성 | `validate_document_plan`, `analyze_document_plan`, `create_document_from_plan`, `inspect_document_authoring_quality`, `inspect_operating_plan_quality`, `create_proposal_document`, `compose_exam`, `verify_question_splits` |
| 공문서·비교·대량 | `inspect_official_document_style`, `inspect_reference_consistency`, `doc_diff`, `create_comparison_table_document`, `mail_merge`, `inspect_mail_merge_placeholders` |
| 서식·그림·생성기 | `set_paragraph_format`, `set_page_setup`, `set_header_footer`, `set_page_number`, `set_list_format`, `format_text`, `create_custom_style`, `insert_picture`, `replace_picture`, `build_image_grid`, `build_meeting_nameplates`, `build_organization_chart` |
| 프리뷰·추출·복구·진단 | `render_preview`, `hwpx_to_markdown`, `hwpx_to_html`, `hwpx_extract_json`, `repair_hwpx`, `mcp_server_health` |
| 고급(`HWPX_MCP_ADVANCED=1`) | `package_parts`, `package_get_xml`, `package_get_text`, `object_find_by_tag`, `object_find_by_attr`, `plan_edit`, `preview_edit`, `apply_edit`, `validate_structure`, `lint_text_conventions` |

> 위 목록은 README 명시분이며, 전체 도구는 저장소 `docs/`를 참고할 것.

## 설치

```bash
# uv 기준
uvx hwpx-mcp-server

# 또는 pip
pip install hwpx-mcp-server
hwpx-mcp-server

# 비-HWPX(PDF/DOCX/XLSX/HTML/TXT) ingest 시
pip install "hwpx-mcp-server[ingest]"
```

요구: Python >= 3.10, python-hwpx >= 2.23.0. PyPI 패키지로 배포.

## 필요 키 · 환경변수

API 키 불필요 (로컬 파일 처리).

| 환경변수 | 설명 | 기본값 |
|---------|------|--------|
| `HWPX_MCP_MAX_CHARS` | 텍스트 반환 최대 길이 | `10000` |
| `HWPX_MCP_AUTOBACKUP` | 저장 전 `.bak` 백업 | `1` |
| `HWPX_MCP_ADVANCED` | 고급 도구 활성화 | `0` |
| `HWPX_MCP_SANDBOX_ROOT` | 허용 경로 root 제한 | unset |
| `HWPX_MCP_FETCH_TIMEOUT_SECONDS` | URL fetch timeout | `20.0` |
| `HWPX_MCP_QUALITY` | 저장 게이트 정책(`transparent`/`strict`) | `transparent` |
| `HWPX_MCP_REQUIRE_CAPABILITY` | capability skew fail-closed | `1` |
| `LOG_LEVEL` | 로그 레벨 | `INFO` |

## 설정 예시

```json
{
  "mcpServers": {
    "hwpx": {
      "command": "uvx",
      "args": ["hwpx-mcp-server"]
    }
  }
}
```

## 비고

- Open XML `.hwpx` 전용 — 바이너리 `.hwp`는 직접 편집 대상 아님.
- 라이선스 Apache 2.0. HWPX Stack 3종(`python-hwpx` 라이브러리 / 본 MCP 서버 / `hwpx-plugins` 스킬 번들) 중 서버 계층.
- 모든 쓰기는 SavePipeline 게이트 통과, raw XML 편집 미노출. 작성자: 고규현.

---
*수집일: 2026-07-03 · 출처: 저장소 README*
