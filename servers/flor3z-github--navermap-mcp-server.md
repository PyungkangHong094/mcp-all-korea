# navermap-mcp-server

> **[flor3z-github/navermap-mcp-server](https://github.com/flor3z-github/navermap-mcp-server)** · ⭐ 1 · TypeScript · 최근 푸시 2025-12-05 · 카테고리: 🗺 Maps & Address

네이버 지도 API를 MCP 도구로 제공하는 서버 — 지오코딩·역지오코딩·경로 탐색·정적 지도 이미지·사용량 조회.

## 개요

네이버 클라우드 플랫폼(NCP) Maps API를 MCP로 감싼 서버다. 주소↔좌표 변환, 출발지-목적지 경로(거리·시간·통행료·택시비·유류비), 마커·경로가 포함된 정적 지도 이미지 생성, 그리고 Billing API를 통한 월별 사용량·비용 조회를 제공한다. 모든 도구는 읽기 전용(`readOnlyHint: true`)이며 npm 패키지로 배포된다.

## 제공 도구

| 도구 | 기능 |
|------|------|
| `navermap_geocode` | 주소 → 좌표 변환 (지오코딩) |
| `navermap_reverse_geocode` | 좌표 → 주소 변환 (역지오코딩) |
| `navermap_get_directions` | 경로 탐색 (거리·시간·통행료·택시비·유류비) |
| `navermap_get_static_map` | 정적 지도 이미지 생성 (마커·경로) |
| `navermap_get_usage` | 월별 API 사용량·비용·무료 한도 조회 |

## 설치

```bash
npm install -g @flor3z-github/navermap-mcp-server
# 또는
npx -y @flor3z-github/navermap-mcp-server
```

## 필요 키 · 환경변수

| 환경변수 | 발급처 | 필수 |
|---------|--------|------|
| `NAVER_CLIENT_ID` | [Naver Cloud Platform](https://www.ncloud.com/) Maps Application | ✅ |
| `NAVER_CLIENT_SECRET` | Naver Cloud Platform | ✅ |
| `NCLOUD_ACCESS_KEY` | Naver Cloud Platform (Billing API, 사용량 조회용) | ⬜ |
| `NCLOUD_SECRET_KEY` | Naver Cloud Platform (Billing API, 사용량 조회용) | ⬜ |

## 설정 예시

```json
{
  "mcpServers": {
    "navermap": {
      "command": "npx",
      "args": ["-y", "@flor3z-github/navermap-mcp-server"],
      "env": {
        "NAVER_CLIENT_ID": "your_client_id",
        "NAVER_CLIENT_SECRET": "your_client_secret",
        "NCLOUD_ACCESS_KEY": "your_access_key",
        "NCLOUD_SECRET_KEY": "your_secret_key"
      }
    }
  }
}
```

## 비고

- Billing API 키(`NCLOUD_*`)가 없어도 나머지 4개 도구는 정상 작동한다(`navermap_get_usage`만 비활성).
- 무료 한도 초과 시 네이버 클라우드 요금이 부과될 수 있다. 라이선스: Apache-2.0.

---
*수집일: 2026-07-02 · 출처: 저장소 README*
