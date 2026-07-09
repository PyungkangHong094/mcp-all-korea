# korean-law-mcp

> **[seo-jinseok/korean-law-mcp](https://github.com/seo-jinseok/korean-law-mcp)** · ⭐ N/A (GitHub API 제한) · Python · 최근 푸시 N/A · 카테고리: 📜 Legal & Government

법제처 Open API로 법령·판례·행정규칙·법령해석례·서식을 검색하는 MCP 서버입니다.

## 개요

국가법령정보센터(법제처) Open API에 연동하여 대한민국 법령·판례·행정규칙·자치법규·법령해석례·법률용어·서식을 자연어로 검색·조회하는 MCP 서버다. 특정 조문과 연결된 하위 법령(시행령/시행규칙) 및 참조 조문을 한 번에 탐색하는 그래프 기반 Deep Search(`explore_legal_chain`)와 신구조문 비교, 연혁 조회 등을 지원한다. PyPI 패키지(`korean-law-mcp`)와 Windows 실행 파일로 배포된다.

## 제공 도구

| 도구 | 기능 |
|------|------|
| `search_korean_law` | (필수) 법령·판례·행정규칙 검색 |
| `read_legal_resource` | ID(`statute:12345` 등)로 법령/판례 전문 조회 |
| `explore_legal_chain` | Deep Search — 하위 법령·참조 조문 일괄 탐색·분석 |
| `get_statute_attachments` | 법령 첨부 별표·서식 목록 조회 |
| `search_legal_terms` | 법률 용어 정의 검색 |
| `search_statutory_interpretations` | 법제처 법령 해석례 검색 |
| `get_external_links` | 법령/판례 ID로 국가법령정보센터 공식 URL 생성 |
| `get_article_history` | 법령 연혁(제개정구분·시행일·개정이유) 조회 |
| `compare_old_new` | 신구조문대비 — 개정 전후 비교 |

## 설치

```bash
# uv 자동 설치 (권장)
uvx korean-law-mcp

# 또는 PyPI
pip install korean-law-mcp
```

Windows 사용자는 [Releases](https://github.com/seo-jinseok/korean-law-mcp/releases)의 `korean-law-mcp.exe`를 내려받아 설치 없이 사용할 수 있다.

## 필요 키 · 환경변수

| 환경변수 | 발급처 | 필수 |
|---------|--------|------|
| `OPEN_LAW_ID` | [국가법령정보센터 Open API](https://www.law.go.kr) (무료 신청) | ✅ |

## 설정 예시

```json
{
  "mcpServers": {
    "korean-law": {
      "command": "uvx",
      "args": ["korean-law-mcp"],
      "env": {
        "OPEN_LAW_ID": "여기에_아이디를_넣으세요"
      }
    }
  }
}
```

## 비고

- 단독 실행 시 반응이 없는 것이 정상이며(MCP stdio 통신 대기), MCP Inspector나 Claude Desktop을 통해 실행한다.

---
*수집일: 2026-07-03 · 출처: 저장소 README*
