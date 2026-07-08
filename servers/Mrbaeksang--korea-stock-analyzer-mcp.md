# korea-stock-analyzer-mcp

> **[Mrbaeksang/korea-stock-analyzer-mcp](https://github.com/Mrbaeksang/korea-stock-analyzer-mcp)** · ⭐ 21 · Python · 최근 푸시 2026-07-08 · 카테고리: 🏦 Finance & Tax

한국 주식을 위한 보수적·데이터 정직 원격 MCP 서버.

## 개요

DART 전자공시의 실측 재무제표와 KRX 시세(FinanceDataReader)만으로 한국 상장사를 분석한다. 데이터가 없으면 `null`+사유로 명시(기본값 주입 없음), 단일 목표가 대신 가정이 명시된 3시나리오(비관/중립/낙관) 밸류에이션 범위를 제시하며 매수·매도 권고를 하지 않는다. FastMCP 3 stateless 아키텍처(Railway 배포)로, `tools/`는 등록만·`services/`는 외부 API+캐싱·`analysis/`는 순수 계산 함수로 계층 분리한다. 모든 응답에 데이터 기준일(`as_of`)과 출처(`data_source`)가 붙는다.

## 제공 도구

| 도구 | 기능 | 주요 파라미터 |
|------|------|--------------|
| `search_company` | 종목명/코드로 상장사 검색 (KOSPI·KOSDAQ) | `query` |
| `get_quote` | 시세·시가총액·52주 고저·거래량 + 시총 정합성 검사 | `ticker` |
| `get_financials` | 실측 연간 재무제표 + 수익성·안정성·성장성·현금흐름 비율 | `ticker`, `years` (2–10) |
| `get_valuation` | PER/PBR 멀티플 + 3시나리오 가치 범위 (가정 명시) | `ticker` |
| `get_risk_flags` | 재무 적신호 6종 + 최근 공시 위험 키워드 | `ticker`, `disclosure_days` |

## 설치

원격 HTTP(권장, 배포된 서버 URL 하나면 됨):

```bash
claude mcp add --transport http korea-stock https://korea-stock-analyzer-mcp-production.up.railway.app/mcp
```

## 필요 키 · 환경변수

호스팅된 원격 서버 사용 시 **API 키 불필요**(공개 데이터만 제공).

직접 배포(self-host) 시:

| 환경변수 | 발급처 | 필수 |
|---------|--------|------|
| `DART_API_KEY` | [opendart.fss.or.kr](https://opendart.fss.or.kr) 무료 발급(일 20,000건) | ✅ |
| `FASTMCP_HTTP_ALLOWED_HOSTS` | 배포 호스트 화이트리스트 | ✅ |
| `RATE_LIMIT_RPS` / `RATE_LIMIT_BURST` | 레이트 리밋(기본 5/15) | ❌ |

## 설정 예시

```json
{
  "mcpServers": {
    "korea-stock": {
      "type": "http",
      "url": "https://korea-stock-analyzer-mcp-production.up.railway.app/mcp"
    }
  }
}
```

## 비고

- 출력은 공시·시세의 산술 가공 결과이며 투자 자문이 아니다(면책 조항). 시나리오 값은 목표 주가가 아님.
- 재무제표는 연간만 제공(분기 미제공), 시세는 일별 스냅샷(실시간 아님), FCF는 근사치.

---
*수집일: 2026-07-02 · 출처: 저장소 README*
