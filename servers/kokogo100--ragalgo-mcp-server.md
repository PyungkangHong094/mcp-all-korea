# ragalgo-mcp-server

> **[kokogo100/ragalgo-mcp-server](https://github.com/kokogo100/ragalgo-mcp-server)** · ⭐ N/A (GitHub API 제한) · JavaScript/Node.js · 최근 푸시 N/A · 카테고리: 🏦 Finance & Tax

KOSPI/KOSDAQ·Upbit 대상 점수화된 뉴스 감성·기술적 분석·재무·스냅샷을 제공하는 RAG 기반 한국 금융 MCP 서버입니다.

## 개요

RagAlgo는 AI 에이전트에 "수학적으로 점수화된 금융 컨텍스트"(한국 주식/암호화폐 및 글로벌 시장)를 제공하는 MCP 서버다. 실시간 틱 데이터 대신 일봉 마감(Daily Close) 기준의 확정 데이터와 0~100 점수·구간(Zone)을 제공해 LLM의 환각을 줄이는 것을 목표로 한다. 한국(KOSPI/KOSDAQ)·미국·일본·영국 주식과 암호화폐(Upbit/Binance)를 지원하며, 클라우드(SSE) 모드와 로컬(stdio, npx) 모드를 모두 제공한다.

## 제공 도구

| 도구 | 기능 |
|------|------|
| `get_news_scored` | [권장] AI 감성 점수(-10~+10)가 붙은 뉴스 (노이즈 필터링) |
| `get_news` | [고급] 점수 없는 원본 뉴스 (0점 노이즈 포함) |
| `get_chart_stock` | 글로벌 주식(US/UK/JP/KR) 기술적 분석 (일봉 마감) |
| `get_chart_coin` | 글로벌 암호화폐 기술적 분석 (일봉 마감) |
| `get_snapshots` | 시장 개요(뉴스+차트+추세) 단일 호출 조회 |
| `get_financials` | 기업 재무 (분기/연간) |
| `search_tags` | 종목명(예: "Samsung")을 RagAlgo 태그로 변환 |

## 설치

```bash
# 로컬(stdio) — Node.js 필요
npx -y ragalgo-mcp-server --stdio
```

클라우드 모드는 설치 없이 SSE URL(`https://ragalgo-service-production.up.railway.app/sse`)로 연결한다.

## 필요 키 · 환경변수

| 환경변수 | 발급처 | 필수 |
|---------|--------|------|
| `RAGALGO_API_KEY` | [RagAlgo Dashboard](https://www.ragalgo.com/dashboard) (무료 1,000콜 키) | ✅ |

## 설정 예시

**클라우드 모드** (설치 불필요, 권장)

```json
{
  "mcpServers": {
    "ragalgo": {
      "url": "https://ragalgo-service-production.up.railway.app/sse",
      "env": { "RAGALGO_API_KEY": "YOUR_API_KEY_HERE" }
    }
  }
}
```

**로컬 모드**

```json
{
  "mcpServers": {
    "ragalgo": {
      "command": "npx",
      "args": ["-y", "ragalgo-mcp-server", "--stdio"],
      "env": { "RAGALGO_API_KEY": "YOUR_API_KEY_HERE" }
    }
  }
}
```

## 비고

- 라이선스: MIT.
- 실시간 WebSocket 스트림은 Business Plan 구독자 전용(모니터링용, LLM 추론 컨텍스트 비권장)이다.
- 실습 예제는 별도 저장소 [ragalgo-examples](https://github.com/kokogo100/ragalgo-examples)에서 제공된다.

---
*수집일: 2026-07-03 · 출처: 저장소 README*
