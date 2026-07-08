# naver_searchad_mcp

> **[alphago2580/naver_searchad_mcp](https://github.com/alphago2580/naver_searchad_mcp)** · ⭐ 0 · Python · 최근 푸시 2026-02-08 · 카테고리: 🔎 Search & Trends

네이버 검색광고 키워드 통계와 입찰가 추정을 제공하며 Claude Desktop DXT 확장을 지원하는 MCP 서버입니다.

## 개요

네이버 검색광고 키워드 통계와 입찰가 추정 도구를 Claude Desktop에서 호출하는 MCP 서버이자 DXT 확장이다. 권장 설치는 DXT(0.2.8+) 방식으로, 호스트 Python이 없거나 임베디드여도 부족한 라이브러리를 사용자 홈 캐시에 자동 설치해 동작한다. 소스/Docker 실행도 지원한다.

## 제공 도구

| 도구 | 기능 |
|------|------|
| `health` | 상태 확인 및 기본 파라미터 확인 |
| `get_keyword_stats` | 키워드 통계 배치 조회 (캐시 옵션) |
| `estimate_average_position_bids` | 평균 노출 위치별 예상 입찰가 추정 |

## 설치

```bash
# 권장: DXT — naver-searchad-0.2.8.dxt 다운로드 후 Claude Desktop Extensions에 추가

# 소스/호스트 Python
git clone https://github.com/alphago2580/naver_searchad_mcp.git
cd naver_searchad_mcp
pip install -e .
python -m naver_searchad_mcp

# Docker
docker build -t naver-searchad-mcp .
```

## 필요 키 · 환경변수

| 환경변수 | 발급처 | 필수 |
|---------|--------|------|
| `NAVER_API_KEY` | [네이버 검색광고](https://searchad.naver.com/) API 사용관리 | ✅ |
| `NAVER_SECRET_KEY` | 네이버 검색광고 (Secret Key) | ✅ |
| `NAVER_CUSTOMER_ID` | 네이버 검색광고 (Customer ID) | ✅ |

DXT 설치 시 UI 필드에 직접 입력, 소스 실행 시 환경변수 또는 `.env` 지원.

## 설정 예시

```json
{
  "mcpServers": {
    "naver-searchad": {
      "command": "python",
      "args": ["-m", "naver_searchad_mcp"],
      "env": {
        "NAVER_API_KEY": "...",
        "NAVER_SECRET_KEY": "...",
        "NAVER_CUSTOMER_ID": "..."
      }
    }
  }
}
```

## 비고

- ⚠️ 라이선스: Proprietary (내부/허가된 사용 범위로 제한) — 공개 재사용 시 라이선스 확인 필요.
- 권장 버전 0.2.8은 Python 3.13 경고를 해소하고 fastmcp/pydantic 자동 부트스트랩을 포함.

---
*수집일: 2026-07-02 · 출처: 저장소 README*
