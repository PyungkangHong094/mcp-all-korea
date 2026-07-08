# korea-stats-mcp

> **[Dayoooun/korea-stats-mcp](https://github.com/Dayoooun/korea-stats-mcp)** · ⭐ 11 · TypeScript · 최근 푸시 2026-02-17 · 카테고리: 📊 Public Data

자연어로 KOSIS 통계를 조회하는 MCP 서버 (원격 호스팅 서버 제공).

## 개요

통계청 KOSIS OpenAPI 기반 MCP 서버로, "한국 인구가 몇 명이야?" 같은 자연어 질문에 실시간 공식 통계를 반환한다. 83개 키워드 즉시 조회, 추세 분석, KOSIS 통계표 검색, 지역·항목별 비교를 지원한다. Vercel에 배포된 원격 서버(`https://korea-stats-mcp-yxup.vercel.app/mcp`)를 `mcp-remote`로 바로 연결하거나 로컬 빌드로 실행할 수 있고, Kakao PlayMCP에도 등재되어 있다.

## 제공 도구

README 명시 8개:

| 도구 | 기능 |
|------|------|
| `quick_stats` | 83개 키워드 빠른 조회 (실업률·GDP·미세먼지 등) |
| `quick_trend` | 시계열 추세 분석 |
| `search_statistics` | KOSIS 통계표 키워드 검색 |
| `get_statistics_list` | 주제별/기관별 통계 목록 탐색 |
| `get_statistics_data` | 특정 통계표 데이터 조회 |
| `compare_statistics` | 시점별/항목별 비교 분석 |
| `analyze_time_series` | 상세 시계열 분석 |
| `get_recommended_statistics` | 분야별 추천 통계 |

## 설치

```bash
# 방법1: 원격 서버(설치 없이, 권장)
npx -y mcp-remote https://korea-stats-mcp-yxup.vercel.app/mcp

# 방법2: 로컬 빌드
git clone https://github.com/Dayoooun/korea-stats-mcp.git
cd korea-stats-mcp && pnpm install && pnpm run build   # → dist/index.js
```

## 필요 키 · 환경변수

원격 서버 사용 시 API 키 불필요(서버 측 처리). 로컬 실행 시 KOSIS 키 필요 여부는 README에 명시 없음.

## 설정 예시

```json
{
  "mcpServers": {
    "korea-stats": {
      "command": "npx",
      "args": ["-y", "mcp-remote", "https://korea-stats-mcp-yxup.vercel.app/mcp"]
    }
  }
}
```

## 비고

- 원격(Vercel)·로컬·Kakao PlayMCP 3가지 연결 방식.
- 라이선스: MIT.

---
*수집일: 2026-07-02 · 출처: 저장소 README*
