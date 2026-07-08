# kakao-api-mcp-server

> **[jeong-sik/kakao-api-mcp-server](https://github.com/jeong-sik/kakao-api-mcp-server)** · ⭐ 16 · TypeScript · 최근 푸시 2025-04-03 · 카테고리: 🗺 Maps & Address

카카오맵 API와 Daum 검색 API를 연동해 장소 검색·좌표-주소 변환·길찾기·웹/이미지/블로그/카페 검색을 제공하는 MCP 서버.

## 개요

카카오맵 Open API와 Daum 검색 Open API를 MCP로 연결하는 서버다. AI 모델이 카카오맵의 장소 검색·좌표변환·길찾기 기능과 Daum의 웹·이미지·블로그·카페 검색 기능을 활용할 수 있다. 카카오 로그인·메시지 전송 등 사용자 계정 기능은 포함하지 않고 공개 Open API만 사용한다.

## 제공 도구

| 도구 | 기능 |
|------|------|
| `mcp_kakao_map_search_places` | 키워드로 카카오맵 장소 검색 (위치·카테고리·연락처) |
| `mcp_kakao_map_coord_to_address` | 경위도 좌표를 도로명·지번 주소로 변환 |
| `mcp_kakao_map_find_route` | 출발지→목적지 길찾기 (거리·시간·예상 택시요금·교통정보) |
| `mcp_kakao_map_search_web` | Daum 웹 문서 검색 |
| `mcp_kakao_map_search_image` | Daum 이미지 검색 |
| `mcp_kakao_map_search_blog` | Daum 블로그 검색 |
| `mcp_kakao_map_search_cafe` | Daum 카페 검색 |

## 설치

```bash
git clone https://github.com/jeong-sik/kakao-api-mcp-server
# TypeScript 서버 — 빌드/실행 방식은 저장소 참조
```
(README 기반 구성 — README에 표준 설치 명령 미명시)

## 필요 키 · 환경변수

| 환경변수 | 발급처 | 필수 |
|---------|--------|------|
| 카카오 REST API 키 | [Kakao Developers](https://developers.kakao.com/) (앱 생성 후 REST API 키 발급) | ✅ |

## 설정 예시

```json
{
  "mcpServers": {
    "kakao-api": {
      "command": "node",
      "args": ["/path/to/kakao-api-mcp-server/build/index.js"],
      "env": {
        "KAKAO_REST_API_KEY": "your_rest_api_key"
      }
    }
  }
}
```
(README 기반 구성 — 정확한 실행 경로·환경변수명은 저장소 소스 확인 권장)

## 비고

- 카카오 로그인·카카오톡 메시지 등 계정 관련 기능은 미포함(공개 Open API 전용). 라이선스: MIT.

---
*수집일: 2026-07-02 · 출처: 저장소 README*
