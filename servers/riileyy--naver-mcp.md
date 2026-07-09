# naver-mcp

> **[riileyy/naver-mcp](https://github.com/riileyy/naver-mcp)** · ⭐ 0 · JavaScript/HTML (Next.js) · 최근 푸시 N/A · 카테고리: 🔎 Search & Trends

네이버 실시간 검색을 제공하는 MCP 서버입니다.

> ⚠️ **경고: 이 저장소는 자체 MCP 도구를 정의하는 독립 MCP 서버가 아니다.** Vercel(`naver-mcp.vercel.app`)에 배포되는 Next.js 데모 웹앱으로, `pages/api/mcp-connect.js`가 MCP **클라이언트**로서 Smithery에 호스팅된 상위 서버 `@isnow890/naver-search-mcp`에 접속해 그 도구 목록을 조회·중계한다. 실제 네이버 검색 도구는 이 저장소가 아닌 상위 서버가 제공한다.

## 개요

네이버 검색 API 기반 MCP를 웹에서 시연하기 위한 Next.js 애플리케이션이다. 사용자가 입력한 API 키/프로필로 `https://server.smithery.ai/@isnow890/naver-search-mcp/mcp`에 StreamableHTTP로 연결하여 상위 MCP 서버의 도구를 나열하는 프록시 엔드포인트(`POST /api/mcp-connect`)를 제공한다. `smithery.yaml`에는 컨테이너 런타임(HTTP, 포트 3000)과 Naver Client ID/Secret 입력이 선언되어 있다.

## 제공 도구

도구 목록: 저장소에 명시 없음. 이 저장소는 도구를 직접 등록하지 않고 상위 서버 `@isnow890/naver-search-mcp`의 도구를 런타임에 조회(`client.listTools()`)하여 중계한다. 실제 네이버 검색 도구 정의는 [isnow890/naver-search-mcp](https://github.com/isnow890/naver-search-mcp)를 참조.

## 설치

독립 실행형 MCP 서버 설치 경로가 저장소에 정의되어 있지 않다. 소스는 Vercel 배포(`vercel dev`) 또는 Docker 컨테이너(포트 3000) 기준이며, 실제 검색 기능은 상위 Smithery 서버를 통해 동작한다.

## 필요 키 · 환경변수

| 환경변수 / 입력 | 발급처 | 필수 |
|---------|--------|------|
| Naver API Client ID (`clientId`) | [네이버 개발자센터](https://developers.naver.com) | ✅ |
| Naver API Client Secret (`clientSecret`) | [네이버 개발자센터](https://developers.naver.com) | ✅ |

> 키 입력은 `smithery.yaml`의 inputs로 선언되어 있다.

## 설정 예시

> (참고) 실제 도구 제공 서버인 상위 @isnow890/naver-search-mcp 연결 예

```json
{
  "mcpServers": {
    "naver-search": {
      "command": "npx",
      "args": ["-y", "@smithery/cli", "run", "@isnow890/naver-search-mcp"]
    }
  }
}
```

## 비고

- 상태: MCP 서버가 아닌 상위 MCP를 소비하는 데모 웹앱(프록시)으로 판명됨(`status: not_mcp`).
- 스타 0, 커밋 76(main). 실제 MCP 도구를 사용하려면 상위 저장소 `@isnow890/naver-search-mcp`를 직접 연동할 것을 권장한다.

---
*수집일: 2026-07-03 · 출처: 저장소 소스 코드(pages/api/mcp-connect.js, smithery.yaml, package.json)*
