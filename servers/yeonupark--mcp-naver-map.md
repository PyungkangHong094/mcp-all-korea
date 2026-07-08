# mcp-naver-map

> **[yeonupark/mcp-naver-map](https://github.com/yeonupark/mcp-naver-map)** · ⭐ 6 · Python · 최근 푸시 2025-04-09 · 카테고리: 🗺 Maps & Address

네이버 클라우드 Geolocation API와 Directions15 API를 연동해 IP 기반 위치 조회와 드라이빙 경로 탐색을 제공하는 MCP 서버.

## 개요

NCP(Naver Cloud Platform)의 Geolocation API와 Directions15 API를 연결하는 Python MCP 서버다. IP 주소를 입력하면 대략적 위경도 위치를 반환하고, 두 지점 간 최적 자동차 경로를 안내한다. `uv`로 실행하며 로컬 stdio로 동작한다.

## 제공 도구

| 도구 | 기능 |
|------|------|
| `get_current_location` | IP 주소 기반 현재 위치(위경도) 조회 (NCP Geolocation API) |
| `get_directions` | 두 지점 간 자동차 경로 탐색 (NCP Directions15 API) |

## 설치

```bash
git clone https://github.com/yeonupark/mcp-naver-map
cd mcp-naver-map
uv sync
```

## 필요 키 · 환경변수

| 환경변수 | 발급처 | 필수 |
|---------|--------|------|
| `NAVER_ACCESS_KEY_ID` | [Naver Cloud Platform](https://www.ncloud.com/) | ✅ |
| `NAVER_SECRET_KEY` | Naver Cloud Platform | ✅ |
| `MAP_CLIENT_ID` | Naver Cloud Platform (Maps) | ✅ |
| `MAP_CLIENT_SECRET` | Naver Cloud Platform (Maps) | ✅ |

## 설정 예시

```json
{
  "mcpServers": {
    "mcp-naver-location": {
      "command": "uv",
      "args": [
        "--directory",
        "/ABSOLUTE/PATH/TO/mcp-naver-map",
        "run", "server"
      ]
    }
  }
}
```

## 비고

- `.env` 파일에 4개 키를 설정한다. Claude Desktop은 터미널에서 실행해야 MCP 서버 연결이 안정적이다(README 안내).
- IP 기반 위치 조회는 IP를 수동 입력해야 한다. 라이선스 파일 존재(MIT, README 명시), GitHub API에는 license 미표기.

---
*수집일: 2026-07-02 · 출처: 저장소 README, 소스 코드(src/server.py)*
