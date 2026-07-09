# hwpConverMdMCP

> **[beomzh/hwpConverMdMCP](https://github.com/beomzh/hwpConverMdMCP)** · ⭐ N/A · Node.js/TypeScript · 최근 푸시 미상 · 카테고리: 🔤 Korean NLP & Language

HWP/HWPX 파일을 Markdown으로 변환하는 hwpConverMd API의 MCP 서버입니다.

## 개요

hwpConverMd(Python FastAPI) 변환 서버 앞단에 붙는 Node.js MCP 서버로, Claude Desktop·Cursor·Claude Code·Flowise 등 MCP 클라이언트에서 HWP/HWPX 문서를 Markdown으로 변환하게 해준다. MCP 서버는 로컬 파일 경로 또는 Base64 콘텐츠를 받아 `hwpConverMd` API(`/api/v1/convert`)에 multipart로 전달하고, 변환된 Markdown과 다운로드 URL을 반환한다. stdio 및 Streamable HTTP(Flowise/웹용) 두 가지 전송 방식을 지원한다.

## 제공 도구

| 도구 | 기능 |
|------|------|
| `convert_hwp_to_md` | 로컬 파일 경로(`filePath`)로 HWP/HWPX → Markdown 변환 |
| `convert_hwp_content_to_md` | Base64 콘텐츠(`content`, `filename`)로 변환, Markdown + `[DOWNLOAD_URL]` 반환 |

## 설치

```bash
npm install
npm run build
```

> 전제조건: Node.js >= 18.0.0, 그리고 별도의 `hwpConverMd`(Python FastAPI) 변환 서버가 `http://localhost:8000`에서 실행 중이어야 함(Docker Compose로 API+MCP+Flowise 스택 일괄 기동 가능).

## 필요 키 · 환경변수

| 환경변수 | 발급처 | 필수 |
|---------|--------|------|
| `HWP_API_URL` | hwpConverMd API 서버 URL (기본 `http://localhost:8000`) | 사실상 필수 |
| `MCP_HTTP_PORT` | Streamable HTTP 포트 (기본 `3000`) | ❌ |

API 키 불필요 (자체 호스팅 변환 서버 연동 방식).

## 설정 예시

```json
{
  "mcpServers": {
    "hwp-converter": {
      "command": "node",
      "args": ["/absolute/path/to/hwpConverMdMCP/dist/transport/stdio.js"],
      "env": {
        "HWP_API_URL": "http://localhost:8000"
      }
    }
  }
}
```

## 비고

- MCP 서버 단독으로는 동작하지 않고, 별도의 `hwpConverMd` FastAPI 변환 서버가 필요하다.
- Streamable HTTP 모드(`npm run start:http`)로 Flowise/웹 클라이언트 연동 가능(엔드포인트 `/mcp`).
- Docker Compose 및 Kubernetes 매니페스트 배포 지원.

---
*수집일: 2026-07-03 · 출처: 저장소 README*
