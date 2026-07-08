# mcp-get-weather

> **[Kinuk97/mcp-get-weather](https://github.com/Kinuk97/mcp-get-weather)** · ⭐ 0 · TypeScript · 최근 푸시 2025-06-19 · 카테고리: 🌦 Weather

기상청 단기예보 실황 API 기반으로 현재 한국 날씨를 조회하는 MCP 서버입니다.

## 개요

공공데이터포털의 기상청 단기예보 실황(초단기실황) API를 호출해 사용자가 말한 지역의 **현재 시각 날씨**를 응답하는 TypeScript 기반 stdio MCP 서버다. 위경도를 기상청 격자좌표(nx/ny)로 변환한 뒤 실황 데이터를 조회한다. 실황 API만 사용하므로 내일·주간 예보는 지원하지 않고 "지금/현재" 질문에만 답한다.

## 제공 도구

| 도구 | 기능 |
|------|------|
| `get-weather-live` | 위도·경도를 받아 해당 지역의 실시간 현재 날씨(기상청 단기예보 실황)를 조회 |

## 설치

```bash
npm install
npm run dev   # 빌드
```

빌드 후 `build/index.js`를 node로 실행한다.

## 필요 키 · 환경변수

| 환경변수 | 발급처 | 필수 |
|---------|--------|------|
| (없음, 소스에 직접 입력) | [공공데이터포털](https://www.data.go.kr) 기상청 단기예보 서비스 키 | ✅ |

API 키는 환경변수가 아니라 `src/util.ts`의 `API_SERVICE_KEY` 상수에 직접 입력하는 방식이다.

## 설정 예시

```json
{
  "mcpServers": {
    "weather": {
      "command": "node",
      "args": ["/your/source/path/build/index.js"]
    }
  }
}
```

## 비고

- 서비스 키를 소스 파일에 하드코딩하는 구조라 배포 시 주의가 필요하다.
- 실황 API 특성상 현재 시각 날씨만 응답 가능(예보 미지원).

---
*수집일: 2026-07-02 · 출처: 저장소 README, 소스 코드(src/index.ts)*
