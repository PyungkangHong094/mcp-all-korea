# narajangteo-bid-mcp

> **[opendata-kr/narajangteo-bid-mcp](https://github.com/opendata-kr/narajangteo-bid-mcp)** · ⭐ N/A (GitHub API rate-limit) · TypeScript · 카테고리: 📊 Public Data

나라장터 입찰공고정보서비스(data.go.kr) API로 공공조달 입찰공고를 자연어 검색하는 MCP 서버입니다.

## 개요

공공데이터포털의 **나라장터 입찰공고정보서비스** Open API를 감싼 로컬 MCP 서버(npm 패키지 `@opendata-kr/narajangteo-bid-mcp`). 입찰공고를 자연어로 검색하고 상세·기초금액·참가자격·낙찰방법·변경이력·품목·첨부파일을 조회한다. 공사/용역/물품/외자 4개 업무구분을 병렬 검색(미지정 시 기타 제외 4구분 동시 검색, 기타공고는 `bidKind=etc` 명시)한다. 부분 실패 표면화, data.go.kr 에러코드 한국어화, 이중 인코딩 방어 기능을 갖췄다.

## 제공 도구

| 도구 | 기능 |
|------|------|
| `search_bid_notices` | 기간/업무구분/지역/추정가격 기준 입찰공고 검색 |
| `get_bid_notice` | 입찰공고번호로 공고 상세 조회 |
| `get_bid_basis_amount` | 기초금액 조회 |
| `get_bid_evaluation` | 낙찰(평가) 정보 조회 |
| `get_bid_change_history` | 공고 변경이력 조회 |
| `get_bid_eligibility` | 참가 가능 지역·자격 조회 |
| `get_bid_items` | 공고 품목 조회 |
| `get_bid_attachments` | 첨부파일 목록 조회 |

## 설치

Node.js 24 이상 필요. npx로 실행한다.

```bash
npx -y @opendata-kr/narajangteo-bid-mcp@latest
```

## 필요 키 · 환경변수

| 환경변수 | 발급처 | 필수 |
|---------|--------|------|
| `DATA_GO_KR_SERVICE_KEY` | [공공데이터포털](https://www.data.go.kr) 나라장터 입찰공고정보서비스 활용신청 후 **Decoding** 서비스키 | ✅ |

## 설정 예시

```json
{
  "mcpServers": {
    "narajangteo-bid": {
      "command": "npx",
      "args": ["-y", "@opendata-kr/narajangteo-bid-mcp@latest"],
      "env": { "DATA_GO_KR_SERVICE_KEY": "발급받은_Decoding_키" }
    }
  }
}
```

## 비고

서비스키는 반드시 **Decoding(원본)** 키 사용 — Encoding 키를 넣으면 이중 인코딩으로 인증 오류(코드 30). 도구명은 소스(`src/server.ts` registerTool)에서 확인.

---
*수집일: 2026-07-03 · 출처: 저장소 README, 소스 코드(src/server.ts, src/tools)*
