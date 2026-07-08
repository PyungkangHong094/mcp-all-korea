# lease-safe-mcp

> **[hjongc/lease-safe-mcp](https://github.com/hjongc/lease-safe-mcp)** · ⭐ 0 · TypeScript · 최근 푸시 2026-07-06 · 카테고리: 🏠 Real Estate

공공 부동산 데이터와 정부 지침 기반의 전월세 안전도 평가 MCP 서버(전월세안전내비, PlayMCP 호환).

## 개요

한국 전월세·전세·월세·이사 안전을 안내하는 PlayMCP 호환 원격 MCP 서버. 행안부 법정동코드 OpenAPI와 국토부 4종 주택(아파트/연립다세대/단독다가구/오피스텔) 매매·전월세 실거래가 OpenAPI를 활용하고, 정부24·RTMS·인터넷등기소·HUG·임대차분쟁조정위 등 공식 지침을 결합한다. 전월세 시장·매매 시장·위험 신호·다음 조치를 한 번에 종합하는 원샷 진단이 대표 도구. Streamable HTTP transport(`POST /mcp`), Stateless, Node.js 20+ / TypeScript.

## 제공 도구

| 도구 | 기능 |
|------|------|
| `assess_lease_safety` | 전월세 안전 종합 진단 (전월세·매매 시장, 위험신호, 조치, 출처 링크) — 대표 도구 |
| `explain_data_availability` | 데이터 조달 가능성 설명 |
| `resolve_legal_dong_code` | 지역명 → 법정동 코드 확인 |
| `compare_rent_market` | 인근 전월세 실거래 비교 |
| `compare_deposit_to_sale_market` | 매매가 대비 보증금 위험 점검 |
| `check_lease_red_flags` | 계약 위험 신호 점검 (법적 결론은 내리지 않음) |
| `build_move_in_protection_plan` | 이사 보호 절차 계획 (전입신고·확정일자·임대차신고) |
| `prepare_contract_questions` | 계약 전 질문 준비 |
| `route_official_help` | 공식 문의처 연결 |
| `explain_dispute_prevention` | 분쟁 예방 설명 |

## 설치

```bash
npm ci --ignore-scripts
npm run build
MCP_ALLOWED_HOSTS=127.0.0.1,localhost npm start
```

MCP 엔드포인트: `http://127.0.0.1:3000/mcp` (Dockerfile 포함, PlayMCP KC Git 소스 빌드 지원)

## 필요 키 · 환경변수

| 환경변수 | 발급처 / 용도 | 필수 |
|---------|--------------|------|
| `DATA_GO_KR_SERVICE_KEY` | [공공데이터포털](https://www.data.go.kr) (API 백엔드 도구 필수) | ✅ |
| `MCP_ALLOWED_HOSTS` | DNS rebinding 보호용 허용 호스트 | 프로덕션 필수 |
| `MCP_AUTH_TOKEN` | Bearer 토큰(16자 이상) | 프로덕션 필수 |
| `MCP_MAX_BODY_BYTES` · `MCP_RATE_LIMIT_PER_MINUTE` · `PUBLIC_DATA_TIMEOUT_MS` | 요청 크기·레이트리밋·타임아웃 튜닝 | ❌ |

## 설정 예시

```json
{
  "mcpServers": {
    "lease-safe": {
      "url": "http://127.0.0.1:3000/mcp"
    }
  }
}
```
*(README 기반 구성 — 프로덕션은 `Authorization: Bearer <MCP_AUTH_TOKEN>` 필요)*

## 비고

- `DATA_GO_KR_SERVICE_KEY`는 인코딩/디코딩 키 모두 허용. 키 누락·플레이스홀더·형식 오류 시 가짜 샘플 데이터 대신 명확히 실패.
- 서버·도구명에 `kakao` 문자열을 쓰지 않음(PlayMCP 규칙). 도구 정의는 `src/server.ts`에서 확인.

---
*수집일: 2026-07-02 · 출처: 저장소 README, 소스 코드(src/server.ts)*
