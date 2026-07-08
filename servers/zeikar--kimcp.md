# kimcp

> **[zeikar/kimcp](https://github.com/zeikar/kimcp)** · ⭐ 8 · Python · 최근 푸시 2025-05-15 · 카테고리: 🗺 Maps & Address

네이버·카카오·TMAP 등 국내 주요 API를 LLM에서 사용할 수 있게 하는 MCP 서버 (KiMCP: Korea-integrated MCP).

## 개요

네이버, 카카오, TMAP 같은 국내 API를 LLM 애플리케이션에서 사용하도록 통합한 MCP 서버다. 네이버 블로그·뉴스·카페·지식iN·지역·이미지·쇼핑 검색, 다음 블로그·카페 검색, 카카오맵 장소 검색, 카카오 자동차 길찾기, TMAP 대중교통 길찾기를 제공한다. 입력한 API 키에 해당하는 도구만 활성화된다.

## 제공 도구

README는 기능 목록으로 제공하며, 개별 도구명은 명시하지 않음(기능 기준 정리):

| 기능 | 소스 API |
|------|----------|
| 네이버 블로그 검색 | 네이버 |
| 네이버 뉴스 검색 | 네이버 |
| 네이버 카페 검색 | 네이버 |
| 네이버 지식iN 검색 | 네이버 |
| 네이버 지역 검색 | 네이버 |
| 네이버 이미지 검색 | 네이버 |
| 네이버 쇼핑 검색 (가격 비교) | 네이버 |
| 다음 블로그 검색 | 카카오/다음 |
| 다음 카페 검색 | 카카오/다음 |
| 카카오맵 장소 검색 | 카카오 |
| 자동차 길찾기 | 카카오맵 |
| 대중교통 길찾기 | TMAP |

## 설치

```bash
git clone https://github.com/zeikar/kimcp
cd kimcp
uv sync
uv run mcp install main.py -f .env
```

## 필요 키 · 환경변수

| 환경변수 | 발급처 | 필수 |
|---------|--------|------|
| `NAVER_CLIENT_ID` | [네이버 개발자 센터](https://developers.naver.com/apps/#/register) | ⬜* |
| `NAVER_CLIENT_SECRET` | 네이버 개발자 센터 | ⬜* |
| `KAKAO_REST_API_KEY` | [Kakao Developers](https://developers.kakao.com/console/app) | ⬜* |
| `SK_APP_KEY` | [SK Open API](https://openapi.sk.com/) (TMAP) | ⬜* |

\* 최소 1개 이상 필요. 입력한 키의 도구만 활성화되고, 미입력 API의 도구는 자동 비활성화된다.

## 설정 예시

```json
{
  "mcpServers": {
    "kimcp": {
      "command": "uv",
      "args": ["run", "mcp", "install", "main.py", "-f", ".env"]
    }
  }
}
```
(README 기반 구성 — `uv run mcp install`로 Claude Desktop에 등록)

## 비고

- 로드맵에 기상청(KMA) 통합 예정(개발 중). 라이선스: MIT.

---
*수집일: 2026-07-02 · 출처: 저장소 README*
