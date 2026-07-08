# mcp-korea-tourism-api

> **[harimkang/mcp-korea-tourism-api](https://github.com/harimkang/mcp-korea-tourism-api)** · ⭐ N/A · Python · 최근 푸시 N/A · 카테고리: 🌏 Tourism & Travel

한국관광공사(KTO) TourAPI 기반으로 관광지·행사·숙박·맛집을 검색하는 MCP 서버입니다.

## 개요

한국관광공사 공식 TourAPI를 감싸 축제·사찰·맛집·숙박·쇼핑 정보를 키워드·지역·GPS 좌표로 검색한다. TTL 캐싱·레이트리밋·자동 재시도를 내장하고 영어 등 8개 언어를 지원한다. PyPI 패키지(`mcp-korea-tourism-api`)로 배포되며 stdio·streamable-http·SSE 전송을 지원한다.

## 제공 도구

| 도구 | 기능 |
|------|------|
| `search_tourism_by_keyword` | 키워드로 관광정보 검색 (콘텐츠타입·지역코드 필터) |
| `get_tourism_by_area` | 지역코드 기반 관광정보 조회 (예: 서울='1') |
| `find_nearby_attractions` | GPS 좌표 인근 관광지 검색 (반경·타입 필터) |
| `search_festivals_by_date` | 기간(YYYYMMDD) 내 축제 검색 |
| `find_accommodations` | 호텔·게스트하우스 등 숙박 검색 |
| `get_detailed_information` | Content ID로 상세정보(개요·이용시간·주차 등) 조회 |
| `get_tourism_images` | Content ID로 관광 이미지 URL 조회 |
| `get_area_codes` | 시도·시군구 지역코드 조회 |

## 설치

```bash
# Smithery 자동 설치
npx -y @smithery/cli install @harimkang/mcp-korea-tourism-api --client claude

# uv (로컬)
git clone https://github.com/harimkang/mcp-korea-tourism-api.git
cd mcp-korea-tourism-api
uv sync
uv run -m mcp_tourism.server
```

Docker 이미지 빌드도 지원.

## 필요 키 · 환경변수

| 환경변수 | 발급처 | 필수 |
|---------|--------|------|
| `KOREA_TOURISM_API_KEY` | [공공데이터포털 KTO TourAPI](https://www.data.go.kr/) | ✅ |

언어별로 별도 API 신청 필요(영어 15101753, 일본어 15101760 등).

## 설정 예시

```json
{
  "mcpServers": {
    "korea-tourism": {
      "command": "uv",
      "args": ["run", "-m", "mcp_tourism.server"],
      "env": { "KOREA_TOURISM_API_KEY": "YOUR_KTO_API_KEY" }
    }
  }
}
```

## 비고

MIT License. stdio(기본)·streamable-http·sse 전송을 `--transport` 또는 `MCP_TRANSPORT` 환경변수로 선택. 다국어(영/일/중간체/중번체/러/스/독/프) 지원.

---
*수집일: 2026-07-02 · 출처: 저장소 README*
