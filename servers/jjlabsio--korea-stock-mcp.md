# korea-stock-mcp

> **[jjlabsio/korea-stock-mcp](https://github.com/jjlabsio/korea-stock-mcp)** · ⭐ 153 · TypeScript · 최근 푸시 2026-07-07 · 카테고리: 🏦 Finance & Tax

DART와 KRX 공식 API를 연동한 한국 주식 분석 MCP 서버.

## 개요

DART(전자공시시스템)와 KRX(한국거래소) 공식 API를 통해 공시 검색·공시보고서 원문 파싱·XBRL 재무제표·KRX 일별 주가/종목 기본정보를 조회한다. 사업보고서 등 대용량 XML 문서(1MB 이상)는 목차(TOC)를 먼저 반환하고 `section_id`로 관련 섹션을 선택 조회하는 방식으로 AI 응답 한도를 관리한다.

## 제공 도구

DART (전자공시시스템):

| 도구 | 기능 |
|------|------|
| `get_disclosure_list` | 공시검색 (유형·회사·날짜별) |
| `get_corp_code` | 고유번호 조회 (회사명 또는 종목코드) |
| `get_disclosure` | 공시보고서 원문 파싱 (대용량은 목차→섹션 조회) |
| `get_financial_statement` | XBRL 재무제표 (정기보고서 내 계정과목) |

KRX (한국거래소):

| 도구 | 기능 |
|------|------|
| `get_stock_base_info` | 종목 기본정보 (코스피/코스닥/코넥스) |
| `get_stock_trade_info` | 일별 매매정보 (주가·거래량·시가총액) |
| `get_market_type` | 종목코드로 시장구분 조회 |
| `get_today_date` | 오늘 날짜 조회 |

## 설치

```bash
npx -y korea-stock-mcp@latest
```

## 필요 키 · 환경변수

| 환경변수 | 발급처 | 필수 |
|---------|--------|------|
| `DART_API_KEY` | [OPEN DART](https://opendart.fss.or.kr) 인증키 신청 | ✅ |
| `KRX_API_KEY` | [KRX OPEN API](https://openapi.krx.co.kr) 마이페이지 → API 인증키 신청 | ✅ |

## 설정 예시

```json
{
  "mcpServers": {
    "korea-stock-mcp": {
      "command": "npx",
      "args": ["-y", "korea-stock-mcp@latest"],
      "env": {
        "DART_API_KEY": "<YOUR_DART_API_KEY>",
        "KRX_API_KEY": "<YOUR_KRX_API_KEY>"
      }
    }
  }
}
```

## 비고

- KRX API는 일별매매정보·종목기본정보(유가/코스닥/코넥스 6개 항목)를 각각 이용신청해야 하며 승인까지 약 1일 소요.
- 복잡한 질의는 고유번호 조회 → 공시 목록 → 본문 → 상세 순으로 단계 분할 권장.

---
*수집일: 2026-07-02 · 출처: 저장소 README*
