# kakao-navigation-mcp-server

> **[CaChiJ/kakao-navigation-mcp-server](https://github.com/CaChiJ/kakao-navigation-mcp-server)** · ⭐ 11 · TypeScript · 최근 푸시 2025-09-14 · 카테고리: 🗺 Maps & Address

카카오 모빌리티 및 카카오맵 API를 연동해 위치 검색(지오코딩)과 길찾기를 제공하는 MCP 서버.

## 개요

Model Context Protocol을 준수해 카카오 모빌리티 및 카카오맵 API와 연동되는 서버다. 주소·장소명을 좌표로 변환하고, 좌표/이름 기반 자동차 길찾기(실시간 교통 반영, 미래 시점 예측 포함)를 제공한다. 국내 환경에 적합한 길찾기 서비스를 목표로 하며 Smithery로 배포된다.

## 제공 도구

| 도구 | 기능 |
|------|------|
| `geocode` | 주소를 좌표 정보로 지오코딩 |
| `direction_search_by_names` | 출발지·목적지 주소(이름)로 길찾기 |
| `direction_search_by_coordinates` | 출발지·목적지 좌표로 길찾기 |
| `future_direction_search_by_coordinates` | 미래 특정 시점의 좌표 기반 길찾기 |
| `address_search_by_place_name` | 장소 이름으로 주소 찾기 |

## 설치

```bash
# Smithery를 통한 설치 (배포 정보는 Smithery에서 확인)
npx -y @smithery/cli install @CaChiJ/kakao-navigation-mcp-server --client claude
```
(README 기반 구성 — README는 Smithery 배포를 안내)

## 필요 키 · 환경변수

| 환경변수 | 발급처 | 필수 |
|---------|--------|------|
| 카카오 REST API 키 | [Kakao Developers](https://developers.kakao.com/) (카카오맵 API 활성화 후 REST API 키 발급) | ✅ |

## 설정 예시

```json
{
  "mcpServers": {
    "kakao-navigation": {
      "command": "npx",
      "args": ["-y", "@smithery/cli", "run", "@CaChiJ/kakao-navigation-mcp-server"],
      "env": {
        "KAKAO_REST_API_KEY": "your_rest_api_key"
      }
    }
  }
}
```
(README 기반 구성 — 정확한 환경변수명·실행 방식은 Smithery 페이지 참조)

## 비고

- 배포·최신 업데이트 정보는 Smithery(@CaChiJ/kakao-mobility-mcp-server)에서 제공된다. 라이선스: MIT.

---
*수집일: 2026-07-02 · 출처: 저장소 README*
