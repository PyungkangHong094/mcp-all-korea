# 33MCP_HWP_Limone

> **[skerishKang/33MCP_HWP_Limone](https://github.com/skerishKang/33MCP_HWP_Limone)** · ⭐ (rate limit) · Python · 최근 푸시 (rate limit) · 카테고리: 🔤 Korean NLP & Language

한글(HWP) 문서를 문서관리부터 고급 서식·표까지 제어하는 고도화 MCP 서버입니다.

## 개요

한글(HWP) 프로그램을 Windows COM(HWPFrame.HwpObject)으로 제어하는 MCP 서버("Advanced HWP MCP Server"). 문서 생성·열기·저장, 텍스트 조작, 서식 제어, 표, 객체 삽입, 문서 구조 관리, PDF 내보내기 등을 제공한다. 기본 한글 MCP 서버 대비 기능을 확장한 버전.

## 제공 도구

README에 명시된 도구 (README 기능 목록 기준).

| 카테고리 | 도구 |
|---------|------|
| 기본 문서 제어 | `create_document`, `open_document`, `save_document`, `get_document_info` |
| 고급 텍스트 조작 | `insert_text_at_position`, `select_text_range`, `find_and_replace`, `insert_text` |
| 서식 제어 | `apply_font_format`, `set_paragraph_format`, `set_page_margins`, `set_page_size` |
| 표 | `create_table`, `merge_table_cells` |
| 객체 삽입 | `insert_image`, `insert_shape`, `insert_hyperlink` |
| 문서 구조 | `insert_header_footer`, `insert_page_break`, `create_table_of_contents`, `apply_heading_style` |
| 고급 기능 | `export_to_pdf`, `initialize_hwp` |

## 설치

```bash
git clone https://github.com/skerishKang/33MCP_HWP_Limone.git
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
      "args": ["G:/path/to/33MCP_HWP/advanced_hwp_server.py"],
      "env": { "PYTHONPATH": "G:/path/to/33MCP_HWP" }
    }
  }
}
```

## 비고

- Windows 전용. 한글 2010 이상 + Python 3.10+ + pywin32 + COM 객체 등록 필요.
- crowwan/hwp-mcp-advanced-custom과 동일 계열("Advanced HWP MCP Server")의 기능 확장 버전으로 보이며, 이 저장소는 도구 수가 더 적다.

---
*수집일: 2026-07-03 · 출처: 저장소 README*
