# opendart-fss-mcp

> **[hypn4/opendart-fss-mcp](https://github.com/hypn4/opendart-fss-mcp)** · ⭐ N/A (GitHub API rate-limit) · Python · 카테고리: 🏦 Finance & Tax

금융감독원 DART API를 85개 도구로 재무제표·정기보고서·지분공시를 조회하는 MCP 서버입니다.

## 개요

금융감독원(FSS)의 전자공시 시스템 DART의 공개 API인 **OpenDART**를 감싼 MCP 서버다. 공시검색·재무제표·정기보고서·지분공시·주요사항·증권신고서·유틸리티 7개 범주에 걸쳐 85개 도구를 제공한다. 한글 초성(chosung) 매칭과 오타 교정을 포함한 6단계 스마트 기업 검색을 지원하며(`"ㅅㅅㅈㅈ"` → 삼성전자), FastMCP와 opendart-fss 파이썬 SDK 위에 구현됐다. stdio·HTTP(Streamable HTTP) 전송을 모두 지원한다.

## 제공 도구

85개 도구가 7개 범주로 구성(개별 도구명은 README에 전량 나열되지 않음; 범주·접두사·개수는 README 표에 명시).

| 범주 | 접두사 | 개수 | 설명 |
|------|--------|------|------|
| Disclosure | `disclosure_` | 5 | 기업 검색, 공시 목록, 문서 뷰어 |
| Financial | `financial_` | 7 | 재무제표 (단일/다중 계정, XBRL) |
| Report | `report_` | 28 | 정기보고서 주요항목 (보수·자본·임원 등) |
| Shareholding | `shareholder_` | 2 | 대주주·임원 지분 |
| Major Events | `event_` | 36 | M&A, 자본변동, 주식이벤트, 소송 등 |
| Registration | `registration_` | 6 | 증권신고서 상세 |
| Utility | `utility_` | 1 | 현재 날짜/시간 (KST) |

## 설치

Python 3.14 이상, uv 권장. PyPI 설치 또는 소스 빌드.

```bash
uv pip install opendart-fss-mcp
```

## 필요 키 · 환경변수

| 환경변수 | 발급처 | 필수 |
|---------|--------|------|
| `OPENDART_API_KEY` | [OpenDART](https://opendart.fss.or.kr) (무료 발급) | ✅ |
| `OPENDART_MCP_TRANSPORT` | 전송 방식(`stdio`/`http`, 기본 stdio) | ❌ |
| `OPENDART_MCP_HOST` | HTTP 바인드 주소(기본 127.0.0.1) | ❌ |
| `OPENDART_MCP_PORT` | HTTP 포트(기본 8000) | ❌ |
| `OPENDART_MCP_LOG_LEVEL` | 로그 레벨(기본 INFO) | ❌ |

## 설정 예시

```json
{
  "mcpServers": {
    "opendart": {
      "command": "uvx",
      "args": ["--from", "opendart-fss-mcp", "opendart-mcp"],
      "env": { "OPENDART_API_KEY": "your_api_key_here" }
    }
  }
}
```

## 비고

카탈로그 원문 설명은 "84개 도구"이나 README(Features 및 범주 표)는 **85개**로 명시 — README 값을 따름. 도구 범주·개수는 README 표에 명시. 라이선스 MIT.

---
*수집일: 2026-07-03 · 출처: 저장소 README*
