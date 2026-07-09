# koreanpulse

> **[whdrnr2583-cmd/koreanpulse](https://github.com/whdrnr2583-cmd/koreanpulse)** · ⭐ (rate limit) · Python · 최근 푸시 (rate limit) · 카테고리: 🏦 Finance & Tax

한국 DART 공시·5%룰 외국인 지분 흐름·행동주의 공시를 영어로 번역·제공하는 한국 주식 인텔리전스 MCP 서버입니다.

## 개요

한국 주식(KRX/KOSPI/KOSDAQ) 데이터를 영어로 제공하는 MCP 서버(pre-alpha v0.1.10). DART 전자공시를 실시간 추적하고, 5%룰 외국인 지분 변동과 행동주의 투자자 공시를 분류하며, 16개 산업 뉴스(전자신문·한국경제·Korea Herald·지디넷코리아)를 영어 번역해 제공한다. 매수/매도 추천이 아닌 데이터·정보 제공용. 7개 도구 중 5개 무료 + 2개 유료(행동주의·외국인 5%룰 분류, Solo $29/mo+ 라이선스). 세 가지 연결 모드: 호스팅 원격 MCP(`https://mcp.koreanpulse.dev/mcp`), `pip install koreanpulse` stdio, Smithery 마켓플레이스.

## 제공 도구

7개 도구 (README 도구 표 기준). 무료 5 + 유료 2.

| 도구 | 기능 | 티어 |
|------|------|------|
| `track_korean_filings` | DART 공시 실시간 + 영어 번역/요약 | 무료 |
| `lookup_corp_code` | 한국 회사명 → DART corp code | 무료 |
| `resolve_stock_code` | KRX 6자리 코드 → DART corp 엔트리 | 무료 |
| `search_korean_industry_news` | 전자신문/한국경제/Korea Herald/zdnet RSS를 16개 산업으로 분류 | 무료 |
| `koreanpulse_about` | 서버 정보, 무료/유료 도구 목록 | 무료 |
| `monitor_activist_investors` | 행동주의 5%룰 공시 자동 태깅 (KCGI/Align/Truston/ValueAct/Elliott 등) | 유료 |
| `monitor_foreign_holders` | 외국인 5%룰 공시 (BlackRock/Vanguard/Norges/GIC/Temasek 등) | 유료 |

## 설치

```bash
pip install koreanpulse
# 또는 원격 MCP (설치 불필요): https://mcp.koreanpulse.dev/mcp 를 커스텀 커넥터로 추가
```

## 필요 키 · 환경변수

| 항목 | 발급처 | 필수 |
|------|--------|------|
| `license_key` (유료 2개 도구용) | koreanpulse Cloud (Solo $29/mo+) | 유료 도구만 |
| DART API 키 | — | 불필요 (무료 도구는 서버 공유 키 사용) |

## 설정 예시

```json
{
  "mcpServers": {
    "koreanpulse": {
      "command": "python",
      "args": ["-m", "koreanpulse"]
    }
  }
}
```

원격 MCP: Claude.ai Settings → Connectors에서 `https://mcp.koreanpulse.dev/mcp` 추가. (README 기반 구성 — stdio 예시는 "4-line config" 언급, 정확한 스니펫은 저장소 문서 참조)

## 비고

- Pre-alpha 상태. watchlist 폴링 + 알림 발송은 Q3 2026 예정.
- Read-only, 거래 실행·투자 자문 없음.

---
*수집일: 2026-07-03 · 출처: 저장소 README*
