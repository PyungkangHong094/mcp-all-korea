# open-proxy-mcp

> **[MarcoYou/open-proxy-mcp](https://github.com/MarcoYou/open-proxy-mcp)** · ⭐ 4 · Python · 최근 푸시 2026-07-06 · 카테고리: 🏦 Finance & Tax

DART 전자공시를 지분구조·재무·주총안건·리스크 이벤트로 구조화하는 AI 기반 거버넌스 분석 MCP 서버(OpenProxy).

## 개요

OpenProxy MCP는 DART OpenAPI 공시 원문을 AI가 바로 쓸 수 있는 구조화 데이터로 변환해, 지분 구조·배당 이력·주총 안건·경영권 분쟁·재무지표·밸류에이션까지 거버넌스 분석 전반을 수행한다. `company → Meeting/Data/Evidence → Action` 흐름의 총 19개 도구를 제공하며, `fly.dev`에 배포된 **원격(Streamable HTTP) MCP 서버**로 로컬 설치 없이 커넥터 URL로 연결한다. Python 3.10+.

## 제공 도구

19개 도구 (Layer별):

| Layer | 도구 |
|-------|------|
| Company | `company` |
| Meeting | `shareholder_meeting_notice`, `shareholder_meeting_results` |
| Data | `corp_gov_report`, `corporate_restructuring`, `dilutive_issuance`, `dividend`, `financial_metrics`, `valuation`, `ownership_structure`, `corporate_deals`, `order_contracts`, `proxy_contest`, `risk_events`, `treasury_share`, `value_up` |
| Evidence | `evidence` |
| Action | `proxy_advise_before_meeting`, `shareholder_commitment` |

## 설치

로컬 설치 없이 배포된 원격 서버에 커넥터로 연결한다 (Claude 유료 플랜의 커넥터 추가 / ChatGPT / Perplexity):

```
https://open-proxy-mcp.fly.dev/mcp?opendart=발급받은_OpenDART_API_키
```

## 필요 키 · 환경변수

| 키 | 발급처 | 필수 |
|----|--------|------|
| `opendart` (URL 쿼리 파라미터) | [DART OpenAPI](https://opendart.fss.or.kr/) (무료) | ✅ |

> API 키는 채팅창이 아니라 커넥터 설정 화면의 서버 주소 입력칸에만 넣는다.

## 설정 예시

```json
{
  "mcpServers": {
    "open-proxy-mcp": {
      "url": "https://open-proxy-mcp.fly.dev/mcp?opendart=<OpenDART_API_KEY>"
    }
  }
}
```
*(README 기반 구성 — README는 각 AI 서비스의 커넥터 추가 UI 절차를 안내)*

## 비고

- 라이선스: PolyForm Noncommercial 1.0.0 (비상업 용도).
- 모든 응답에 `data.usage` 블록으로 DART API 호출 수·MCP 도구 호출 수를 노출 (분당 1000 한도, 내부 rolling window cap 910).
- `proxy_advise_before_meeting`은 자체 Open Proxy Guideline을 기본 의결권 정책으로 사용.

---
*수집일: 2026-07-02 · 출처: 저장소 README*
