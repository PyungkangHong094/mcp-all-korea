# korea-payments-mcp

> **[junter1989k-ai/korea-payments-mcp](https://github.com/junter1989k-ai/korea-payments-mcp)** · ⭐ N/A · JavaScript/Node · 카테고리: 🏦 Finance & Tax

토스페이먼츠 결제창으로 카드·카카오페이·네이버페이·가상계좌 등 한국 결제를 처리하는 MCP 서버입니다.

## 개요

AI 에이전트(Claude, ChatGPT, Cursor 등)가 한국에서 결제 링크를 생성하고 결제를 처리할 수 있게 해주는 원격 MCP 서버다. v0.1은 토스페이먼츠(Toss Payments) 호스티드 결제창을 경유하며, 카드(카카오페이/네이버페이/토스페이 간편결제 포함), 가상계좌, 계좌이체, 휴대폰 결제를 지원한다. 자금을 보관·이동·저장하지 않는 무상태(stateless) 변환 계층으로, 데이터베이스가 없다. 공식 MCP Registry에 `app.wishpool/korea-payments-mcp`로 등록되어 있다.

## 제공 도구

| 도구 | 기능 |
|------|------|
| `create_payment_link` | KRW 결제 링크 생성(card/virtual_account/transfer/mobile_phone), 호스티드 결제 URL 반환 |
| `query_payment_status` | 상태 조회(READY/IN_PROGRESS/WAITING_FOR_DEPOSIT/DONE/CANCELED/ABORTED/EXPIRED) |
| `confirm_payment` | 구매자 인증 후 결제 승인(토스 필수 단계, 10분 이내) |

## 설치

원격 MCP 서버이므로 설치 없이 URL만 등록한다.

- MCP endpoint: `https://mcp-kr.wishpool.app/mcp` (Streamable HTTP, stateless JSON-RPC)

로컬 개발: `node test/serve.js` (http://localhost:3213/mcp), 런타임 의존성 0개, Node ≥ 18.

## 필요 키 · 환경변수

API 키는 환경변수가 아니라 **요청 헤더**로 전달한다.

| 헤더 | 발급처 | 필수 |
|------|--------|------|
| `x-toss-secret-key` | [토스페이먼츠 개발자센터](https://developers.tosspayments.com) — `test_sk_...` 테스트, `live_sk_...` 운영 | ✅ |

공개 데모 키는 없으며 본인 키를 지참(BYO)해야 한다.

## 설정 예시

```json
{
  "mcpServers": {
    "korea-payments": {
      "url": "https://mcp-kr.wishpool.app/mcp",
      "headers": {
        "x-toss-secret-key": "test_sk_..."
      }
    }
  }
}
```
*(README의 원격 endpoint + 헤더 인증 방식 기반 구성)*

## 비고

- 토스 흐름 3단계: `create_payment_link`(인증) → `query_payment_status`(IN_PROGRESS) → `confirm_payment`(10분 이내 승인, DONE). 가상계좌는 confirm 시 계좌 발급 후 입금 시 DONE.
- 자금·자격증명을 저장하지 않는 무상태 서버. 라이선스 MIT.
- 자매 서버: 대만/일본/인도네시아/인도 결제 MCP.

---
*수집일: 2026-07-03 · 출처: 저장소 README*
