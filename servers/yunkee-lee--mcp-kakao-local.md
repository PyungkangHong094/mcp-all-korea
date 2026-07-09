# mcp-kakao-local

> **[yunkee-lee/mcp-kakao-local](https://github.com/yunkee-lee/mcp-kakao-local)** · ⭐ (조회 실패) · Python · 최근 푸시 (조회 실패) · 카테고리: 🗺 Maps & Address

카카오 로컬 API 및 카카오맵에 연결해 주소 지오코딩·장소 검색·위치 상세정보를 제공하는 MCP 서버입니다.

## 개요

카카오 로컬(Kakao Local) API와 카카오맵에 연결하는 Python MCP 서버다. 주소를 좌표로 변환하고, 키워드·카테고리로 장소를 검색하며, 특정 장소의 상세 정보(이름·주소·리뷰·사진 등)를 조회한다. FastMCP 기반으로 uv로 실행한다.

## 제공 도구

README에는 도구 표가 없어 소스(`src/mcp_kakao_local/server.py`)의 `@mcp.tool` 등록부에서 확인:

| 도구 | 기능 |
|------|------|
| `find_coordinates` | 주어진 주소의 좌표 조회(지오코딩) |
| `search_by_keyword` | 키워드 관련 장소 검색 |
| `search_by_category` | 카테고리 그룹 코드로 장소 검색 |
| `get_place` | 장소 상세(이름·주소·리뷰·사진 등) 조회 |

이 외에 `CategoryGroupCode` MCP 리소스를 제공한다.

## 설치

```bash
uv sync
uv run src/mcp_kakao_local
```

Python 3.13+, uv 필요. 개발 모드는 `mcp dev src/mcp_kakao_local/server.py`.

## 필요 키 · 환경변수

| 환경변수 | 발급처 | 필수 |
|---------|--------|------|
| `REST_API_KEY` | [카카오 개발자센터](https://developers.kakao.com) | ✅ |

프로젝트 루트에 `.env` 파일을 만들어 `REST_API_KEY="YOUR_REST_API_KEY_HERE"`를 지정한다. 정확한 변수명은 저장소의 `src/mcp_kakao_local/kakao_local_client.py`에서 확인하라고 README가 안내한다.

## 설정 예시

```json
{
  "mcpServers": {
    "mcp-kakao-local": {
      "command": "uv",
      "args": ["--directory", "/path/to/mcp-kakao-local", "run", "src/mcp_kakao_local"]
    }
  }
}
```
*(README 기반 구성 — README에는 실행 명령만 있고 클라이언트 설정 스니펫은 제시되지 않음)*

## 비고

- 도구 목록은 README에 명시되어 있지 않아 소스 코드에서 추출했다.

---
*수집일: 2026-07-03 · 출처: 저장소 README, 소스 코드*
