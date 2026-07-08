# kakao-real-estate-mcp

> **[choihyeokbin/kakao-real-estate-mcp](https://github.com/choihyeokbin/kakao-real-estate-mcp)** · ⭐ 0 · Python · 최근 푸시 2026-06-24 · 카테고리: 🏠 Real Estate

국토교통부 공공 API와 카카오맵 API를 활용한 실거래가 기반 매물 검색·시세 조회·중간지점 추천 MCP 서버.

## 개요

국토부 실거래가(아파트/오피스텔/연립다세대 매매·전월세)와 카카오맵 API(키워드·카테고리 검색, 좌표→행정구역)를 결합해, 지역·매물종류·거래유형·가격으로 매물을 검색하고 역세권/학군/신축 종합 '살기좋은순' 정렬을 제공한다. 두 지점의 중간지점 매물 추천과 특정 아파트 시세 조회도 지원. Python 3.12, FastMCP, httpx, Docker(카카오클라우드 배포).

## 제공 도구

| 도구 | 기능 |
|------|------|
| `search_property` | 지역·매물종류·거래유형·가격 범위로 실거래 매물 검색 (역세권/학군 정렬, 주변 지하철·학교·어린이집 + 도보시간, 카카오맵 링크) |
| `find_midpoint_property` | 두 직장/학교의 중간 지점 기반 최적 매물 추천 (각 지점까지 거리 표시) |
| `get_market_price` | 특정 아파트 실거래 시세 조회 (평형별 평균/최저/최고, 매매+전월세, 최근 거래 내역) |

## 설치

```bash
cp .env.example .env   # API 키 입력
pip install -e .
python -m kakao_real_estate.server
# 또는 Docker
docker build -t kakao-real-estate-mcp .
docker run -p 8000:8000 kakao-real-estate-mcp
```

MCP 엔드포인트: `http://localhost:8000/mcp`

## 필요 키 · 환경변수

| 환경변수 | 발급처 | 필수 |
|---------|--------|------|
| `DATA_GO_KR_API_KEY` | [공공데이터포털](https://www.data.go.kr) | ✅ |
| `KAKAO_REST_API_KEY` | [카카오 Developers](https://developers.kakao.com) | ✅ |

## 설정 예시

```json
{
  "mcpServers": {
    "kakao-real-estate": {
      "url": "http://localhost:8000/mcp"
    }
  }
}
```
*(README 기반 구성 — HTTP 서버 방식)*

## 비고

- 라이선스: MIT (README 명시).
- 지원 지역: 서울 25개 구, 경기 주요 시, 인천 8개 구, 부산·대구·대전·광주·울산·세종.
- 서버 파일 `src/kakao_real_estate/server.py`에 도구 3개 정의.

---
*수집일: 2026-07-02 · 출처: 저장소 README*
