# HwpForge

> **[ai-screams/HwpForge](https://github.com/ai-screams/HwpForge)** · ⭐ N/A (API rate limit) · Rust · 최근 푸시 N/A · 카테고리: 🔤 Korean NLP & Language

한글 HWPX 문서를 Markdown과 상호 변환하고 JSON 편집·검증하는 9가지 도구를 제공하는 Rust 기반 MCP 서버입니다.

## 개요

HWPX 문서(ZIP + XML, OWPML 국가표준 KS X 6101)를 다루는 순수 Rust 라이브러리이자 MCP 서버다. 한글 2014~2025+ HWPX 읽기·쓰기와 HWP5(.hwp) 읽기를 지원한다. LLM-first 설계로 Markdown ↔ HWPX 양방향 변환과 JSON 라운드트립 편집을 제공한다. MCP 서버(코드명 "Anvil")는 베타이며, HWP5 경로는 MCP 대신 CLI("Hammer") 워크플로를 우선한다. crates.io에 `hwpforge`(라이브러리), `hwpforge-bindings-cli`(CLI), `hwpforge-bindings-mcp`(MCP)로 배포된다.

## 제공 도구

| 도구 | 기능 |
|------|------|
| `hwpforge_convert` | Markdown → HWPX 변환 |
| `hwpforge_inspect` | HWPX 구조 확인 |
| `hwpforge_to_json` | HWPX → JSON 추출 |
| `hwpforge_patch` | JSON으로 섹션 교체 |
| `hwpforge_templates` | 스타일 프리셋 조회 |
| `hwpforge_validate` | HWPX 구조/무결성 검증 |
| `hwpforge_restyle` | 스타일 프리셋 일괄 적용 |
| `hwpforge_from_json` | JSON → HWPX 직접 생성 |
| `hwpforge_to_md` | HWPX → Markdown 변환 |

(도구 9개 + 리소스 4개 + 프롬프트 3개)

## 설치

```bash
cargo install hwpforge-bindings-mcp   # MCP 서버(Anvil)
cargo install hwpforge-bindings-cli   # CLI(Hammer, 선택)
```

npm 경유 `npx -y` 실행도 지원한다(README).

## 필요 키 · 환경변수

API 키 불필요. (로컬 문서 처리)

## 설정 예시

```json
{
  "mcpServers": {
    "hwpforge": {
      "command": "hwpforge-mcp"
    }
  }
}
```

(README 기반 구성 — 클라이언트별 MCP Server 등록 UI 사용)

## 비고

- 라이선스: MIT OR Apache-2.0.
- MCP surface는 베타. HWP5는 읽기/점검/재출력 중심(CLI 우선).
- GitHub 메타데이터는 수집 시점 API rate limit으로 별점·푸시일 미확보.

---
*수집일: 2026-07-02 · 출처: 저장소 README*
