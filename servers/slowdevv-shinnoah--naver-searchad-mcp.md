# naver-searchad-mcp

> **[slowdevv-shinnoah/naver-searchad-mcp](https://github.com/slowdevv-shinnoah/naver-searchad-mcp)** · ⭐ 0 · (언어 미상) · 최근 푸시 2026-01-12 · 카테고리: 🔎 Search & Trends

네이버 검색광고 API로 키워드 검색량·경쟁강도·연관키워드를 조회하는 MCP 서버입니다.

## 개요

네이버 검색광고 API를 Claude Code/Desktop에서 바로 쓸 수 있게 해주는 MCP 서버다. 시드 키워드로 연관 키워드를 최대 500개 추출하고, PC/모바일 월간 검색량과 경쟁강도(compIdx)·광고경쟁정도(plAvgDepth)를 조회한다. `scope` 프리셋으로 필요한 메타데이터만 선택할 수 있어 SEO 키워드 리서치·광고 캠페인 기획에 활용한다. 리텐션 주식회사가 공개했다.

## 제공 도구

| 도구 | 기능 |
|------|------|
| `get_related_keywords` | 시드 키워드로 연관 키워드·검색량·경쟁강도 조회 (파라미터: `keyword`, `limit` 최대 500, `scope`, `includeTotal`) |

scope 프리셋: `basic`(검색량) / `competition`(경쟁지수, 기본) / `clicks`(클릭수) / `ctr`(CTR) / `full`(전체 필드).

## 설치

```bash
git clone https://github.com/slowdevv-shinnoah/naver-searchad-mcp.git
# node로 cli.js 실행 (아래 설정 참조)
```

## 필요 키 · 환경변수

| 환경변수 | 발급처 | 필수 |
|---------|--------|------|
| `NAVER_ADS_CUSTOMER_ID` | [네이버 검색광고](https://searchad.naver.com/) → 도구 → API 사용관리 | ✅ |
| `NAVER_ADS_API_KEY` | 네이버 검색광고 (API License / Access Key) | ✅ |
| `NAVER_ADS_SECRET_KEY` | 네이버 검색광고 (Secret Key) | ✅ |

## 설정 예시

```json
{
  "mcpServers": {
    "naver-searchad": {
      "command": "node",
      "args": ["/path/to/naver-searchad-mcp/cli.js"],
      "env": {
        "NAVER_ADS_CUSTOMER_ID": "your-customer-id",
        "NAVER_ADS_API_KEY": "your-api-key",
        "NAVER_ADS_SECRET_KEY": "your-secret-key"
      }
    }
  }
}
```

## 비고

- README의 API Reference에 문서화된 도구는 `get_related_keywords` 하나뿐이다 (다른 도구가 있더라도 README에 명시 없음).
- 라이선스: MIT.

---
*수집일: 2026-07-02 · 출처: 저장소 README*
