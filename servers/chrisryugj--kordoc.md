# kordoc

> **[chrisryugj/kordoc](https://github.com/chrisryugj/kordoc)** · ⭐ 1359 · TypeScript · 최근 푸시 2026-07-08 · 카테고리: 🔤 Korean NLP & Language

한글(HWP, HWPX) 및 PDF 등 문서를 파싱해 텍스트·마크다운으로 변환하며 문서 비교·표 추출·양식 채우기·서식 보존 편집·문서 생성 도구를 제공하는 MCP 서버입니다.

## 개요

HWP 3.x/5.x, HWPX, HWPML, PDF, XLS, XLSX, DOCX 등 관공서에서 쏟아지는 문서를 마크다운으로 변환하고, 표 재현·신구대조·양식 채우기·서식 무손실 라운드트립·HWPX 생성까지 지원하는 CLI + MCP 서버다. Node.js 18+ 기반이며 `npx -y kordoc setup` 대화형 마법사가 Claude Desktop/Cursor/Claude Code 등 클라이언트 설정을 자동 패치한다. Claude Code 플러그인(스킬) 형태로도 설치 가능하다.

## 제공 도구

| 도구 | 기능 |
|------|------|
| `parse_document` | HWP/HWPX/PDF/XLSX/DOCX → 마크다운 (메타데이터 포함) |
| `detect_format` | 매직 바이트로 포맷 감지 |
| `parse_metadata` | 메타데이터만 빠르게 추출 |
| `parse_pages` | 특정 페이지 범위만 파싱 |
| `parse_table` | N번째 테이블만 추출 |
| `compare_documents` | 두 문서 비교 (크로스 포맷) |
| `parse_form` | 양식 필드를 JSON으로 추출 |
| `fill_form` | 양식 템플릿에 값 채우기 (HWPX 원본 서식 보존) |
| `patch_document` | 편집된 마크다운을 원본 HWPX/HWP에 서식 보존 반영 |
| `generate_document` | 마크다운(표·수식·차트 포함) → HWPX 생성, 공문서 프리셋 |
| `place_seal` | 도장/서명 이미지를 앵커 문구 위에 부유 배치 |

## 설치

```bash
npx -y kordoc setup   # 대화형 마법사가 클라이언트 설정 자동 패치
```

CLI 단독 사용: `npx kordoc <파일>`. Claude Code 플러그인: `/plugin marketplace add chrisryugj/kordoc` → `/plugin install kordoc@kordoc`.

## 필요 키 · 환경변수

API 키 불필요. (로컬 문서 파싱)

## 설정 예시

```json
{
  "mcpServers": {
    "kordoc": {
      "command": "npx",
      "args": ["-y", "kordoc", "mcp"]
    }
  }
}
```

(setup 마법사가 위 형태로 자동 구성 — Windows는 `cmd /c npx` 래핑)

## 비고

- 라이선스: MIT. npm 패키지 `kordoc`.
- `MODULE_NOT_FOUND` 발생 시 `npm uninstall -g kordoc` 후 `npx -y kordoc@latest setup`으로 해결.
- 도구 수는 버전에 따라 확장됨(README 표 기준 11개).

---
*수집일: 2026-07-02 · 출처: 저장소 README*
