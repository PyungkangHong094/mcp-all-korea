# law-mcp

> **[finalchild/law-mcp](https://github.com/finalchild/law-mcp)** · ⭐ 31 · TypeScript · 최근 푸시 2025-07-07 · 카테고리: 📜 Legal & Government

한국 법령 및 자치법규(조례)를 조회하는 실험적 MCP 서버 (Claude Code 전용).

## 개요

법제처 국가법령정보센터(open.law.go.kr) API를 통해 한국 법령·자치법규(조례)를 검색·조회하는 MCP 서버다. Deno로 작성되었으며 플랫폼별 바이너리(Windows/macOS/Linux)로 빌드해 사용한다. `get_law_details`가 법령 정보를 파일로 저장하면 Claude Code가 CLI로 그 파일을 읽는 방식이라, **Claude Desktop 등 일반 MCP 클라이언트에서는 정상 동작하지 않고 Claude Code 환경에서만 작동하는 실험적 구현**이다.

## 제공 도구

| 도구 | 기능 |
|------|------|
| `search_laws` | 법령·자치법규 검색 (법령명/본문, 페이지네이션, 8종 정렬 옵션) |
| `get_law_details` | 특정 법령·자치법규 상세 조회 후 JSON·Markdown 파일로 저장 (조문·부칙·개정문·제개정이유 포함) |

## 설치

```bash
# 현재 플랫폼용 바이너리 빌드
deno task build:current
```

## 필요 키 · 환경변수

| 환경변수 | 발급처 | 필수 |
|---------|--------|------|
| `LAW_API_OC` | [open.law.go.kr](https://open.law.go.kr) — 이메일 ID 부분 | ✅ |

## 설정 예시

```json
{
  "mcpServers": {
    "law-mcp": {
      "command": "/path/to/law-mcp/build/law-mcp",
      "env": {
        "LAW_API_OC": "your-email-id"
      }
    }
  }
}
```

Apple Silicon은 `build/law-mcp-darwin-arm64` 바이너리를 지정한다. 위 설정은 Claude Code(VS Code) settings.json에 추가한다.

## 비고

- **실험적**: 파일 읽기에 의존하므로 Claude Code 전용. ISC License.
- MCP Desktop Extension(DXT)으로 패키징 가능(플랫폼별 바이너리 빌드 지원).
- 최근 푸시가 2025-07로 배치 내에서 가장 오래됨.

---
*수집일: 2026-07-02 · 출처: 저장소 README*
