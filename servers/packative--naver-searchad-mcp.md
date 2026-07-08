# naver-searchad-mcp

> **[packative/naver-searchad-mcp](https://github.com/packative/naver-searchad-mcp)** · ⭐ 4 · TypeScript · 최근 푸시 2026-06-29 · 카테고리: 🔎 Search & Trends

네이버 검색광고 API로 캠페인·광고그룹·키워드·통계 관리 47개 도구를 제공하는 MCP 서버입니다.

## 개요

네이버 검색광고(SearchAd) API 전체를 포괄하는 47개 도구를 제공하는 MCP 서버다. 캠페인·광고그룹·광고소재·키워드 CRUD, 제외키워드, 광고확장, 키워드 도구(검색량·입찰가 추정), 성과 통계, 비즈머니/예산, 라벨, 비즈니스 채널, 계정·품질지수 관리를 다룬다. `ND-SPACE/naver-searchad-mcp`의 포크로, Packative가 기능을 확장했다. `--ro`/`--rw`/`--rwd` 플래그로 접근 권한을 제어하며 기본값은 읽기 전용이다.

## 제공 도구

47개 도구를 카테고리별로 제공한다. 대표 도구는 다음과 같다.

| 카테고리 | 대표 도구 |
|------|------|
| 캠페인 | `list_campaigns`, `get_campaign`, `create_campaign`, `update_campaign`, `delete_campaign` |
| 광고그룹 | `list_adgroups`, `get_adgroup`, `create_adgroup`, `update_adgroup`, `delete_adgroup` |
| 광고소재 | `list_ads`, `get_ad`, `create_ad`, `update_ad`, `delete_ad` |
| 키워드 | `list_keywords`, `get_keyword`, `create_keyword`, `update_keyword`, `delete_keyword` |
| 제외키워드 | 캠페인/광고그룹 단위 제외키워드 관리 |
| 광고확장 | 사이트링크·콜아웃 등 확장 관리 |
| 키워드 도구 | 키워드 제안·검색량·입찰가 추정 |
| 성과 통계 | 기간별 통계·breakdown·비동기 리포트 |
| 비즈머니 | 계정 잔액·거래내역·비용 |
| 라벨/채널/계정 | 라벨, 비즈니스 채널, 회원정보·품질지수·IP 제외 |

권한 모드: `--ro`(읽기 26개, 기본) / `--rw`(생성·수정 포함 39개) / `--rwd`(삭제 포함 47개).

## 설치

```bash
npm install -g @packative/naver-searchad-mcp
```

## 필요 키 · 환경변수

| 환경변수 | 발급처 | 필수 |
|---------|--------|------|
| `NAVER_API_KEY` | [네이버 검색광고](https://searchad.naver.com/) → 도구 → API 사용관리 | ✅ |
| `NAVER_SIGN_KEY` | 네이버 검색광고 (요청 서명용 시크릿 키) | ✅ |
| `NAVER_CUSTOMER_ID` | 네이버 검색광고 (광고주 Customer ID) | ✅ |

## 설정 예시

```json
{
  "mcpServers": {
    "naver-searchad": {
      "command": "npx",
      "args": ["-y", "@packative/naver-searchad-mcp", "--rw"],
      "env": {
        "NAVER_API_KEY": "your-api-key",
        "NAVER_SIGN_KEY": "your-secret-key",
        "NAVER_CUSTOMER_ID": "your-customer-id"
      }
    }
  }
}
```

## 비고

- Node.js 18 이상 필요. HMAC-SHA256 서명 인증 사용.
- 기본 권한은 읽기 전용이므로 생성·수정·삭제가 필요하면 `--rw`/`--rwd` 플래그를 명시해야 한다.

---
*수집일: 2026-07-02 · 출처: 저장소 README*
