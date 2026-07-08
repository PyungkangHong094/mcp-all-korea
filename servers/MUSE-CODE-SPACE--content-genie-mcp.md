# content-genie-mcp

> **[MUSE-CODE-SPACE/content-genie-mcp](https://github.com/MUSE-CODE-SPACE/content-genie-mcp)** · ⭐ N/A · TypeScript · 최근 푸시 N/A · 카테고리: 🧩 Miscellaneous

네이버·다음·유튜브 등 실시간 트렌드와 100여 개 한국 기념일 DB, 바이럴 점수 예측을 제공하는 한국 크리에이터용 MCP 서버.

## 개요

한국 콘텐츠 크리에이터를 위한 MCP 서버로, 네이버 데이터랩·다음·구글·유튜브(KR)·줌 다섯 소스의 실시간 트렌드를 하나로 통합하고, 100여 개 한국 기념일 + 데이 시리즈 + 절기 이벤트 DB를 얹어 시즌 콘텐츠를 기획하며, 한국 콘텐츠 CTR을 움직이는 구조적 패턴(숫자·괄호·감정 트리거·긴급성 단어)으로 학습된 바이럴 점수 예측기를 제공한다. v2.12.0(2026-05) 리팩터에서 소스별 서킷 브레이커(3회 실패 → 5분 open) + stale-cache 폴백을 도입해 특정 스크레이퍼 장애가 전체를 멈추지 않도록 했다. npm(`content-genie-mcp`) 배포.

## 제공 도구

README에 17개 도구 명시(6개 파일 registry: trends/seo/contentIdeas/viralScoring/competitorAnalysis/koreanEvents).

| 도구 | 기능 |
|------|------|
| `get_korean_trends` | 네이버+다음+구글+유튜브+줌 통합 한국 트렌드 |
| `analyze_news_trends` | 뉴스 트렌드 분석 |
| `analyze_seo_keywords` | SEO 키워드 분석 |
| `generate_hashtag_strategy` | 해시태그 전략 생성 |
| `optimize_title_hashtags` | 제목·해시태그 최적화 |
| `generate_content_ideas` | 콘텐츠 아이디어 생성 |
| `generate_script_outline` | 스크립트 개요 생성 |
| `create_content_calendar` | 한국 기념일 반영 콘텐츠 캘린더 |
| `get_seasonal_content_guide` | 시즌/절기 콘텐츠 가이드 |
| `repurpose_content` | 콘텐츠 재활용/변환 |
| `predict_viral_score` | 바이럴 점수(S~D 등급) 예측 |
| `predict_content_performance` | 콘텐츠 성과 예측 |
| `benchmark_content_performance` | 콘텐츠 성과 벤치마크 |
| `generate_ab_test_variants` | A/B 테스트 변형 생성 |
| `analyze_competitor_content` | 경쟁 콘텐츠 분석 |
| `analyze_influencer_collab` | 인플루언서 협업 분석 |
| `analyze_thumbnail` | 썸네일 분석 |

## 설치

npm 배포. npx로 즉시 실행.

```bash
# Claude Code
claude mcp add content-genie -- npx -y content-genie-mcp
```

## 필요 키 · 환경변수

README 설정 예시에 API 키 요구 없음. 트렌드는 공개 소스 스크레이핑으로 수집. (API 키 불필요)

## 설정 예시

```json
{
  "mcpServers": {
    "content-genie": {
      "command": "npx",
      "args": ["-y", "content-genie-mcp"]
    }
  }
}
```

## 비고

- 도구 목록은 README에 명시(17개, 확인됨).
- MCP Resources 2종(`resource://content-genie/korean-events/{year}`, `resource://content-genie/sources`) + MCP Prompts 2종(`viral-title`, `competitor-analysis`) 제공.
- 소스별 서킷 브레이커 + LRU/TTL 캐시(15분, 100 엔트리) + stale 폴백. Node 20/22 CI, 38개 테스트.

---
*수집일: 2026-07-02 · 출처: 저장소 README*
