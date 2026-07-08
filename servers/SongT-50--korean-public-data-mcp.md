# korean-public-data-mcp

> **[SongT-50/korean-public-data-mcp](https://github.com/SongT-50/korean-public-data-mcp)** · ⭐ 1 · Python · 최근 푸시 2026-03-08 · 카테고리: 📊 Public Data

날씨·부동산 실거래가·대기질·경제통계·사업자조회 등 한국 5대 공공데이터를 AI에 연결하는 MCP 서버.

## 개요

공공데이터포털(4개 API), 에어코리아, 한국은행 ECOS를 묶어 자연어로 실시간 데이터를 조회하는 MCP 서버다. 아파트 실거래가(서울 25구 + 주요 도시), 단기 날씨 예보(25개 도시·72시간), 실시간 대기질, 경제통계(금리·물가·환율·코스피 등 8종), 사업자등록번호 상태 조회를 제공한다. Render에 배포된 원격 서버로도 사용 가능하다.

## 제공 도구

| 도구 | 기능 | 출처 |
|------|------|------|
| `check_business_registration` | 사업자등록번호 상태 조회(최대 100건 일괄) | 국세청 |
| `get_real_estate_trades` | 아파트 실거래가 조회 | 국토교통부 |
| `get_weather_forecast` | 단기 날씨 예보(25개 도시·72시간) | 기상청 |
| `get_air_quality` | 실시간 대기질(PM10·PM2.5·오존 등) | 에어코리아 |
| `get_economic_stats` | 경제통계(금리·물가·환율·코스피 등 8종) | 한국은행 ECOS |
| `list_supported_options` | 지원 지역/도시/지표 목록 | — |

## 설치

```bash
git clone https://github.com/SongT-50/korean-public-data-mcp.git
cd korean-public-data-mcp
pip install -r requirements.txt
cp .env.example .env   # API 키 입력
claude mcp add korean-public-data -- python server.py
```

원격(설치 없이): `claude mcp add korean-public-data --transport streamable-http https://korean-public-data-mcp.onrender.com/mcp`

## 필요 키 · 환경변수

| 환경변수 | 발급처 | 필수 |
|---------|--------|------|
| `DATA_GO_KR_API_KEY` | [공공데이터포털](https://www.data.go.kr) | ✅ |
| `ECOS_API_KEY` | [한국은행 ECOS](https://ecos.bok.or.kr) | ✅ |

## 설정 예시

```json
{
  "mcpServers": {
    "korean-public-data": {
      "command": "python",
      "args": ["/path/to/korean-public-data-mcp/server.py"],
      "env": { "DATA_GO_KR_API_KEY": "your_key", "ECOS_API_KEY": "your_ecos_key" }
    }
  }
}
```

## 비고

- 무료 Render 인스턴스는 비활성 시 슬립(첫 요청 30~60초 지연).
- 라이선스: MIT.

---
*수집일: 2026-07-02 · 출처: 저장소 README*
