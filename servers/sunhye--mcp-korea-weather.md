# mcp-korea-weather

> **[sunhye/mcp-korea-weather](https://github.com/sunhye/mcp-korea-weather)** · ⭐ N/A (GitHub API 제한) · TypeScript/Node.js · 최근 푸시 N/A · 카테고리: 🌦 Weather

기상청(KMA) API로 실황·초단기예보(기온·강수·바람·습도)를 제공하는 Fastify/Node 기반 MCP 서버입니다.

## 개요

기상청(KMA) 초단기실황·초단기예보 Open API(VilageFcstInfoService_2.0)에 연동하여 위경도 기반 날씨 정보를 제공하는 MCP 서버다. Fastify/Node.js로 작성되었고 Docker 컨테이너(PORT 8080, tini, non-root, healthcheck)에서 바로 실행되도록 구성되어 있으며, MCP JSON-RPC(initialize / tools/list / tools/call)를 처리한다. 입력한 위경도를 기상청 격자 좌표(nx, ny)로 변환해 조회한다.

## 제공 도구

| 도구 | 기능 |
|------|------|
| `get_korea_weather` | 기상청 초단기실황 (기온/강수/풍속/습도) — 위경도 입력 |
| `get_korea_forecast` | 기상청 초단기예보 (향후 3개 타임슬롯 요약) — 위경도 입력 |

> 도구 목록은 소스 코드(`src/index.ts`, `src/mcp.js`)의 도구 등록부에서 확인했다 (README에는 개별 도구명 미기재).

## 설치

```bash
# Docker 빌드 및 실행
docker build -t mcp-korea-weather .
docker run --rm -p 8080:8080 \
  -e KMA_SERVICE_KEY=*** \
  -e KMA_API_BASE_URL=https://apis.data.go.kr/1360000/VilageFcstInfoService_2.0 \
  mcp-korea-weather

# 상태 확인
curl -s http://127.0.0.1:8080/health
```

## 필요 키 · 환경변수

| 환경변수 | 발급처 | 필수 |
|---------|--------|------|
| `KMA_SERVICE_KEY` | [공공데이터포털](https://www.data.go.kr) (기상청 단기예보) | ✅ |
| `KMA_API_BASE_URL` | 기상청 API 베이스 URL (예: `.../VilageFcstInfoService_2.0`) | ✅ |

## 설정 예시

> (README 기반 구성) — HTTP MCP 서버로 :8080에서 동작

```json
{
  "mcpServers": {
    "korea-weather": {
      "url": "http://127.0.0.1:8080"
    }
  }
}
```

> README에는 `claude_desktop_config.json` 예시가 없으며, Docker HTTP 서버(:8080) 실행 방식만 제공된다. 위 스니펫은 HTTP MCP 연결 표준형으로 구성한 것이다.

## 비고

- Cloudflare Workers는 제외된 Smithery-hardened 구성이다.

---
*수집일: 2026-07-03 · 출처: 저장소 README, 소스 코드(src/index.ts, src/mcp.js)*
