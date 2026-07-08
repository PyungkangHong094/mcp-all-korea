# naver-land-mcp

> **[kimduksoo/naver-land-mcp](https://github.com/kimduksoo/naver-land-mcp)** · ⭐ 1 · Python · 최근 푸시 2026-03-09 · 카테고리: 🏠 Real Estate

네이버 부동산 비공식 API로 지역·좌표 기반 매물 조회, 단지 정보, 시세 추이를 제공하는 MCP 서버.

## 개요

네이버 부동산의 비공식 API를 활용해 지역 계층 탐색(시도→시군구→읍면동), 좌표 기반 매물 검색(아파트/오피스텔/빌라), 단지별 매물·상세·시세/실거래가 추이, 주변 학군 정보를 제공한다. rate limit에 강건하도록 dual endpoint(`new.land`↔`m.land`) 자동 전환, 302 abuse 감지 backoff, 요청 간 랜덤 딜레이 등 방어 로직을 내장. Python 3.11+, FastMCP.

## 제공 도구

| 도구 | 기능 |
|------|------|
| `search_regions` | 지역 코드 계층 탐색 (시도→시군구→읍면동) |
| `get_region_info` | 지역 좌표 + 매물 클러스터 조회 (rate limit 강건) |
| `get_complexes` | 특정 동의 단지 목록 |
| `search_listings` | 좌표 기반 매물 검색 (가장 안정적) |
| `get_articles` | 단지별 매물 목록 (1페이지) |
| `get_all_articles` | 단지별 매물 전체 (자동 페이징) |
| `get_complex_detail` | 단지 상세 (세대수, 면적, 입주년도, 건설사) |
| `get_price_info` | 시세 / 실거래가 추이 |
| `get_school_info` | 주변 학군 (초/중/고) |

## 설치

```bash
cd naver-land-mcp
uv sync
uv run python -m server
# Claude Code 등록
claude mcp add -s user naver-land -- uv run --directory /path/to/naver-land-mcp python -m server
```

## 필요 키 · 환경변수

API 키 불필요 (네이버 부동산 비공식 API 직접 호출).

## 설정 예시

```json
{
  "mcpServers": {
    "naver-land": {
      "command": "uv",
      "args": ["run", "--directory", "/path/to/naver-land-mcp", "python", "-m", "server"]
    }
  }
}
```

## 비고

- 비공식 API를 사용하므로 네이버 API 변경 시 동작하지 않을 수 있음. 과도한 요청 시 IP 기반 rate limit(302 → `/error/abuse`) 발생 가능.
- 거래유형 코드: 매매 `A1`, 전세 `B1`, 월세 `B2`. 부동산 타입: `APT`/`OPST`/`VL`/`ABYG`/`JGC` (콜론 구분 다중 검색).
- 좌표 기반 검색(`search_listings`)이 가장 안정적. 라이선스: MIT (README 명시).

---
*수집일: 2026-07-02 · 출처: 저장소 README*
