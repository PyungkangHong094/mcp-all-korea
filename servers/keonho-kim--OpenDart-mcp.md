# OpenDart-mcp

> **[keonho-kim/OpenDart-mcp](https://github.com/keonho-kim/OpenDart-mcp)** · ⭐ (rate limit) · Python · 최근 푸시 (rate limit) · 카테고리: 🏦 Finance & Tax

DART API를 MCP로 제공해 기업 기본정보·금융정보 조회·분석을 지원하는 파이썬 MCP 서버입니다.

## 개요

DART(Data Analysis, Retrieval and Transfer System) API를 MCP 기반으로 제공하는 파이썬 라이브러리. 기업 기본정보, 단일회사 전체 재무제표(XBRL 표준 계정, IFRS/GAAP), 재무제표 목록, 부채 총괄 현황, 타법인 출자 현황, 임원·직원 현황, 주식 총수 현황 조회를 지원한다. Docker 이미지로 빌드해 Claude Desktop에서 사용한다.

## 제공 도구

7개 도구 (README "제공 도구 목록(src/dart_mcp/tools)" 기준).

| 도구 | 기능 |
|------|------|
| `find_company_by_name` | 회사 이름으로 회사 정보 검색 |
| `get_company_financial_stmt_list` | 회사의 재무제표 목록 조회 |
| `get_debt_summary` | 부채 총괄 현황 조회 |
| `get_financial_stmt` | 단일회사 전체 재무제표 조회 |
| `get_investment_summary` | 타법인 출자 현황 조회 |
| `get_people_summary` | 임원 및 직원 현황 조회 |
| `get_stock_summary` | 주식 총수 현황 조회 |

## 설치

```bash
git clone https://github.com/keonho-kim/OpenDart-mcp.git
cd OpenDart-mcp
docker build -t opendart-mcp .
```

## 필요 키 · 환경변수

| 환경변수 | 발급처 | 필수 |
|---------|--------|------|
| `DART_API_KEY` | [DART 전자공시시스템](https://dart.fss.or.kr/) 오픈API | ✅ |

## 설정 예시

```json
{
  "mcpServers": {
    "opendart-mcp": {
      "command": "docker",
      "args": ["run", "--rm", "-i", "--net=host",
               "-e", "DART_API_KEY=<PUT_YOUR_DART_API_KEY>", "opendart-mcp"]
    }
  }
}
```

## 비고

- Docker 실행 방식(Docker Desktop 필요).
- 파일명 기준 도구는 `*.py` 형태지만 등록 도구명은 확장자 제외 이름으로 표기.

---
*수집일: 2026-07-03 · 출처: 저장소 README*
