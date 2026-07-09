# cafe-mcp

> **[dangamsoft/cafe-mcp](https://github.com/dangamsoft/cafe-mcp)** · ⭐ N/A · 미상 (npm 배포) · 최근 푸시 미상 · 카테고리: 🧩 Miscellaneous

한국 사주명리(오행·격국·용신) 분석을 OWL 온톨로지 기반으로 제공하는 MCP 서버입니다.

## 개요

CAFE(Cross-weighted Analysis of the Five Elements) 엔진의 공개 레이어로, 한국 사주명리학(四柱命理)을 W3C OWL 2 온톨로지(1,711 RDF triples)로 모델링하고, 로컬 stdio MCP 서버에서 무료 만세력(birth-chart) 도구 5종을 제공한다. 서버는 로컬에서 stdio로 실행되며 호스팅된 CAFE 백엔드(`https://24plus.ai.kr/api`의 `/try/panels`)에 요청을 보낸다 — API 키·로컬 엔진·DB 불필요. AI 선정 최종 용신, 전체 리포트, NCODE 성격 프로파일 등 고급 기능은 24Plus 유료 서비스로 여기 노출되지 않는다.

## 제공 도구

무료 5종. 모든 도구는 `birth`(`YYYYMMDDHHMM`)와 `gender`(0=여, 1=남)를 받으며 `name`·`is_lunar`는 선택.

| 도구 | 기능 |
|------|------|
| `saju_chart` | 사주 원국(사주팔자) — 천간·지지, 십성, 신살 |
| `ohaeng_balance` | 오행(五行) 분포 |
| `gyeokguk` | 격국(格局) 구조/패턴 |
| `eumyang_johu` | 음양·조후(陰陽·調候) 균형 |
| `yongshin_candidates` | 고전 5종 용신(用神) 후보(격국·억부·병약·조후·통관) |

## 설치

```json
{
  "mcpServers": {
    "cafe-mcp": {
      "command": "npx",
      "args": ["-y", "@dangamsoft/cafe-mcp"]
    }
  }
}
```

npx로 자동 설치·실행(별도 빌드 불필요).

## 필요 키 · 환경변수

API 키 불필요.

| 환경변수 | 발급처 | 필수 |
|---------|--------|------|
| `CAFE_MCP_API_URL` | 커스텀 백엔드 URL (기본 `https://24plus.ai.kr/api`) | ❌ |

## 설정 예시

```json
{
  "mcpServers": {
    "cafe-mcp": {
      "command": "npx",
      "args": ["-y", "@dangamsoft/cafe-mcp"]
    }
  }
}
```

## 비고

- 로컬 stdio 서버가 호스팅된 CAFE 백엔드(24plus.ai.kr)에 의존 — 백엔드가 필요.
- 코드 라이선스 Apache 2.0, 공개 OWL 온톨로지는 CC BY 4.0. CAFE 추론 엔진·ML 가중치·해석 템플릿은 비공개(proprietary).
- 6대 고전(적천수·자평진전·난강망·궁통보감·연해자평·삼명통회) 기반.

---
*수집일: 2026-07-03 · 출처: 저장소 README*
