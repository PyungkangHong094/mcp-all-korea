# dart-mcp-test

> **[2geonhyup/dart-mcp-test](https://github.com/2geonhyup/dart-mcp-test)** · ⭐ N/A · Python · 카테고리: 🏦 Finance & Tax

DART API로 상장기업 재무 데이터를 분석·시각화하는 Claude 확장 MCP 서버입니다.

## 개요

금융감독원 DART 오픈API를 활용해 상장기업의 재무 데이터를 조회·분석하는 Python MCP 서버다. Claude와 함께 주요/상세 재무 분석, 사업부별 매출, 시각화, DCF 등 밸류에이션을 수행할 수 있다. 코스피·코스닥 종목을 대상으로 하며 XBRL 재무제표를 파싱한다. 주가·시가총액이나 해외기업 분석은 지원하지 않는다. 별도 가이드 사이트(https://dart-mcp.vercel.app/)를 제공한다.

## 제공 도구

| 도구 | 기능 |
|------|------|
| `search_disclosure` | 공시 검색 |
| `search_detailed_financial_data` | 상세 재무 데이터 조회(XBRL 기반) |
| `search_business_information` | 사업 정보(사업부문 등) 조회 |
| `search_json_financial_data` | JSON 형식 재무 데이터 조회 |
| `get_current_date` | 현재 날짜 조회 |
| `test_connection_to_dart` | DART API 연결 테스트 |

*도구 목록 출처: 소스 `dart.py`의 `@mcp.tool()` 등록 함수 (README에는 도구명 미명시).*

## 설치

GitHub에서 ZIP 다운로드 후 `dart-mcp` 폴더로 압축 해제하고, `uv`로 실행한다(README 안내 방식).

## 필요 키 · 환경변수

| 환경변수 | 발급처 | 필수 |
|---------|--------|------|
| `DART_API_KEY` | [DART 오픈API opendart.fss.or.kr](https://opendart.fss.or.kr) | ✅ |

## 설정 예시

```json
{
  "mcpServers": {
    "dart-mcp": {
      "command": "uv",
      "args": ["--directory", "/Users/{컴퓨터이름}/Downloads/dart-mcp", "run", "dart.py"],
      "env": {
        "DART_API_KEY": "{DART_API_KEY}"
      }
    }
  }
}
```

## 비고

- 코스피·코스닥 종목만 조회 가능하며 주가·시가총액 등 실시간 정보는 미지원.
- 제공 정보는 실제와 다를 수 있으며 투자 책임은 이용자에게 있음(README 명시).
- 저장소명은 `dart-mcp-test`이나 README/설정은 `dart-mcp` 폴더명 기준.

---
*수집일: 2026-07-03 · 출처: 저장소 README, 소스 코드(dart.py)*
