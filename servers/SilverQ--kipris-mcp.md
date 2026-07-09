# kipris-mcp

> **[SilverQ/kipris-mcp](https://github.com/SilverQ/kipris-mcp)** · ⭐ N/A (GitHub API rate-limit) · JavaScript (Node.js) · 카테고리: 📊 Public Data

KIPRIS Plus Open API로 한국 특허·상표 등 지식재산 데이터를 검색·조회하는 MCP 서버입니다.

## 개요

특허청 KIPRIS Plus Open API를 MCP 도구로 노출하는 stdio 서버다. 자연어를 KIPRIS 검색식으로 변환하거나, 검색식을 직접 입력해 특허·실용신안을 검색하고 출원번호로 서지정보를 단건 조회한다. AND(`*`)/OR(`+`)/NOT(`!`) 연산자와 TI·AP·INV·IPC 등 필드코드를 지원한다. 무료 계정은 월 1,000건·초당 50건 미만 호출 제한이 있다.

## 제공 도구

| 도구 | 기능 |
|------|------|
| `kipris_search` | KIPRIS 검색식(query) 직접 입력 검색 |
| `kipris_item_search` | 필드별 조건 입력 검색 (출원인·발명자·IPC·날짜 등) |
| `kipris_free_search` | 키워드 자유 검색 |
| `kipris_bibliography` | 출원번호로 서지정보 단건 조회 |
| `kipris_build_query` | 자연어 → KIPRIS 검색식 변환 |

## 설치

Node.js 18 이상 필요. 저장소를 클론해 의존성을 설치한 뒤 `src/index.js`를 실행한다.

```bash
cd kipris-mcp
npm install
```

## 필요 키 · 환경변수

| 환경변수 | 발급처 | 필수 |
|---------|--------|------|
| `KIPRIS_API_KEY` | [KIPRIS Plus](https://plus.kipris.or.kr) (회원가입 후 발급) | ✅ |

## 설정 예시

```json
{
  "mcpServers": {
    "kipris": {
      "command": "node",
      "args": ["/절대경로/kipris-mcp/src/index.js"],
      "env": { "KIPRIS_API_KEY": "여기에_발급받은_API키_입력" }
    }
  }
}
```

## 비고

검색 결과 500건 초과 시 경고 메시지 반환. 도구 목록은 README 표에 명시.

---
*수집일: 2026-07-03 · 출처: 저장소 README*
