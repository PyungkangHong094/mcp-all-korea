# korean-dart-mcp

> **[chrisryugj/korean-dart-mcp](https://github.com/chrisryugj/korean-dart-mcp)** · ⭐ (rate limit) · TypeScript/Node · 최근 푸시 (rate limit) · 카테고리: 🏦 Finance & Tax

OpenDART 83개 API를 15개 도구로 묶고 내부자 시그널·회계 리스크·HWP/PDF 첨부 변환까지 제공하는 MCP 서버입니다.

## 개요

금융감독원 [OpenDART](https://opendart.fss.or.kr/) 전자공시 API를 기반으로 하는 MCP 서버 겸 CLI. OpenDART의 83개 엔드포인트를 자주 쓰는 조합 위주 15개 도구로 enum 압축했고, 공시·재무·지분·주요사항·정기보고서·XBRL 조회에 더해 "버핏급 애널리스트 프레임"(내부자 매수/매도 클러스터, 0-100 회계 리스크 스코어, N년 퀄리티 체크리스트)과 HWP/HWPX/PDF 첨부의 마크다운 변환을 제공한다. npm 패키지 `korean-dart-mcp`로 배포되며 Claude Desktop, Cursor, Windsurf, Claude Code에서 사용 가능.

## 제공 도구

15개 도구를 4개 그룹으로 구성 (README 도구 표 기준).

| 도구 | 기능 |
|------|------|
| `resolve_corp_code` | 회사명 → corp_code (SQLite FTS, 전수 11.6만 건) |
| `search_disclosures` | 공시 검색 (page/preset 22종/all_pages 3모드 + 90일 자동분할) |
| `get_company` | 기업 개황 (업종·대표자·설립일) |
| `get_financials` | 재무정보 (summary 주요계정 / full 전체 BS·IS·CF) |
| `download_document` | 공시 원문 → markdown/raw/text |
| `get_xbrl` | XBRL → raw ZIP / markdown / markdown_full |
| `get_periodic_report` | 정기보고서 29 섹션 enum |
| `get_shareholders` | 지배구조 4섹션 병렬 합성 |
| `get_executive_compensation` | 임원 보수 6섹션 |
| `get_major_holdings` | 5%룰(majorstock) + 임원 지분(elestock) |
| `get_corporate_event` | 주요사항보고서 36 이벤트 enum (single/timeline) |
| `insider_signal` | 임원 거래 매수/매도 클러스터 시그널 집계 |
| `disclosure_anomaly` | 회계·거버넌스 리스크 0-100 score + verdict |
| `buffett_quality_snapshot` | N년 ROE/부채/CAGR + 버핏 체크리스트 (corps 배열) |
| `get_attachments` | HWP/HWPX/PDF/DOCX/XLSX 첨부 → 마크다운 (kordoc) |

## 설치

```bash
npx -y korean-dart-mcp setup   # 대화형 마법사 (클라이언트 자동 감지·설정)
```

## 필요 키 · 환경변수

| 환경변수 | 발급처 | 필수 |
|---------|--------|------|
| `OPENDART_API_KEY` | [OpenDART](https://opendart.fss.or.kr/) | ✅ (무료, 일 20,000건) |

## 설정 예시

```json
{
  "mcpServers": {
    "korean-dart": {
      "command": "npx",
      "args": ["-y", "korean-dart-mcp"],
      "env": { "OPENDART_API_KEY": "<YOUR_API_KEY>" }
    }
  }
}
```

## 비고

- Node.js 20.19+ 필요. Windows는 `cmd /c npx` 자동 래핑.
- 자매 프로젝트 [korean-law-mcp](https://github.com/chrisryugj/korean-law-mcp) (법제처 41 API → 15 도구).
- 엔드포인트 1:1 커버리지는 아님 (83→15 압축). 희귀 엔드포인트 직접 호출이 필요하면 RealYoungk/opendart-mcp(83 도구) 등이 더 넓다.

---
*수집일: 2026-07-03 · 출처: 저장소 README*
