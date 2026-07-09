# hwpx-mcp

> **[Dayoooun/hwpx-mcp](https://github.com/Dayoooun/hwpx-mcp)** · ⭐ (rate limit) · Node/TypeScript · 최근 푸시 (rate limit) · 카테고리: 🔤 Korean NLP & Language

한글 HWPX 문서를 표·문단·스타일·이미지까지 읽기·생성·편집하는 강화 MCP 서버입니다.

## 개요

AI 도구(Claude 등)와 연동해 한글 HWPX 문서를 자동 편집하는 MCP 서버. HWPX가 ZIP+XML 구조라는 점을 이용해 한글 프로그램 없이 Node.js만으로 읽고 쓴다(Windows/macOS/Linux 공용). [mjyoo2/hwp-extension](https://github.com/mjyoo2/hwp-extension)을 포크해 테이블 저장 실패·텍스트 겹침·파일 손상·스타일 유실 등 원본 버그를 수정했고, 원자적 쓰기(atomic write)와 깊이 기반 XML 파싱을 도입했다.

## 제공 도구

총 77개 도구를 카테고리별로 제공 (README 도구 목록 기준). 대표 도구는 각 카테고리 앞부분.

| 카테고리 | 개수 | 예시 도구 |
|---------|------|----------|
| 문서 관리 | 5 | `create_document`, `open_document`, `close_document`, `save_*` |
| 문서 정보 | 5 | 문서 메타/구조 조회 |
| 단락(Paragraphs) | 8 | 문단 삽입·수정·삭제 |
| 텍스트 스타일 | 4 | 글꼴·서식 적용 |
| 검색/치환 | 4 | 찾기·바꾸기 |
| 테이블(Tables) | 12 | 표 생성·셀 병합·편집 |
| 페이지 설정 | 2 | 여백·용지 |
| 이미지 | 5 | 이미지 삽입·관리 |
| 도형(Shapes) | 3 | 도형 삽입 |
| 머리글/바닥글 | 4 | 헤더·푸터 |
| 각주/미주 | 4 | 각주·미주 |
| 북마크/하이퍼링크 | 4 | 링크·북마크 |
| 수식(Equations) | 2 | 수식 삽입 |
| 메모/주석 | 3 | 메모 |
| 섹션(Sections) | 5 | 섹션 관리 |
| 스타일 정의 | 4 | 스타일 정의 |
| 단 설정 | 2 | 단 레이아웃 |
| 내보내기 | 2 | export |
| 실행 취소/복구 | 2 | undo/redo |

> 개별 도구 77개 전체 이름은 저장소 README의 "🔌 MCP Tools (77개)" 섹션 참조.

## 설치

```bash
git clone https://github.com/Dayoooun/hwpx-mcp.git
cd hwpx-mcp/mcp-server
npm install
npm run build
```

## 필요 키 · 환경변수

API 키 불필요 (로컬 파일 편집, 네트워크 호출 없음).

## 설정 예시

```json
{
  "mcpServers": {
    "hwpx-mcp": {
      "command": "node",
      "args": ["C:/path/to/hwpx-mcp/mcp-server/dist/index.js"]
    }
  }
}
```

## 비고

- 한글 프로그램 없이 동작하나, 결과물 확인은 한컴오피스 권장(LibreOffice는 HWPX 제한적 지원).
- 원본 mjyoo2/hwp-extension의 Fork.

---
*수집일: 2026-07-03 · 출처: 저장소 README*
