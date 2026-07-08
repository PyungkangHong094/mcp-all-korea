# korean-dart-mcp

> **[aesthetic-legalism5470/korean-dart-mcp](https://github.com/aesthetic-legalism5470/korean-dart-mcp)** · ⭐ 3 · TypeScript · 최근 푸시 2026-07-08 · 카테고리: 🏦 Finance & Tax

OpenDART 83개 API를 15개 도구로 묶은 공시·재무·지분·XBRL 분석 MCP 서버 + CLI.

## 개요

금융감독원 OpenDART 전자공시를 기반으로 공시 검색·재무제표·지분·XBRL 데이터를 조회한다. 애널리스트 프레임(내부자 시그널·회계 리스크 스코어·버핏식 퀄리티 체크리스트)과 HWP/PDF 첨부의 마크다운화를 제공한다. `get_xbrl format="markdown_full"`은 presentation/calculation linkbase를 파싱해 전체 계정·계층·합산 검증을 수행하고, `search_disclosures`는 90일 자동분할로 OpenDART 전체시장 3개월 제약을 우회한다.

## 제공 도구

README에서 확인된 15개 도구:

| 도구 | 기능 |
|------|------|
| `resolve_corp_code` | 회사명/종목코드 → corp_code 해석 |
| `get_company` | 기업 개황 조회 |
| `search_disclosures` | 공시 검색(22개 preset, 90일 자동분할) |
| `get_periodic_report` | 정기보고서 주요정보 조회 |
| `get_financials` | 재무 지표(ROE·부채·성장성 등) |
| `get_shareholders` | 주주 현황 |
| `get_major_holdings` | 대량보유 상황 |
| `get_executive_compensation` | 임원 보수 |
| `get_corporate_event` | 주요사항 보고(증자·합병·자기주식 등) |
| `get_xbrl` | XBRL 재무제표(`markdown`/`markdown_full` 포맷) |
| `get_attachments` | 첨부문서 목록/추출(HWP·PDF → 마크다운) |
| `download_document` | 공시 원본 문서 다운로드 |
| `insider_signal` | 임원·대주주 매수/매도 클러스터 시그널 |
| `disclosure_anomaly` | 회계 리스크 0-100 스코어 + verdict |
| `buffett_quality_snapshot` | 5년 퀄리티 5지표 자동 랭킹 |

## 설치

```bash
npx -y korean-dart-mcp setup
```

대화형 마법사가 OpenDART 키 입력·클라이언트(Claude Desktop/Cursor/Claude Code/Windsurf/VS Code/Gemini CLI/Zed/Antigravity) 자동 감지·설정 패치를 수행한다. Node.js 20.19+ 필요. Windows는 `cmd /c npx` 자동 래핑.

## 필요 키 · 환경변수

| 환경변수 | 발급처 | 필수 |
|---------|--------|------|
| OpenDART 인증키 | [opendart.fss.or.kr](https://opendart.fss.or.kr) 무료 발급(일 20,000건) | ✅ |

## 설정 예시

```json
{
  "mcpServers": {
    "korean-dart": {
      "command": "npx",
      "args": ["-y", "korean-dart-mcp"],
      "env": {
        "DART_API_KEY": "<OpenDART_인증키>"
      }
    }
  }
}
```
*(README 기반 구성 — 정확한 환경변수명·인자는 setup 마법사가 자동 설정)*

## 비고

- 자매 프로젝트: korean-law-mcp(법제처 41 API → 15 도구).
- 리서치 보조용이며 투자 판단 책임은 사용자에게 있다. 차트·실시간 주가는 제공하지 않는다.
- v0.9.1 보안 하드닝(ZIP slip/bomb 방어, 재귀 depth 가드 등).

---
*수집일: 2026-07-02 · 출처: 저장소 README*
