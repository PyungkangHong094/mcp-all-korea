# mcp-bizinfo

> **[kwanGDss/mcp-bizinfo](https://github.com/kwanGDss/mcp-bizinfo)** · ⭐ N/A · JavaScript/Node · 카테고리: 📊 Public Data

기업마당(Bizinfo) 지원사업 데이터를 지역·대상·키워드·자연어로 검색하는 MCP 서버입니다.

## 개요

중소벤처기업부 기업마당(Bizinfo) 지원사업 공고 데이터를 검색하는 Node.js 패키지다. 하나의 로직을 HTTP REST 서버(`/search`, `/search-natural`, `/health`), CLI, MCP 서버(STDIO) 세 가지 진입점으로 노출한다. 지역·대상·키워드 기반 검색과 자연어 한 문장 질의를 지원한다. npm 패키지명은 `@kwangdss/bizinfo-mcp`.

## 제공 도구

| 도구 | 기능 |
|------|------|
| `search_bizinfo` | 기업마당 지원사업 공고 검색 (`region`, `target`, `keywords`, `page`, `page_size`) |
| `search_bizinfo_natural` | 자연어 질의(`prompt`)를 파싱해 지원사업 검색 |

*도구 목록 출처: 소스 `mcp-server.mjs`의 `server.registerTool` 호출 (README에는 도구명 미명시).*

## 설치

MCP 서버(STDIO):

```bash
npx -y @kwangdss/bizinfo-mcp@latest bizinfo-mcp-server
```

HTTP 서버/CLI:

```bash
npm install                    # 또는 npm install -g @kwangdss/bizinfo-mcp
npm start                      # HTTP 서버 (PORT=3000 기본)
npx @kwangdss/bizinfo-mcp "광주 소상공인 사업 알려줘"   # CLI
```

## 필요 키 · 환경변수

| 환경변수 | 발급처 | 필수 |
|---------|--------|------|
| `BIZINFO_API_KEY` | 기업마당 Open API 키 | 선택 |

미설정 시 패키지에 포함된 데모 키(`QP6yn2`)를 사용한다.

## 설정 예시

```json
{
  "mcpServers": {
    "bizinfo": {
      "command": "npx",
      "args": ["-y", "@kwangdss/bizinfo-mcp@latest", "bizinfo-mcp-server"]
    }
  }
}
```

## 비고

- 의존성: `@modelcontextprotocol/sdk`, `dotenv`, `zod`. ESM(`type: module`) 패키지.
- 환경변수는 실행 디렉터리의 `.env` 또는 시스템 환경변수에서 로드.
- 원 저장소는 `smhrd/bizinfo-mcp`(package.json homepage 기준). 라이선스 MIT.

---
*수집일: 2026-07-03 · 출처: 저장소 README, 소스 코드(mcp-server.mjs)*
