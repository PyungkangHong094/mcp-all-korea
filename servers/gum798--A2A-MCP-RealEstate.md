# A2A-MCP-RealEstate

> **[gum798/A2A-MCP-RealEstate](https://github.com/gum798/A2A-MCP-RealEstate)** · ⭐ 3 · Python · 최근 푸시 2025-09-08 · 카테고리: 🏠 Real Estate

국토부 실거래가와 위치 데이터로 투자가치·삶의질을 종합 평가하는 한국 부동산 추천 MCP 시스템(FastMCP).

## 개요

FastMCP 기반의 한국 부동산 AI 추천 시스템으로, 국토부 공공데이터 실거래가 조회, 지하철·편의시설·공원 등 위치 기반 분석, 그리고 투자가치·삶의질을 가중치로 평가해 사용자 성향별(투자/삶의질/균형) 맞춤 추천을 수행한다. 두 개의 FastMCP 서버(부동산 추천 서버 + 위치 서비스 서버)와 웹 인터페이스(FastAPI)를 함께 제공. Python 3.12+.

## 제공 도구

**Real Estate Recommendation 서버**

| 도구 | 기능 |
|------|------|
| `get_real_estate_data` | 부동산 실거래가 조회 — `lawd_cd`, `deal_ymd`, `property_type` |
| `analyze_location` | 위치 분석 (지하철, 편의시설) — `address`, `lat`, `lon` |
| `evaluate_investment_value` | 투자가치 평가 |
| `evaluate_life_quality` | 삶의질가치 평가 |
| `recommend_property` | 종합 부동산 추천 — `user_preference` 등 |

**Location Service 서버**

| 도구 | 기능 |
|------|------|
| `find_nearest_subway_stations` | 가장 가까운 지하철역 검색 |
| `address_to_coordinates` | 주소 → 좌표 변환 |
| `find_nearby_facilities` | 주변 편의시설 검색 |
| `calculate_location_score` | 위치 점수 계산 |

## 설치

```bash
git clone <repo-url> && cd A2A-MCP-RealEstate
python -m venv venv && source venv/bin/activate
pip install -r requirements.txt
cp .env.example .env   # API 키 입력
python runner.py       # 웹 인터페이스 (http://localhost:8080/web/)
# 또는 MCP 서버 단독 실행
python app/mcp/real_estate_recommendation_mcp.py
```

## 필요 키 · 환경변수

| 환경변수 | 발급처 | 필수 |
|---------|--------|------|
| `MOLIT_API_KEY` | [공공데이터포털](https://www.data.go.kr) 국토부 실거래가 | ✅ |
| `NAVER_CLIENT_ID` | [네이버 클라우드 플랫폼](https://www.ncloud.com) | ✅ |
| `NAVER_CLIENT_SECRET` | 네이버 클라우드 플랫폼 | ✅ |

## 설정 예시

```json
{
  "mcpServers": {
    "korean-realestate": {
      "command": "python",
      "args": ["app/mcp/real_estate_recommendation_mcp.py"],
      "cwd": "/path/to/A2A-MCP-RealEstate"
    }
  }
}
```

## 비고

- 라이선스: MIT. A2A(Agent-to-Agent) 구조로 추천 서버와 위치 서버가 분리됨.
- 투자가치(가격/면적/층/교통/미래가치)와 삶의질(환경/편의/안전/교육/문화)을 가중치로 A+~C 등급화.

---
*수집일: 2026-07-02 · 출처: 저장소 README*
