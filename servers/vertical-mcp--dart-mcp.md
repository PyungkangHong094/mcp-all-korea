# dart-mcp

> **[vertical-mcp/dart-mcp](https://github.com/vertical-mcp/dart-mcp)** · ⭐ N/A · TypeScript · 카테고리: 🏦 Finance & Tax

금감원 DART 전자공시(OpenDART) API로 기업 공시·개황·재무제표를 조회하는 MCP 서버입니다.

## 개요

금융감독원(FSS)이 운영하는 DART 전자공시시스템의 공개 API(OpenDART)를 래핑한 TypeScript MCP 서버다. 기업 공시 검색, 기업 개황, 재무제표(BS/IS/CIS/CF/SCE)를 조회한다. 연결/별도 재무제표(CFS/OFS)와 시장 구분(KOSPI/KOSDAQ/KONEX)을 지원한다.

## 제공 도구

| 도구 | 기능 |
|------|------|
| `search_disclosures` | 날짜 범위·`corp_code`·공시 유형·시장으로 공시 검색 |
| `get_company_info` | 기업 개황(명칭·대표·등록번호·주소·홈페이지·업종·설립일·결산월) 조회 |
| `get_financial_summary` | 연도/보고서별 전체 재무제표 라인아이템 조회(CFS/OFS 선택) |

## 설치

```bash
npx @vertical-mcp/dart-mcp
```

또는 전역 설치: `npm install -g @vertical-mcp/dart-mcp && dart-mcp`

## 필요 키 · 환경변수

| 환경변수 | 발급처 | 필수 |
|---------|--------|------|
| `DART_API_KEY` | [OpenDART opendart.fss.or.kr](https://opendart.fss.or.kr) (40자 `crtfc_key`) | ✅ |

## 설정 예시

```json
{
  "mcpServers": {
    "dart-mcp": {
      "command": "npx",
      "args": ["-y", "@vertical-mcp/dart-mcp"],
      "env": {
        "DART_API_KEY": "your-40-char-key-here"
      }
    }
  }
}
```

## 비고

- OpenDART는 6자리 종목코드가 아닌 8자리 `corp_code`를 사용한다. 전체 매핑은 `/api/corpCode.xml`에서 받을 수 있으며 `list_corp_codes` 도우미는 v0.2 로드맵.
- 레이트 리밋: API 키당 약 20,000회/일(OpenDART 정책).
- FSS와 무관한 비공식 커뮤니티 래퍼. 라이선스 MIT © 2026 Yongbum Kim.

---
*수집일: 2026-07-03 · 출처: 저장소 README*
