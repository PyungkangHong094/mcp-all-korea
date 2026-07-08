# creir-mcp

> **[codivery/creir-mcp](https://github.com/codivery/creir-mcp)** · ⭐ 0 · Rust · 최근 푸시 2026-02-13 · 카테고리: 🔎 Search & Trends

네이버·카카오·구글 검색을 통합하고 날씨·위치·시간 기반 순위화를 수행하는 한국 특화 검색 MCP 서버입니다.

## 개요

LLM용 한국 특화 검색 MCP 서버(Rust)다. 네이버(블로그·뉴스·카페·지식iN·백과), 카카오(웹·로컬), 구글 CSE 결과를 통합하고, 신선도·출처품질·의도매칭·키워드중복·위치근접·날씨연관 등 6개 신호로 문맥 인지 순위화를 수행한다. 한국어 NLP 파이프라인(동의어 확장, 접미사 정규화, 불용어 필터, 토큰화), 위치 인텔리전스(GPS·법정동/시군구 매칭, juso.go.kr 주소 API), KMA 날씨·AirKorea 미세먼지 등 실시간 문맥을 결합한다. L1/L2 캐싱, rate limiting, stdio·Streamable HTTP 이중 전송을 지원한다.

## 제공 도구

| 도구 | 기능 |
|------|------|
| `creir_search` | 네이버·카카오·구글 통합 한국어 웹 검색 (소스 필터, 정렬, 위치·시간 문맥) |
| `creir_local` | 한국 지역 업체·POI 검색 (좌표·반경 기반) |
| `creir_extract` | 한국 웹페이지 본문 추출·정제 |
| `creir_trends` | 한국 트렌드·문맥 추천 (realtime_search / weather_context / seasonal) |

## 설치

```bash
git clone https://github.com/codivery/creir-mcp.git
cd creir-mcp
export NAVER_CLIENT_ID=your_id
export NAVER_CLIENT_SECRET=your_secret
export KAKAO_REST_API_KEY=your_key
cargo run                       # stdio (Claude Desktop)
cargo run -- --http --port 8080 # HTTP (MCP Inspector)
```

## 필요 키 · 환경변수

| 환경변수 | 발급처 | 필수 |
|---------|--------|------|
| `NAVER_CLIENT_ID` | [네이버 개발자센터](https://developers.naver.com) | ✅ |
| `NAVER_CLIENT_SECRET` | 네이버 개발자센터 | ✅ |
| `KAKAO_REST_API_KEY` | [카카오 개발자](https://developers.kakao.com) | ✅ |

## 설정 예시

```json
{
  "mcpServers": {
    "creir": {
      "command": "cargo",
      "args": ["run", "--manifest-path", "/path/to/creir-mcp/Cargo.toml"],
      "env": {
        "NAVER_CLIENT_ID": "your_id",
        "NAVER_CLIENT_SECRET": "your_secret",
        "KAKAO_REST_API_KEY": "your_key"
      }
    }
  }
}
```

## 비고

- Rust로 구현. Docker 멀티스테이지 빌드(~63MB 이미지) 지원.
- 구글 CSE 사용 시 별도 CSE 키·엔진 ID가 필요할 수 있으나 README에 환경변수 명시는 없음(네이버·카카오 키만 Quick Start에 표기).
- 라이선스: MIT.

---
*수집일: 2026-07-02 · 출처: 저장소 README*
