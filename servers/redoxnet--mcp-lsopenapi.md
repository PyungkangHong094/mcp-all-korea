# mcp-lsopenapi

> **[redoxnet/mcp-lsopenapi](https://github.com/redoxnet/mcp-lsopenapi)** · ⭐ 1 · C# · 최근 푸시 2026-06-09 · 카테고리: 🏦 Finance & Tax

LS증권 OpenAPI 위에 시세·차트·스크리너·포트폴리오를 자연어로 붙이는 MCP 서버.

## 개요

LS증권 OpenAPI를 Claude·ChatGPT·Copilot 등에 연결한다. 국내/해외 시세·10단계 호가, 일·주·월·년·분·틱 차트와 이동평균·RSI·MACD·볼린저밴드, 기업정보(PER/PBR/EPS·분기재무·외국인보유), ETF(NAV·괴리율·구성종목), 시장 스크리너, LS 큐레이션 99개 신호 카탈로그(Q-Click, AND/OR 결합), 지수/업종/테마 컨텍스트, 프로그램매매/기관 수급, LS 실계좌 read-only 조회(v1.6), 로컬 페이퍼 포트폴리오·관심종목을 제공한다. 커지기 쉬운 응답은 요약 우선으로 보내 토큰을 절약한다. v1.0에서 압축된 32-tool `standard` 도구 표면을 고정했다.

## 제공 도구

README(영문)에서 확인된 `ls_*` 도구(발췌):

| 도구 | 기능 |
|------|------|
| `ls_get_quote` · `ls_get_multi_quote` · `ls_get_global_market_quote` · `ls_get_overseas_quote` | 국내/해외 현재가·호가·일괄 비교 |
| `ls_get_chart` · `ls_get_overseas_chart` · `ls_add_indicator` · `ls_reframe_chart` | 차트·기술지표·기간/지표 변경 |
| `ls_search_stock` · `ls_search_overseas_stock` · `ls_get_stock_info` · `ls_get_fundamentals_rank` | 종목 검색·기업 정보·펀더멘털 랭킹 |
| `ls_get_etf_info` · `ls_get_etf_holdings` | ETF 정보·구성종목 |
| `ls_list_screeners` · `ls_run_screener` · `ls_combine_screeners` | 저장 신호(Q-Click) 목록·실행·AND/OR 결합 |
| `ls_get_top_stocks` · `ls_get_high_low_stocks` · `ls_get_market_warnings` | 등락·신고저가·관리/경고 종목 |
| `ls_get_index_quote` · `ls_get_index_history` · `ls_get_industry_indices` · `ls_get_industry_stocks` | 지수·업종 시세/시계열/구성종목 |
| `ls_get_stock_themes` · `ls_get_theme_stocks` | 테마 역조회·테마 종목 |
| `ls_get_program_trading` · `ls_analyze_program_flow` · `ls_get_investor_flow` · `ls_get_market_funds_trend` | 프로그램매매·수급·자금동향 |
| `ls_get_short_selling_trend` · `ls_get_analyst_opinions` · `ls_get_stock_events` | 공매도 추이·투자의견·종목 이벤트 |
| `ls_call_tr` · `ls_describe_tr` · `ls_search_tr` | LS TR 직접 호출·설명·검색 |
| `ls_accounts` · `ls_preview_order` · `ls_trading_policy` · `ls_portfolio_io` · `ls_watchlist` | 실계좌 조회·주문 프리뷰·거래정책·포트폴리오 입출력·관심종목 |

## 설치

```bash
dnx RedoxNet.Mcp.LsOpenApi --yes
```

.NET SDK 10 이상 필요(`dnx` 런처). 첫 실행 시 NuGet(`RedoxNet.Mcp.LsOpenApi`)에서 패키지를 받아 캐시한다.

## 필요 키 · 환경변수

| 환경변수 | 발급처 | 필수 |
|---------|--------|------|
| `LS_APPKEY` | [LS증권 OpenAPI](https://openapi.ls-sec.co.kr) 앱키 | ✅ |
| `LS_APPSECRETKEY` | LS증권 OpenAPI 시크릿키 | ✅ |
| `LS_MARKET` | `real`(기본) 또는 `virtual`(모의계좌) | ❌ |
| `LS_TOOL_PROFILE` · `LSOPENAPI_DB_PATH` · `LS_LOG_LEVEL` | 도구 프로파일·로컬 DB 경로·로그 레벨 | ❌ |

## 설정 예시

```json
{
  "mcpServers": {
    "lsopenapi": {
      "command": "dnx",
      "args": ["RedoxNet.Mcp.LsOpenApi", "--yes"],
      "env": {
        "LS_APPKEY": "...",
        "LS_APPSECRETKEY": "...",
        "LS_MARKET": "real"
      }
    }
  }
}
```

## 비고

- LS 실계좌 조회는 read-only(v1.6)이며 발주는 v1.7 예정. 매 호출마다 LS REST를 다시 쳐 항상 최신(캐시 없음).
- 인라인 차트(Plotly)는 `io.modelcontextprotocol/ui` 캐패빌리티를 지원하는 호스트(Claude Desktop 등)에서만 렌더링.
- 개발자용 상세 문서(환경변수·도구 시그니처·스키마)는 영문 README(`README.en.md`)에 있다.

---
*수집일: 2026-07-02 · 출처: 저장소 README(README.en.md)*
