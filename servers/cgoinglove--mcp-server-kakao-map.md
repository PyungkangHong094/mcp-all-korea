# mcp-server-kakao-map

> **[cgoinglove/mcp-server-kakao-map](https://github.com/cgoinglove/mcp-server-kakao-map)** · ⭐ 16 · TypeScript · 최근 푸시 2025-04-04 · 카테고리: 🗺 Maps & Address

카카오맵 API 키워드 검색으로 대한민국 내 장소를 추천하는 MCP 서버.

## 개요

카카오맵 API 키워드 검색을 활용해 대한민국 내 식당·상점·공공시설·관광명소 등 위치 기반 장소를 추천하는 MCP 서버다. 한국어 쿼리에 최적화되어 있으며 단일 도구를 제공한다.

## 제공 도구

| 도구 | 기능 |
|------|------|
| `kakao_map_place_recommender` | 한국어 키워드로 관련 장소 추천 (카카오맵 키워드 검색). `query` 예: '이태원 맛집', '강남역 근처 카페' |

## 설치

```bash
npx -y mcp-server-kakao-map
```
(README 기반 구성 — README는 환경변수 설정만 명시)

## 필요 키 · 환경변수

| 환경변수 | 발급처 | 필수 |
|---------|--------|------|
| `KAKAO_API_KEY` | [Kakao Developers](https://developers.kakao.com/) (REST API 키, 카카오맵 API 활성화 필요) | ✅ |

## 설정 예시

```json
{
  "mcpServers": {
    "kakao-map": {
      "command": "npx",
      "args": ["-y", "mcp-server-kakao-map"],
      "env": {
        "KAKAO_API_KEY": "your_rest_api_key"
      }
    }
  }
}
```
(README 기반 구성)

## 비고

- `KAKAO_API_KEY`는 카카오 애플리케이션의 **REST API 키**를 사용해야 한다(카카오맵 API 활성화 ON 필요). 라이선스: MIT.

---
*수집일: 2026-07-02 · 출처: 저장소 README*
