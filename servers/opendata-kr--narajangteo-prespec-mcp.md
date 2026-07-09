# narajangteo-prespec-mcp

> **[opendata-kr/narajangteo-prespec-mcp](https://github.com/opendata-kr/narajangteo-prespec-mcp)** · ⭐ N/A (GitHub API rate-limit) · TypeScript · 카테고리: 📊 Public Data

나라장터 사전규격정보서비스(data.go.kr) API를 자연어로 검색·조회하는 MCP 서버입니다.

## 개요

공공데이터포털의 **나라장터 사전규격정보서비스** Open API를 감싼 로컬 MCP 서버(npm 패키지 `@opendata-kr/narajangteo-prespec-mcp`). 발주기관이 입찰공고 전 규격서를 사전공개하는 단계(사전규격)를 자연어로 검색·조회한다. 20개 오퍼레이션을 5개 도구로 묶었고, 공사/용역/물품/외자 4개 업무구분을 병렬 검색하며 업무구분 미지정 시 전 구분을 동시 조회한다. 부분 실패 표면화, data.go.kr 에러코드 한국어화, 이중 인코딩 방어 기능을 갖췄다.

## 제공 도구

| 도구 | 기능 |
|------|------|
| `search_prespecs` | 기간/업무구분 기준 사전규격 통합 검색 |
| `search_prespecs_by_institution` | 발주기관별 검색 |
| `search_prespecs_by_product` | 품목별 검색 |
| `search_prespecs_advanced` | 복합 조건 검색 |
| `get_prespec_opinions` | 사전규격등록번호로 규격서 의견 조회 |

## 설치

Node.js 24 이상 필요. npx로 실행한다.

```bash
npx -y @opendata-kr/narajangteo-prespec-mcp@latest
```

## 필요 키 · 환경변수

| 환경변수 | 발급처 | 필수 |
|---------|--------|------|
| `DATA_GO_KR_SERVICE_KEY` | [공공데이터포털](https://www.data.go.kr) 나라장터 사전규격정보서비스 활용신청 후 **Decoding** 서비스키 | ✅ |

## 설정 예시

```json
{
  "mcpServers": {
    "narajangteo-prespec": {
      "command": "npx",
      "args": ["-y", "@opendata-kr/narajangteo-prespec-mcp@latest"],
      "env": { "DATA_GO_KR_SERVICE_KEY": "발급받은_Decoding_키" }
    }
  }
}
```

## 비고

서비스키는 반드시 **Decoding(원본)** 키 사용 — Encoding 키를 넣으면 이중 인코딩으로 인증 오류(코드 30). 도구명은 소스(`src/server.ts` registerTool)에서 확인.

---
*수집일: 2026-07-03 · 출처: 저장소 README, 소스 코드(src/server.ts, src/tools)*
