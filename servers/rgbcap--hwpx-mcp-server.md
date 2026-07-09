# hwpx-mcp-server

> **[rgbcap/hwpx-mcp-server](https://github.com/rgbcap/hwpx-mcp-server)** · ⭐ N/A · TypeScript/Node.js · 최근 푸시 미상 · 카테고리: 🔤 Korean NLP & Language

한글 .hwpx 파일 텍스트 추출·찾아바꾸기·스타일 변경을 제공하는 MCP 서버입니다.

## 개요

ZIP 기반 XML 포맷인 `.hwpx`(한글 워드프로세서) 파일을 읽고 편집하는 MCP 서버다. 텍스트 추출, 찾아바꾸기, 폰트/크기/굵기 등 스타일 변경, 새 파일 생성을 도구로 제공한다. 스타일 편집은 정규식 기반 XML 패칭을 사용하므로 레이아웃은 한글에서 열어 확인하도록 권고한다. 레거시 바이너리 `.hwp`는 지원하지 않고 `.hwpx`만 대상으로 한다.

## 제공 도구

| 도구 | 기능 |
|------|------|
| `hwpx_read_text` | .hwpx 파일에서 전체 텍스트 추출 |
| `hwpx_edit_text` | 텍스트 찾아바꾸기 |
| `hwpx_set_style` | 폰트/크기/굵게/기울임/밑줄 변경 |
| `hwpx_create` | 새 .hwpx 파일 생성 |

## 설치

```bash
npm install
npm run build
```

## 필요 키 · 환경변수

API 키 불필요 (로컬 파일 처리).

## 설정 예시

README는 gemini-cli(`~/.gemini/settings.json`) 예시를 제공한다.

```json
{
  "mcpServers": {
    "hwpx": {
      "command": "node",
      "args": ["/absolute/path/to/hwpx-mcp-server/dist/index.js"]
    }
  }
}
```

## 비고

- `.hwpx` 전용, 레거시 바이너리 `.hwp` 미지원.
- 스타일 편집은 정규식 기반 XML 패칭 — 편집 후 한글에서 레이아웃 확인 권고.
- `mimetype` 엔트리는 비압축(ZIP store)으로 유지되어야 함.

---
*수집일: 2026-07-03 · 출처: 저장소 README*
