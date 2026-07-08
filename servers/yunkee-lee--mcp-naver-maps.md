# mcp-naver-maps

> **[yunkee-lee/mcp-naver-maps](https://github.com/yunkee-lee/mcp-naver-maps)** · ⭐ 1 · Python · 최근 푸시 2025-05-12 · 카테고리: 🗺 Maps & Address

네이버 지도 API(지오코딩)와 네이버 검색 API(로컬 검색)에 연결하는 MCP 서버.

## 개요

NCP Maps API의 Geocoding과 네이버 개발자 검색 API의 지역(로컬) 검색을 연동하는 Python MCP 서버다. 주소를 좌표로 변환하고, 네이버 로컬 서비스에 등록된 장소를 검색한다. `uv`로 의존성을 관리하고 실행한다.

## 제공 도구

| 도구 | 기능 |
|------|------|
| `geocode` | 입력 주소 관련 주소 정보 검색 (지오코딩, NCP Maps API) |
| `localSearch` | 네이버 로컬 서비스 등록 장소 검색 (네이버 검색 API) |

## 설치

```bash
git clone https://github.com/yunkee-lee/mcp-naver-maps
cd mcp-naver-maps
uv sync
uv run src/mcp_naver_maps
```

## 필요 키 · 환경변수

| 환경변수 | 발급처 | 필수 |
|---------|--------|------|
| `NAVER_MAPS_CLIENT_ID` | [Naver Cloud Platform](https://www.ncloud.com/) Maps | ✅ |
| `NAVER_MAPS_CLIENT_SECRET` | Naver Cloud Platform Maps | ✅ |
| `NAVER_CLIENT_API` | [Naver Developers](https://developers.naver.com/) 검색 API | ✅ |
| `NAVER_CLIENT_SECRET` | Naver Developers 검색 API | ✅ |

## 설정 예시

```json
{
  "mcpServers": {
    "naver-maps": {
      "command": "uv",
      "args": [
        "--directory", "/path/to/mcp-naver-maps",
        "run", "src/mcp_naver_maps"
      ],
      "env": {
        "NAVER_MAPS_CLIENT_ID": "your_maps_client_id",
        "NAVER_MAPS_CLIENT_SECRET": "your_maps_client_secret",
        "NAVER_CLIENT_API": "your_search_client_id",
        "NAVER_CLIENT_SECRET": "your_search_client_secret"
      }
    }
  }
}
```
(README 기반 구성)

## 비고

- Python 3.13+ 필요. 환경변수 정확한 이름은 `src/mcp_naver_maps/naver_maps_client.py`에서 확인하도록 README가 안내한다.
- 개발용으로 `mcp dev src/mcp_naver_maps/server.py` 지원. 라이선스: MIT.

---
*수집일: 2026-07-02 · 출처: 저장소 README, 소스 코드(src/mcp_naver_maps/server.py)*
