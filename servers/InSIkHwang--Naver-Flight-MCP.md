# Naver-Flight-MCP

> **[InSIkHwang/Naver-Flight-MCP](https://github.com/InSIkHwang/Naver-Flight-MCP)** · ⭐ N/A (GitHub API rate-limit) · TypeScript · 카테고리: 🌏 Tourism & Travel

네이버 항공권 검색 API로 직항·왕복 최저가 항공권 정보를 조회하는 MCP 서버입니다.

## 개요

네이버 항공권 검색 API(`flight-api.naver.com`)의 Server-Sent Events 응답을 처리해 최저가 항공권을 조회하는 MCP 서버다. 성인 1명·직항·이코노미 고정 조건으로 왕복 항공편의 출발/도착 시간, 소요시간, 항공편명, 총요금을 최저가 순 상위 10개로 반환한다. SSE 스트림을 완전히 수집해 가장 많은 데이터가 담긴 응답을 선택하는 방식이다.

## 제공 도구

| 도구 | 기능 |
|------|------|
| `search_naver_flights` | 출발지·도착지 공항코드와 출발일·복귀일로 최저가 항공권 검색 |

입력 파라미터: `departure`(출발 공항코드), `arrival`(도착 공항코드), `departureDate`(YYYY-MM-DD), `returnDate`(YYYY-MM-DD).

## 설치

저장소를 클론해 의존성 설치 후 TypeScript를 빌드하고 `dist/index.js`를 실행한다.

```bash
git clone https://github.com/InSIkHwang/Naver-Flight-MCP.git
cd Naver-Flight-MCP
npm install
npm run build
```

## 필요 키 · 환경변수

API 키 불필요. 설정 예시의 `env`가 비어 있다(`{}`).

## 설정 예시

```json
{
  "mcpServers": {
    "naver-flight": {
      "command": "node",
      "args": ["C:/Users/{사용자명}/naver-flight-mcp/dist/index.js"],
      "env": {}
    }
  }
}
```

## 비고

검색 조건(성인 1명·직항·이코노미)은 고정. 도구명은 소스(`src/index.ts`)에서 확인. 라이선스 MIT.

---
*수집일: 2026-07-03 · 출처: 저장소 README, 소스 코드(src/index.ts)*
