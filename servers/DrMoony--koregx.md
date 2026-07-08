# koregx

> **[DrMoony/koregx](https://github.com/DrMoony/koregx)** · ⭐ 0 · TypeScript · 최근 푸시 2026-05-11 · 카테고리: 📜 Legal & Government

한국 헬스케어 법령·행정해석·식약처/복지부 행정규칙·HIRA 결정을 통합 조회하는 웹 서비스 겸 MCP 서버.

## 개요

KoRegX는 한국 헬스케어 규제 정보를 교차 연결한 오픈소스 도구다. 5개 데이터셋을 연결한다: 헬스케어 법령(약사법·의료기기법·첨단재생의료법 등 29개 본법+시행령+시행규칙, 1,746 조문), 법제처 행정해석 83건, 식약처·복지부 행정규칙 124건, HIRA 약평위/암질심 결정 20건(2024–2025). 핵심 가치는 "이 법조항이 어떻게 해석됐고 어떤 고시로 구체화됐나"를 한 번에 답하는 것으로, 원격 MCP 서버(`https://koregx.vercel.app/api/mcp`, 9개 도구)로 제공된다. Next.js 16 + Postgres + pgvector + Gemini 기반.

## 제공 도구

| 도구 | 기능 |
|------|------|
| `search_law` | 법령 검색(category·agencyName 필터) |
| `search_interpretation` | 법제처 행정해석 검색 ⭐ USP |
| `search_admin_rule` | 행정규칙 검색(agency·ruleType 필터) |
| `search_hira_decision` | HIRA 약평위/암질심 결정 검색 |
| `get_law_article` | 조문 단일 조회 |
| `get_interpretation` | 행정해석 본문 조회 |
| `get_admin_rule` | 행정규칙 본문 조회 |
| `chain_law_lifecycle` | 조문 + 행정해석 + 행정규칙 통합 dossier ⭐ |
| `chain_natural_query` | 자연어 Q&A (Gemini 기반 의미검색 + 인용 검증) |

## 설치

원격 MCP 서버라 설치 불필요 — URL만 등록한다. 로컬 개발 시:

```bash
git clone https://github.com/DrMoony/koregx.git
cd koregx
npm install
cp .env.example .env.local
npx prisma migrate deploy
npm run ingest:law && npm run ingest:hira
npm run dev -- --port 3300
```

## 필요 키 · 환경변수

원격 MCP 사용 시 **API 키 불필요**. 로컬 셀프호스트 시:

| 환경변수 | 발급처 | 필수 |
|---------|--------|------|
| `LAW_OC` | [open.law.go.kr](https://open.law.go.kr) | ✅(로컬) |
| `DATABASE_URL` | [Neon Postgres](https://console.neon.tech) (pgvector) | ✅(로컬) |
| `NEXT_PUBLIC_CLERK_PUBLISHABLE_KEY` / `CLERK_SECRET_KEY` | [Clerk](https://dashboard.clerk.com) | ✅(로컬) |
| `GEMINI_API_KEY` | [Google AI Studio](https://aistudio.google.com/apikey) | ❌(chain_natural_query에만) |

## 설정 예시

```json
{
  "mcpServers": {
    "koregx": {
      "url": "https://koregx.vercel.app/api/mcp"
    }
  }
}
```

claude.ai(Web)는 Settings → Connectors → Add custom connector에 위 URL을 등록한다.

## 비고

- MIT 라이선스. v0.2 LIVE(https://koregx.vercel.app). 약물 catalog·의료 판례는 범위 외.
- 원격 커넥터 방식이라 일반 사용자는 키 없이 즉시 사용 가능.

---
*수집일: 2026-07-02 · 출처: 저장소 README*
