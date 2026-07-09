# dart-mcp

> **[nss133/dart-mcp](https://github.com/nss133/dart-mcp)** · ⭐ N/A · Python · 카테고리: 🏦 Finance & Tax

OPEN DART(금감원 전자공시) 1차 공시 원본·지분공시·재무제표를 법무 검토용으로 제공하는 MCP 서버입니다.

## 개요

OPEN DART(금융감독원 전자공시)를 MCP 서버로 노출하는 Python(FastMCP) 서버다. 법무·내부통제 검토에 쓰이는 1차 공시 원본(공시서류 원문·지분공시·재무제표)을 도구로 제공한다. 모든 엔드포인트는 OPEN DART 공식 API 경로를 원문 그대로 사용하며, `OPENDART_API_KEY`만 필요한 독립 서버다. 공시 검색으로 `rcept_no`를 얻어 `get_document`로 원문 텍스트를 추출하는 흐름을 지원한다.

## 제공 도구

| 도구 | 엔드포인트 | 기능 |
|------|-----------|------|
| `dart_resolve` | corpCode.xml | 종목코드/회사명/고유번호 해석 |
| `search_disclosures` | list.json | 공시 검색(기업·기간·유형) |
| `get_company` | company.json | 기업개황(대표자·설립·업종 등) |
| `get_document` | document.xml | 공시서류 원문 텍스트 |
| `major_holders` | majorstock.json | 대량보유(5%) 상황보고 |
| `insider_holdings` | elestock.json | 임원·주요주주 소유상황 |
| `financial_statements` | fnlttSinglAcntAll.json | 단일회사 전체 재무제표 |

## 설치

```bash
cd dart_mcp
pip install -e .
cp .env.example .env   # OPENDART_API_KEY 입력
```

Claude Code 등록:

```bash
claude mcp add dart --scope user \
  --env "PYTHONPATH=$(pwd)/src" -- python3 -m dart_mcp.server
```

## 필요 키 · 환경변수

| 환경변수 | 발급처 | 필수 |
|---------|--------|------|
| `OPENDART_API_KEY` | [OPEN DART opendart.fss.or.kr](https://opendart.fss.or.kr) (무료) | ✅ |
| `DART_CACHE_DIR` | corp_code 매핑 캐시 경로(기본 `data/`) | 선택 |

## 설정 예시

```json
{
  "mcpServers": {
    "dart": {
      "command": "python3",
      "args": ["-m", "dart_mcp.server"],
      "env": {
        "PYTHONPATH": "/path/to/dart_mcp/src",
        "OPENDART_API_KEY": "발급받은_키"
      }
    }
  }
}
```
*(README의 `claude mcp add` 명령 기반 구성)*

## 비고

- 공시유형(`kind`): A 정기 · B 주요사항 · C 발행 · D 지분 · E 기타 · F 외부감사. 보고서(`reprt_code`): 11011 사업(연간)·11012 반기·11013 1Q·11014 3Q.
- corp_code 매핑(상장사 ~3,970개)은 최초 1회 다운로드 후 주간 캐시. DART status `013`(데이터 없음)은 정상 처리.
- `get_document`는 본문 텍스트를 추출하며 `max_chars` 초과 시 `truncated=true` 반환.

---
*수집일: 2026-07-03 · 출처: 저장소 README*
