# mcp-visit-korea

> **[pjookim/mcp-visit-korea](https://github.com/pjookim/mcp-visit-korea)** · ⭐ N/A · TypeScript · 최근 푸시 N/A · 카테고리: 🌏 Tourism & Travel

지역·키워드·위치 기반으로 한국 관광 정보를 조회하는 MCP 서버입니다.

## 개요

한국관광공사 TourAPI를 감싼 경량 MCP 서버(패키지명 `mcp-ktour`). 지역코드 조회, 지역/키워드/위치 기반 관광 검색, 콘텐츠 상세 조회의 3개 도구를 제공한다. TypeScript로 작성되었고 Smithery로 자동 설치할 수 있다.

## 제공 도구

| 도구 | 기능 |
|------|------|
| `get_area_code` | 광역시/도 및 하위 지역 코드 조회 |
| `search_tour_info` | 지역·키워드·위치 기반 관광정보 검색 |
| `get_detail_common` | 관광지·축제·숙박 등 콘텐츠 상세 조회 |

(도구 목록 출처: `index.ts` 소스 확인)

## 설치

```bash
# Smithery 자동 설치
npx -y @smithery/cli install @pjookim/mcp-visit-korea --client claude
```

## 필요 키 · 환경변수

| 환경변수 | 발급처 | 필수 |
|---------|--------|------|
| `TOUR_API_KEY` | [공공데이터포털 TourAPI](https://www.data.go.kr/) | ✅ |

(Smithery 설정 스키마에서는 `tourApiKey`로 입력; 소스는 `TOUR_API_KEY` 환경변수를 읽음. 키 미제공 시 관련 호출 실패)

## 설정 예시

```json
{
  "mcpServers": {
    "mcp-visit-korea": {
      "command": "node",
      "args": ["path/to/mcp-visit-korea/dist/index.js"],
      "env": { "TOUR_API_KEY": "YOUR_TOUR_API_KEY" }
    }
  }
}
```
(README 기반 구성 — README는 Smithery 자동 설치 위주)

## 비고

README가 간결해 상세 설정은 Smithery 페이지 및 소스(`index.ts`)를 참조.

---
*수집일: 2026-07-02 · 출처: 저장소 README, 소스 코드(index.ts, smithery.yaml, package.json)*
