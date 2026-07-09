# hwp-mcp-advanced-custom

> **[crowwan/hwp-mcp-advanced-custom](https://github.com/crowwan/hwp-mcp-advanced-custom)** · ⭐ (rate limit) · Python · 최근 푸시 (rate limit) · 카테고리: 🔤 Korean NLP & Language

한글(HWP) 문서를 59개 기능으로 생성·편집·서식·표·PDF 변환까지 제어하는 고도화 MCP 서버입니다.

## 개요

한글(HWP) 프로그램을 Windows COM(HWPFrame.HwpObject)으로 제어하는 고도화 MCP 서버. 기본 문서 제어부터 실행 중인 한글 연결, 정밀 위치 지정, 서식 유지 삽입/삭제, 표 CSV 추출, 템플릿 채우기, 대량작업 성능 최적화까지 제공한다. `open_document` 시 버전 경고·접근 권한·암호 대화상자를 자동 처리한다.

## 제공 도구

README에 명시된 도구를 카테고리별로 정리 (README 기능 목록 기준).

| 카테고리 | 도구 |
|---------|------|
| 기본 문서 제어 | `create_document`, `open_document`, `save_document`, `close_document`, `close_all_documents`, `quit_hwp`, `get_document_info` |
| 실행 중 한글 연결 | `get_running_hwp_documents`, `connect_to_running_hwp`, `switch_to_document`, `get_active_document_info`, `list_all_hwp_windows`, `connect_to_hwp_window` |
| 고급 텍스트 조작 | `insert_text_at_position`, `select_text_range`, `find_and_replace`, `insert_text` |
| 서식 제어 | `apply_font_format`, `set_paragraph_format`, `set_page_margins`, `set_page_size` |
| 표 | `create_table`, `merge_table_cells`, `get_table_as_csv` |
| 객체 삽입 | `insert_image`, `insert_shape`, `insert_hyperlink` |
| 문서 구조 | `insert_header_footer`, `insert_page_break`, `create_table_of_contents`, `apply_heading_style` |
| 텍스트 읽기 | `get_text_all`, `get_text_by_page`, `get_selected_text`, `get_paragraph_text`, `save_as_text` |
| 분석·자동화 | `batch_replace`, `find_text`, `fill_template`, `get_document_structure` |
| 정밀 위치 이동 | `move_to_page`, `move_to_paragraph_number`, `move_to_document_start`, `move_to_document_end` |
| 텍스트 삭제 | `delete_selected_text`, `delete_all_occurrences`, `delete_current_line`, `delete_current_paragraph`, `delete_page_content` |
| 서식 유지/조회 | `get_current_char_shape`, `insert_text_preserving_format` |
| 고급 삽입 | `insert_after_text`, `insert_before_text`, `append_to_paragraph`, `prepend_to_paragraph`, `insert_at_page_start`, `insert_at_page_end` |
| 선택·교체 | `select_paragraph_by_number`, `select_page_content`, `replace_paragraph` |
| 성능 최적화 | `set_screen_updating`, `set_automation_mode`, `optimize_for_bulk_operations`, `restore_normal_mode` |
| 내보내기 | `export_to_pdf`, `initialize_hwp` |

## 설치

```bash
git clone https://github.com/crowwan/hwp-mcp-advanced-custom.git
pip install -r requirements.txt      # 또는: pip install mcp fastmcp pywin32
```

## 필요 키 · 환경변수

API 키 불필요 (로컬 COM 제어).

## 설정 예시

```json
{
  "mcpServers": {
    "advanced-hwp": {
      "command": "python",
      "args": ["D:/path/to/hwp-mcp-advanced-custom/advanced_hwp_server.py"],
      "env": { "PYTHONPATH": "D:/path/to/hwp-mcp-advanced-custom" }
    }
  }
}
```

## 비고

- Windows 전용. 한글 2010 이상 + Python 3.10+ + pywin32 필요.
- COM은 하나의 프로세스에만 연결되므로 별도 프로세스로 연 문서는 직접 제어 불가.

---
*수집일: 2026-07-03 · 출처: 저장소 README*
