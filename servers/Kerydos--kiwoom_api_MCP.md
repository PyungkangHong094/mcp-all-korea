# kiwoom_api_MCP

> **[Kerydos/kiwoom_api_MCP](https://github.com/Kerydos/kiwoom_api_MCP)** · ⭐ N/A · TypeScript/Node · 카테고리: 🏦 Finance & Tax

키움 REST API 문서를 검색·조회하고 요청 예제 코드를 생성하는 MCP 서버입니다.

## 개요

키움증권 REST API의 문서(`kiwoom_api_docs.txt`)를 로컬에서 검색·조회할 수 있게 해주는 Node.js MCP 서버다. 실제 주문/시세 API를 호출하는 것이 아니라, API ID·이름·카테고리로 문서를 찾고 요청/응답 파라미터와 예제 코드를 제공하는 문서 도우미다. Python/JavaScript/cURL 형식의 요청 예제 코드를 생성한다. Docker 및 Docker Compose로 HTTP/SSE 서버로 실행한다.

## 제공 도구

| 도구 | 기능 |
|------|------|
| `search_kiwoom_api` | 키움 REST API 검색 (`query` 필수, `category`/`subcategory` 선택) |
| `get_kiwoom_api_detail` | 특정 API 상세 조회 (`api_id`, 예: ka10001) |
| `list_kiwoom_apis` | API 목록 조회 (`category` 필터, `limit` 기본 50) |
| `get_kiwoom_api_categories` | 카테고리 목록 조회 |
| `get_kiwoom_request_example` | 요청 예제 코드 생성 (`api_id`, `language`: python/javascript/curl) |

## 설치

Docker 실행:

```bash
docker build -t kiwoom-api-server:latest .
docker run -d --name kiwoom-api-server \
  -p 8082:8082 \
  -e KIWOOM_DOCS_PATH=/app/kiwoom_api_docs.txt \
  -v "$(pwd)/kiwoom_api_docs.txt:/app/kiwoom_api_docs.txt:ro" \
  kiwoom-api-server:latest
```

로컬 개발: `npm install && npm run build && npm start`

## 필요 키 · 환경변수

외부 API 키 불필요(문서 검색 서버). 설정 환경변수만 사용한다.

| 환경변수 | 기본값 | 설명 |
|---------|--------|------|
| `PORT` | `8082` | 서버 포트 |
| `NODE_ENV` | `production` | 실행 환경 |
| `KIWOOM_DOCS_PATH` | `./kiwoom_api_docs.txt` | API 문서 파일 경로 |

## 설정 예시

```json
{
  "mcpServers": {
    "kiwoom-api": {
      "url": "http://localhost:8082/sse"
    }
  }
}
```

## 비고

- SSE 트랜스포트 기반 원격 MCP 서버(`/sse`, `/message`, `/health`, `/` 엔드포인트).
- 실시간 시세·주문이 아닌 키움 API **문서** 검색 용도. 라이선스 MIT.

---
*수집일: 2026-07-03 · 출처: 저장소 README*
