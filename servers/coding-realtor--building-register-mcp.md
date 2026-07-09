# building-register-mcp

> **[coding-realtor/building-register-mcp](https://github.com/coding-realtor/building-register-mcp)** · ⭐ N/A (GitHub API rate-limit) · Python · 카테고리: 🏠 Real Estate

data.go.kr 건축물대장 API로 표제부·층별·공시가격 등 12개 도구를 제공하는 MCP 서버입니다.

## 개요

공공데이터포털의 **건축HUB 건축물대장정보 서비스** API를 감싼 로컬 MCP 서버다. 건축물대장 표제부·총괄표제부·기본개요·층별개요·전유부·전유공용면적·주택가격(공시가격)·오수정화시설·부속지번·지역지구구역을 조회하는 12개 도구를 제공하며, `smart_building_lookup`이 일반/집합건축물을 자동 판별한다. 주소로 시군구·법정동 코드를 먼저 검색한 뒤 건축물 정보를 조회하는 흐름이다.

## 제공 도구

| 도구 | 기능 |
|------|------|
| `smart_building_lookup` | 스마트 조회 — 일반/집합건축물 자동 판별 |
| `search_bjdong_code` | 지역명으로 시군구코드·법정동코드 검색 |
| `get_building_title_info` | 표제부 (대지면적, 건축면적, 용적률 등) |
| `get_building_recap_title_info` | 총괄표제부 |
| `get_building_basis_ouln_info` | 기본개요 |
| `get_building_floor_ouln_info` | 층별개요 |
| `get_building_expos_info` | 전유부 (동/호 정보) |
| `get_building_expos_pubuse_area_info` | 전유공용면적 |
| `get_building_house_price_info` | 주택가격 (공시가격) |
| `get_building_wclf_info` | 오수정화시설 |
| `get_building_atch_jibun_info` | 부속지번 |
| `get_building_jijigu_info` | 지역지구구역 |

## 설치

[uv](https://docs.astral.sh/uv/) 설치 후 저장소를 클론해 `data-go-mcp-building-register` 엔트리포인트로 실행한다.

```bash
git clone https://github.com/coding-realtor/building-register-mcp.git
cd building-register-mcp
```

## 필요 키 · 환경변수

| 환경변수 | 발급처 | 필수 |
|---------|--------|------|
| `BUILDING_REGISTER_API_KEY` | [공공데이터포털 건축HUB 건축물대장정보 서비스](https://www.data.go.kr/data/15044713/openapi.do) | ✅ |

## 설정 예시

```json
{
  "mcpServers": {
    "building-register": {
      "command": "uv",
      "args": ["run", "--directory", "/path/to/building-register-mcp", "data-go-mcp-building-register"],
      "env": { "BUILDING_REGISTER_API_KEY": "your_api_key_here" }
    }
  }
}
```

## 비고

README에 영어/한국어 병기. 도구 목록은 README 표에 명시.

---
*수집일: 2026-07-03 · 출처: 저장소 README*
