# kakao-keywordad-mcp

> **[PlatAid/kakao-keywordad-mcp](https://github.com/PlatAid/kakao-keywordad-mcp)** · ⭐ N/A · Python · 최근 푸시 미상 · 카테고리: 🔎 Search & Trends

카카오 키워드광고(검색광고) 캠페인·광고그룹·키워드·성과 리포트를 조회·분석하는 MCP 서버입니다.

## 개요

카카오 키워드광고(검색광고) 오픈 API를 감싸 캠페인·광고그룹·키워드·소재의 조회와 성과 리포트를 제공하는 **읽기 전용** MCP 서버다(생성/삭제 미포함). 자매 프로젝트 `KAKAOMomentMCP`와 동일한 비즈니스 토큰 인증 계층을 공유하며, 검색광고 특화로 키워드 계층과 품질지수(`get_keyword_quality`)가 추가된다. 회사 구성원 다수가 하나의 호스팅 서버(GCP Cloud Run)에 연동해 쓰는 것을 목표로 하며, OAuth 로그인-온-커넥트(호스팅)와 세션 로그인(로컬/stdio) 두 인증 모드를 지원한다. 비공식 프로젝트로 카카오와 무관하다.

## 제공 도구

읽기 툴 21종 + 리소스 2종. 모든 툴의 첫 인자는 `business_token`.

| 도구 | 기능 |
|------|------|
| `get_token_info` | 비즈니스 토큰 정보·접근 가능 광고계정(`ad_account_ids`) 확인 |
| `get_user_info` | 사용자 정보 조회 |
| `list_ad_accounts` | 광고계정 목록 |
| `get_ad_account` | 광고계정 상세 |
| `get_account_balance` | 계정 잔액 |
| `get_biz_right` | 비즈니스 권한 조회 |
| `list_campaigns` / `get_campaign` | 캠페인 목록 / 상세 |
| `list_adgroups` / `get_adgroup` | 광고그룹 목록 / 상세 |
| `list_keywords` / `get_keyword` | 키워드 목록 / 상세 |
| `get_keyword_quality` | 키워드 품질지수 |
| `list_creatives` / `get_creative` | 소재 목록 / 상세 |
| `get_account_performance` | 계정 성과 |
| `get_campaign_performance` | 캠페인 성과 |
| `get_adgroup_performance` | 광고그룹 성과 |
| `get_keyword_performance` | 키워드 성과 |
| `get_creative_performance` | 소재 성과 |
| `get_performance_report` | 통합 리포트(level=AD_ACCOUNT/CAMPAIGN/AD_GROUP/KEYWORD/CREATIVE) |

리소스: `kakao://metric-glossary`, `kakao://report-dimensions`

## 설치

```bash
uv venv --python 3.13 && uv pip install -e ".[dev]"
.venv/bin/kakao-keywordad-mcp   # stdio 서버
```

## 필요 키 · 환경변수

`.env`에는 앱 수준 발급 자격증명만 저장(비즈니스 토큰·광고계정 ID는 런타임 인자로 전달, `.env`에 저장하지 않음).

| 환경변수 | 발급처 | 필수 |
|---------|--------|------|
| `KAKAO_REST_API_KEY` | [카카오 개발자센터](https://developers.kakao.com) (OAuth client_id) | ✅ |
| `KAKAO_BUSINESS_CLIENT_SECRET` | 카카오 비즈니스 인증 Client Secret | ✅ |
| `KAKAO_REDIRECT_URI` | 앱에 등록한 Redirect URI | ✅ |

## 설정 예시

```json
{
  "mcpServers": {
    "kakao-keywordad": {
      "command": "kakao-keywordad-mcp",
      "env": {
        "KAKAO_REST_API_KEY": "...",
        "KAKAO_BUSINESS_CLIENT_SECRET": "...",
        "KAKAO_REDIRECT_URI": "..."
      }
    }
  }
}
```
(README 기반 구성 — README에는 명시적 클라이언트 설정 JSON 없음)

## 비고

- 비공식 프로젝트, 카카오와 무관. 라이선스 MIT.
- 선행조건: 카카오 비즈니스 앱 전환 + 실명확인 + 키워드광고 권한(`keyword_management`) 승인 + Redirect URI 등록.
- README상 "엔드포인트 쿼리 파라미터명·리포트 지표 필드명은 문서 기반 최선 추정, 라이브 검증에서 확정" 명시.
- 호스팅 시 `/mcp` 기본 개방이므로 엔드포인트 URL 비공개 및 접근 통제 권고.

---
*수집일: 2026-07-03 · 출처: 저장소 README*
