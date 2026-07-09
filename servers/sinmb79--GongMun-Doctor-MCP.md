# GongMun-Doctor-MCP

> **[sinmb79/GongMun-Doctor-MCP](https://github.com/sinmb79/GongMun-Doctor-MCP)** · ⭐ (rate limit) · Python · 최근 푸시 (rate limit) · 카테고리: 🔤 Korean NLP & Language

공문서(.hwpx/.hwp)를 3단계 AI 교정으로 맞춤법·문법·공문 문체를 로컬에서 교정하는 MCP 서버입니다.

## 개요

한국 공문서(.hwpx/.hwp)를 로컬 PC에서 자동 교정하는 MCP 서버. Claude/Codex 등 AI 에이전트에게 "이 문서 교정해줘"라고 하면 파일이 외부로 나가지 않고 PC 안에서 교정된다(네트워크 호출·클라우드 API 키 없음). 교정 규칙은 3단계(L1 맞춤법·띄어쓰기 / L2 문법·조사 / L3 행정업무운영편람 기준 공문서체)로 구성되며, 6개 분야 50종 행정문서 템플릿도 제공한다.

## 제공 도구

10개 도구 (README 도구 표 기준).

| 도구 | 기능 |
|------|------|
| `correct_document` | 단일 문서 교정 |
| `correct_documents_in_folder` | 폴더 내 문서 일괄 교정 |
| `list_rules` | 교정 규칙 목록 조회 |
| `get_correction_report` | 교정 보고서 조회 |
| `preview_text_corrections` | 파일 수정 없이 텍스트 교정 미리보기 |
| `list_document_templates` | 행정문서 템플릿 목록 |
| `match_document_templates` | 키워드로 템플릿 검색 |
| `get_template_variables` | 템플릿 입력 변수 조회 |
| `render_document_template` | 템플릿 렌더링(문서 생성) |
| `get_server_info` | 서버 정보 조회 |

## 설치

```bash
git clone https://github.com/sinmb79/GongMun-Doctor-MCP.git
cd GongMun-Doctor-MCP
python -m pip install "mcp[cli]>=1.0,<2"
python -m pip install -e . --no-deps
```

## 필요 키 · 환경변수

API 키 불필요 (100% 로컬 처리).

## 설정 예시

```bash
# Claude Code
claude mcp add --transport stdio gongmun-doctor -- python -m gongmun_doctor.mcp.server
# Codex
codex mcp add gongmun-doctor -- python -m gongmun_doctor.mcp.server
```

```json
{
  "mcpServers": {
    "gongmun-doctor": {
      "command": "python",
      "args": ["-m", "gongmun_doctor.mcp.server"]
    }
  }
}
```

## 비고

- Python 3.12 또는 3.13 권장 (3.14는 `lxml` 빌드 문제 가능).
- 50종 템플릿: 일반행정 15 / 감사 5 / 민원 5 / 건설공사 10 / 인사 5 / 계약조달 10.

---
*수집일: 2026-07-03 · 출처: 저장소 README*
